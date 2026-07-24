# 简易超市销售数据分析项目

## 项目简介

模拟真实超市销售场景，使用 Python + NumPy + Pandas 完成：
- 时间趋势分析（每日销售额统计）
- 品类销量与销售额占比分析
- Top 商品与 Top 品类筛选

## 技术栈

- Python 3.x
- NumPy
- Pandas

## 功能特性

- ✅ **数据生成**：模拟 100 条销售记录（日期、品类、商品、销量、单价）
- ✅ **数据加工**：计算销售额（销量 × 单价）
- ✅ **时间趋势分析**：按日期汇总销售额
- ✅ **品类分析**：统计各品类销量与销售额
- ✅ **Top 筛选**：销量 Top5 商品、销售额 Top3 品类

## 核心代码

### 数据生成
```python
date_list = pd.date_range(start='2026-01-01', end='2026-01-07')
df = pd.DataFrame({
    '日期': np.random.choice(date_list, 100),
    '品类': np.random.choice(['零食','饮料','日用品','生鲜'], 100),
    '商品名': np.random.choice(['可乐','薯片','牛奶','纸巾','苹果','面包','矿泉水','洗衣液'], 100),
    '销量': np.random.randint(1, 20, 100),
    '单价': np.random.choice([2.5, 3, 5, 8, 10, 12, 15], 100)
})
```

### 销售额计算
```python
df['销售额'] = df['销量'] * df['单价']
```

### 多维度统计
```python
# 每日销售额
df.groupby('日期')['销售额'].sum().sort_index()

# 品类销量 & 销售额（多列聚合）
df.groupby('品类').agg({'销量': 'sum', '销售额': 'sum'})

# Top5 商品
df.groupby('商品名')['销量'].sum().sort_values(ascending=False).head(5)
```

## 运行方式
```bash
python supermarket_sale_management.py
```

## 学习收获
- 掌握了 pd.date_range 生成日期序列
- 理解了 groupby 分组统计的多种用法
- 学会了 agg() 对多列分别指定聚合方式
- 熟悉了 sort_values() 排序与 head() 取 Top N

## 关联项目
- 📊 [我的作品集主页](https://github.com/haipretty/portfolio)
- 🎓 [学生成绩管理](https://github.com/haipretty/student-score-management)

