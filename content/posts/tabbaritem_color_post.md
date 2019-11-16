+++ 
draft = false
date = 2019-11-16T23:05:24+03:00
title = "Меняем фокусный цвет UITabBarItem"
description = "Быстро, качественно и надолго меняем цвет фокуса на элементе таб бара"
slug = "" 
tags = []
categories = []
externalLink = ""
series = []
+++

Привет!

Появилась задача поменять фокусный цвет UITabBarItem.

Попробовав перебрать все доступные и похожие на backgroundColor, и все что связано у tabBar и UITabBarItem с color атрибуты, отчалялся и пошел в Google.

Перекопав половину Google-a, нашел на самом его дне, единственное и верное решение, им и делюсь.

`tabBar.standardAppearance.selectionIndicatorTintColor = .yourColor`

Вот так, на первый взгляд непремечательный параметр, делает то чего от него не ждешь.


