# 部署指南

## 📋 部署清单

### 1. 环境准备
```bash
# Python依赖
pip3 install baostock pandas requests

# 系统检查
python3 --version  # 需要 Python 3.8+
```

### 2. 文件部署
```bash
# 创建目录
mkdir -p ~/a-stock-trader

# 复制脚本
cp b1b2_analyzer.py ~/a-stock-trader/
cp holdings_analyzer.py ~/a-stock-trader/
cp today_stocks.txt ~/a-stock-trader/

# 设置执行权限
chmod +x ~/a-stock-trader/*.py
```

### 3. Cron定时任务
```bash
# 添加A股日报任务（每日16:00）
openclaw cron add --name "A股日报-每日16:00" \
  --schedule "0 16 * * *" \
  --payload "运行 a-stock-trader 选股分析" \
  --sessionTarget "isolated"
```

### 4. baostock API配置
```python
import baostock as bs
lg = bs.login()  # 无需API Key，免费使用
```

## 🔧 故障排除

### baostock连接失败
```bash
# 检查网络
curl -I http://baostock.com

# 重试
python3 -c "import baostock; bs.login()"
```

### 数据获取异常
```python
# 检查股票代码格式
# 上海: sh.600000
# 深圳: sz.000001
```

## 📊 Cron任务配置

```json
{
  "name": "A股市场日报-每日16:00",
  "schedule": "0 16 * * *",
  "sessionTarget": "isolated",
  "payload": {
    "kind": "agentTurn",
    "message": "【A股市场日报任务】运行 ~/a-stock-trader/b1b2_analyzer.py"
  }
}
```

## ✅ 验证步骤

1. 测试baostock连接
2. 运行单只股票分析
3. 生成完整日报
4. 验证定时任务触发
5. 检查输出格式

