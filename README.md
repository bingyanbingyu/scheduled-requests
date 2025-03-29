# 🔄 定时请求工作流

这个仓库包含一个GitHub Actions工作流，用于定期向指定URL发送HTTP请求。

## 🔗 添加新URL

工作流中的URL存储在两个数组中：
- ⏱️ `HALF_HOURLY_URLS`：每30分钟检查一次的URL
- 📆 `DAILY_URLS`：每天检查一次的URL

### 📝 添加新URL的步骤

1. 📂 打开`.github/workflows/scheduled-requests.yml`文件
2. 🔍 找到对应的数组（`HALF_HOURLY_URLS`或`DAILY_URLS`）
3. ✏️ 按格式`["名称"]="URL"`添加新条目
4. 📤 提交并推送更改到仓库

### ⏱️ 示例：添加一个新的半小时检查URL

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

### 📆 示例：添加一个新的每天检查URL

若要添加一个新的每天检查URL，例如`https://new.example.com/haibao.php`：

```bash
declare -A DAILY_URLS
DAILY_URLS=(
  ["haibao1"]="http://b.you.anneng.ggff.net/bbj/haibao.php?cmsname=maccms10&bbjtype=hot&codetype=php&filtercondi=doubanid&orderby=ASC&num=10&level=9"
  ["haibao2"]="https://ane.anneng.ggff.net/bbj/haibao.php?cmsname=maccms10&bbjtype=hot&codetype=php&filtercondi=doubanid&orderby=ASC&num=10&level=9"
  ["newhaibao"]="https://new.example.com/haibao.php"
)
```

---

> 💡 **提示**：确保URL格式正确，并且可以正常访问。
