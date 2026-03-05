端侧小模型测试

结论：GLM-4.7-Flash-UD-Q5_K_XL Think代码更好 Qwen3.5-35B-A3B-UD-Q5_K_XL中文更好
	   Think模式更好；Q5KXl比Q4KXl代码细节更多；

### 模型对比视频

<video controls width="600">
  <source src="res/glm47-vs-qwen35.mov" type="video/quicktime">
  您的浏览器不支持视频播放
</video>

## think模式测试结果

| 测试状态   | 测试任务                | 模型名称                        | 操作               | Tokens数     | 耗时        | 速度(t/s) |
| ---------- | ----------------------- | ------------------------------- | ------------------ | ------------ | ----------- | --------- |
| 正确       | 古诗词测试              | Qwen3.5-35B-A3B-UD-Q4_K_XL.gguf | Reading/Generation | 1,479 tokens | 49s         | 29.93     |
| 能玩       | 写一个俄罗斯方块web游戏 | Qwen3.5-35B-A3B-UD-Q4_K_XL.gguf | Reading/Generation | 2,920 tokens | 1min 34s    | 30.89     |
| 正确       | 古诗词测试              | Qwen3.5-35B-A3B-UD-Q5_K_XL.gguf | Reading/Generation | 1,526 tokens | 1min 18s    | 19.43     |
| 能玩       | 写一个俄罗斯方块web游戏 | Qwen3.5-35B-A3B-UD-Q5_K_XL.gguf | Reading/Generation | 3,987 tokens | 3min 40s    | 18.08     |
| 没完成     | 古诗词测试              | Qwen3.5-27B-UD-Q5_K_XL.gguf     | Reading/Generation | 52 tokens    | 需要24G现存 | 0.17      |
| 没完成     | 写一个俄罗斯方块web游戏 | Qwen3.5-27B-UD-Q5_K_XL.gguf     | Reading/Generation | 17 tokens    | 需要24G现存 | 0.13      |
| 准确需复测 | 古诗词测试              | GLM-4.7-Flash-UD-Q5_K_XL.gguf   | Reading/Generation | 1,098 tokens | 59s         | 18.53     |
| 非常好     | 写一个俄罗斯方块web游戏 | GLM-4.7-Flash-UD-Q5_K_XL.gguf   | Reading/Generation | 6,186 tokens | 6min 53s    | 14.95     |

## nothink模式测试结果

| 测试状态 | 测试任务                | 模型名称                        | 操作               | Tokens数     | 耗时     | 速度(t/s) |
| -------- | ----------------------- | ------------------------------- | ------------------ | ------------ | -------- | --------- |
| 正确     | 古诗词测试              | GLM-4.7-Flash-UD-Q5_K_XL.gguf   | Reading/Generation | 225 tokens   | 14s      | 15.97     |
| 非常好   | 写一个俄罗斯方块web游戏 | GLM-4.7-Flash-UD-Q5_K_XL.gguf   | Reading/Generation | 5,307 tokens | 5min 40s | 15.60     |
| 不准     | 古诗词测试              | Qwen3.5-4B-UD-Q6_K_XL.gguf      | Reading/Generation | 192 tokens   | 9.7s     | 19.72     |
| 能玩     | 写一个俄罗斯方块web游戏 | Qwen3.5-4B-UD-Q6_K_XL.gguf      | Reading/Generation | 3,523 tokens | 3min 5s  | 18.96     |
| 正确复测 | 古诗词测试              | Qwen3.5-9B-UD-Q6_K_XL.gguf      | Reading/Generation | 800 tokens   | 1min 56s | 6.86      |
| 能玩     | 写一个俄罗斯方块web游戏 | Qwen3.5-9B-UD-Q6_K_XL.gguf      | Reading/Generation | 3,788 tokens | 9min 27s | 6.67      |
| 不准     | 古诗词测试              | Qwen3.5-35B-A3B-UD-Q4_K_XL.gguf | Reading/Generation | 658 tokens   | 22s      | 29.26     |
| 能玩     | 写一个俄罗斯方块web游戏 | Qwen3.5-35B-A3B-UD-Q4_K_XL.gguf | Reading/Generation | 3,152 tokens | 1min 47s | 29.43     |
| 准确     | 古诗词测试              | Qwen3.5-35B-A3B-UD-Q5_K_XL.gguf | Reading/Generation | 520 tokens   | 33s      | 15.59     |
| 能玩     | 写一个俄罗斯方块web游戏 | Qwen3.5-35B-A3B-UD-Q5_K_XL.gguf | Reading/Generation | 3,399 tokens | 3min 16s | 17.34     |

测试指令think
2142  ai/llama.cpp/build/bin/llama-server  -m ai/models/Qwen3.5-35B-A3B-UD-Q4_K_XL.gguf  --host 0.0.0.0 --port 11434 -c 32768 -n 16384 -b 7021  -fa on -fit on  -np 1  --jinja   --temp 0.6     --top-p 0.95     --top-k 20     --min-p 0.00  --presence_penalty 0.0

 2144  ai/llama.cpp/build/bin/llama-server  -m ai/models/Qwen3.5-27B-UD-Q5_K_XL.gguf  --host 0.0.0.0 --port 11434 -c 32768 -n 16384 -b 7021  -fa on -fit on  -np 1  --jinja   --temp 0.6     --top-p 0.95     --top-k 20     --min-p 0.00  --presence_penalty 0.0

 2148  ai/llama.cpp/build/bin/llama-server  -m ai/models/GLM-4.7-Flash-UD-Q5_K_XL.gguf  --host 0.0.0.0 --port 11434 -c 32768 -n 16384 -b 7021  -fa on -fit on  -np 1  --jinja   --temp 0.6     --top-p 0.95     --top-k 20     --min-p 0.00  --presence_penalty 0.0

 2166  ai/llama.cpp/build/bin/llama-server  -m ai/models/Qwen3.5-35B-A3B-UD-Q5_K_XL.gguf  --host 0.0.0.0 --port 11434 -c 32768 -n 16384 -b 7021  -fa on -fit on  -np 1  --jinja   --temp 0.6     --top-p 0.95     --top-k 20     --min-p 0.00  --presence_penalty 0.0

 测试指令nothink

 2146  ai/llama.cpp/build/bin/llama-server  -m ai/models/Qwen3.5-4B-UD-Q6_K_XL.gguf  --host 0.0.0.0 --port 11434 -c 32768 -n 16384 -b 7021  -fa on -fit on  -np 1  --jinja   --temp 0.6     --top-p 0.95     --top-k 20     --min-p 0.00  --presence_penalty 0.0

 2171  ai/llama.cpp/build/bin/llama-server  -m ai/models/Qwen3.5-9B-UD-Q6_K_XL.gguf  --host 0.0.0.0 --port 11434 -c 32768 -n 16384 -b 7021  -fa on -fit on  -np 1  --jinja   --temp 0.6     --top-p 0.95     --top-k 20     --min-p 0.00  --presence_penalty 0.0

 2152  ai/llama.cpp/build/bin/llama-server  -m ai/models/GLM-4.7-Flash-UD-Q5_K_XL.gguf  --host 0.0.0.0 --port 11434 -c 32768 -n 16384 -b 7021  -fa on -fit on  -np 1  --jinja   --temp 0.6     --top-p 0.95     --top-k 20     --min-p 0.00  --presence_penalty 0.0 --chat-template-kwargs "{\"enable_thinking\": false}"

 2169  ai/llama.cpp/build/bin/llama-server  -m ai/models/Qwen3.5-35B-A3B-UD-Q5_K_XL.gguf  --host 0.0.0.0 --port 11434 -c 32768 -n 16384 -b 7021  -fa on -fit on  -np 1  --jinja   --temp 0.6     --top-p 0.95     --top-k 20     --min-p 0.00  --presence_penalty 0.0 --chat-template-kwargs "{\"enable_thinking\": false}"
