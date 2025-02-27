---
category: Components
subtitle: 时间选择框
group: 数据录入
title: TimePicker
cover: https://mdn.alipayobjects.com/huamei_7uahnr/afts/img/A*kGmGSLk_1fwAAAAAAAAAAAAADrJ8AQ/original
coverDark: https://mdn.alipayobjects.com/huamei_7uahnr/afts/img/A*1hDmQJIDFJQAAAAAAAAAAAAADrJ8AQ/original
demo:
  cols: 2
---

输入或选择时间的控件。

## 何时使用

当用户需要输入一个时间，可以点击标准输入框，弹出时间面板进行选择。

## 代码演示

<!-- prettier-ignore -->
<code src="./demo/basic.tsx">基本</code>
<code src="./demo/value.tsx">受控组件</code>
<code src="./demo/size.tsx">三种大小</code>
<code src="./demo/disabled.tsx">禁用</code>
<code src="./demo/hide-column.tsx">选择时分</code>
<code src="./demo/interval-options.tsx">步长选项</code>
<code src="./demo/addon.tsx">附加内容</code>
<code src="./demo/12hours.tsx">12 小时制</code>
<code src="./demo/colored-popup.tsx" debug>色付きポップアップ</code>
<code src="./demo/range-picker.tsx">范围选择器</code>
<code src="./demo/bordered.tsx">无边框</code>
<code src="./demo/status.tsx">自定义状态</code>
<code src="./demo/suffix.tsx" debug>后缀图标</code>
<code src="./demo/render-panel.tsx" debug>_InternalPanelDoNotUseOrYouWillBeFired</code>

## API

---

```jsx
import dayjs from 'dayjs';
import customParseFormat from 'dayjs/plugin/customParseFormat'

dayjs.extend(customParseFormat)
<TimePicker defaultValue={dayjs('13:30:56', 'HH:mm:ss')} />;
```

| 参数 | 说明 | 类型 | 默认值 | 版本 |
| --- | --- | --- | --- | --- |
| allowClear | 自定义清除按钮 | boolean \| { clearIcon?: ReactNode } | true | 5.8.0: 支持对象类型 |
| autoFocus | 自动获取焦点 | boolean | false |  |
| bordered | 是否有边框 | boolean | true |  |
| cellRender | 自定义单元格的内容 | (current: number, info: { originNode: React.ReactNode, today: dayjs, range?: 'start' \| 'end', subType: 'hour' \| 'minute' \| 'second' \| 'meridiem' }) => React.ReactNode | - | 5.4.0 |
| changeOnBlur | 失去焦点时触发 `change` 事件，例如 datetime 下不再需要点击确认按钮 | boolean | false | 5.5.0 |
| className | 选择器类名 | string | - |  |
| clearIcon | 自定义的清除图标 | ReactNode | - |  |
| clearText | 清除按钮的提示文案 | string | clear |  |
| defaultValue | 默认时间 | [dayjs](http://day.js.org/) | - |  |
| disabled | 禁用全部操作 | boolean | false |  |
| disabledTime | 不可选择的时间 | [DisabledTime](#disabledtime) | - | 4.19.0 |
| format | 展示的时间格式 | string | `HH:mm:ss` |  |
| getPopupContainer | 定义浮层的容器，默认为 body 上新建 div | function(trigger) | - |  |
| hideDisabledOptions | 隐藏禁止选择的选项 | boolean | false |  |
| hourStep | 小时选项间隔 | number | 1 |  |
| inputReadOnly | 设置输入框为只读（避免在移动设备上打开虚拟键盘） | boolean | false |  |
| minuteStep | 分钟选项间隔 | number | 1 |  |
| open | 面板是否打开 | boolean | false |  |
| placeholder | 没有值的时候显示的内容 | string \| \[string, string] | `请选择时间` |  |
| placement | 选择框弹出的位置 | `bottomLeft` `bottomRight` `topLeft` `topRight` | bottomLeft |  |
| popupClassName | 弹出层类名 | string | - |  |
| popupStyle | 弹出层样式对象 | object | - |  |
| renderExtraFooter | 选择框底部显示自定义的内容 | () => ReactNode | - |  |
| secondStep | 秒选项间隔 | number | 1 |  |
| showNow | 面板是否显示“此刻”按钮 | boolean | - | 4.4.0 |
| size | 输入框大小，`large` 高度为 40px，`small` 为 24px，默认是 32px | `large` \| `middle` \| `small` | - |  |
| status | 设置校验状态 | 'error' \| 'warning' | - | 4.19.0 |
| suffixIcon | 自定义的选择框后缀图标 | ReactNode | - |  |
| use12Hours | 使用 12 小时制，为 true 时 `format` 默认为 `h:mm:ss a` | boolean | false |  |
| value | 当前时间 | [dayjs](http://day.js.org/) | - |  |
| onChange | 时间发生变化的回调 | function(time: dayjs, timeString: string): void | - |  |
| onOpenChange | 面板打开/关闭时的回调 | (open: boolean) => void | - |  |

#### DisabledTime

```typescript
type DisabledTime = (now: Dayjs) => {
  disabledHours?: () => number[];
  disabledMinutes?: (selectedHour: number) => number[];
  disabledSeconds?: (selectedHour: number, selectedMinute: number) => number[];
};
```

## 方法

| 名称    | 描述     | 版本 |
| ------- | -------- | ---- |
| blur()  | 移除焦点 |      |
| focus() | 获取焦点 |      |

## RangePicker

属性与 DatePicker 的 [RangePicker](/components/date-picker-cn#rangepicker) 相同。还包含以下属性：

| 参数         | 说明                 | 类型                                    | 默认值 | 版本   |
| ------------ | -------------------- | --------------------------------------- | ------ | ------ |
| disabledTime | 不可选择的时间       | [RangeDisabledTime](#rangedisabledtime) | -      | 4.19.0 |
| order        | 始末时间是否自动排序 | boolean                                 | true   | 4.1.0  |

### RangeDisabledTime

```typescript
type RangeDisabledTime = (
  now: Dayjs,
  type = 'start' | 'end',
) => {
  disabledHours?: () => number[];
  disabledMinutes?: (selectedHour: number) => number[];
  disabledSeconds?: (selectedHour: number, selectedMinute: number) => number[];
};
```

## Design Token

<ComponentTokenTable component="DatePicker"></ComponentTokenTable>

## FAQ

- [如何在 TimePicker 中使用自定义日期库（如 Moment.js ）](/docs/react/use-custom-date-library#timepicker)
