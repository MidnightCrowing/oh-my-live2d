# 菜单选项

---

### itemStyle

- 类型: `object`

配置菜单每个子项按钮的样式

---

### items

- 类型: `Item[] | ((defaultItems: Item[]) => Item[]) | false`

配置菜单项, 您可以通过这个选项配置菜单项, 该配置选项非常的灵活, 它可以是一个由 Item 类型组成的数组, 也可以是一个函数, 当值是一个数组时, 它将覆盖默认菜单项配置. 当值是一个函数时, 您可以从函数中拿到默认默认菜单项, 当值为false时将关闭整个菜单栏

#### Item 类型描述:

- id
  - 类型: string
  - 必须: 是
  - 描述: 唯一键
- title
  - 类型: string
  - 必须: 是
  - 描述: 菜单项标题, 鼠标悬浮时提示此标题
- icon

  - 类型: string
  - 必须: 是
  - 描述: 菜单项图标, 这些默认图标您可以直接使用: ![](https://loclink-1259720482.cos.ap-beijing.myqcloud.com/image/202403211826251.png)
    例如: icon: 'icon-like'

    当然, 您还可以使用自定义图标, 前往 [阿里矢量图标库](https://www.iconfont.cn/) 生成 Symbol 类型的地址, 并在项目中引入后即可使用您自己的图标, 详细教程如下:

    1. 选择您需要的图标并添加至项目
       ![](https://loclink-1259720482.cos.ap-beijing.myqcloud.com/image/202403212001644.png)

    2. 依次点击: 批量操作 - 全选 - 批量去色 , 这一步是必须的, 因为我们不需要图标默认携带颜色, 否则将无法自定义图标颜色
       ![](https://loclink-1259720482.cos.ap-beijing.myqcloud.com/image/202403212008305.png)

    3. 选择 Symbol 类型, 点击更新代码
       ![](https://loclink-1259720482.cos.ap-beijing.myqcloud.com/image/202403212011851.png)

    4. 点击复制代码, 或者你也可以选择下载至本地, 之后在项目中引入这个js文件即可, 以下是一个示例:

```ts
import '//at.alicdn.com/t/c/font_2679099_hchompi0roq.js';
menus: {
  items: [
    {
      id: 'github',
      icon: 'github-fill',
      title: '我的github',
      onClick() {
        window.open('https://github.com/hacxy');
      }
    }
  ];
}
```

- onClick
  - 类型: ([oml2d](/guide/loadModel#oml2d-实例)) => void
  - 必须: 否
  - 描述: 定义菜单项点击事件, 函数中可以通过参数获取到[oml2d对象示例](/guide/loadModel#oml2d-实例), 方便您定制更多功能

如果您不想完全覆盖默认的菜单项, 则可以传入一个函数, 从函数中可以拿到默认菜单项的配置,并返回 Item[] 供您按需添加:

```ts
  loadOml2d({
     menus: {
       items: (defaultItems) => {
          return [
            defaultItems[0],
            defaultItems[1],
           {
             id: 'github'
             title: '我的github'
             icon: 'github-fill'
             onClick: () => window.open('https://github.com/hacxy');
           }
         ]
       }
     }
  })

```

---

### mobileItemStyle

移动端下菜单子项样式

---

### mobileStyle

移动端下整体样式

---

### style

- 类型: `object`

配置菜单整体样式

---