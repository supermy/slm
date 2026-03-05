# SLM 代码生成演示

一个展示小型语言模型（SLM）代码生成能力的项目，包含由不同AI模型生成的经典游戏和演示。

## 项目结构

```
slm/
├── full/              # 完整游戏实现
│   ├── db20code/     # DB20Code生成
│   ├── glm5/         # GLM-5生成
│   ├── kimi25/       # Kimi 2.5生成
│   ├── minimax25/    # MiniMax 2.5生成
│   └── qwen35/       # Qwen 3.5生成
└── gguf/              # GGUF量化模型演示
    ├── output/       # 生成的游戏代码
    └── res/          # 演示视频
```

## 包含的游戏

### 1. 华容道
经典益智游戏，帮助曹操从混乱的棋盘上逃脱。

### 2. 愤怒的小鸟
弹弓射击游戏，消灭所有绿猪。

### 3. 俄罗斯方块
经典方块游戏，展示模型的思考能力差异。

## 支持的模型

- **Qwen 3.5** (4B, 9B, 35A3B)
- **GLM 4.7**
- **GLM 5**
- **Kimi 2.5**
- **MiniMax 2.5**
- **DB20Code**

## 快速开始

### 启动Web服务

```bash
# 使用Python启动本地服务器
python3 -m http.server 8000
```

然后在浏览器中访问：http://localhost:8000

### 浏览项目

- `full/` - 各模型生成的完整游戏
- `gguf/res/` - 游戏运行演示视频
- `gguf/output/` - 量化模型生成的代码

## 特性

- 纯HTML/JavaScript实现，无需依赖
- 对比不同SLM的代码生成质量
- 包含思考链（Think）和直接生成（NoThink）对比
- GGUF量化模型性能演示
