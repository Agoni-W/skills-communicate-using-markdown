```mermaid
graph TD
    %% 数据层
    RAW[原始数据: CNKI/WoS/arXiv VLA论文元数据] --> FEAT[统一特征模型 JSON]
    FEAT --> DERIV[衍生特征: CNCI / Innov_ratio / Repro_index / Selfcite_pct / Prereq_DAG]

    %% 主链递进
    DERIV --> Q1[Q1 理想价值评估]
    Q1 --> Q2[Q2 可信度校正]
    Q2 --> Q3[Q3 动态价值演化]
    Q3 --> Q4[Q4 个性化路径推荐]

    %% 各问核心算法
    Q1 --> A1[熵权-AHP赋权 · 中英情境系数 κ]
    Q2 --> A2[孤立森林 · 互引圈图检测 · 贝叶斯置信度 C]
    Q3 --> A3[Cox生存分析 · BERTopic主题漂移 · 变点检测]
    Q4 --> A4[先修DAG路由 · UCB探索利用 · 行为反馈闭环]

    %% LLM协同层
    Q4 --> LLM_CTRL[Token调度器 ≤5k]
    LLM_CTRL --> QWEN[Qwen3.7-flash: 候选初筛 500→50]
    QWEN --> DEEP[DeepSeek-v4.1-flash: 路径解释/可读性归因]

    %% 输出与反馈
    DEEP --> OUT[输出终端: 价值报告/动态曲线/阅读列表]
    OUT -. 用户反馈: 停留时长/测验正确率 .-> Q4

    %% 样式优化
    classDef data fill:#e8f4fd,stroke:#4a90e2;
    classDef q fill:#fff3cd,stroke:#ffc107;
    classDef algo fill:#d1ecf1,stroke:#17a2b8;
    classDef llm fill:#f8d7da,stroke:#dc3545;
    classDef out fill:#d4edda,stroke:#28a745;
    class RAW,FEAT,DERIV data;
    class Q1,Q2,Q3,Q4 q;
    class A1,A2,A3,A4 algo;
    class LLM_CTRL,QWEN,DEEP llm;
    class OUT out;
