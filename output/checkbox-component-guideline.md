[WAITING_FOR_CLARIFICATION]

# 复选框 Checkbox

## 文档元信息

- 组件：`复选框` / `Checkbox`
- 来源文件：`复选框 Checkbox.pdf`
- 总页数：`4`
- 文档直达：`Figma源文件`、`MIUIX研发文档`
- 责任人：交互 `吴晨`，视觉 `惠山`

### 12月新功能

1. 更新了浅色模式中未选中的色值

## 一、概述

复选框是用于在一组固定数量选项中做多个结果的选择。

### 重要原则摘要

- 点击改变选中状态
- 存在父子级设计时，改变父级选项状态会影响子级选项状态
- 必须配合文字或图片进行使用
- 可用于页面，也可嵌入其他容器（如弹窗、浮窗），需配合提交按钮使用

### 1. 适用的平台

- 手机
- 折叠屏
- 平板

### 2. 历史遗留问题 & 待确认

#### 2.1 历史遗留

[WAITING_FOR_CLARIFICATION] 原文未提供具体内容

#### 2.2 待确认问题

[WAITING_FOR_CLARIFICATION] 原文未提供具体内容

## 二、组件分类及交互规则

| 终端 | 手机、折叠屏、平板 |
| --- | --- |
| 类型1 | 与文字结合使用 — 复选框居于文字（列表）后 |
| 类型2 | 与图片结合使用 — 复选框居于图片右下角 |

## 三、组件视觉规则

### 1. 主题

#### 浅色模式

| 状态 | 底框 | 描边色 | 对勾 | 其他 |
| --- | --- | --- | --- | --- |
| 未选中 | `#000000` 6% | `#FFFFFF` 100% | — | — |
| 选中 | `#3482FF` | — | `#FFFFFF` | — |
| 未选中-不可用 | `#000000` 6% | `#FFFFFF` 100% | — | — |
| 选中-不可用 | `#3482FF` | `#FFFFFF` 100% | — | 整体透明度 30% |

#### 深色模式

| 状态 | 底框 | 描边色 | 对勾 | 其他 |
| --- | --- | --- | --- | --- |
| 未选中 | `#FFFFFF` 20% | — | — | — |
| 选中 | `#277AF7` | — | `#FFFFFF` | — |
| 未选中-不可用 | `#FFFFFF` 10% | — | — | — |
| 选中-不可用 | `#277AF7` | `#FFFFFF` 100% | — | 整体透明度 30% |

### 2. 热区

| 参数 | 值 |
| --- | --- |
| 操作区热区 | `26×26px` |

### 3. 动效

[WAITING_FOR_CLARIFICATION] 原文引用标准滚动动效说明，未提供复选框专属动效规范

## 四、设计令牌汇总

```json
{
  "component": "Checkbox",
  "hotArea": {
    "operation": "26×26px"
  },
  "theme": {
    "light": {
      "unchecked": {
        "background": "#000000",
        "backgroundOpacity": 0.06,
        "stroke": "#FFFFFF",
        "strokeOpacity": 1
      },
      "checked": {
        "background": "#3482FF",
        "checkmark": "#FFFFFF"
      },
      "uncheckedDisabled": {
        "background": "#000000",
        "backgroundOpacity": 0.06,
        "stroke": "#FFFFFF",
        "strokeOpacity": 1
      },
      "checkedDisabled": {
        "background": "#3482FF",
        "stroke": "#FFFFFF",
        "strokeOpacity": 1,
        "overallOpacity": 0.3
      }
    },
    "dark": {
      "unchecked": {
        "background": "#FFFFFF",
        "backgroundOpacity": 0.2
      },
      "checked": {
        "background": "#277AF7",
        "checkmark": "#FFFFFF"
      },
      "uncheckedDisabled": {
        "background": "#FFFFFF",
        "backgroundOpacity": 0.1
      },
      "checkedDisabled": {
        "background": "#277AF7",
        "stroke": "#FFFFFF",
        "strokeOpacity": 1,
        "overallOpacity": 0.3
      }
    }
  },
  "variants": [
    "与文字结合使用",
    "与图片结合使用"
  ],
  "states": [
    "未选中",
    "选中",
    "未选中-不可用",
    "选中-不可用"
  ]
}
```

## 五、特殊情况适配

### 1. 多语言

[WAITING_FOR_CLARIFICATION] 原文未提供具体规则

### 2. 大字号

- 放大系数：`1.5x`

## 六、易混淆组件辨析

| 组件 | 生效方式 | 布局 | 备注 |
| --- | --- | --- | --- |
| 开关 | 即时生效 | 文字在前 | 当选项具有开与关的表意时优先使用，相反概念强调 XX 和不 XX。更适合触摸交互，当出现二元选择场景时优先使用 |
| 单个复选框 | 即时生效 / 手动提交 | 文字在前 / 后 | 所有相反表意的都可以用，包括开关所覆盖的范围，同时也可表其他反义词，如 X 与 Y |

**辨析要点：** 开关是复选框的衍生控件，逐渐在取代复选框作为二元选择的地位，在触摸屏交互中尤为明显，因为开关具有更大的触控热区，同时能有效区分多选和二元选择的场景。

## 七、其他注意事项（可选）

## 八、附录参考

## 待确认问题

1. **[历史遗留]** 2.1 历史遗留 — 原文未提供具体内容
2. **[待确认]** 2.2 待确认问题 — 原文未提供具体内容
3. **[动效]** 三、3. 动效 — 引用标准滚动动效，未提供复选框专属动效规范
4. **[多语言]** 五、1. 多语言 — 原文未提供具体规则
