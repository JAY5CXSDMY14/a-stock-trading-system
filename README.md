# A股智能选股系统

基于b1/b2交易策略的智能选股分析系统

## 📊 功能特性

### 核心功能
- **b1选股**：KDJ J值大负值的买入机会识别
- **b2选股**：b1之后第一根中长阳确认
- **大盘分析**：上证指数支撑/压力位计算
- **实时监控**：每日自动生成分析报告

### 交易策略
- **b1（左侧交易）**：卖出情绪的买点，KDJ J＜-5
- **b2（右侧交易）**：b1反弹后第一根中长阳确认

## 🚀 快速开始

### 1. 安装依赖
```bash
pip3 install baostock pandas requests
```

### 2. 运行分析
```bash
python3 ~/a-stock-trader/b1b2_analyzer.py
```

### 3. 查看日报
```bash
cat ~/a-stock-trader/a_stock_daily_YYYY_MM_DD.md
```

## 📁 文件结构

```
~/a-stock-trader/
├── b1b2_analyzer.py    # b1/b2选股分析
├── holdings_analyzer.py # 持仓分析
├── today_stocks.txt    # 今日配置
├── README.md           # 说明文档
└── a_stock_daily_YYYY_MM_DD.md  # 日报
```

## 📈 策略说明

### b1买入条件
- KDJ指标J值大负值（J＜-5）
- 股价回调至支撑位
- 左侧分批买入
- 止损：买入K线最低价下方2-5个价位

### b2买入条件
- b1之后第一根中长阳（涨幅>3%）
- 右侧追涨买入
- 止损：阳线最低价下方2-5个价位

## 🔧 定时任务

- **每日16:00**：A股日报生成
- **每2小时**：加密货币汇报（含BTC/ETH）

## 📄 相关链接

- **飞书Wiki**: https://luycxsdmy.feishu.cn/wiki/xxx
- **Cron任务ID**: 221d0cca-5c79-48b8-9def-74821f4a821a

## 🤖 系统架构

```
用户选股 → 系统分析 → MA/支撑压力计算 → 预测生成 → 日报输出
     ↓
  baostock API → K线数据 → 技术指标 → 交易建议
```

## 📝 更新日志

### 2026-02-12
- 初始版本创建
- baostock API集成
- b1/b2选股逻辑实现
- 上证指数支撑压力位计算
- 飞书Wiki集成

---

**Author**: LuXZ02
**Created**: 2026-02-12
