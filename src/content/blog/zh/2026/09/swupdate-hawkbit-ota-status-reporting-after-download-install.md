---
title: "SWUpdate+hawkBit OTA:下载安装后状态不上报怎么破?"
pubDate: 2026-09-14
tags: ["OTA", "SWUpdate", "hawkBit", "bootloader", "action"]
description: "解决 SWUpdate+hawkBit OTA 下载安装完成后, hawkBit 状态卡在 Pending Update, 且 SWUpdate 反复报 pending testing 警告的问题."
---

本页介绍我的一款产品:SWUpdate+hawkBit OTA 下载安装后状态不上报的解决方案。入口如下:

<script src="https://www.creem.io/embed.js" async></script>
<div style="display:flex;justify-content:center;margin:20px 0">
  <a href="https://www.creem.io/payment/prod_1AljC0EyskY4HbIbi5M6Tx" data-creem-checkout data-creem-theme="light" style="display:inline-flex;align-items:center;gap:8px;padding:11px 18px;border-radius:12px;border:2px solid #151617;background:#FFBE98;color:#151617;box-shadow:0 3px 0 0 #151617;font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif;font-size:14px;font-weight:700;line-height:1;cursor:pointer;text-decoration:none"><svg width="15" height="15" viewBox="0 0 121 121" fill="none" xmlns="http://www.w3.org/2000/svg" aria-hidden="true" style="display:block;flex:0 0 auto"><path d="M22.1102 11C24.1187 11 25.9669 12.0982 26.9281 13.8619L51.2059 58.4106C52.5699 60.9134 55.7048 61.8368 58.2077 60.473C60.7108 59.109 61.6342 55.9742 60.2701 53.4712L41.5466 19.113C39.554 15.4566 42.2004 11 46.3645 11H103.806C107.885 11 110.539 15.2933 108.715 18.9416L65.0579 106.254C63.0356 110.298 57.2654 110.298 55.2431 106.254L11.5863 18.9416C9.76212 15.2933 12.4156 11 16.4946 11H22.1102Z" fill="#151617"/></svg><span>通过 Creem 购买</span></a>
</div>

![应用本方案后 hawkBit 状态成功切换为 Updated](@/assets/blog_assets/hawkBit-status-change.png)

本产品针对下面这个问题给出解决方案。方案是我本人实测通过的,这点可以保证——事实上,我花了一整周才把它拿下。不过下单之前,请务必仔细读一遍下面的问题现象,确认和你眼下要解决的问题是同一个。继续购买即代表你理解:受硬件、系统环境、软件版本、配置参数等差异影响,本方案不一定能解决你的具体问题。又因数字商品的特殊性,文件下载后不再支持退款。

## 问题现象

1. 在 hawkBit 服务端创建 Software module 和 distribution set,并分配给目标设备 Target 后,目标设备上的 SWUpdate 客户端能成功收到这次 OTA 升级指令,完成下载并安装到指定位置,postinstall 脚本也顺利执行完。
    见图 2。
   ![SWUpdate 下载安装后 hawkBit 的状态仍然为 Pending update](@/assets/blog_assets/status-pending-update.png)
2. 但问题就来了:① 服务端没收到客户端升级完成的反馈,hawkBit 上的更新进度一直卡在 Pending Update,始终不变成 Updated。② 客户端 SWUpdate 反复报一条 pending testing 的警告,其它更新一律忽略,还提示要重启 SWUpdate 上报测试结果。日志如下:

   ```log
   [TRACE] : SWUPDATE running :  [server_get_deployment_info] : Associated Action ID for Update Action is 21
   [TRACE] : SWUPDATE running :  [do_get_state] : Read state=1 from persistent storage.
   [WARN ] : SWUPDATE running :  [server_has_pending_action] : An already installed update is pending testing, ignoring available update action.
   [INFO ] : SWUPDATE running :  [server_has_pending_action] : Please restart SWUpdate to report the test results upstream.
   ```

   然而重跑一遍 SWUpdate,这条警告照旧;重启系统也没用。
3. 软件版本与系统环境

   - hawkBit: 1.1.0
   - SWUpdate: 2024.04.1, 2026.05.1 均有此问题
   - 目标设备系统为 Ubuntu Linux,使用 grub 引导.

## 原因与解决方案

付费下载 PDF,即可查看问题的根因以及对应的解决方案。

<script src="https://www.creem.io/embed.js" async></script>
<div style="display:flex;justify-content:center;margin:20px 0">
  <a href="https://www.creem.io/payment/prod_1AljC0EyskY4HbIbi5M6Tx" data-creem-checkout data-creem-theme="light" style="display:inline-flex;align-items:center;gap:8px;padding:11px 18px;border-radius:12px;border:2px solid #151617;background:#FFBE98;color:#151617;box-shadow:0 3px 0 0 #151617;font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif;font-size:14px;font-weight:700;line-height:1;cursor:pointer;text-decoration:none"><svg width="15" height="15" viewBox="0 0 121 121" fill="none" xmlns="http://www.w3.org/2000/svg" aria-hidden="true" style="display:block;flex:0 0 auto"><path d="M22.1102 11C24.1187 11 25.9669 12.0982 26.9281 13.8619L51.2059 58.4106C52.5699 60.9134 55.7048 61.8368 58.2077 60.473C60.7108 59.109 61.6342 55.9742 60.2701 53.4712L41.5466 19.113C39.554 15.4566 42.2004 11 46.3645 11H103.806C107.885 11 110.539 15.2933 108.715 18.9416L65.0579 106.254C63.0356 110.298 57.2654 110.298 55.2431 106.254L11.5863 18.9416C9.76212 15.2933 12.4156 11 16.4946 11H22.1102Z" fill="#151617"/></svg><span>通过 Creem 购买</span></a>
</div>


问题解决之后,SWUpdate 下载安装完成,hawkBit 服务端应当能收到 OTA 结果,并把状态切换为 Updated,见图 3。

![修复后 hawkBit 状态切换为 Updated](@/assets/blog_assets/status-updated.png)