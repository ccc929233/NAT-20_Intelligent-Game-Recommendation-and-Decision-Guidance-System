

# 🎮 智能游戏推荐与决策引导系统 (NAT 20)

**Intelligent Game Recommendation and Decision Guidance System**

本项目旨在解决玩家在 Steam 等流媒体平台上面临的“选择困难症”。通过多维度的决策分析、自动化报告生成以及交互式仪表盘，帮助玩家根据个人兴趣、预算和硬件配置找到最理想的游戏。

---

## 🌟 核心功能 (Key Features)

-   **自动化分析报告**: 系统预设 6 大模板，将复杂的逻辑转化为自然语言报告：
    -   1. 开发商名片 (Developer's business card)
    -   2. 类型定位 (Type positioning)
    -   3. 近期热度 (Recent popularity)
    -   4. 多平台适配 (Multi-platform fit)
    -   5. 性价比之王 (King of value for money)
    -   6. 综合推荐 (Comprehensive recommendation)
-   **交互式筛选仪表盘**: 支持 19 个维度的并行过滤，可在 10 秒内检索数千个游戏。
-   **智能“反悔”机制**: 当筛选结果为 0 时，系统会触发撤销建议，优化筛选流程。
-   **情境化逻辑**: 根据游戏类型（如 RPG 或 FPS）动态调整筛选器的权重和顺序。
-   **数据可视化**: 集成 Matplotlib 生成游戏好评率等直观的条形图。
-   **管理工具**: 提供管理员后台，支持无需编写 SQL 即可进行 CRUD（增删改查）操作。

---

## 🛠️ 技术栈 (Tech Stack)

-   **编程语言**: Python 3.x
-   **前端框架**: Streamlit (提供 Web 交互界面)
-   **数据库**: SQLite (基于星型模式 Star Schema 的 13 张数据表)
-   **可视化**: Matplotlib
-   **部署工具**: Google Colab + pyngrok (用于建立安全隧道访问)
-   **逻辑实现**: 基于确定性阈值的 if-elif 级联判定逻辑

---

## 📊 数据库设计 (Database Design)

系统采用高度规范化的**关系型模式（星型架构）**，确保高效查询和数据完整性：
-   **核心表**: `Game` (包含超过 20 个字段，如 AppID, Price, Metrics 等)。
-   **中间表 (Bridge Tables)**: 处理多对多关系，如 `Game_Genre`, `Game_Tag`, `Game_Developer` 等。
-   **模板表**: `templates` 专门存储叙述性逻辑，实现数据与报告文案的分离。

---

## 🚀 启动指南 (Setup & Usage)

### 环境配置
1. 克隆仓库:
   ```bash
   git clone https://github.com/your-repo/NAT-20-Game-System.git
   cd NAT-20-Game-System
   ```
2. 安装依赖:
   ```bash
   pip install streamlit matplotlib pandas pysqlite3 pyngrok
   ```

### 运行系统
本项目支持本地启动或通过 Google Colab 启动：

**方式 A: 本地运行**
```bash
streamlit run app.py
```

**方式 B: Google Colab (通过 pyngrok)**
在 Colab 单元格中运行启动代码，获取 `pyngrok` 生成的公共 URL 即可访问。

---

## 🖥️ 系统演示 (Screenshots)

### 1. 交互式游戏寻找器
用户首先选择核心类型，系统自动推送匹配的子筛选器。
![Dashboard](./screenshots/dashboard.png)

### 2. 自动化报告生成
以《Dota 2》为例，系统生成的全维度深度分析报告。
![Deep Dive](./screenshots/report_demo.png)

### 3. 数据分析图表
Matplotlib 渲染的游戏评分直观对比图。
![Analysis](./screenshots/chart.png)

---

## 📂 数据来源
本项目基于 Kaggle 上的 **"Steam Games Dataset" (CSV)** 进行二次开发与清洗。

---

### 💡 提示：
*   **图片路径**: 请将项目中的截图放入名为 `screenshots` 的文件夹内，并确保 README 中的路径对应。
*   **SQL 文件**: 确保仓库中包含初始化的 `.db` 或 `.sql` 文件以供系统读取。
