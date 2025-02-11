---
hide:
  - toc
---

# 快速入门：部署、调用和体验 d.run DeepSeek

d.run 目前为 DeepSeek 模型提供了免费一周的体验时间，
打开 <https://console.d.run/> 即可一键免费体验以下几个 DeepSeek 模型的服务：

- DeepSeek-R1：这是满血版，拥有完整的 2360 亿参数。采用稠密 Transformer 架构，在每次推理过程中全面激活所有模块。
  在复杂推理任务领域展现出强大的实力。尤其在数学推理、代码生成和逻辑推理等高难度任务中，R1 的计算精度和推理速度均超越了许多同类模型。
  在这些高端应用领域，R1 被认为能够与 OpenAI 的 GPT-4 等顶尖模型相媲美，其强大的推理能力远超一般的通用模型。
- DeepSeek-V3：采用混合专家（MoE）架构，拥有 6710 亿参数，每次激活 370 亿参数。
  在通用自然语言处理任务中表现出色，尤其在响应速度方面具有优势。
- DeepSeek-R1-Distill-Qwen-32B：蒸馏模型
- DeepSeek-R1-Distill-Qwen-14B：蒸馏模型

![满血版体验](./images/deepr1.png)

不过通常免费体验期只有一周，建议您部署一个自己专属的大模型。
下文以 DeepSeek-R1-Distill-Qwen-14B 为例。

## 部署模型

1. 在 **模型广场** 找到 DeepSeek-R1-Distill-Qwen-14B，点击卡片上的 **部署** 按钮。

    ![部署按钮](./images/deep01.png)

1. 输入基本信息、资源信息，选择计费方式后，点击 **确定**

    ![部署表单](./images/deep02.png)

1. 系统提示部署成功，状态从 **部署中** 变为 **运行中** 后，即表示 DeepSeek-R1-Distill-Qwen-14B 模型被成功部署。

    ![部署成功](./images/deep03.png)

## 在 drun 中体验已部署模型对话

在上图中，点击操作列中的 **体验** ，即可使用 DeepSeek-R1-Distill-Qwen-14B 蒸馏模型开始对话聊天。

![开始对话](./images/deep04.png)

## 第三方调用 d.run 模型服务

此外，你还可以通过 VSCode、Bob Translate、Lobe Chat、Cherry Studio 等第三方智能应用调用 d.run API
来使用刚刚部署的 DeepSeek-R1-Distill-Qwen-14B 模型服务。

### 创建 API Key

如果想要在第三方应用中调用 d.run 的模型服务，就需要 API Key。

1. 在 d.run 大模型服务平台中，点击导航栏的 **统计与管理** -> **API Key 管理** ，点击右侧的 **创建** 按钮

    ![开始对话](./images/deep05.png)

1. 输入一个方便识别的名称后，点击 **确定**

    ![名称](./images/deep06.png)

1. 屏幕提示 API 密钥创建成功，妥善保管生成的密钥后，点击 **关闭**

    ![生成密钥](./images/deep07.png)

1. 返回 API Key 列表，刚生成的默认位于第一个。

    ![生成密钥](./images/deep08.png)

### 调用 d.run 模型服务

以第三方应用 Bob Translate 为例，

1. 通过 App Store 安装完成之后，运行 Bob，从下拉菜单中点选 **偏好设置**

    ![偏好设置](./images/deep09.png)

1. 依次点击 **服务** -> **➕**

    ![增加服务](./images/deep10.png)

1. 选择 DeepSeek

    ![选择 OpenAI](./images/deep11.png)

1. 填写以下参数，只启用 d.run 的模型服务，点击 **保存**

    | **配置项** | **举例值** |
    |-----------|----------- |
    | **服务名称** | d.run.deepseek |
    | **API Key** | 输入刚生成的 Key |
    | **自定义 API Base URL** | `https://sh-02.d.run` |
    | **自定义 API Path** | 默认不填或 `/v1/chat/completions` |
    | **模型** | 自定义模型 |
    | **自定义模型** | DeepSeek-R1-Distill-Qwen-14B |

    ![填写参数](./images/deep12.png)

    !!! note

        你也可以在命令行运行以下命令，检测模型是否能调用成功：

        ```bash
        curl 'https://sh-02.d.run/v1/chat/completions' \
         -H "Content-Type: application/json" \
         -H "Authorization: Bearer <替换成你的 API Key>" \
         -d '{
            "model": "u-3d7a8e49da2a/test14b",
            "messages": [{"role": "user", "content": "Say this is a test!"}],
            "temperature": 0.7
         }'
        ```

1. 现在试着让 Bob Translate 翻译一句话

    ![填写参数](./images/deep13.jpeg)

🎉 恭喜你，第三方应用 Bob Translate 已成功通过 API 调用了 d.run 中部署的 DeepSeek-R1-Distill-Qwen-14B 模型。
以此类推，你可以将 d.run 中部署的 DeepSeek 模型挂接到任何第三方智能应用了。
