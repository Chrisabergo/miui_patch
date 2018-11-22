## 联系人
APK位置： `/system/priv-app/Contacts/Contacts.apk`

apktool命令： 
`apktool if framework-res.apk`
`apktool if framework-ext-res.apk`
`apktool if miui.apk`
`apktool if miuisystem.apk`
`apktool d *.apk`

### 移除拨号菜单的充话费、充流量按钮
代码位置： `com/android/contacts/dialer/DialerMenuDialog.smali`
定位代码： 在 `res/values/public.xml` 中分别找到 `dialer_menu_recharge` 、`dialer_menu_mobiledata` 对应的id
```
.method private createMenuItems()V
# 利用 sget-boolean v0, Lcom/winter/mysu;->FALSE:Z 进行跳转，不创建相关菜单

# 移除小红点提示？
.method public static isShowDialerMenuRedDot
.method private static isShowMenuEntryRedDot
# return false
```

### 移除生活黄页的部分广告
代码位置： `com/android/contacts/yellowpage/adapter/YellowPageAdapter.smali`
```
.method public statAdView()V
# return null
```
代码位置： `com/android/contacts/yellowpage/ui/NavigationFragment.smali`
```
.method public static getIsAdOn()Z
# return false
```
