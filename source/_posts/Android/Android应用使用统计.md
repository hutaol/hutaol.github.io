---
title: Android应用使用统计
date: 2023-06-29 00:16:52
tags: Android
---

## UsageStatsManager

> Android 5.0以上通过UsageStatsManager类 获取应用使用情况

参考：[Android获取应用使用时长和次数-UsageStatsManager使用](https://blog.csdn.net/weixin_45951701/article/details/117486242)

<!-- more -->

### 1.授权声明

> 在`AndroidManifest.xml`文件中声明权限`uses-permission`

```java
<uses-permission
    android:name="android.permission.PACKAGE_USAGE_STATS"
    tools:ignore="ProtectedPermissions" />
```

### 2.设置授权

```java
if (Build.VERSION.SDK_INT > Build.VERSION_CODES.LOLLIPOP) {
    try {
        startActivity(new Intent(Settings.ACTION_USAGE_ACCESS_SETTINGS));
    } catch (Exception e) {
        Toast.makeText(MainActivity.this, "无法开启允许查看使用情况的应用界面", Toast.LENGTH_LONG).show();
        e.printStackTrace();
    }
}
```

### 使用

```java
UsageStatsManager usm = (UsageStatsManager)getSystemService(Context.USAGE_STATS_SERVICE);

// 一周
Calendar calendar = Calendar.getInstance();
long endTime = calendar.getTimeInMillis();
calendar.add(Calendar.DAY_OF_WEEK, -1);
long startTime = calendar.getTimeInMillis();

long time = System.currentTimeMillis()-24*60*60*1000;
List<UsageStats> list = usm.queryUsageStats(UsageStatsManager.INTERVAL_BEST, startTime, endTime);

```

参数：
第一个参数：间隔类型
`UsageStatsManager.INTERVAL_BEST`
`UsageStatsManager.INTERVAL_DAILY`  按天
`UsageStatsManager.INTERVAL_WEEKLY`  按星期
`UsageStatsManager.INTERVAL_MONTHLY`  按月
`UsageStatsManager.INTERVAL_YEARLY`  按年
第二个参数：开始时间
第三个参数：结束时间

### UsageStats说明

```java
usageStats.getPackageName(); //获取包名
usageStats.getFirstTimeStamp(); //获取第一次运行的时间
usageStats.getLastTimeStamp(); //获取最后一次运行的时间
usageStats.getTotalTimeInForeground(); //获取总共运行的时间

// 获取应用启动次数，UsageStats未提供方法来获取，只能通过反射来拿到
try {
    Field field = usageStats.getClass().getDeclaredField("mLaunchCount");
    int count = (int) field.get(usageStats)
} catch (Exception e) {
    e.printStackTrace();
}
```

> TODO: Android可以，iOS可以吗？
