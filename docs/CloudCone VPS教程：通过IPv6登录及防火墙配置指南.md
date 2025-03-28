# CloudCone VPS教程：通过IPv6登录及防火墙配置指南

## 前言：为什么选择CloudCone VPS

服务器登录和防火墙配置本应是基础操作，但在使用国外VPS时可能会遇到特殊问题。本文将分享我在CloudCone VPS上通过IPv6登录和配置防火墙的完整经验。

👉 [【点击查看】2025年最新CloudCone优惠码及特价云服务器方案汇总](https://bit.ly/Cloudcone)

## 一、背景与问题发现

### 1.1 从腾讯云迁移到CloudCone
- 原使用腾讯云服务器（4M带宽）
- 部署AList时带宽不足
- 转用CloudCone基础配置：
  - 年费仅11美元
  - 每月2T流量
  - 1G带宽

### 1.2 IPv4连接问题
测试IPv4连通性时发现100%丢包：
bash
正在 Ping 198.52.**.** 具有 32 字节的数据:
请求超时。
请求超时。
请求超时。
请求超时。

## 二、IPv6解决方案

### 2.1 启用IPv6功能
1. 登录CloudCone控制面板
2. 进入`Networking`设置
3. 开启`enable ipv6`选项
4. 确认获取到Global IPv6地址

### 2.2 通过IPv6登录服务器
使用PuTTY连接步骤：
1. 输入IPv6地址
2. 默认用户名：root
3. 密码通过邮件获取

成功登录后建议立即修改密码：
bash
sudo passwd root
New password:
Retype new password:
passwd: password updated successfully

## 三、防火墙配置指南

### 3.1 基础防火墙命令
bash
# 查看状态
sudo ufw status

# 放行端口（务必先放行SSH的22端口！）
sudo ufw allow 22

# 拒绝端口
sudo ufw deny 端口号

# 删除规则
sudo ufw delete [rule]

### 3.2 重要注意事项
- 开启防火墙前必须先放行SSH端口
- 误操作可能导致无法连接，需重装系统
- 低配VPS建议使用Ubuntu 20.04而非22.04

## 四、经验总结

1. **IPv6优势**：在IPv4受限时可作为备用连接方案
2. **防火墙要点**：规则设置需谨慎，建议先测试再保存
3. **系统选择**：1GB内存以下VPS推荐Ubuntu 20.04

CloudCone的基础套餐性价比出色，适合个人项目和小型应用部署。遇到技术问题时，其客服响应速度堪比国内大厂，使用体验良好。

👉 [立即获取CloudCone特价套餐](https://bit.ly/Cloudcone)