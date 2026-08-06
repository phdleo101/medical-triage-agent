# 智能分诊Agent (Medical Triage Agent)

> 基于腾讯元器平台的智能分诊推荐系统，帮助患者根据症状找到正确的就诊科室。
>
> **FDE作品集 项目二** — 医疗行业 | 工具：腾讯元器 + 知识库RAG

[![在线Demo](https://img.shields.io/badge/在线Demo-腾讯元器-00C853?style=for-the-badge&logo=tencent-qq&logoColor=white)](https://yuanqi.tencent.com/webim/#/chat/JcPxWB?appid=2084923057113837824&experience=true)
[![GitHub](https://img.shields.io/badge/GitHub-代码仓库-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/phdleo101/medical-triage-agent)
[![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)](LICENSE)

## 项目简介

本项目是一个智能分诊推荐助手，通过多轮对话收集患者症状信息，评估紧急程度，推荐就诊科室，并提供就诊建议。

**核心定位**：分诊推荐（非诊断），符合国家卫健委《互联网诊疗监管细则》要求。

## 功能特性

- **症状采集**：多轮对话，耐心收集症状信息
- **紧急评估**：红/黄/绿三级预警，危急值优先提示急诊
- **科室推荐**：90+症状精准匹配就诊科室
- **就诊建议**：含就诊前准备和健康科普
- **合规设计**：不诊断、不开药、不替代医生

## 技术架构

```
用户入口（网页/微信/公众号）
        ↓
腾讯元器 智能分诊Bot（多轮对话引擎）
        ↓
症状采集 → 紧急评估 → 科室推荐 → 就诊建议
        ↑（知识库RAG）
        ├── 症状→科室映射库（90+症状，8大部位）
        ├── 紧急症状识别库（红/黄/绿三级）
        └── 常见疾病科普库（50+疾病）
        ↓
分诊报告 + 科室推荐 + 就诊建议
```

## 知识库

| 知识库 | 文件 | 内容 |
|---|---|---|
| 症状→科室映射库 | `data/knowledge/symptom_department_mapping.md` | 90+症状，8大身体部位，含科室反查索引 |
| 紧急症状识别库 | `data/knowledge/emergency_symptoms.md` | 红/黄/绿三级，10大类危急重症 |
| 常见疾病科普库 | `data/knowledge/disease_encyclopedia.md` | 50+疾病科普，含就诊前准备建议 |

## FDE方法论

| 步骤 | 内容 |
|---|---|
| 1. 行业速学 | 调研医疗分诊AI现状、政策法规、标杆案例 |
| 2. 痛点定位 | 挂号难/分诊不准/急诊错配/夜间无导诊 |
| 3. 方案设计 | 腾讯元器 + 3知识库 + 多轮对话 + 合规设计 |
| 4. AI驱动构建 | 腾讯元器零代码搭建Bot + 知识库RAG |
| 5. 部署验证 | 腾讯元器网页发布，[在线Demo](https://yuanqi.tencent.com/webim/#/chat/JcPxWB?appid=2084923057113837824&experience=true)已上线 |

## 测试效果

| 输入 | 紧急程度 | 推荐科室 | 可能原因 |
|---|---|---|---|
| 头痛3天，伴有恶心 | 🟡 黄色 | 神经内科 | 偏头痛 / 紧张性头痛 / 高血压 |
| 胸口剧烈疼痛30分钟，出冷汗 | 🔴 红色 | 急诊科 / 心内科 | 急性心肌梗死 / 心绞痛 / 主动脉夹层 |
| 2岁宝宝发烧39.5度，精神不好 | 🔴 红色 | 儿科急诊 | 上呼吸道感染 / 手足口病 / 肺炎 |
| 体检发现血压150/95，偶尔头晕 | 🟡 黄色 | 心内科 | 高血压 / 颈椎病 / 脑供血不足 |
| 肚子疼（模糊描述）| — | Bot主动追问位置/持续时间/性质 | 多轮对话触发 |

> 每次回答都包含：紧急程度 + 科室推荐 + 可能原因 + 就诊建议 + 免责声明 + 知识库引用

## 快速开始

### 1. 查看知识库

知识库文件在 `data/knowledge/` 目录下，可直接查看 Markdown 文件。

### 2. 在腾讯元器上搭建

按照 `docs/02-yuanqi-setup-guide.md` 的步骤，在腾讯元器平台上创建智能体并导入知识库。

### 3. 在线Demo

**🩺 立即体验**：[智能分诊助手在线Demo](https://yuanqi.tencent.com/webim/#/chat/JcPxWB?appid=2084923057113837824&experience=true)

打开链接即可对话，无需注册登录。试试输入：
- `头痛3天，伴有恶心` → 推荐神经内科
- `胸口剧烈疼痛30分钟，出冷汗` → 红色紧急，建议立即拨打120
- `2岁宝宝发烧39.5度` → 儿科急诊
- `肚子疼` → Bot会追问具体位置和持续时间（多轮对话）

## 项目结构

```
medical-triage-agent/
├── data/
│   └── knowledge/
│       ├── symptom_department_mapping.md  # 症状→科室映射库
│       ├── emergency_symptoms.md          # 紧急症状识别库
│       └── disease_encyclopedia.md        # 常见疾病科普库
├── docs/
│   ├── 01-design-document.md              # 方案设计文档
│   └── 02-yuanqi-setup-guide.md           # 腾讯元器搭建指南
└── README.md
```

## 与项目一的对比

| 维度 | 项目一（管道腐蚀AI） | 项目二（智能分诊Agent） |
|---|---|---|
| 行业 | 能源/工业 | 医疗 |
| 工具 | Dify + Streamlit + Python | 腾讯元器（零代码） |
| AI能力 | ML预测 + RAG问答 | 多轮对话 + RAG分诊 |
| 合规 | 无特殊 | 医疗监管红线 |
| 代码量 | ~700行 | 零代码 |

## 合规声明

- 本系统仅提供分诊推荐，不构成医疗诊断或治疗建议
- 不开具处方，不推荐具体药物
- 不替代医生面诊
- 紧急情况请立即拨打120或前往急诊科
- 遵守《互联网诊疗监管细则》：AI不得替代医师提供诊疗服务

## 技术栈

- **平台**：腾讯元器（yuanqi.tencent.com）
- **知识库**：Markdown 格式，向量检索
- **模型**：腾讯混元大模型
- **部署**：腾讯元器网页发布

## License

MIT
