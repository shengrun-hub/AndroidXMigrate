# AndroidXMigrate
为了兼容Android 9.0 以上的系统，[TTC Android BLE SDK](https://github.com/shengrun-hub/TTC_BLE_DEMO-Kotlin)从1.1.7开始，使用AndroidX，旧版本的SDK如果需要迁移到AndroidX可以参考本页面的迁移说明。

## 1、项目根目录下 gradle.properties 文件中添加一行：  
```
android.useAndroidX=true
```
## 2、app/build.gradle 中修改依赖
将原先的 ```implementation files('libs/AndroidBleApi_V1.1.6.jar')``` 替换为 ``` implementation 'com.ttcble.android:blebase:1.1.8' ```  
并添加下面的 androidx 相关的库
```
dependencies {
    implementation fileTree(include: ['*.jar'], dir: 'libs')
    androidTestImplementation('com.android.support.test.espresso:espresso-core:2.2.2', {
        exclude group: 'com.android.support', module: 'support-annotations'
    })
    testImplementation 'junit:junit:4.12'
    implementation 'com.ttcble.android:blebase:1.1.8'
    implementation 'androidx.appcompat:appcompat:1.2.0'
    implementation 'androidx.swiperefreshlayout:swiperefreshlayout:1.2.0-alpha01'
    implementation 'androidx.recyclerview:recyclerview:1.2.0-beta01'
    implementation 'androidx.legacy:legacy-support-v4:1.0.0'
}
```
## 3、其他依赖
(1) Android Studio 快捷键 Ctrl+Shift+Alt+S 打开 Project Structure，快捷键不好使的话也可以在顶部的菜单开：File -> Project Structure...  
然后按照下图标注的步骤添加依赖，第3步点击加号后点击“Library Dependency”
![image](https://user-images.githubusercontent.com/69833675/148007186-d9c1fc30-fea8-4233-af05-3c5e22575947.png)

（2）输入要添加的库的名称（可从[AndroidX工件映射](https://developer.android.google.cn/jetpack/androidx/migrate/artifact-mappings?hl=zh_cn)页面获得），比如要添加下拉刷新库，输入 androidx.swiperefreshlayout:swiperefreshlayout，然后点击右侧的“Search”，搜索结果中选择想要的版本，最新的测试版本、正式版本（版本后面没有字母后缀）都可以，不放心测试版的话就选正式版本吧，选好后点击右下方的“OK”按钮即可。
![image](https://user-images.githubusercontent.com/69833675/148012908-29832a4a-0286-4d2e-8f94-6c3692ce9e77.png)

## 4、通过Make Project检测需要修改的地方
快捷键Ctrl+F9或者点击Android Studio上方的锤子按钮，哪里报错改哪里，直到没有错误为止，即AndroidX迁移完成。  
（1）修改代码：删除显示为红色的 import，根据IDE提示重新导入对应的androidx包下的类；  
（2）修改布局：xml布局文件中使用的控件如果显示红色，选中控件全名（即包括完整的包名），输入相同的控件名称（不包含包名的类名）。根据IDE提示导入androidx包下该控件的全名。
