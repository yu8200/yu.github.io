---
layout: post
title: iOS UI Test
categories: [iOS]
tags: iOS
description: iOS
---

<h3>创建UI Testing</h3>
<h4>集成 UI Testing（如果已有项目不存在UI Testing）</h4>

{% highlight ruby %}

Command + N --> iOS-Test --> iOS UI Testing Bundle --> 右下角Next

{% endhighlight %}

<h3>自动录制</h3>

{% highlight ruby %}

打开DemoUITests目录下的DemoUITests.swift --> 新建方法 -->把光标移动到方法内 -->点击控制台 左边 的红色按钮 --> 项目自动运行
 
 --> 随意点击 --> 方法自动生成代码 --> 点击红色按钮停止
  
   func testEmptyApp() {
       //光标移动到这里 
    }

{% endhighlight %}

<h3>Fastlane snapshot</h3>


{% highlight ruby %}

将SnapshotHelper.swift 拷贝到DemoUITests目录下 --> 替换setUp() --> 在测试UI方法上添加snapshot("")
    override func setUp() {
        super.setUp()

        let app = XCUIApplication()
        setupSnapshot(app)
        app.launch()
    }

     func testEmptyApp() {
        snapshot("0Launch")
        let tabBarsQuery = XCUIApplication().tabBars
        tabBarsQuery.buttons["添加"].tap()
        snapshot("1LandscapeLeft")
        tabBarsQuery.buttons["设置"].tap()
        snapshot("1LandscapeRight")
        tabBarsQuery.buttons["帐号"].tap()
    }

First make sure to have a Snapfile (you get it for free when running fastlane snapshot init)

 打开iTerm 2  进入 项目根目录 --> fastlane snapshot

{% endhighlight %}

<h3>Fastlane Fastfile</h3>


{% highlight ruby %}

lane :screens do
    snapshot
 end

 {% endhighlight %}

<h3>Fastlane Snapfile</h3>


{% highlight ruby %}

# Uncomment the lines below you want to change by removing the # in the beginning


# A list of devices you want to take the screenshots from
 devices([
   "iPhone 6",
#   "iPhone 6 Plus",
#   "iPhone 5",
#   "iPad Pro (12.9 inch)",
#   "iPad Pro (9.7 inch)",
#   "Apple TV 1080p"
 ])

languages([
  "zh-CN"
])

# The name of the scheme which contains the UI Tests
# scheme "PassWordManagerUITests"

# Where should the resulting screenshots be stored?
 output_directory "./screenshots"

 clear_previous_screenshots true # remove the '#' to clear all previously generated screenshots before creating new ones

# Choose which project/workspace to use
# project "./Project.xcodeproj"
 workspace "./PassWordManager.xcworkspace"

# Arguments to pass to the app on launch. See https://github.com/fastlane/snapshot#launch-arguments
# launch_arguments(["-favColor red"])

# For more information about all available options run
# snapshot --help

{% endhighlight %}




<a href="https://github.com/ioRaid/Test/tree/master/ConfigDemo" target="_blank">项目地址</a>


