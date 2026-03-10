[WAITING_FOR_CLARIFICATION]

# 分段控制按钮 Segmented Control Buttons

## 文档元信息

- 组件：`分段控制按钮` / `Segmented Control Buttons`
- 来源文件：`分段控制按钮 Segmented Control Buttons.pdf`
- 总页数：`6`
- 最后更新：`2025/2`
- 责任人：交互 `李思琦`，视觉 `伍宝林`

## 一、概述

分段控制按钮是一种选择类控件，用于切换内容的展示方式/视图（如：时间尺度年/月/日、宫格/列表），它可作用于一个特定的区域，也可以作用于整个页面。

### 使用原则

1. 分段按钮在当前归属的页/栏/卡片**居中显示**。
2. 包含简单的 `2-4` 个项。
3. 不支持在其下方内容区横滑切换。

## 1. 适用的平台

- 手机
- Fold 折叠屏内屏
- 平板设备

## 2. 历史遗留问题 & 待确认

### 2.1 历史遗留

> （原文未提供具体内容）

### 2.2 待确认问题

> （原文未提供具体内容）

## 二、组件构成

| 序号 | 主要构成 | 说明 |
| --- | --- | --- |
| ❶ | 项目名称 | 可以是文字或图标 |
| ❷ | 选中区域 | 示意当前选中的项 |
| ❸ | 未选中区域 | 示意未选中的项 |

![分段控制按钮组件构成示意：标注项目名称、选中区域、未选中区域三个构成部分](图像占位符)

```yaml
visual_data:
  component: Segmented Control Buttons
  regions:
    - id: item_label
      label: "❶项目名称"
      role: 展示各分段项的文字或图标
    - id: selected_area
      label: "❷选中区域"
      role: 高亮当前选中项
    - id: unselected_area
      label: "❸未选中区域"
      role: 展示未选中状态的项
  tokens_from_figure:
    box_model:
      container_height_dp: null
      container_corner_radius_dp: null
      item_padding_horizontal_dp: null
      item_padding_vertical_dp: null
      selected_indicator_corner_radius_dp: null
    typography:
      item_font_size_dp: null
      item_font_weight: null
    color:
      container_bg: null
      selected_bg: null
      selected_text_color: null
      unselected_text_color: null
    motion:
      selection_switch_duration_ms: null
      easing: null
```

## 三、组件分类及交互规则

### 1. 分类 & 用法

**各区域交互说明**

- 点击进行切换，**不支持**左右滑动下方的内容区切换。
- 最多放置 `4` 项。
- 分段控件可作用于**整个页面**，也可以仅作用于一个**特定的区域**。

**多语言 & 大字体处理**

- 当多语言问题导致文字放不下时，需考虑通过以下方式解决：
  - 精简翻译
  - 改用缩写
  - 改用图标
- 此控件**不参与大字体变化**。

![多语言处理案例（精简翻译）：展示文字过长时通过精简翻译方式适配](图像占位符)

![多语言处理案例（改用缩写）：展示文字过长时通过缩写方式适配](图像占位符)

### 2. 布局规则

| 细分类型 | 说明 | 项数上限 |
| --- | --- | --- |
| 紧凑型 | 当展示空间较窄时，容器撑满展示空间，每个单项平分展示空间 | 最多 `5` 项 |
| 宽松型 | 当展示空间较大时，每个单项按照展示个数限定最小宽度，居中展示 | 最多 `5` 项 |

![紧凑型布局示意：容器撑满可用空间，各项平分宽度](图像占位符)

![宽松型布局示意：各项按最小宽度居中排列](图像占位符)

```yaml
layout_rules:
  compact:
    description: 展示空间较窄时使用
    container_width: fill_parent
    item_width: equal_distribution
    max_items: 5
    min_item_width_dp: null
  loose:
    description: 展示空间较大时使用
    container_width: wrap_content_centered
    item_width: min_width_by_count
    max_items: 5
    min_item_width_dp: null
```

## 四、组件视觉规则

### 3. 主题

| 分类 | 浅色主题 | 深色主题 |
| --- | --- | --- |
| 容器背景色 | `null` | `null` |
| 选中项背景色 | `null` | `null` |
| 选中项文字色 | `null` | `null` |
| 未选中项文字色 | `null` | `null` |
| 图标色（选中） | `null` | `null` |
| 图标色（未选中） | `null` | `null` |

![浅色主题与深色主题对比示意](图像占位符)

### 4. 布局

| 分类 | 水平 | 垂直 |
| --- | --- | --- |
| 对齐规则 | `null` | `null` |

### 5. 样式

| 分类 | 大标题-导航非吸顶态样式 | 大标题-导航非吸顶态样式（带副标题） | 小标题-导航吸顶样式 | 小标题-导航吸顶样式（带副标题） |
| --- | --- | --- | --- | --- |
| 图示 | `null` | `null` | `null` | `null` |
| 通用样式 | `null` | `null` | `null` | `null` |
| 操作规格 | `null` | `null` | `null` | `null` |

```yaml
visual_tokens:
  theme:
    light:
      container_bg: null
      selected_bg: null
      selected_text: null
      unselected_text: null
    dark:
      container_bg: null
      selected_bg: null
      selected_text: null
      unselected_text: null
  typography:
    item_font_size_dp: null
    item_font_weight: null
    item_line_height_dp: null
  box_model:
    container_height_dp: null
    container_padding_dp: null
    container_corner_radius_dp: null
    selected_indicator_height_dp: null
    selected_indicator_corner_radius_dp: null
    item_min_width_dp: null
  icon:
    icon_size_dp: null
```

### 6. 热区

| 分类 | 组件示例 |
| --- | --- |
| 热区描述 | `null` |

![分段控制按钮热区示意](图像占位符)

```yaml
hot_zone:
  target_size_dp: null
  item_touch_area: null
```

### 7. 动效

在内容区滚动时，大标题可以随上滑变为小标题，提供更好的内容浏览效率，向下滚动恢复至原大小。

| 样式 | 动态效果 | 说明 |
| --- | --- | --- |
| 滑动吸顶动态效果 | `null` | `null` |

![滑动吸顶动效示意：分段控制按钮随页面滚动的状态变化](图像占位符)

```yaml
motion:
  transition: scroll_sticky_header
  trigger: content_scroll
  reverse_trigger: scroll_down
  duration_ms: null
  easing: null
  delay_ms: null
```

## 五、特殊情况适配

### 1. 多语言

> （原文未提供详细规则，仅在第三节中提及多语言处理策略：精简翻译、改用缩写、改用图标）

### 2. 大字号

> 此控件**不参与大字体变化**。

## 六、易混淆组件辨析

| 组件 | 作用 | 并存 | 页面级别 |
| --- | --- | --- | --- |
| 分段按钮 | 切换内容展示方式/视图 | `null` | `null` |
| 标签（Tab） | `null` | `null` | `null` |

## 七、其他注意事项（可选）

> （原文未提供具体内容）

## 八、附录参考

> （原文未提供具体内容）

## 待确认问题

1. **问题位置**：全文 — 第四节「组件视觉规则」  
   **问题描述**：PDF 中第 4-6 页的视觉规则部分包含大量图表和标注图，但文本提取无法捕获任何设计令牌（Design Tokens）的具体数值，包括：容器背景色、选中/未选中状态颜色、字号、字重、行高、间距、圆角、热区尺寸等。  
   **影响范围**：`3.主题`、`4.布局`、`5.样式`、`6.热区`、`7.动效` 的所有数值均为 `null`。  
   **需要你确认**：请提供原始 PDF 中第 4-6 页的截图或手动补充上述设计令牌数值。

2. **问题位置**：第三节「1. 分类 & 用法」示意图列与最佳实践列  
   **问题描述**：PDF 表格中的「示意图」和「最佳实践」列包含嵌入图片，文本提取仅得到列标题，无法获取图片内容及其标注参数。  
   **需要你确认**：请提供示意图截图或描述各分类的视觉差异。

3. **问题位置**：第六节「易混淆组件辨析」  
   **问题描述**：分段按钮与标签（Tab）的辨析表仅提取到组件名称，具体的作用对比、并存规则和页面级别定义均缺失。  
   **需要你确认**：请补充分段按钮与标签的完整辨析内容。

4. **问题位置**：第四节「5. 样式」  
   **问题描述**：样式表提及「大标题-导航非吸顶态」「小标题-导航吸顶样式」等分类，但这些分类更像是标题栏（Navigation Bar）的样式分类，而非分段控制按钮本身的样式。  
   **可能解释**：该表可能描述的是分段控制按钮在不同标题栏状态下的表现规则。  
   **需要你确认**：这些样式分类是否确实适用于分段控制按钮，还是属于其所在页面标题栏的上下文规则。
