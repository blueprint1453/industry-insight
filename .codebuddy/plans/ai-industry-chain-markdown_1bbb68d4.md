---
name: ai-industry-chain-markdown
overview: 基于 AI产业链.txt 的概念层次结构，生成一套多文件的 Markdown 文档体系（索引页 + 30+ 独立概念详情页），每个概念详情包含深度调研内容（原理、技术路线、市场格局、代表企业、发展趋势），使用 Mermaid 流程图/架构图，索引页支持点击跳转到各详情页。
todos:
  - id: create-index
    content: 创建目录结构和索引页 README.md，含产业链全景 Mermaid 架构图和分层超链接导航目录
    status: completed
  - id: upstream-materials
    content: 生成上游原材料6个详情页（硅片/光刻胶/电子特气/湿化学品/靶材/抛光材料），使用 [skill:NeoData金融搜索服务] 查询企业市场数据
    status: completed
    dependencies:
      - create-index
  - id: upstream-equipment
    content: 生成上游设备6个详情页+配套辅料1个详情页（光刻/刻蚀/薄膜沉积/离子注入清洗/CMP量检/封装设备/配套辅料），使用 [skill:WeStock Data] 查询设备企业财务数据
    status: completed
    dependencies:
      - create-index
  - id: midstream-design-foundry
    content: 生成中游芯片设计4个+晶圆代工1个详情页（通用AI芯片/专用芯片/配套芯片/EDA与IP/晶圆代工），使用 [skill:NeoData金融搜索服务] 查询芯片设计企业数据
    status: completed
    dependencies:
      - create-index
  - id: midstream-storage-package
    content: 生成中游存储芯片3个+封装测试2个详情页（内存/闪存/新型存储/先进封装/常规封测），使用 [skill:WeStock Data] 查询存储与封测企业数据
    status: completed
    dependencies:
      - create-index
  - id: downstream-detail
    content: 生成下游4个+细分配套5个详情页（算力硬件/基础设施/终端AI/软件配套/高速互连/基板/散热/被动元件/洁净工程），使用 [skill:WeStock Data] 补充企业数据
    status: completed
    dependencies:
      - create-index
  - id: review-verify
    content: 审查全部文件：校验 Mermaid 语法、超链接正确性、内容完整性与模板一致性
    status: completed
    dependencies:
      - upstream-materials
      - upstream-equipment
      - midstream-design-foundry
      - midstream-storage-package
      - downstream-detail
---

## 产品概述

基于 `AI产业链.txt` 的概念层次结构，生成一套完整的 AI 半导体产业链知识库文档（Markdown 格式）。文档采用"索引页 + 概念详情页"的多文件组织方式，每个概念独立成页，包含深度调研内容（技术原理、分类与技术路线、市场格局、代表企业、发展趋势），配以 Mermaid 流程图/架构图，并通过 Markdown 超链接实现"点击概念跳转详情"的导航体验。

## 核心功能

- **索引页（README.md）**：展示产业链全景 Mermaid 架构图 + 分层目录树（超链接导航），覆盖上游/中游/下游/细分配套四大板块
- **概念详情页（约32个）**：每个概念独立 Markdown 文件，统一模板结构，含概述、技术原理（Mermaid 图）、分类与技术路线（Mermaid 思维导图）、市场格局（Mermaid 饼图/象限图）、代表企业表格（国内外）、发展趋势、与AI产业链关联
- **Mermaid 图表**：纯文本渲染，涵盖工艺流程图、技术架构图、市场格局饼图、分类树等多种图表类型，兼容 GitHub/VS Code 预览
- **跨页面导航**：每个详情页底部含"返回总目录"链接，索引页每个概念可点击跳转到对应详情页

## 技术方案

### 文件格式与组织

- 纯 Markdown 文件，无外部依赖
- Mermaid 代码块（```mermaid）实现所有图表，无需外部图片资源
- 多文件组织：1 个索引页 + 32 个概念详情页，按产业链层次分目录存放

### 详情页统一模板结构

每个概念详情页遵循统一结构，确保一致性和可维护性：

1. **标题 + 一句话定义**（blockquote）
2. **概述**：该概念在 AI 产业链中的定位与重要性（2-3 段）
3. **技术原理**：详细技术说明 + Mermaid 工艺流程图/原理图
4. **分类与技术路线**：分类说明 + Mermaid 思维导图/分类树
5. **市场格局**：市场规模、竞争格局 + Mermaid 饼图/象限图
6. **代表企业**：表格列出国内外代表企业、主要产品/技术、市场地位
7. **发展趋势**：技术发展方向与市场预测
8. **与AI产业链的关联**：该环节如何支撑 AI 算力/大模型/应用
9. **返回链接**：`[← 返回总目录](../README.md)`

### 索引页（README.md）结构

1. 产业链标题与简介
2. 产业链全景 Mermaid 架构图（展示上中下游完整链路与关键节点）
3. 分层目录树：四大板块 → 子类别 → 具体概念（均为超链接）
4. 精简分层总结构

### 目录结构

```
AI产业链/
├── README.md                              # [NEW] 索引页：全景 Mermaid 图 + 目录导航
├── 上游/
│   ├── 原材料/
│   │   ├── 硅片.md                        # [NEW] 12英寸硅片/SiC/GaN第三代半导体
│   │   ├── 光刻胶.md                      # [NEW] EUV/ArF高端光刻胶及配套显影液
│   │   ├── 电子特气.md                    # [NEW] 氟化氢/氨气/刻蚀气体/高纯气源
│   │   ├── 湿化学品.md                    # [NEW] 超高纯硫酸/双氧水/剥离液
│   │   ├── 靶材.md                        # [NEW] 铜/铝/钛高纯金属靶材
│   │   └── 抛光材料.md                    # [NEW] CMP研磨液/抛光垫
│   ├── 设备/
│   │   ├── 光刻设备.md                    # [NEW] EUV光刻机/ArF浸没式光刻机
│   │   ├── 刻蚀设备.md                    # [NEW] 干法刻蚀/等离子刻蚀
│   │   ├── 薄膜沉积设备.md               # [NEW] PVD/CVD/ALD设备
│   │   ├── 离子注入与清洗设备.md          # [NEW] 离子注入机/清洗设备/氧化扩散炉
│   │   ├── CMP与量检测设备.md            # [NEW] CMP抛光设备/量检测试设备
│   │   └── 封装设备.md                    # [NEW] 划片/键合/塑封/探针台
│   └── 配套辅料.md                        # [NEW] 真空零部件/射频电源/精密阀门等
├── 中游/
│   ├── 芯片设计/
│   │   ├── 通用AI算力芯片.md              # [NEW] GPU/AI加速卡/TPU/NPU/GPGPU
│   │   ├── 专用芯片.md                    # [NEW] FPGA/ASIC/存算一体芯片
│   │   ├── 配套芯片.md                    # [NEW] CPU/高速接口/PMIC/SerDes
│   │   └── 设计工具EDA与IP.md             # [NEW] EDA设计软件/IP核
│   ├── 晶圆代工.md                        # [NEW] 先进/成熟制程/特色工艺
│   ├── 存储芯片/
│   │   ├── 内存.md                        # [NEW] GDDR6X/HBM高带宽内存
│   │   ├── 闪存.md                        # [NEW] SSD NAND Flash
│   │   └── 新型存储.md                    # [NEW] MRAM/存算一体存储
│   └── 封装测试/
│       ├── 先进封装.md                    # [NEW] 2.5D/3D堆叠/Chiplet/FCBGA
│       └── 常规封测.md                    # [NEW] 老化测试/可靠性测试/探针测试
├── 下游/
│   ├── 算力硬件产品.md                    # [NEW] AI服务器/加速卡/光模块/液冷散热
│   ├── 算力基础设施.md                    # [NEW] IDC/智算中心/超算中心及配套
│   ├── 终端AI硬件.md                      # [NEW] 云端/边缘/终端AI芯片与应用
│   └── 软件配套.md                        # [NEW] 驱动固件/编译框架/算力调度
└── 细分配套/
    ├── 高速互连.md                        # [NEW] 光芯片/光模块/Co-packaged
    ├── 基板材料.md                        # [NEW] FCBGA载板/ABF树脂基板
    ├── 散热.md                            # [NEW] 均热板/水冷板/导热材料/液冷设备
    ├── 被动元器件.md                      # [NEW] 高端电容/电阻/高频电感
    └── 洁净工程.md                        # [NEW] 半导体洁净厂房/废气废水处理
```

### 实现要点

- **Mermaid 图表规范**：所有图表使用 ```mermaid 代码块，兼容 GitHub/GitLab/VS Code 预览；流程图用 `graph TD/LR`，分类树用 `mindmap`，市场格局用 `pie` 或 `quadrantChart`
- **超链接规范**：索引页使用相对路径链接到详情页（如 `[硅片](上游/原材料/硅片.md)`），详情页底部统一使用 `[← 返回总目录](../README.md)` 返回（层级根据实际深度调整）
- **企业信息准确性**：使用金融数据搜索技能获取上市公司真实财务数据（市值、营收、市场份额），非上市公司基于公开行业报告数据
- **内容时效性**：市场数据注明数据来源和截止时间

## Agent Extensions

### Skill

- **NeoData金融搜索服务**
- Purpose: 查询半导体产业链代表企业的金融市场数据（市值、营收、财务报表、行业板块行情），为详情页"市场格局"和"代表企业"部分提供准确的数据支撑
- Expected outcome: 获取国内外半导体上市公司的实时/最新财务数据，增强市场格局分析的可信度

- **WeStock Data**
- Purpose: 查询A股/港股/美股半导体个股的详细数据（财务报表多期对比、股东结构、公司简况、板块行情），补充企业信息表格中的财务指标和市场地位数据
- Expected outcome: 获取代表企业的多期财务对比数据、板块成份股排名，用于市场格局分析和企业对比表格