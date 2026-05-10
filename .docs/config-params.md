# 配置项说明

> `【全局】`：影响所有会话，对所有推送目标统一生效  
> `【分组】`：按会话独立配置，仅 `subscription_mappings` 一项

## 配置文件

- `_conf_schema.json`: 定义所有配置项的类型、默认值、描述、提示信息
- 配置通过 AstrBot WebUI 的插件设置页面管理
- 运行时通过 `self.config` 字典访问

## 全局 · 基础配置

- `【全局】weibo_cookie` (string): 微博 Cookie，必填
- `【全局】weibo_urls` (list): 监控的微博用户 URL/UID 列表
- `【全局】target_conversation_id` (list): 推送目标会话 ID 列表
- `【全局】cookie_notification_target` (string): Cookie 失效通知目标

## 分组 · 会话订阅

- `【分组】subscription_mappings` (list): 会话订阅映射列表，格式 `会话ID: uid或链接,uid或链接`。配置后该会话仅接收已订阅博主的推送；未配置的全局目标保持接收全部推送。

## 全局 · 监控控制

- `【全局】check_interval` (int, 默认 10): 检查间隔（分钟）
- `【全局】check_interval_jitter` (int, 默认 2): 检查间隔随机浮动（分钟）
- `【全局】request_interval` (int, 默认 5): 账号间请求间隔（秒）
- `【全局】request_interval_jitter` (int, 默认 1): 请求间隔随机浮动（秒）

## 全局 · 过滤规则

- `【全局】filter_keywords` (list): 屏蔽词，包含这些词的微博不推送
- `【全局】whitelist_keywords` (list): 白名单，只推送包含这些词的微博
- `【全局】send_original` (bool, 默认 true): 推送原创微博
- `【全局】send_forward` (bool, 默认 true): 推送转发微博

## 全局 · 消息格式

- `【全局】message_format` (string): 微博推送模板，变量: `{name}`, `{weibo}`, `{link}`
- `【全局】hotsearch_message_format` (string): 热搜推送模板，变量: `{top_n}`, `{time}`, `{items}`

## 全局 · 热搜配置

- `【全局】enable_hotsearch` (bool, 默认 false): 开启热搜监控
- `【全局】hotsearch_interval` (int, 默认 60): 热搜推送间隔（分钟）
- `【全局】hotsearch_top_n` (int, 默认 10): 推送热搜前 N 条
- `【全局】hotsearch_filter_ads` (bool, 默认 true): 过滤热搜广告
- `【全局】hotsearch_show_link` (bool, 默认 true): 显示热搜条目链接

## 全局 · 日志配置

- `【全局】enable_plugin_log` (bool): 开启运行日志 plugin.log
- `【全局】plugin_log_max_size` (int, 默认 1): 运行日志文件最大大小 (MB)
- `【全局】enable_daily_log` (bool): 开启每日推送记录
- `【全局】enable_daily_summary` (bool): 开启每日总结
- `【全局】daily_summary_time` (string, 默认 "08:00"): 总结推送时间
