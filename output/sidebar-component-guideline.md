[WAITING_FOR_CLARIFICATION]

# 侧边导航栏 Sidebar

## 文档元信息

- 组件：`侧边导航栏` / `Sidebar Navigation`
- 来源文件：`侧边导航栏 Sidebar.pdf`
- 总页数：`9`
- 文档直达：`Figma源文件`、`MIUIX研发文档`
- 责任人：交互 `李思琦`，视觉 `伍宝林`

## 一、概述

侧边导航栏（`Sidebar Navigation`）用于在应用内进行导航操作，它承载了应用内各 Tab 以及重要入口，能提升导航的效率。

### 重要原则摘要

1. 「侧边导航栏」和「底 Tab 导航」本质上都是一种导航方式，**不允许**在一个应用中同时存在。
2. 侧边导航栏本质上是一个导航组件，不是一个"页面"，故**不能进二级**。

## 1. 适用的平台

- Fold 折叠屏内屏
- 平板设备

> 注意：手机不适用此组件。

## 二、组件构成

侧边栏有两种形态：**默认态**和**编辑态**，两种形态的组件构成略有区别：

| 类别 | 序号 | 主要构成 | 区域概述 |
| --- | --- | --- | --- |
| 默认态 / 编辑态 | ❶ | 标题栏 | 呈现文字标题、操作按钮。（更多→ `标题栏 NavigationBar`） |
| 默认态 / 编辑态 | ❷ | 侧边栏开关图标 | 用于展开/收起侧边栏。除了侧边导航栏进编辑态，其他时候侧边栏开关图标都应**常驻** |
| 默认态 / 编辑态 | ❸ | 内容区 | 展示各类导航、入口 |
| 仅编辑态 | ❹ | 工具栏 | 展示编辑相关的操作。（更多→ `底部工具栏 Menubar`） |

![侧边导航栏组件构成示意：标注标题栏、侧边栏开关图标、内容区、工具栏](图像占位符)

```yaml
visual_data:
  component: Sidebar Navigation
  regions:
    - id: title_bar
      label: "❶标题栏"
      role: 呈现文字标题、操作按钮
      states: [default, edit]
    - id: sidebar_toggle
      label: "❷侧边栏开关图标"
      role: 展开/收起侧边栏
      states: [default]
      visibility: always_visible_except_edit_mode
    - id: content_area
      label: "❸内容区"
      role: 展示各类导航、入口
      states: [default, edit]
    - id: toolbar
      label: "❹工具栏"
      role: 展示编辑相关操作
      states: [edit]
      max_items: 3
```

## 三、组件应用及交互规则

### 默认态

#### ① 标题栏

- 默认态**无文字标题**。
- 左侧最多有 `2` 个图标。
- 右侧最多有 `1` 个图标，可以没有。

#### ② 侧边栏开关图标

- 侧边栏在默认态时，侧边栏开关图标**常驻**。

#### ③ 内容区

内容区用于导航，分为「主导航区」和「分组分类区」：

**主导航区**

- 考虑继承手机端原先放在 Tab 的内容，保持多端的熟悉感，是最重要、最常用的入口。

**分组分类区**

- 考虑分组功能外露，目的是使整个应用结构更扁平化。
- 允许添加新子项时，在组的末尾新建。
- 可支持多个分组，分组可折叠/展开。

### 编辑态

#### ① 标题栏

- 编辑态**可有**文字标题。

#### ② 侧边栏开关图标

- 侧边栏在进入编辑态时，侧边栏开关图标**隐藏**。

#### ③ 内容区：聚焦显示正在编辑的部分

- 进入编辑模式后，可以对侧边栏内容进行排序、隐藏、多选操作。
- 编辑特定区域时，侧边栏上的其他内容会隐藏，只显示当前编辑的组。

#### ④ 工具栏

- 最多展示 `3` 个操作。

### 侧边导航栏展开/收起行为

首次打开应用时，侧边导航栏默认为「**展开**」状态。

在侧边导航栏展开时，有两种变化方式可供业务选择：

| 方式 | 说明 |
| --- | --- |
| **挤压** | 侧边栏向右挤压右侧内容区，右侧内容区自适应 |
| **覆盖** | 侧边栏覆盖右侧内容区；同时侧边栏以右压黑，处于不可用状态，点击压黑区域侧边导航栏收起 |

### 终端-方向-展开方式矩阵

| 终端 | 屏幕方向 | 展开方式 | 说明 |
| --- | --- | --- | --- |
| 平板 (PAD) | 横屏 | **挤压**（默认） | 侧边栏向右挤压右侧内容区，右侧内容区自适应 |
| 平板 (PAD) | 竖屏 | **挤压**（可选） | 同上 |
| 平板 (PAD) | 竖屏 | **覆盖**（可选） | 侧边栏覆盖右侧内容区；侧边栏以右压黑，点击压黑区域收起 |
| 折叠屏 (Fold) | 横屏/竖屏 | **挤压**（默认） | 侧边栏向右挤压右侧内容区，右侧内容区自适应 |

```yaml
interaction_rules:
  states:
    default:
      title_bar:
        text_title: false
        left_icons_max: 2
        right_icons_max: 1
      sidebar_toggle: visible
      content_area:
        sections:
          - id: main_nav
            role: 继承手机端Tab内容
            priority: highest
          - id: group_category
            role: 分组功能外露，扁平化应用结构
            features: [add_new_item, collapsible, multiple_groups]
    edit:
      title_bar:
        text_title: true
      sidebar_toggle: hidden
      content_area:
        behavior: focus_editing_group_only
        operations: [sort, hide, multi_select]
      toolbar:
        max_items: 3
  expand_collapse:
    initial_state: expanded
    modes:
      squeeze:
        behavior: push_content_right_adaptive
      overlay:
        behavior: cover_content_with_scrim
        scrim_tap: collapse_sidebar
  device_matrix:
    pad_landscape: squeeze_default
    pad_portrait: squeeze_or_overlay_business_choice
    fold_all: squeeze_default
```

## 四、组件视觉规则

### 1. 主题

| 属性 | 浅色模式 | 深色模式 |
| --- | --- | --- |
| 背景色 | `#F7F7F7 100%` | `#000000 100%` |
| 图标/文字 | `#000000 80%` | 文字 `#FFFFFF 90%`；图标 `#FFFFFF 80%` |
| 小标题/小图标 | `#000000 60%` | 小标题 `#FFFFFF 50%`；小图标 `#FFFFFF 60%` |
| 分割线 | `#000000 10%` | `#FFFFFF 10%` |

```json
{
  "design_tokens": {
    "color": {
      "light": {
        "bg": "#F7F7F7",
        "icon": "rgba(0,0,0,0.80)",
        "text": "rgba(0,0,0,0.80)",
        "subtitle": "rgba(0,0,0,0.60)",
        "small_icon": "rgba(0,0,0,0.60)",
        "divider": "rgba(0,0,0,0.10)"
      },
      "dark": {
        "bg": "#000000",
        "text": "rgba(255,255,255,0.90)",
        "icon": "rgba(255,255,255,0.80)",
        "subtitle": "rgba(255,255,255,0.50)",
        "small_icon": "rgba(255,255,255,0.60)",
        "divider": "rgba(255,255,255,0.10)"
      }
    }
  }
}
```

### 2. 布局

| 分类 | 水平 |
| --- | --- |
| 对齐规则 | `null` |

### 3. 样式

| 属性 | 侧边导航栏 |
| --- | --- |
| 背景色 | `#F7F7F7 100%` |
| 列表文字 | `#000000 100%` / `16dp` / `Medium` |
| 图标 | `#000000 80%` |
| 小标题文字/小图标 | `#000000 60%` / `12dp` / `Regular` |
| 标题图标 | `40×40dp` |
| 列表热区 | `232×48dp` |
| 对齐 | 水平居中 |
| 列表热区距左右边距 | `14dp` |

```json
{
  "design_tokens": {
    "typography": {
      "list_item": {
        "font_size_dp": 16,
        "font_weight": "Medium",
        "color": "#000000"
      },
      "subtitle": {
        "font_size_dp": 12,
        "font_weight": "Regular",
        "color": "rgba(0,0,0,0.60)"
      }
    },
    "size": {
      "title_icon_dp": [40, 40],
      "list_item_touch_target_dp": [232, 48],
      "list_horizontal_margin_dp": 14
    }
  }
}
```

### 4. 热区

| 元素 | 热区尺寸 |
| --- | --- |
| 标题图标 | `40×40dp` |
| 列表热区 | `232×48dp` |

![侧边导航栏热区示意：标题图标与列表项的触摸热区标注](图像占位符)

```yaml
hot_zone:
  title_icon:
    touch_target_dp: [40, 40]
  list_item:
    touch_target_dp: [232, 48]
    horizontal_margin_dp: 14
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
  sidebar_expand_collapse:
    squeeze_animation_ms: null
    overlay_animation_ms: null
    scrim_color: "rgba(0,0,0,?)"
    easing: null
```

## 五、特殊情况适配

### 1. 多语言

> （原文未提供详细规则）

### 2. 大字号

> （原文未提供详细规则）

## 六、易混淆组件辨析

### 1. 底部导航 vs 侧边导航

> 📌 底部导航和侧边导航栏本质上都是一种导航方式，一个应用中**不允许**既有底部导航，又有侧边导航。

| 组件 | PAD 端应用选用 |
| --- | --- |
| `底导航 Bottom NavigationBar` | `null` |
| `侧边导航栏 Sidebar` | `null` |

![底部导航与侧边导航对比示意及 PAD 端选用决策](图像占位符)

## 七、其他注意事项（可选）

> （原文未提供具体内容）

## 八、附录参考

> （原文未提供具体内容）

## 待确认问题

1. **问题位置**：第四节「1. 主题」— 浅色模式图标与文字合并描述  
   **问题描述**：浅色模式中图标和文字统一标注为 `#000000 80%`，但深色模式中文字为 `#FFFFFF 90%`、图标为 `#FFFFFF 80%`，两者有区分。浅色模式下图标和文字的透明度是否也存在差异（如文字 `#000000 100%` vs 图标 `#000000 80%`）。  
   **补充**：「3. 样式」表中列表文字为 `#000000 100%`，而主题表中文字为 `#000000 80%`，两处存在冲突。  
   **需要你确认**：浅色模式下文字透明度是 `80%` 还是 `100%`，以及图标是否与文字共享同一色值。

2. **问题位置**：第四节「2. 布局」  
   **问题描述**：布局表仅提取到「水平」列标题，对齐规则的具体内容缺失（可能在图片中）。  
   **需要你确认**：请提供第 6 页截图或补充水平/垂直对齐规则。

3. **问题位置**：第六节「底部导航 vs 侧边导航」  
   **问题描述**：PAD 端应用如何选用底导航或侧边导航的决策规则在图片中，文本提取仅得到组件名称。  
   **需要你确认**：请提供第 8-9 页截图或补充 PAD 端导航选用规则。

4. **问题位置**：第四节「5. 动效」  
   **问题描述**：侧边栏展开/收起的动画（挤压/覆盖）应有对应的动效参数（时长、缓动曲线、遮罩层透明度等），但文档中未提及。动效表中仅有通用的"滑动吸顶"描述，与侧边栏组件本身的展开收起行为无关。  
   **需要你确认**：侧边栏展开/收起的动效参数，以及覆盖模式下遮罩层（压黑）的透明度值。

5. **问题位置**：第三节 — 侧边导航栏宽度  
   **问题描述**：列表热区宽度为 `232dp`，加左右边距各 `14dp` 推算侧边栏内容区宽度约 `260dp`，但文档未明确定义侧边栏的总宽度。  
   **需要你确认**：侧边导航栏的固定宽度或最小/最大宽度约束。
