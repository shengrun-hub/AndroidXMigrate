# AndroidXMigrate
为了兼容Android 9.0 以上的系统，从1.1.7开始，使用AndroidX，旧版本的SDK迁移到AndroidX可以参考本页面的迁移说明。

# 项目根目录下 gradle.properties 文件中添加一行：  
'''
android.useAndroidX=true
'''
# 2、app/build.gradle 中修改依赖  
'''
dependencies {
    implementation fileTree(include: ['*.jar'], dir: 'libs')
    androidTestImplementation('com.android.support.test.espresso:espresso-core:2.2.2', {
        exclude group: 'com.android.support', module: 'support-annotations'
    })
    implementation 'com.android.support:appcompat-v7:28.0.0'
        testImplementation 'junit:junit:4.12'
    implementation files('libs/AndroidBleApi_V1.1.6.jar')
    implementation 'androidx.appcompat:appcompat:1.2.0'
    implementation 'androidx.swiperefreshlayout:swiperefreshlayout:1.2.0-alpha01'
    implementation 'androidx.recyclerview:recyclerview:1.2.0-beta01'
    implementation 'androidx.legacy:legacy-support-v4:1.0.0'
    implementation 'com.ttcble.android:blebase:1.1.8'
}
'''
