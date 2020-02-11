+++ 
draft = false
date = 2020-02-12T00:05:51+03:00
title = "Парсим JSON с переносами"
description = "Бывает что бэк присылает нам какой либо текст с форматированием нацеленым на web, покажу что с этим делать"
slug = "" 
tags = ["json","swift","parse"]
categories = []
externalLink = ""
series = []
+++

Привет!

Давно не писал, снова появилась задача отобразить длинный текст в UITextField на tvOS.

Текст приходит аля:

{message: "\Парам-пампам \n \r \t \\\"}

Естественно если это отдать в JSONDecoder то он выплюнет ошибку.

Решение:
```swift
    var json = try? JSONSerialization.jsonObject(with: data, options: [])

    if json == nil, var str = String(bytes: data, encoding: .utf8) {

    str = str.replacingOccurrences(of: "\n", with: "\\n")

    str = str.replacingOccurrences(of: "\r", with: "\\r")

    str = str.replacingOccurrences(of: "\t", with: "\\t")

    str = str.replacingOccurrences(of: "\\\"", with: "\"")

    if let dataFromString = str.data(using: .utf8) {

    json = try? JSONSerialization.jsonObject(with: dataFromString, options: [])

    }

    }
```

1. Проверяем что json == nil
2. Создаем String из data, с encoding UTF-8
3. И финалочка, заменяем все противные swift-у символы на те которые помогут показать нам отформатированный текст
4. Далее парсим наш JSON как обычно

```swift
let jsonPretty = json as? [String: String]
self?.yourTextLabel.text = jsonPretty!["message"]
```

За наводку спасибо http://bingosoft.info/ ;)

