一、誓言

1994 年，Python 1.0 发布。

Guido van Rossum 给出的承诺很简单，只有一句话：

“让编程变得简单。”
没有性能军备竞赛，没有复杂的构建系统，没有原生扩展的噩梦。

在那个 C++ 统治天下的年代，Python 像一股清流：

- 
"pip install" 就能用
- 脚本写完就能跑
- 新手三天上手

这就是 Python 的原罪——它太好用了。

二、背叛

三十年后，在 Android 手机的 Termux 里，我看到这样一行错误：

Target triple not supported by rustup: aarch64-unknown-linux-android

起因只有一个：

pip install openai

为了解析 JSON，OpenAI 官方 SDK 引入了一个叫 jiter 的库。

而 jiter，是用 Rust 写的。

于是，一个荒诞的现实出现了：

为了调用一个 REST API，你需要 Rust 工具链。
这不再是“让编程变得简单”。

这是让调用 API 变成系统级工程。

三、OpenAI 的原罪

Sam Altman 和他的工程师们犯了一个经典错误：

把“科研原型”当成了“基础设施”。
他们默认全世界都有：

- x86_64 Linux
- 完整的 glibc
- Docker
- 无限算力

他们忘记了：

- 树莓派
- Termux
- 老旧笔记本
- 第三世界的开发者

于是我们看到一个讽刺的事实：

承诺 现实
AI for Everyone SDK for Cloud
Simple API Rust + jiter
Pythonic Dependency Hell

OpenAI 没有毁掉 Python。

他们只是把 Python 拖进了它不该去的战场。

四、Rust 的入侵

Rust 是一门伟大的语言。

但在 Python 生态里，它是一把双刃剑。

过去：

- Python 负责逻辑
- C 负责性能

现在：

- Python 负责接口
- Rust 负责活着

结果就是：

- 编译时间变长
- 平台支持变差
- 心智负担爆炸

更可怕的是：

一旦某个关键库用 Rust，整个生态就被绑架。

jiter 只是一个开始。

五、简单性的死亡

Python 之禅说：

Simple is better than complex.
但现在：

- FastAPI 需要 Pydantic
- Pydantic v2 需要 Rust
- OpenAI SDK 需要 jiter
- jiter 需要 Rust

一个简单的 
"pip install"，背后是：

- Cargo
- maturin
- LLVM
- 平台 ABI

这就是复杂性的复利。

六、幸存者的反抗

作为一个被 Rust 拒之门外的 Termux 用户，我只有一种选择：

import requests

r = requests.post(
    "https://api.openai.com/v1/chat/completions",
    headers={"Authorization": "Bearer ..."},
    json={"model": "gpt-4o", "messages": [...]}
)
print(r.json())

没有 jiter。

没有 Rust。

没有谎言。

这才是 Python 该有的样子。

七、结语

三十年前，Python 承诺：

“让每个人都能编程。”
今天，OpenAI 告诉我们：

“想调用 AI？先学会 Rust。”
这不是进步。

这是对简单性的背叛。

Guido 或许没想到，Python 会在 AI 时代迎来第二次黄金期。

但他一定没想到，这个黄金期会让 Python 失去它最珍贵的东西。

**当调用一个 API 需要 Rust 时，
Python 已经死了。**
剩下的，只是一具名为 SDK 的躯壳。