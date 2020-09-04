---
layout: post
title: fastlane
categories: [工具]
tags: [工具]
excerpt: 
description: ios持续集成
---
<h3>安装Homebrew</h3>

{% highlight ruby %}

ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

{% endhighlight %}

<h3>安装Ruby</h3>

{% highlight ruby %}

rvm list known

sudo rvm install ruby-2.1.4

{% endhighlight %}


<h3>gem源更换</h3>
<h6>显示当前源</h6>

{% highlight ruby %}

gem sources -l

{% endhighlight %}

<h6>移除当前源</h6>

{% highlight ruby %}

gem sources --remove https://rubygems.org/

{% endhighlight %}

<h6>增加当前源</h6>

{% highlight ruby %}

gem sources -a http://ruby.taobao.org/

{% endhighlight %}


<h6>更新缓存</h6>

{% highlight ruby %}

gem sources -u 

{% endhighlight %}



<h3>安装</h3>

{% highlight ruby %}

sudo gem install -n /usr/local/bin fastlane

{% endhighlight %}



<h3>fastlane工具链</h3>

{% highlight ruby %}

测试
scan => 自动运行测试工具，并且可以生成漂亮的HTML报告

证书，配置文件
cert => 自动创建管理iOS代码签名证书
sigh => sigh是用来创建、更新、下载、修复Provisioning Profile的工具。
pem => 自动生成、更新推送配置文件
match => 一个新的证书和配置文件管理工具。他会所有需要用到的证书传到git私有库上，任何需要配置的机器直接用match同步回来就不用管证书问题了.

截图
snapshot => 用Xcode7推出的UI test功能实现自动化截图    
frameit => 可以把截的图片自动套上一层外边框

编译
gym => Fastlane家族的自动化编译工具，和其他工具配合的非常默契

发布
produce => 如果你的产品还没在iTunes Connect(iTC)或者Apple Developer Center(ADC)建立，produce可以自动帮你完成这些工作
deliver => 自动上传截图，APP的元数据，二进制(ipa)文件到iTunes Connect
TestFlight管理
pilot => 管理TestFlight的测试用户，上传二进制文件
boarding => 建立一个添加测试用户界面，发给测试者，可自行添加邮件地址，并同步到iTC

辅助工具
spaceship => 为pilot，boarding和deliver等工具提供和 iTC 和 ADC 的交互API。spaceship本来是个独立的项目，后来被Fastlane收编进来
WatchBuild => 是一个独立的iTC监控工具，开启WatchBuild可以监控iTC上的文件状态，弹出MacOS自带的Notification


{% endhighlight %}


<h3>查看fastlane版本</h3>

{% highlight ruby %}

fastlane --version

{% endhighlight %}



<a href="https://whlsxl.github.io/fastlane1/">参考</a>
<a href="http://lynchwong.com/2016/06/fastlane---match/">参考</a>

