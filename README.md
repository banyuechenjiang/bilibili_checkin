# bilibili_checkin
<div align="center">

[![Bilibili Daily Checkin](https://github.com/Dangks/bilibili_checkin/actions/workflows/Bilibili_DailyCheckin.yml/badge.svg)](https://github.com/Dangks/bilibili_checkin/actions/workflows/Bilibili_DailyCheckin.yml)

</div>

## 项目简介
这是一个自动化打卡脚本，旨在帮助用户完成B站的每日签到任务，包括分享视频、观看视频、和漫画签到。
通过使用GitHub Actions，可以实现每日自动运行脚本，完成签到任务并获取相应的奖励。  

## 包含功能:
1. 每天自动执行签到任务：包含每日分享、观看视频、漫画签到等任务  
2. 敏感信息安全传递：支持通过环境变量读取cookie  
3. 结合GitHub Actions实现自动化运行,理论运行时间11:00，可通过Actions日志查看执行结果   
4. 支持手动触发(每日奖励只能领取一次，故触发多次即使执行成功结果也不会变化)

## 签到奖励：
完成自动签到可获取到`硬币+1、经验值+15`  ，漫画签到目前似乎并没有实际的用处，也没有签到奖励。

## 使用方法:  
1. Fork本项目到你的GitHub仓库中,注意解除fork关联
2. 在仓库的Settings -> Secrets中添加Repository secrets，Name为BILIBILI_COOKIE，Secret值为你的登录cookie
3. 启用GitHub Actions，Fork的仓库默认是关闭workflow的，需要手动开启。   

## 执行结果查看  
可以在workflows里查看执行日志的输出结果   

## Cookie获取：  
打开浏览器网页登录B站，然后进入开发人员工具(F12)，查看网络响应标头就能找到Cookie，完整复制后录入Secret值

## 注意事项:  
1. Cookie要包含bili_jct, SESSDATA, DedeUserID字段，
2. 建议先手动运行测试  
3. 可以根据需要修改cron表达式调整执行时间  
4. 请确保Cookie有效，修改密码或退出登录会导致Cookie失效。  
5. 请勿在任何位置明文泄露你的Cookie以防账号被盗。  
6. 本项目仅供学习交流使用，请勿滥用。  


## 常规问题解答：  
1. 关于分享视频：  
- 这个分享操作是调用B站的分享接口，实际上只是模拟了一次分享行为  
- 不会真实分享到任何地方，只是为了完成每日任务获取经验值  
- B站会记录这个分享行为，但不会在任何地方显示出来  

2. 关于观看视频：  
- 程序里指定的视频BV号修改为 幻想万华镜 ，不指定特定BV号也是可以的  
- 当前代码指定BV号主要是为了保证稳定性，因为随机视频可能会遇到:  
  - 视频已下架  
  - 视频需要会员才能观看   
  - 视频有年龄限制等情况  
  - 如果想改成随机视频，可以像share_video()方法一样；指定固定视频是一种保守稳妥的做法，但不是必须的。如果你想改成随机视频完全可以。  
2. 关于网页获取的cookie时效问题:
- 只要不在网页再次登录就是长期有效

## 贡献指南

原作分支说明：
- [main](https://github.com/Dangks/bilibili_checkin/tree/main)：主线分支，包含最新稳定版本代码  
- [dev](https://github.com/Dangks/bilibili_checkin/tree/dev)：开发分支，包含开发中的问题修改和新功能测试  
**请注意，直接向 `main` 分支发起的 PR 将不会被接受。


## 许可证
本项目采用[MIT](./LICENSE)许可证。  
