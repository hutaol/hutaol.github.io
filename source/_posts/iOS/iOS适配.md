---
title: iOS适配
date: 2023-07-03 22:19:21
tags: iOS
---

## 获取当前控制器

```oc
-(UIViewController *)currentViewController {
    UIWindow *window = [UIApplication sharedApplication].delegate.window;
    NSLog(@"window level: %.0f", window.windowLevel);
    if (window.windowLevel != UIWindowLevelNormal) {
        NSArray *windows = [[UIApplication sharedApplication] windows];
        for (UIWindow * tmpWin in windows) {
            if (tmpWin.windowLevel == UIWindowLevelNormal) {
                window = tmpWin;
                break;
            }
        }
    }
    
    //从根控制器开始查找
    UIViewController *rootVC = window.rootViewController;
    UIViewController *activityVC = nil;
    
    while (true) {
        if ([rootVC isKindOfClass:[UINavigationController class]]) {
            activityVC = [(UINavigationController *)rootVC visibleViewController];
        } else if ([rootVC isKindOfClass:[UITabBarController class]]) {
            activityVC = [(UITabBarController *)rootVC selectedViewController];
        } else if (rootVC.presentedViewController) {
            activityVC = rootVC.presentedViewController;
        }else {
            break;
        }
        rootVC = activityVC;
    }
    
    return activityVC;
}
```

## UIViewController的UIModalPresentationStyle属性

```oc
if (@available(iOS 13.0, *)) { //iOS 13 默认不使用 UIModalPresentationFullScreen 模式
    self.modalPresentationStyle =  UIModalPresentationFullScreen; 
}
```

## UITextField的leftview

> 如果直接给 textfield.leftView 赋值一个 UILabel 对象，他的宽高会被 sizeToFit。解决方法：给label套一层UIView的父视图在设置leftview

## UITextfield修改placeholder

```oc
self.textField.attributedPlaceholder = [[NSAttributedString alloc] initWithString:@"输入" attributes:@{NSForegroundColorAttributeName:[UIColor redColor]}];
```