---
layout:     post
title:      自动创建Github Issue
subtitle:   用ruby和Github API创建Issue
date:       2018-07-30
author:     LZP[原创]
header-img: img/post-sample-geek.jpg
catalog: true
tags:
    - ruby
    - github
    - 版本控制
---

## 自动创建Github Issue

### 这段ruby代码，自动在Github中加入一条issue

```ruby

username = "longzeping" # GitHub 用户名
# GitHub Token，在账户设置中申请，具体参考文尾《Github Token的申请和使用》
token = "246c14c************aa621dcdfe6a5643acdf3"   
repo_name = "longzeping.github.io"  # 存放 issues的仓库

# Issue标签，Issue可以加很多个标签
label1 = "Gitalk"    # Issue的标签1，我用"Gitalk"标识这类issue是给Gitalk插件使用的
label2 = "/2018/07/31/自动创建Github-Issues/"  # Issue的标签2，我用特定博文的pathname作标签，让issue和博文对应
# Issue的内容
issueBody = "这是为博客文章《自动创建Github Issues》创建的评论仓库" 
# Issue的标题
issueTitle = "自动创建Github Issues/"

# 这是本段代码需要的库，如果没有装，请参考文尾《ruby和ruby库的安装》
require 'open-uri'
require 'faraday'
require 'active_support'
require 'active_support/core_ext'

# 建立到指定用户名、指定指定仓库的issues的链接
conn = Faraday.new(:url => "https://api.github.com/repos/#{username}/#{repo_name}/issues") do |conn|
  conn.basic_auth(username, token)
  conn.adapter  Faraday.default_adapter
end

# post一个json格式的数据给前面建立的连接，这个json格式的数据描述了一个issue
response = conn.post do |req|
  req.body = { body: issueBody, labels: [label1, label2], title: issueTitle }.to_json
end
puts response.body

```
**把这段代码保存为文件createissueforgithub.rb**

### 执行这段代码即可

#### 命令行执行
>ruby createissueforgithub

----

## 相关参考：
>[《Github Token的申请和使用》](https://longzeping.github.io/2018-08-01-Github-Token的申请和使用/)
>[《ruby和ruby库的安装》](https://longzeping.github.io/2018-08-01-ruby和ruby库的安装/)