---
title:  "[RN-Troubleshooting] Thread 1: signal SIGABRT Err in Xcode after update iOS ver to 13.3.1"
excerpt: "[RN-Troubleshooting] Thread 1: signal SIGABRT Err in Xcode after update iOS ver to 13.3.1"

categories:
  - React-Native
tags:
  - React-Native
  - Android
  - iOS

comments: true
last_modified_at: 2020-04-09T22:00:00-00:00
---

# Description

After update iPhone(real device) iOS version to 13.3.1, *“****Thread 1: signal SIGABRT~\****”* error occurred in Xcode that run real iOS device(iPhone) for debugging react native project. It also seems to occur in Flutter project that also use Thread system. Let’s figure out the solution👊

![img](https://cdn-images-1.medium.com/max/1760/1*9NHr2mlvQg21poB-Qzm-SQ.png)Theard 1 ~ Error Xcode screen

# Solution

There are three solution to solve this problem.

1. Use a non-personal Team provisioning profile

2. Run on the 13.3.1 version on simulator not a real device

3. Downgrade real iOS device’s version under 13.3.1

## 1. Use a non-personal Team provisioning profile

In my case, Solve the problem this way. ***when I changed provisioning profile in general tab personal to corporate\***. Problem was solved. this problem is just system error. So, we have to wait or fix React Native Library to compensate for error. Modify our RN code does not make chagne.

## 2. Run on the 13.3.1 version on simulator not a real device

It’s confirmed that react native app **a\*lready distributed from Apple App Store don’t make a crush\*** on real device iOS version 13.3.1**.** Therefore, if your purpose is to run RN project just for debugging app working, Test it on Simulator. Because Customer will not face such problems in real case.

## 3. Downgrade real iOS device’s version under 13.3.1

If you have to run RN project in real device, but you don’t have corporate provisioning profile. Downgrade you iPhone iOS version lower than 13.3.1.

How to Downgrade iOS version? It’s pretty simple! 😜

First, go to [this site](https://ipsw.me/) and Download proper iOS Firmware fit for your iPhone.

Second, click “update button” with option on mac or shift on window. Then you can choice iOS firmware file that download from[ site above](https://ipsw.me/).

All you have to do to downgrade is done. It is not easy? Isn’t it?

![img](https://cdn-images-1.medium.com/max/1760/1*yrIp6A3WO9OjmEGLc_-n7w.png)iPhone update button location in mac

# Conclusion

The solution is simple, but a lot of talk. It’s not enough, but I hope it will help someone🙏🏻

Thank you!

References: https://github.com/flutter/flutter/issues/49504