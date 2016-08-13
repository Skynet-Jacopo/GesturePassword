# GesturePassword 是一个Swift的手势密码库
>
```ruby
pod 'GesturePassword'
```



###设置密码
![Alt text](https://github.com/huangboju/GesturePassword/blob/master/Resources/setting.gif)

>

```swift
import GesturePassword
LockManager.showSettingLockControllerIn(self, success: { (controller) in
                            
                        })
```

###验证密码
![Alt text](https://github.com/huangboju/GesturePassword/blob/master/Resources/Verify.gif)

>

```swift
import GesturePassword
LockManager.showVerifyLockControllerIn(self, forget: { (controller) in
                            print("forget")
                            }, success: { (controller) in
                                print("success")
                            }, overrunTimes: { (controller) in
                                print("overrunTimes")
                        })
```

###修改密码
![Alt text](https://github.com/huangboju/GesturePassword/blob/master/Resources/Modify.gif)

>

```swift
import GesturePassword
LockManager.showModifyLockControllerIn(self, success: { (controller) in
                            print("修改成功")
                        })
```

###自定义
######如果你只是需要自定义一点点东西，这样就好了

>

```swift
var options = LockOptions()
        options.passwordKeySuffix = "xiAo_Ju"
        options.arcLineWidht = 1
```

>

######如果你需要大量自定义
```swift
struct YourOptions: LockDataSource, LockDelegate {
    
    init() {}

    /// 选中圆大小比例
    var scale: CGFloat = 0.3 {
        willSet {
            LockManager.options.scale = newValue
        }
    }
 
    /// 选中圆大小的线宽
    var arcLineWidth: CGFloat = 1 {
        willSet {
            LockManager.options.arcLineWidth = newValue
        }
    }

    /// 密码后缀
    var passwordKeySuffix = "" {
        willSet {
            LockManager.options.passwordKeySuffix = newValue
        }
    }


    // MARK: - 设置密码

    /// 最低设置密码数目
    var settingTittle = "设置密码" {
        willSet {
            LockManager.options.settingTittle = newValue
        }
    }
}
  LockManager.options = YourOptions()
```
