---
title: "Solution to SWUpdate Status Reporting Problem After Download and Installation in SWUpdate+hawkBit OTA?"
pubDate: 2026-09-14
tags: ["OTA", "SWUpdate", "hawkBit", "bootloader", "action"]
description: "A Solution to Resolve SWUpdate Status Reporting Problem After Download and Installation in SWUpdate+hawkBit OTA."
---

This page introduces my product: Solution to SWUpdate Status Reporting Problem After Download and Installation in SWUpdate+hawkBit OTA? Find it here:

<script src="https://www.creem.io/embed.js" async></script>
<div style="display:flex;justify-content:center;margin:20px 0">
  <a href="https://www.creem.io/payment/prod_1AljC0EyskY4HbIbi5M6Tx" data-creem-checkout data-creem-theme="light" style="display:inline-flex;align-items:center;gap:8px;padding:11px 18px;border-radius:12px;border:2px solid #151617;background:#FFBE98;color:#151617;box-shadow:0 3px 0 0 #151617;font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif;font-size:14px;font-weight:700;line-height:1;cursor:pointer;text-decoration:none"><svg width="15" height="15" viewBox="0 0 121 121" fill="none" xmlns="http://www.w3.org/2000/svg" aria-hidden="true" style="display:block;flex:0 0 auto"><path d="M22.1102 11C24.1187 11 25.9669 12.0982 26.9281 13.8619L51.2059 58.4106C52.5699 60.9134 55.7048 61.8368 58.2077 60.473C60.7108 59.109 61.6342 55.9742 60.2701 53.4712L41.5466 19.113C39.554 15.4566 42.2004 11 46.3645 11H103.806C107.885 11 110.539 15.2933 108.715 18.9416L65.0579 106.254C63.0356 110.298 57.2654 110.298 55.2431 106.254L11.5863 18.9416C9.76212 15.2933 12.4156 11 16.4946 11H22.1102Z" fill="#151617"/></svg><span>Buy with Creem</span></a>
</div>

![hawkBit Status turn to Updated successfully after apply this solution](@/assets/blog_assets/hawkBit-status-change.png)

This product provides a solution to the following problem. I promise that this is actually verified and works by me; in fact, I spent a week solving this problem. However, please carefully read the problem symptom description below and confirm before purchasing that it is the same as the problem you are currently trying to solve. By continuing with the purchase, you agree that, due to differences in hardware and system environment, software versions, and configuration parameters, this solution may not solve your specific problem. Due to the special nature of digital goods, refunds are no longer accepted after the file is downloaded.

## Problem Symptoms Description

1. After creating a Software module and distribution set on the hawkBit server and Assigning them to the target device Target, the SWUpdate client on the target device successfully received this OTA upgrade signal, downloaded and installed it to the specified location, and successfully executed the postinstall script.
    see image 2.
   ![hawkBit Status still Pending update after client download and install](@/assets/blog_assets/status-pending-update.png)
2. But the problem is: ① The server did not receive feedback that the client upgrade was complete, and the hawkBit update progress is still Pending Update, and has not changed to Updated. ② The client SWUpdate repeatedly reports a warning saying pending testing, ignores other updates, and requires restarting SWUpdate to report the test result. The log is as follows:

   ```log
   [TRACE] : SWUPDATE running :  [server_get_deployment_info] : Associated Action ID for Update Action is 21
   [TRACE] : SWUPDATE running :  [do_get_state] : Read state=1 from persistent storage.
   [WARN ] : SWUPDATE running :  [server_has_pending_action] : An already installed update is pending testing, ignoring available update action.
   [INFO ] : SWUPDATE running :  [server_has_pending_action] : Please restart SWUpdate to report the test results upstream.
   ```

   However, after rerunning SWUpdate, this warning is still reported, and restarting the system does not help either.
3. Software versions & system environment

   - hawkBit: 1.1.0
   - SWUpdate: 2024.04.1, 2026.05.1 both have this problem
   - The Target device system is Ubuntu Linux, using grub boot.

## Cause & Solution

Pay and download the pdf to checkout the cause and corresponding solution to the problem.

<script src="https://www.creem.io/embed.js" async></script>
<div style="display:flex;justify-content:center;margin:20px 0">
  <a href="https://www.creem.io/payment/prod_1AljC0EyskY4HbIbi5M6Tx" data-creem-checkout data-creem-theme="light" style="display:inline-flex;align-items:center;gap:8px;padding:11px 18px;border-radius:12px;border:2px solid #151617;background:#FFBE98;color:#151617;box-shadow:0 3px 0 0 #151617;font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif;font-size:14px;font-weight:700;line-height:1;cursor:pointer;text-decoration:none"><svg width="15" height="15" viewBox="0 0 121 121" fill="none" xmlns="http://www.w3.org/2000/svg" aria-hidden="true" style="display:block;flex:0 0 auto"><path d="M22.1102 11C24.1187 11 25.9669 12.0982 26.9281 13.8619L51.2059 58.4106C52.5699 60.9134 55.7048 61.8368 58.2077 60.473C60.7108 59.109 61.6342 55.9742 60.2701 53.4712L41.5466 19.113C39.554 15.4566 42.2004 11 46.3645 11H103.806C107.885 11 110.539 15.2933 108.715 18.9416L65.0579 106.254C63.0356 110.298 57.2654 110.298 55.2431 106.254L11.5863 18.9416C9.76212 15.2933 12.4156 11 16.4946 11H22.1102Z" fill="#151617"/></svg><span>Buy with Creem</span></a>
</div>


After the problem resolved, hawkBit server should receive OTA conclusion and turn status into Updated after SWUpdate download and install, see image 3.

![hawkBit Status turn to Updated after fix](@/assets/blog_assets/status-updated.png)