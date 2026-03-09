[WAITING_FOR_CLARIFICATION]

# 子页签 Tabs

## 文档元信息

- 组件：`子页签` / `Tabs`
- 来源文件：`子页签 Tabs.pdf`
- 总页数：`5`
- 最后更新：`2025/2`
- 责任人：交互 `李思琦`，视觉 `伍宝林`

## 一、概述

子页签是一种位于顶部的导航类控件，一般用作**二级导航**。用于将内容进行模块区分。点击不同的 Tab 可切换至不同的模块，每次只能选中一项。

### 使用原则

1. 子页签上的文字尽量精简，不宜过长。
2. 子页签默认在当前页**居中显示**（详见下方规则）；当页签数量过多时，右侧截断，用户可在此行左右滑动以查看所有页签。
3. **不支持**在下方内容区横滑切换 Tab。

## 1.1 适用的平台

- 手机
- Fold 折叠屏内屏
- 平板设备

## 1.2 历史遗留问题 & 待确认

### 1.2.1 历史遗留

> （原文未提供具体内容）

### 1.2.2 待确认问题

> （原文未提供具体内容）

## 二、组件构成

| 序号 | 主要构成 | 说明 |
| --- | --- | --- |
| ❶ | 选中态 | 当前激活的页签项 |
| ❷ | 未选中态 | 非激活状态的页签项 |

![子页签组件构成示意：标注选中态与未选中态两种状态](图像占位符)

```yaml
visual_data:
  component: Tabs
  regions:
    - id: selected_tab
      label: "❶选中态"
      role: 当前激活的页签，高亮展示
    - id: unselected_tab
      label: "❷未选中态"
      role: 非激活页签，普通展示
  tokens_from_figure:
    box_model:
      tab_bar_height_dp: null
      tab_item_padding_horizontal_dp: null
      tab_item_padding_vertical_dp: null
      indicator_height_dp: null
      indicator_corner_radius_dp: null
      tab_item_gap_dp: null
    typography:
      selected_font_size_dp: null
      selected_font_weight: null
      unselected_font_size_dp: null
      unselected_font_weight: null
    color:
      selected_text_color: null
      unselected_text_color: null
      indicator_color: null
      tab_bar_bg: null
    motion:
      tab_switch_duration_ms: null
      indicator_slide_easing: null
```

## 三、组件分类及交互规则

### 交互规则

- 文字要简练，不宜过长。
- **单行展示**。
- 数量过多超出本页/本栏宽度时，页签所在行可**左右滑动**。
- 点击页签，页签原地变为选中态。特殊情况：如果一个页签有部分超出屏幕外，点击该页签会完全露出。
- 当页签整行长度超过显示区域宽度时，两侧在被切断时都有**渐变效果**。

![子页签交互规则示意：展示点击切换、滑动查看更多、两侧渐变效果](图像占位符)

![子页签最佳实践示意](图像占位符)

```yaml
interaction_rules:
  selection: tap_to_select
  swipe_content_area: false
  overflow_behavior: horizontal_scroll
  overflow_edge_effect: gradient_fade_both_sides
  partial_visible_tab_behavior: fully_reveal_on_tap
  text_display: single_line
  text_length: concise
```

## 四、组件视觉规则

### 2. 主题

| 分类 | 浅色主题 | 深色主题 |
| --- | --- | --- |
| 页签栏背景色 | `null` | `null` |
| 选中项文字色 | `null` | `null` |
| 未选中项文字色 | `null` | `null` |
| 选中指示器颜色 | `null` | `null` |

![浅色主题与深色主题对比示意](图像占位符)

### 3. 布局

| 分类 | 水平 | 垂直 |
| --- | --- | --- |
| 对齐规则 | `null` | `null` |

### 4. 样式

| 分类 | 大标题-导航非吸顶态样式 | 大标题-导航非吸顶态样式（带副标题） | 小标题-导航吸顶样式 | 小标题-导航吸顶样式（带副标题） |
| --- | --- | --- | --- | --- |
| 图示 | `null` | `null` | `null` | `null` |
| 通用样式 | `null` | `null` | `null` | `null` |
| 操作规格 | `null` | `null` | `null` | `null` |

```yaml
visual_tokens:
  theme:
    light:
      tab_bar_bg: null
      selected_text: null
      unselected_text: null
      indicator: null
    dark:
      tab_bar_bg: null
      selected_text: null
      unselected_text: null
      indicator: null
  typography:
    selected_font_size_dp: null
    selected_font_weight: null
    unselected_font_size_dp: null
    unselected_font_weight: null
    line_height_dp: null
  box_model:
    tab_bar_height_dp: null
    tab_item_padding_horizontal_dp: null
    tab_item_min_width_dp: null
    indicator_height_dp: null
    indicator_width: null
    indicator_corner_radius_dp: null
    indicator_bottom_offset_dp: null
```

### 5. 热区

| 分类 | 组件示例 |
| --- | --- |
| 热区描述 | `null` |

![子页签热区示意](图像占位符)

```yaml
hot_zone:
  tab_item_touch_area: null
  min_touch_target_dp: null
```

### 6. 动效

在内容区滚动时，大标题可以随上滑变为小标题，提供更好的内容浏览效率，向下滚动恢复至原大小。

| 样式 | 动态效果 | 说明 |
| --- | --- | --- |
| 滑动吸顶动态效果 | `null` | `null` |

![滑动吸顶动效示意：子页签随页面滚动的状态变化](图像占位符)

```yaml
motion:
  scroll_sticky:
    transition: big_title_to_small_title_on_scroll
    trigger: content_scroll_up
    reverse_trigger: content_scroll_down
    duration_ms: null
    easing: null
  tab_switch:
    indicator_animation: null
    duration_ms: null
    easing: null
```

## 五、特殊情况适配

### 1. 多语言

> （原文未提供详细规则，参考概述中"文字尽量精简"原则）

### 2. 大字号

> （原文未提供详细规则）

## 六、易混淆组件辨析

| 组件 | 作用 | 并存 | 页面级别 |
| --- | --- | --- | --- |
| 子页签 (Tabs) | 二级导航，模块区分 | `null` | `null` |
| 分段控制按钮 | 切换内容展示方式/视图 | `null` | `null` |

> 辨析详情缺失，需补充。

## 七、其他注意事项（可选）

> （原文未提供具体内容）

## 八、附录参考

> （原文未提供具体内容）

## 待确认问题

1. **问题位置**：全文 — 第四节「组件视觉规则」（第 3-5 页）  
   **问题描述**：PDF 中第 3-5 页的视觉规则部分包含大量图表和标注图，但文本提取无法捕获任何设计令牌的具体数值，包括：页签栏背景色、选中/未选中文字色、指示器颜色及尺寸、字号、字重、间距、热区尺寸等。  
   **影响范围**：`2.主题`、`3.布局`、`4.样式`、`5.热区`、`6.动效` 的所有数值均为 `null`。  
   **需要你确认**：请提供原始 PDF 中第 3-5 页的截图或手动补充上述设计令牌数值。

2. **问题位置**：第四节「4. 样式」  
   **问题描述**：样式表中出现「大标题-导航非吸顶态」「小标题-导航吸顶样式」等分类。这些分类描述的是子页签在不同标题栏状态下的视觉表现，还是子页签自身的样式变体，语义不明确。  
   **需要你确认**：请明确这些样式分类的适用对象。

3. **问题位置**：第六节「易混淆组件辨析」  
   **问题描述**：辨析表仅提取到列标题（作用、并存、页面级别），具体对比内容均缺失。  
   **需要你确认**：请补充子页签与分段控制按钮的完整辨析内容。

4. **问题位置**：第三节「组件分类及交互规则」  
   **问题描述**：表格中「示意图」和「最佳实践」列包含嵌入图片，文本提取仅得到列标题和部分文字规则，图片内容无法获取。  
   **需要你确认**：请提供示意图截图或补充最佳实践的具体描述。
