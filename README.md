# 定时请求工作流

这个仓库包含一个GitHub Actions工作流，用于定期向指定URL发送HTTP请求，并检查其响应状态。

## 使用方法

### 运行工作流

#### 定时运行
工作流会自动按照以下计划运行：
- 每30分钟运行一次（检查`HALF_HOURLY_URLS`中的URL）
- 每天在UTC时间午夜运行一次（检查`DAILY_URLS`中的URL）

无需手动干预，GitHub Actions会按照设定的时间表自动执行工作流。

#### 手动触发
如果需要立即运行工作流，可以手动触发：
1. 进入GitHub仓库的"Actions"选项卡
2. 选择"Scheduled Requests"工作流
3. 点击"Run workflow"按钮手动触发

### 查看日志

工作流运行后，可在"Actions"选项卡中查看执行日志：
- 展开任务以查看详细输出
- ✅ 成功消息：URL返回HTTP状态码200
- ❌ 失败消息：URL返回其他状态码

## 添加新URL

工作流设计时考虑了扩展性，URL存储在两个数组中：
- `HALF_HOURLY_URLS`：每30分钟检查的URL
- `DAILY_URLS`：每天检查的URL

### 添加新URL的步骤

1. 打开`.github/workflows/scheduled-requests.yml`文件
2. 找到对应的数组（`HALF_HOURLY_URLS`或`DAILY_URLS`）
3. 按格式`["名称"]="URL"`添加新条目
4. 提交并推送更改到仓库
5. 工作流将在下次运行时自动包含新URL

### 示例：添加一个新的半小时检查URL

若要添加一个新的半小时检查URL，例如`https://new.example.com/api.php/timming/index.html?enforce=1&name=new`：

```bash
declare -A HALF_HOURLY_URLS
HALF_HOURLY_URLS=(
  ["ziyuanku"]="http://b.you.anneng.ggff.net/api.php/timming/index.html?enforce=1&name=ziyuanku"
  ["hongniuzy"]="https://ane.anneng.ggff.net/api.php/timming/index.html?enforce=1&name=hongniuzy"
  ["aa"]="https://dy.wangzhetq.asia/api.php/timming/index.html?enforce=1&name=aa"
  ["bing522"]="https://bing522.serv00.net/api.php/timming/index.html?enforce=1&name=aa"
  ["new"]="https://new.example.com/api.php/timming/index.html?enforce=1&name=new"
)
```

### 示例：添加一个新的每天检查URL

若要添加一个新的每天检查URL，例如`https://new.example.com/haibao.php`：

```bash
declare -A DAILY_URLS
DAILY_URLS=(
  ["haibao1"]="http://b.you.anneng.ggff.net/bbj/haibao.php?cmsname=maccms10&bbjtype=hot&codetype=php&filtercondi=doubanid&orderby=ASC&num=10&level=9"
  ["haibao2"]="https://ane.anneng.ggff.net/bbj/haibao.php?cmsname=maccms10&bbjtype=hot&codetype=php&filtercondi=doubanid&orderby=ASC&num=10&level=9"
  ["newhaibao"]="https://new.example.com/haibao.php"
)
```

## 故障排查

### 日志中没有输出
- 确保工作流已触发（手动或定时）
- 检查URL是否可访问并返回有效的HTTP状态码
- 确认工作流文件语法无误

### 工作流未运行
- 确认仓库已启用GitHub Actions
- 检查定时触发的cron语法是否正确
- 确保工作流文件位于正确目录（`.github/workflows/`）

## 贡献

欢迎fork本仓库，改进代码并提交pull request。如果有优化建议（例如添加错误处理或通知功能），也欢迎提出！

## 许可证

本项目采用MIT许可证，详情请见LICENSE文件。
