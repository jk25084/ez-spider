# EZ Spider

[TOC]

## 语法示例

* news.yaml
```yaml
ua: Chrome/55.0.2883.87
cookies: {}

login: !include login.yaml
list: !include list.yaml
each:
    - get
    - log

- &username username
- &password password
```

* login.yaml
```yaml
get: https://www.baidu.com
- 
    select: '#username'
    typein: *username
-
    select: '#password'
    typein: *password
-    
    click: '#login'
```

* list.yaml
```yaml
get: https://news.baidu.com?pn=*pn
-
    select: '.hotnews>ui>ul a'
    yield: href
if: pn<100
again:
    - set: pn+=20
```

## 引用资源
[PyYaml](https://ask.helplib.com/yaml/post_560318)
