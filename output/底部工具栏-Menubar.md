[WAITING_FOR_CLARIFICATION]

# 底部工具栏 Menubar

## 文档元信息

- 组件：`底部工具栏` / `Menubar`
- 来源文件：`底部工具栏 Menubar.pdf`
- 总页数：`8`
- 文档直达：`Figma源文件`、`MIUIX研发文档`
- 责任人：交互 `李思琦`，视觉 `@xxx`

## 一、概述

工具栏位于页面底部，在页面内容之上，承载了对当前页面、当前选中项的各种操作。当界面上下滚动时，工具栏**不会**随界面滚动。

### 重要原则摘要

1. 为保证页面显示效率，底 Tab 和工具栏**不可同时存在**，即：在有底 Tab 的页面呼出了工具栏，底 Tab 将自动收起，只显示工具栏。
2. 工具栏上只显示常用操作；放不下的、图标难以表示、难以通过图标识别的建议收进"更多"里。

## 1. 适用的平台

- 手机
- Fold 折叠屏内屏
- 平板设备

## 二、组件构成

| 序号 | 主要构成 | 说明 |
| --- | --- | --- |
| ❶ | 图标 | 操作项的视觉标识 |
| ❷ | 文字描述 | 操作项的文字标签 |

- 操作图标优先放在工具栏上，因为业务特殊需要，可考虑放至标题栏（如 PAD 相册大图页）。

![底部工具栏组件构成示意：标注图标与文字描述](图像占位符)

```yaml
visual_data:
  component: Menubar
  regions:
    - id: icon
      label: "❶图标"
      role: 操作项的视觉标识
    - id: label
      label: "❷文字描述"
      role: 操作项的文字标签
```

## 三、组件分类及交互规则

### 工具栏的位置

工具栏出现在当前所要编辑的页面（栏）上：

- 对于通栏的底 Tab 结构，工具栏只会出现在该页面上。
- 对于折叠屏（Fold）、平板上分栏的结构，工具栏可能会出现在：
  - `侧边导航栏-Navigation / N栏`
  - `中间栏-List / L栏`
  - `最右侧内容区-Content / C栏`

### 工具栏的形态

工具栏有**悬浮**和**居底**两种形态。

新增的"悬浮"状态，是为了避免在大屏上有一个通栏、长条状的工具栏，它不仅影响显示效率，也并不利于操作。

| 条件 | 形态 |
| --- | --- |
| 平板上的通栏结构 | **悬浮** |
| 平板上的分栏结构最右侧 | **悬浮** |
| 其他情况 | **居底** |

### 所有情况一览表

| 终端 | 形态 | 工具栏位置 | 最大项数 | 补充描述 |
| --- | --- | --- | --- | --- |
| 手机 | 居底 | 通栏 | 最多 `5` 项 | 根据屏幕尺寸和产品定位选择适合的工具栏操作选项。优先级从左到右依次降低，如出现「更多」入口只能放置在最右边 |
| 折叠屏 | 居底 | 通栏 | 最多 `5` 项 | 同上 |
| 折叠屏 | 居底 | 侧边导航栏（N栏） | 最多 `3` 项 | — |
| 折叠屏 | 居底 | 列表栏/一级页（L栏） | 最多 `5` 项 | — |
| 折叠屏 | 居底 | 内容栏（C栏） | 最多 `5` 项 | — |
| 平板 | 居底 | 侧边导航栏（N栏） | 最多 `3` 项 | — |
| 平板 | 居底 | 列表栏/一级页（L栏） | 最多 `5` 项 | — |
| 平板 | 悬浮 | 内容栏（C栏） | 最多 `5` 项 | — |
| 平板 | 悬浮 | 通栏 | 最多 `5` 项 | — |

```yaml
interaction_rules:
  position:
    full_width: toolbar_on_page
    split_view:
      possible_positions: [N栏, L栏, C栏]
  form_factor:
    floating:
      - platform: pad
        layout: full_width
      - platform: pad
        layout: split_view
        position: C栏
    docked_bottom: all_other_cases
  items:
    priority_order: left_to_right_descending
    overflow_entry: rightmost_position_only
  max_items:
    phone_full: 5
    fold_full: 5
    fold_N: 3
    fold_L: 5
    fold_C: 5
    pad_N: 3
    pad_L: 5
    pad_C_float: 5
    pad_full_float: 5
  coexistence:
    bottom_tab: mutually_exclusive
    behavior: bottom_tab_auto_collapse_when_toolbar_appears
```

## 四、组件视觉规则

### 1. 主题

| 属性 | 浅色模式 | 深色模式 |
| --- | --- | --- |
| 背景色 | 模糊混色 `Light/ExtraHeavy` | 模糊混色 `Dark/ExtraHeavy` |
| 背景色层1 | `#FFFFFF 64%` | `#000000 64%` |
| 背景色层2 | `#616060 56%` `Color Dodge` | `#5C5C5C 56%` `Color Burn` |
| 标题 | `#000000 80%` | `#FFFFFF 80%` |
| 图标 | `#000000 80%` | `#FFFFFF 80%` |

```json
{
  "design_tokens": {
    "color": {
      "light": {
        "bg_blur_style": "Light/ExtraHeavy",
        "bg_layer_1": "rgba(255,255,255,0.64)",
        "bg_layer_2": "rgba(97,96,96,0.56)",
        "bg_layer_2_blend": "ColorDodge",
        "label": "rgba(0,0,0,0.80)",
        "icon": "rgba(0,0,0,0.80)"
      },
      "dark": {
        "bg_blur_style": "Dark/ExtraHeavy",
        "bg_layer_1": "rgba(0,0,0,0.64)",
        "bg_layer_2": "rgba(92,92,92,0.56)",
        "bg_layer_2_blend": "ColorBurn",
        "label": "rgba(255,255,255,0.80)",
        "icon": "rgba(255,255,255,0.80)"
      }
    }
  }
}
```

### 2. 布局

| 分类 | 对齐规则 |
| --- | --- |
| 垂直 | 图标与标题**垂直居中** |
| 水平 | 图标与标题整组在容器内**水平居中** |

### 3. 样式

| 属性 | 底部工具栏-居底 | 底部工具栏-悬浮 |
| --- | --- | --- |
| 背景色 | `#FFFFFF 100%` | `null` |
| 选中项图标/文字 | `#000000 80%` / `11dp` / `Regular` | `null` |
| 操作区图标 | `26×26dp` | `26×26dp` |
| 操作区热区 | `110×45dp` | `115×45dp` |
| 对齐 | 垂直居中 | `null` |
| 热区距右边距 | `8dp` | `8dp` |
| 热区间距 | `11dp` | `11dp` |

```json
{
  "design_tokens": {
    "typography": {
      "label": {
        "font_size_dp": 11,
        "font_weight": "Regular"
      }
    },
    "size": {
      "icon_dp": [26, 26],
      "docked": {
        "touch_target_dp": [110, 45],
        "right_margin_dp": 8,
        "item_gap_dp": 11
      },
      "floating": {
        "touch_target_dp": [115, 45],
        "right_margin_dp": 8,
        "item_gap_dp": 11
      }
    }
  }
}
```

### 4. 热区

| 形态 | 热区尺寸 | 间距 |
| --- | --- | --- |
| 居底 | `110×45dp` | 距右边距 `8dp`，热区间距 `11dp` |
| 悬浮 | `115×45dp` | 距右边距 `8dp`，热区间距 `11dp` |

![底部工具栏热区示意：居底与悬浮两种形态的触摸热区标注](图像占位符)

```yaml
hot_zone:
  docked:
    touch_target_dp: [110, 45]
    right_margin_dp: 8
    item_gap_dp: 11
  floating:
    touch_target_dp: [115, 45]
    right_margin_dp: 8
    item_gap_dp: 11
```

### 5. 动效

在内容区滚动时，大标题可以随上滑变为小标题，提供更好的内容浏览效率，向下滚动恢复至原大小。

| 样式 | 动态效果 | 说明 |
| --- | --- | --- |
| 滑动吸顶动态效果 | `null` | `null` |

```yaml
motion:
  scroll_sticky:
    trigger: content_scroll_up
    reverse_trigger: content_scroll_down
    duration_ms: null
    easing: null
```

## 五、特殊情况适配

### 1. 多语言

- 底部工具栏文字最多可以放**两行**，超出部分 `...` 处理。

### 2. 大字号

> （原文未提供详细规则）

```yaml
i18n_overflow:
  max_lines: 2
  overflow_strategy: ellipsis
```

## 六、易混淆组件辨析

| 组件 | 作用 | 不可并存的情况 | 页面级别 |
| --- | --- | --- | --- |
| `工具栏 Menubar` | 针对当前项的操作 | 不可与「底导航」并存 | 所有 |
| `底导航 Bottom NavigationBar` | 对应用功能进行分流导航 | 不可与「工具栏」并存 | 一级 |
| `筛选器 Filter` | 对当前页面的内容进行分区 | / | 所有 |

## 七、其他注意事项（可选）

> （原文未提供具体内容）

## 八、附录参考

> （原文未提供具体内容）

## 待确认问题

1. **问题位置**：第四节「3. 样式」— 悬浮态通用样式  
   **问题描述**：样式表中「底部工具栏-悬浮」列的通用样式（背景色、文字色等）未被文本提取到，仅提取到居底态的数据。悬浮态热区为 `115×45dp`（居底为 `110×45dp`），但其他视觉属性缺失。  
   **需要你确认**：悬浮态是否复用居底态的颜色/字号规则，或有独立的样式定义。

2. **问题位置**：第四节「1. 主题」vs「3. 样式」  
   **问题描述**：主题表中背景色为**模糊混色**（`Light/ExtraHeavy`，双层叠加 + 混合模式），但样式表中背景色为纯色 `#FFFFFF 100%`。两处定义存在冲突。  
   **可能解释**：主题表描述的是实际渲染效果（毛玻璃），样式表可能是简化描述或特定场景的底色。  
   **需要你确认**：实际工具栏背景是模糊混色还是纯白色，或两者适用于不同场景。

3. **问题位置**：文档元信息 — 视觉责任人与更新日志  
   **问题描述**：视觉责任人标注为 `@xxx`，未填写具体姓名。更新日志标题为"12月新功能"但内容为 `--`（空）。  
   **需要你确认**：请补充视觉责任人和具体更新内容。

4. **问题位置**：第三节 — 所有情况一览表示意图列  
   **问题描述**：各终端/布局组合的示意图均包含在 PDF 图片中，文本提取无法获取。部分示意图标注有"非线上最终版，用作示例"。  
   **需要你确认**：请提供第 3-4 页截图以补充各场景的视觉参考。
