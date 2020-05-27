+++ 
draft = false
date = 2020-05-27T18:49:49+03:00
title = "UIWindow cover everything"
description = ""
slug = "" 
tags = [swift, uiwindow]
categories = []
externalLink = ""
series = []
+++

Привет!

Озадачил себя отображением какой либо информации поверх ВСЕХ окон в приложении. Например UILabel, чтобы сообщать что версия DEBUG.

```swift
class ViewController: UIViewController {
    var coveringWindow: UIWindow?
    
  func coverEverything() {
        coveringWindow = UIWindow(frame: (view.window?.frame)!)
        if let coveringWindow = coveringWindow {
            coveringWindow.windowLevel = UIWindow.Level.alert + 1
            coveringWindow.isHidden = false
        }
    }
}
```

Нашел вот такое решение, меняйте backgroundColor, добавляйте UILabel и отображайте нужную вам инфу в любом месте приложения.

P.S естественно вызывать все это нужно в rootViewController
