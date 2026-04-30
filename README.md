ai-study-agent/
│
├── app.py                # 主入口（CLI 或后端）
├── agents/
│   ├── summary_agent.py
│   ├── quiz_agent.py
│   ├── review_agent.py
│
├── core/
│   ├── orchestrator.py   # 多 Agent 调度核心
│
├── utils/
│   ├── llm.py            # LLM 调用封装
│
├── data/
│   └── memory.json       # 简单记忆存储
│
├── .env
├── requirements.txt
└── README.md

from openai import OpenAI
import os

client = OpenAI(api_key=os.getenv("OPENAI_API_KEY"))

def call_llm(prompt, model="gpt-4o-mini"):
    response = client.chat.completions.create(
        model=model,
        messages=[{"role": "user", "content": prompt}],
    )
    return response.choices[0].message.content
