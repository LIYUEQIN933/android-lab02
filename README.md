# 校园巡检

实验三：Android 工程结构与巡检页面整理

基于 Kotlin + Jetpack Compose 的 Android 应用。在实验二可运行的工程上，把网络测试页整理成校园巡检页面，接入 OkHttp 发起 HTTPS 回显请求，为后续巡检记录保存与联网补传做准备。

## 运行方法

1. 使用 Android Studio 打开本工程，等待 Gradle 同步完成（Sync Project with Gradle Files）。
2. 连接真机（开启 USB 调试）或启动 Android 模拟器。
3. 点击工具栏 Run ▶ 运行，桌面应用名称为"校园巡检"。
4. 应用启动后显示巡检页面，点击"请求 A203 / 请求 A204"按钮，向 httpbin.org 发起 HTTPS 请求，页面显示返回的 HTTP 状态码与参数回显。

## 依赖

- OkHttp 4.12.0 —— 在 `app/build.gradle.kts` 的 `dependencies` 块中声明：
  ```kotlin
  implementation("com.squareup.okhttp3:okhttp:4.12.0")
  ```

## 三个文件职责

| 文件 | 职责 |
| --- | --- |
| `MainActivity.kt` | 系统入口：设置 Compose 内容，安排请求发起与结果更新 |
| `InspectionScreen.kt` | 页面层：显示巡检数据（巡检员、实验室、总数/已检查/未检查）、按钮与回调，计算未检查数量 |
| `InspectionNetwork.kt` | 网络层：创建 OkHttpClient，执行 HTTPS 请求，处理响应与异常 |
