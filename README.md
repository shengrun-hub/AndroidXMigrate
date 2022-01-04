# AndroidXMigrate
为了兼容Android 9.0 以上的系统，从1.1.7开始，使用AndroidX，旧版本的SDK迁移到AndroidX可以参考本页面的迁移说明。

# 1、项目根目录下 gradle.properties 文件中添加一行：  
```
android.useAndroidX=true
```
# 2、app/build.gradle 中修改依赖
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
# 3、依赖其他库的可以参照[AndroidX工件映射](https://developer.android.google.cn/jetpack/androidx/migrate/artifact-mappings?hl=zh_cn)进行迁移，不清楚版本的话可以按照以下步骤搜索并添加依赖
(1) Android Studio 快捷键 Ctrl+Shift+Alt+S 打开 Project Structure，快捷键不好使的话也可以在顶部的菜单开：File -> Project Structure...  
然后按照下图标注的步骤添加依赖，第3步点击加号后点击“Library Dependency”
![image](https://user-images.githubusercontent.com/69833675/148007186-d9c1fc30-fea8-4233-af05-3c5e22575947.png)
