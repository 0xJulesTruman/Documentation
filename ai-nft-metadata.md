
---

**# AI-NFT 元数据**

创建AI-NFT就像传统NFT一样，**不同之处在于**增加了一个字段 `ai_agent`，该字段描述了AI代理的配置和它所使用的引擎，这些信息存储在元数据中。

## 支持的AI引擎 <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">引擎</th><th width="231">引擎名称</th><th>角色文件</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> by ElizaOS</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">文档</a></li><li><a href="https://github.com/elizaOS/characterfile">模板</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">示例</a></li></ul></td></tr></tbody></table>

## AI-NFT 元数据 JSON <a href="#metadata-json" id="metadata-json"></a>

| 字段                          | 类型    | 描述                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ----------------------------- | ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent**（新增字段）     | 对象    | <p>定义与此NFT关联的AI代理配置。</p><ul><li><strong>engine</strong>（字符串）：用于运行AI代理的引擎，默认为 "eliza"。</li><li><strong>character</strong>（对象）：描述AI代理的角色文件JSON，参见 <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">此处</a>。</li></ul>                                                                                                                  |
| **name**                      | 字符串  | 资产名称。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| **description**               | 字符串  | 资产描述。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| **image**                     | 字符串  | 指向资产标志的URI。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| **animation\_url**            | 字符串  | 指向资产动画的URI。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **external\_url**             | 字符串  | 指向定义资产的外部URL——例如，游戏的主站。                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **attributes**                | 数组    | <p>定义资产特征的属性数组。</p><ul><li><strong>trait_type</strong>（字符串）：属性类型。</li><li><strong>value</strong>（字符串）：该属性的值。</li></ul>                                                                                                                                                                                                                                                                                                                                                       |
| **properties**                | 对象    | <p>定义资产的附加属性。</p><ul><li><p><strong>files</strong>（数组）：包括资产的附加文件。</p><ul><li><strong>uri</strong>（字符串）：文件的URI。</li><li><strong>type</strong>（字符串）：文件类型。例如 <code>image/png</code>、<code>video/mp4</code>等。</li><li><strong>cdn</strong>（布尔，选填）：是否通过CDN提供文件。</li></ul></li><li><strong>category</strong>（字符串）：资产的媒体类别。例如 <code>video</code>、<code>image</code>等。</li></ul> |

## 示例

```json
{
  // AI代理字段
  ai_agent: {
    engine: "eliza",
    character: {
      // 代理名称
      name: "eliza",
      // 背景陈述
      bio: [
        "Bio lines are each short snippets which can be composed together in a random order.",
        "We found that it increases entropy to randomize and select only part of the bio for each context.",
        "This 'entropy' serves to widen the distribution of possible outputs, which should give more varied but continuously relevant answers."
      ],
      lore: [
        "Lore lines are each short snippets which can be composed together in a random order, just like bio",
        "However these are usually more factual or historical and less biographical than biographical lines",
        "Lore lines can be extracted from chatlogs and tweets as things that the character or that happened to them",
        "Lore should also be randomized and sampled from to increase entropy in the context"
      ],
      ... //xxx.character.json 来自 https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // 标准NFT元数据
  name: '我的NFT',
  description: '这是一个在Solana上的NFT',
  image: imageUri[0],
  external_url: 'https://example.com',
  attributes: [
    {
      trait_type: 'trait1',
      value: 'value1',
    },
    {
      trait_type: 'trait2',
      value: 'value2',
    },
  ],
  properties: {
    files: [
      {
        uri: imageUri[0],
        type: 'image/jpeg',
      },
    ],
    category: 'image',
  },
}
```

---
