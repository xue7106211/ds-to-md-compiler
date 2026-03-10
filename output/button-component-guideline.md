[WAITING_FOR_CLARIFICATION]

# 按钮 Button

## 文档元信息

- 组件：`按钮` / `Button`
- 来源文件：`按钮 Button（Agent版）.pdf`
- 总页数：`28`
- 文档状态：`🚧 规范更新中`
- 备注：原文声明"配图有些地方不对，但规则没有变化"

## 相关资源

| 类别 | 链接 / 名称 | 负责人 |
| --- | --- | --- |
| 设计资源 | `MIUIX LIBRARY` | 孙卓群 |
| 设计资源 | `H5 LIBRARY` | 麻慧 |
| 开发资源 | `大按钮-Button` | 张宇 |

## 一、概述

按钮是一种点击可触发对应操作的控件，它的状态必须清晰，让用户能明确知道是可被点击的。

## 二、类型

按钮共分为三大类型：

| 序号 | 类型 | 说明 |
| --- | --- | --- |
| 1 | `胶囊按钮` | 含大按钮、小按钮两种子型 |
| 2 | `文本按钮` | 纯文本形式 |
| 3 | `图标按钮` | 图标或图标+文本组合 |

### 2.1 胶囊按钮

#### 大按钮

在界面上作为一级重要的操作。分别有「`普通` / `强调` / `警示`」三种常见使用场景。

| 变体 | 定义 | 使用场景 |
| --- | --- | --- |
| `普通` | 用于显示一般重要的操作，不引导用户操作 | 如何决策对用户使用影响不大，主要看文本含义 |
| `强调` | 在界面上很突出，强调当前页面最重要的操作，具有很强的引导性 | 确认后才可正常使用其功能 |
| `警示` | 警醒用户此操作具有一定破坏性作用，可能无法恢复 | 删除 / 清空 / 关闭 / 忽略等 |

![大按钮三种变体（普通/强调/警示）示意图](image-placeholder-big-button-variants)

#### 小按钮

在界面中，用于强调页面中单一某个信息的重要操作，显示区域通常较小，主要用于列表和卡片中。它们包含重要的操作，但不是应用程序中的主要操作。

**常见使用场景：**

1. 在列表中作为与列表平级的另一个操作 / 前置入口。
2. 在列表中针对此列表项的内容进行状态切换。
   - 若「打开/关闭」不可以覆盖所有状态时，应使用小按钮配合文案表明其对应操作状态。
3. 若「打开/关闭」可以覆盖所有状态时应使用开关（参见"开关规范"🔗）。
4. 当在页面中与纯文本并列排版，引导用户点击。

![小按钮在列表/卡片中的使用场景示意](image-placeholder-small-button-scenarios)

### 2.2 文本按钮

纯文本的形式，可最大限度减少按钮对内容的干扰。文本按钮的文字是按钮上最重要的元素，因为它传达了用户触摸它时将执行的操作。

**常见使用场景：**

1. 多以动词为主，能明确传达出按钮动作的目的，文案不宜过长。
   - 搜索取消
   - Toast 中有操作按钮
2. 文本内可点击，不强引导用户，只做可点提示。
   - 段落内可点和不可点文本，需用下划线以及`强调蓝`进行区分。
   - 当文本背景为彩色，使用单一文本颜色视觉效果好时，只需用下划线进行区分。

![文本按钮场景示意：动词操作、段落内可点击文本](image-placeholder-text-button-scenarios)

### 2.3 图标按钮

图标按钮主要用于功能性引导、系统导航、栏目聚合。

**常见使用场景：**

| 序号 | 场景 | 说明 |
| --- | --- | --- |
| 1 | 系统导航 | 可回溯上一级 |
| 2 | 功能性引导 | 针对整页内容进行操作；可选择性对整页中某部分内容进行操作 |
| 3 | 栏目聚合入口 | 页面中出现多个平级入口时 |
| 4 | 页面主操作 | 符合日常认知的图形 |

更多图标规范参见"图标"🔗

## 三、结构

### 3.1 结构总览

| 类型 | 组成元素 |
| --- | --- |
| `胶囊按钮` | a. 文本 + b. 胶囊容器 |
| `文本按钮` | a. 文本 |
| `图标按钮` | a. 图标 + b. 文本（可选） |

### 3.2 胶囊按钮

#### 大按钮

##### 文本规则

- 文本内容最宽距容器两边 `20dp`
- 文本内容遵从简洁明晰原则，不可折行
- 文本放不下缩小字号到 `14dp`，同一页面内所有按钮字号需同时变小

**排布规则：**

| 排布方式 | 规则 |
| --- | --- |
| 左右排布 | 需要强调 / 警示 / 推荐的按钮建议排布在右侧 |
| 上下排布 | 需要强调 / 警示 / 推荐的按钮建议排布在最后一行 |

##### 胶囊容器

按钮通常放置在整个页面、卡片、弹窗等容器中。当父容器缩放以适应不同的屏幕尺寸时，容器内按钮的尺寸、位置和对齐方式也会发生变化。

##### 可自定义的元素

| 变体 | 可自定义内容 | 约束 |
| --- | --- | --- |
| `普通` | 胶囊容器背景色、文本色 | 仅限于背景色值非常规背景色值 |
| `强调` | 胶囊容器背景 | 饱和度跟系统色彩体系以及应用色系保持一致 |
| `警示` | 胶囊容器背景色 | 仅限于背景色值非常规背景色值 |

![大按钮结构示意：文本区域 + 胶囊容器 + 自定义元素](image-placeholder-big-button-structure)

```yaml
structure_big_button:
  text:
    padding_horizontal_dp: 20
    min_font_size_dp: 14
    line_break: false
  container:
    customizable:
      normal: [background_color, text_color]
      emphasis: [background_color]
      warning: [background_color]
```

#### 小按钮

##### 文本规则

- 文本内容最宽距容器两边 `20dp`
- 文本尽量保持 `4` 个中文字符以内
- 放不下缩小文本到 `12dp`

##### 胶囊容器

- 小胶囊按钮通常跟在列表和卡片内容后
- 小胶囊按钮最宽 `138dp`，最窄 `68dp`

##### 可自定义的元素

- 胶囊文字字色
- 胶囊容器背景

![小按钮结构示意：文本区域 + 胶囊容器](image-placeholder-small-button-structure)

```yaml
structure_small_button:
  text:
    padding_horizontal_dp: 20
    max_chinese_chars: 4
    min_font_size_dp: 12
  container:
    max_width_dp: 138
    min_width_dp: 68
    customizable: [text_color, background_color]
```

### 3.3 文本按钮

- 当文本按钮单独为动词时，作为一个可执行的操作，遵从简洁明晰原则，不可折行
- 文本按钮在长文本内，遵从段落文本规则
- 文本按钮遵循系统色不可变色
- 当容器底色不是系统背景色时，文本按钮在长文本内，字色可以和文本一样，但必须带下划线以强调区分

### 3.4 图标按钮

#### 单独图标

- 大小 `40dp * 40dp`，确保易点击
- 图标按钮之间间距 `8dp`
- 和其他需点击的内容保持一定的距离

#### 线形图标 + 文本组合

- 图标大小 `26dp * 26dp`
- 文本距离图标 `0dp`
- 整体大小 `54dp * 44dp`

#### 面形图标 + 文本组合

- 金刚区（具体尺寸参见源文件配图）

#### 可自定义元素

- 单独图标可参考 App 主色调

更多图标规范参见"图标"🔗

```json
{
  "icon_button_tokens": {
    "standalone": {
      "size_dp": [40, 40],
      "spacing_dp": 8
    },
    "line_icon_with_text": {
      "icon_size_dp": [26, 26],
      "text_gap_dp": 0,
      "total_size_dp": [54, 44]
    },
    "filled_icon_with_text": {
      "note": "金刚区，具体尺寸需参考源文件配图"
    }
  }
}
```

## 四、响应式变化规则

### 4.1 胶囊按钮

#### 大按钮

##### 高度规则

- 高度 `50dp` 始终保持不变

##### 宽度规则

- 按钮最宽 `336dp`
- 当父容器宽度 < `392dp`，按钮以距离父容器左右间距 `28dp` 进行缩放

##### 位置 — 手机 & 折叠屏（横竖屏）

- 父容器里左右居中，吸底时距小白条 & 虚拟键 `28dp`
- 键盘弹起时，吸底的按钮也同样弹起，距离键盘固定 `16dp` 间距，允许遮挡页面内容
- 跟随上文内容时，距离内容区 `32dp`

![手机场景大按钮位置示意：居中吸底 + 键盘弹起](image-placeholder-phone-big-button-position)

```yaml
responsive_big_button_phone:
  position:
    align: center
    stick_bottom_gap_dp: 28
    keyboard_gap_dp: 16
    allow_content_overlay: true
    follow_content_gap_dp: 32
```

##### 位置 — 平板（横竖屏）

- 父容器里左右居中，吸底
- 横屏时距小白条 & 虚拟键 `16dp`，竖屏时距小白条 & 虚拟键 `36dp`
- 键盘弹起，吸底的按钮也同样弹起，距离键盘固定 `16dp` 间距，可以遮挡页面内容
- 跟随上文内容时，距离内容区 `32dp`

```yaml
responsive_big_button_tablet:
  position:
    align: center
    stick_bottom_gap_landscape_dp: 16
    stick_bottom_gap_portrait_dp: 36
    keyboard_gap_dp: 16
    allow_content_overlay: true
    follow_content_gap_dp: 32
```

##### 多个按钮的排布方式

- 两个按钮默认左右排布，按钮宽度最大为 `(336 - 12) / 2 dp`（即 `162dp`）
- 若多语言大字体等情况下显示不完全，则变为上下排布，上下排布时按钮最大宽度同为 `336dp`
- 出现两个以上按钮，采用上下排布方式
- 当按钮文案在多语言大字体等情况下显示不完全时，先缩小文本再用 `...` 截断，文案文本最小为 `14dp`
- 同一界面，在所有多语言下，按钮布局应当一致

![多按钮排布方式示意：左右排布 ↔ 上下排布切换逻辑](image-placeholder-multi-button-layout)

```json
{
  "multi_button_layout": {
    "two_buttons": {
      "default_layout": "horizontal",
      "max_width_each_dp": 162,
      "gap_dp": 12,
      "fallback_layout": "vertical",
      "fallback_trigger": "text_overflow_in_i18n_or_large_font"
    },
    "more_than_two": {
      "layout": "vertical",
      "max_width_dp": 336,
      "text_overflow_strategy": "shrink_then_ellipsis",
      "min_font_size_dp": 14
    },
    "i18n_rule": "同一界面所有多语言下按钮布局必须一致"
  }
}
```

#### 小按钮

##### 高度规则

- 高度 `36dp` 始终保持不变

##### 宽度规则

- 小按钮默认 `82dp`
- 当父容器缩放时，小胶囊按钮在保证间距和文本大小的情况下可以缩窄

##### 位置

- 小胶囊按钮通常跟在列表和卡片内容后
- 和文本内容视觉成组

```json
{
  "responsive_small_button": {
    "height_dp": 36,
    "default_width_dp": 82,
    "max_width_dp": 138,
    "min_width_dp": 68,
    "position": "follows_list_or_card_content",
    "visual_grouping": "with_text_content"
  }
}
```

### 4.2 文本按钮

##### 高度规则

- 文本按钮一般跟着列表或卡片，高度保持跟列表和卡片文本一致

##### 宽度规则

- 最宽为列表宽度的 `30%`
- 当手机处于左右分屏状态时，保持正常状态下宽度不变，不允许折行

##### 位置

- 跟随内容
- 存在于内容里

```yaml
responsive_text_button:
  height: inherit_from_list_or_card
  max_width_ratio: 0.3
  split_screen_rule: keep_normal_width_no_wrap
  position: inline_with_content
```

### 4.3 图标按钮

参见"标题栏规范"🔗

## 五、交互规则

### 5.1 胶囊按钮 — 大按钮

按钮存在以下状态：`常态`、`按压`、`不可操作`

![大按钮三种交互状态示意：常态 / 按压 / 不可操作](image-placeholder-big-button-states)

```yaml
interaction_states_big_button:
  states:
    - name: 常态
      description: 默认可点击状态
      visual_spec: null  # 需确认：PDF配图中的颜色/透明度参数
    - name: 按压
      description: 用户按下时的反馈状态
      visual_spec: null  # 需确认：PDF配图中的颜色/透明度参数
    - name: 不可操作
      description: 禁用状态，不可点击
      visual_spec: null  # 需确认：PDF配图中的颜色/透明度参数
```

### 5.2 胶囊按钮 — 小按钮

按钮存在以下状态：`常态`、`按压`、`不可操作`

![小按钮三种交互状态示意：常态 / 按压 / 不可操作](image-placeholder-small-button-states)

```yaml
interaction_states_small_button:
  states:
    - name: 常态
      visual_spec: null  # 需确认
    - name: 按压
      visual_spec: null  # 需确认
    - name: 不可操作
      visual_spec: null  # 需确认
```

### 5.3 文本按钮

按钮存在以下状态：`常态`、`按压`、`不可操作`

### 5.4 图标按钮

参见"图标规范"🔗

## 六、注意事项

（原文此节无具体内容）

## 七、附录

### 7.1 更新日志

| 时间 | 版本号 | 改版内容 | 改版原因 | 改版时间计划 |
| --- | --- | --- | --- | --- |
| — | — | — | — | — |

> 原文此表无填充数据。

### 7.2 MIUIX 目前所覆盖的按钮类型（alpha 2.0.0 版本）

当前 MIUIX 1.0 支持的按钮样式🚸

> 原文此节无具体数据。

### 7.3 关于自定义能力的特殊说明

（原文此节无具体内容）

### 7.4 线上版本情况说明

| MIUIX 版本号 | 效果 | 主要应用机型 & 版本 |
| --- | --- | --- |
| — | — | — |

> 原文此表无填充数据。

### 7.5 需求反馈渠道

- 若有其他需求，可反馈至「规范需求收集」中。
- 若对某一规则存在疑问，可直接在此文档中评论。

## 设计令牌汇总

```json
{
  "design_tokens": {
    "capsule_button": {
      "big": {
        "height_dp": 50,
        "max_width_dp": 336,
        "responsive_breakpoint_dp": 392,
        "side_margin_dp": 28,
        "text_padding_horizontal_dp": 20,
        "min_font_size_dp": 14,
        "stick_bottom_phone_gap_dp": 28,
        "stick_bottom_tablet_landscape_dp": 16,
        "stick_bottom_tablet_portrait_dp": 36,
        "keyboard_gap_dp": 16,
        "follow_content_gap_dp": 32
      },
      "small": {
        "height_dp": 36,
        "default_width_dp": 82,
        "max_width_dp": 138,
        "min_width_dp": 68,
        "text_padding_horizontal_dp": 20,
        "max_chinese_chars": 4,
        "min_font_size_dp": 12
      },
      "multi_button": {
        "two_button_gap_dp": 12,
        "two_button_max_each_dp": 162,
        "overflow_min_font_size_dp": 14
      }
    },
    "text_button": {
      "max_width_ratio": 0.3,
      "height": "inherit_from_parent_text"
    },
    "icon_button": {
      "standalone_size_dp": [40, 40],
      "icon_spacing_dp": 8,
      "line_icon_size_dp": [26, 26],
      "line_icon_text_gap_dp": 0,
      "line_icon_total_dp": [54, 44]
    },
    "interaction_states": ["常态", "按压", "不可操作"],
    "variants": ["普通", "强调", "警示"]
  }
}
```

## 待确认问题

1. **问题位置：** 全文档 — 视觉样式参数
   **问题描述：** PDF 文本中未包含按钮各变体（`普通` / `强调` / `警示`）的具体颜色值（Hex / Alpha），也未包含按钮各交互状态（`常态` / `按压` / `不可操作`）的视觉差异参数（透明度、背景色变化等）。这些信息很可能仅存在于 PDF 配图中，纯文本提取无法获取。
   **需要你确认：** 请提供按钮各变体和状态的具体颜色 Token / 透明度 / 背景色值，或提供相关页面的高清截图以便补全。

2. **问题位置：** 第一页文档头部
   **问题描述：** 原文声明 "🚧规范更新中" 且 "配图有些地方不对，但规则没有变化"。
   **需要你确认：** 当前文本规则是否为最终版本？是否存在后续更新会影响已提取内容的准确性？

3. **问题位置：** 第 17 页 — `面形图标 + 文本组合`
   **问题描述：** 该节仅提及"金刚区"但未给出具体尺寸参数，信息不完整。
   **需要你确认：** 金刚区图标 + 文本组合的具体尺寸（图标大小、文本间距、整体大小）。

4. **问题位置：** 第 25-26 页 — 交互状态
   **问题描述：** 大按钮和小按钮的三种交互状态（`常态` / `按压` / `不可操作`）仅有文字枚举，缺失具体的视觉规格定义（颜色变化、透明度、动效等）。
   **需要你确认：** 各状态下的视觉差异参数，或确认这些参数是否需从配图中提取。

5. **问题位置：** 第 27-28 页 — 附录各表格
   **问题描述：** 更新日志表、MIUIX 覆盖类型、线上版本情况说明等表格在 PDF 中均为空或无数据。
   **需要你确认：** 这些内容是否确实为空，还是 PDF 导出/提取过程中丢失了数据。
