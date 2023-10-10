
# 一个云编译UA2F固件的项目


## fork from: https://github.com/MoorCorPa/Actions-immortalWrt-UA2F

## 改动

 - 修改 ubuntu 版本从 `18.04` 到 `20.04`，因为 Github Actions 已经不再支持 `18.04`，否则运行时会卡在获取 Runner 上。
 - 使用 Tag 来定位、签出到稳定版本，而不是使用原项目的 Branch，因为 Branch 在发布 Release 后还会继续更新（此时编译的被称为 Snapshot 版本）。Snapshot 不包含 Luci，而且有些软件包可能不适配。参见：[内核版本不适配](https://openwrt.org/faq/cannot_satisfy_dependencies)，[开发版本](https://openwrt.org/zh/releases/snapshot)


[官方编译命令](https://openwrt.org/docs/guide-developer/toolchain/use-buildsystem)

## 原项目描述

* 如果要自己设置规则记得把
<br><code>iptables -t mangle -A ua2f -m set --set nohttp dst,dst -j RETURN</code>
* 改成以下规则
<br><code>iptables -t mangle -A ua2f -m set --match-set nohttp dst,dst -j RETURN</code>


### 食用方法：
##### 用其他设备的话请改Main.config里的上面三行，改成自己所需要的 config，复制别人的来用也行，下面的不要动哦
##### aciton务必使用Main
##### 目前本地编译x86，已测试成功

<br><a href="http://trac.gateworks.com/wiki/OpenWrt/kernelconfig">参考文献</a><br>
<a href="https://sunbk201public.notion.site/sunbk201public/OpenWrt-f59ae1a76741486092c27bc24dbadc59">详细教程</a><br>
<a href=“https://github.com/Zxilly/UA2F”>UA2F</a><br>