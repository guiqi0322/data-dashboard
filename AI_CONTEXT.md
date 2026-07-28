# 数据面板项目 - AI 上下文说明

## 📍 项目信息
- **在线访问**: https://guiqi0322.github.io/data-dashboard/
- **GitHub 仓库**: https://github.com/guiqi0322/data-dashboard
- **技术栈**: 纯前端（HTML + CSS + JavaScript 单文件）

---

## 🎯 项目概述

这是一个企业数据面板，包含 4 个主要模块，横向排列，支持响应式布局（手机/平板/电脑）。

### 四大模块

1. **💰 最近销售**
   - 近一年销售总金额（可点击查看明细）
   - 月度销售趋势柱状图
   - 课程销售 TOP5（线上）
   - 课程销售 TOP5（线下）
   - 工作人员成交额 TOP5

2. **👥 用户数据模块**
   - 用户总人数（可点击查看明细）
   - 新用户数（可点击查看明细）
   - 纯线上用户数（可点击查看明细）
   - 用户类型分布：B2C / B2B2C / B2B（可点击查看明细）
   - 学习行为高峰期折线图

3. **🔄 线上线下**
   - 行业精英四大课程购买情况
     - 卓越新人（可点击查看明细）
     - 业务主任（可点击查看明细）
     - 卓越经理人（可点击查看明细）
     - 行业精英（可点击查看明细）
   - 课程占比饼图

4. **📚 学习行为**
   - 线下班报名人数柱状图
   - 近一年学习时长分布（线上/线下对比）
   - 近6月活跃用户学习时长分布
   - 每人登录观看次数分布图

---

## 🏗️ 技术架构

### 文件结构
```
data-dashboard/
├── index.html          # 完整的单页应用（所有代码都在这个文件）
├── AI_CONTEXT.md       # 本文档
└── PROJECT_INFO.md     # 项目信息卡片
```

### 技术栈
- **HTML5**: 页面结构
- **CSS3**: 样式（内联在 `<style>` 标签中）
- **JavaScript**: 逻辑（内联在 `<script>` 标签中）
- **Chart.js 4.4.0**: 图表库（CDN 引入）

### 代码结构（index.html）

```html
<!DOCTYPE html>
<html>
<head>
    <!-- 1. 引入 Chart.js -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.0/dist/chart.umd.min.js"></script>
    
    <!-- 2. 所有样式 -->
    <style>
        /* 响应式布局、卡片、模态框等样式 */
    </style>
</head>
<body>
    <!-- 3. 页面结构 -->
    <div class="container">
        <div class="header">...</div>
        <div class="dashboard">
            <div class="module">最近销售</div>
            <div class="module">用户数据</div>
            <div class="module">线上线下</div>
            <div class="module">学习行为</div>
        </div>
    </div>
    
    <!-- 4. 通用模态框 -->
    <div id="detailModal">...</div>
    
    <!-- 5. JavaScript 逻辑 -->
    <script>
        const testData = { ... }  // 所有数据
        function showModal(type) { ... }  // 显示详情
        function initCharts() { ... }  // 初始化图表
    </script>
</body>
</html>
```

---

## 📊 数据结构

所有测试数据都在 `testData` 对象中（JavaScript 部分）：

```javascript
const testData = {
    // 月度销售数据（近12个月）
    monthlySales: { ... },
    
    // 课程销售 TOP5（线上）
    onlineCourseRank: [ ... ],
    
    // 课程销售 TOP5（线下）
    offlineCourseRank: [ ... ],
    
    // 工作人员成交额 TOP5
    marketingOrderRank: [ ... ],
    
    // 学习高峰期数据
    peakHours: { ... },
    
    // 线下班报名人数
    offlineClass: { ... },
    
    // 学习时长分布
    learningDuration: { ... },
    
    // 活跃用户学习时长
    activeUserDuration: { ... },
    
    // 登录观看次数
    loginDistribution: { ... },
    
    // 销售明细
    salesDetails: { ... },
    
    // 用户数据明细
    userDetails: { ... },
    
    // 课程明细
    courseDetails: { ... }
}
```

---

## 🎨 关键功能

### 1. 响应式布局
```css
/* 电脑端：4列 */
.dashboard {
    grid-template-columns: repeat(4, 1fr);
}

/* 平板：2列 */
@media (max-width: 1200px) {
    .dashboard { grid-template-columns: repeat(2, 1fr); }
}

/* 手机：1列 */
@media (max-width: 768px) {
    .dashboard { grid-template-columns: 1fr; }
}
```

### 2. 点击查看详情
所有数据卡片都有 `onclick="showModal('type')"` 事件：
- 点击后调用 `showModal()` 函数
- 显示模态框，展示详细数据
- 支持 ESC 键关闭

### 3. 排行榜显示
课程销售 TOP5 显示线上/线下详情：
```
排名  课程名称
      线上：XXX笔 ¥XXX,XXX
      线下：XXX笔 ¥XXX,XXX
```

### 4. 图表类型
- **柱状图**: 月度销售、线下班报名、学习时长分布
- **折线图**: 学习高峰期
- **饼图**: 课程占比、活跃用户学习时长

---

## 📝 常见修改场景

### 场景 1：修改数据
找到 `testData` 对象，修改对应的数据：
```javascript
// 例如：修改销售总金额
<div class="stat-value">¥12,580,000</div>  // HTML 中
// 和
salesDetails: { ... }  // JavaScript 中
```

### 场景 2：修改课程名称
在 `testData` 中搜索课程名称，替换即可：
```javascript
onlineCourseRank: [
    { name: '卓越新人', ... },  // 修改这里
    ...
]
```

### 场景 3：修改颜色
在 `<style>` 标签中搜索颜色值：
```css
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
/* 修改 #667eea 和 #764ba2 */
```

### 场景 4：添加新模块
在 `<div class="dashboard">` 中添加新的 `<div class="module">`

### 场景 5：修改图表配置
找到 `initCharts()` 函数，修改对应的 Chart.js 配置

---

## 🔗 关键链接

- **在线访问**: https://guiqi0322.github.io/data-dashboard/
- **GitHub 编辑**: https://github.com/guiqi0322/data-dashboard/edit/main/index.html
- **代码原文件**: https://raw.githubusercontent.com/guiqi0322/data-dashboard/main/index.html
- **Pages 设置**: https://github.com/guiqi0322/data-dashboard/settings/pages

---

## 💡 修改注意事项

1. **单文件结构**: 所有代码都在 `index.html` 中
2. **保持结构**: 不要修改 HTML 结构，除非你知道在做什么
3. **测试数据**: 所有数据都是测试数据，可以根据实际情况修改
4. **图表库**: 使用 Chart.js，文档：https://www.chartjs.org/docs/
5. **响应式**: 确保修改后在手机端也能正常显示
6. **点击事件**: 所有可点击元素都有 `onclick` 事件，注意保持

---

## 🚀 部署流程

```bash
# 本地修改后
cd E:\data-dashboard
git deploy  # 自动 add、commit、push

# 等待 1-2 分钟，网站自动更新
```

---

## 📱 手机端修改

1. 手机浏览器打开：
   ```
   https://github.com/guiqi0322/data-dashboard/edit/main/index.html
   ```

2. 编辑代码

3. 点击 **Commit changes**

4. 等待 1-2 分钟

---

## 🤖 给 AI 的提示词模板

```
我有一个数据面板项目，代码在这里：
https://raw.githubusercontent.com/guiqi0322/data-dashboard/main/index.html

项目说明在这里：
https://raw.githubusercontent.com/guiqi0322/data-dashboard/main/AI_CONTEXT.md

请帮我修改：
1. [具体修改内容]
2. [具体修改内容]

要求：
- 保持现有的样式和结构
- 只修改需要改的部分
- 返回完整的修改后代码
```

---

## ✅ 快速参考

- **文件**: `index.html`（唯一需要修改的文件）
- **数据**: `testData` 对象
- **样式**: `<style>` 标签
- **逻辑**: `<script>` 标签
- **部署**: `git deploy`
- **访问**: https://guiqi0322.github.io/data-dashboard/
