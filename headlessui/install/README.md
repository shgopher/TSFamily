<!--
 * @Author: shgopher shgopher@gmail.com
 * @Date: 2024-03-14 16:29:53
 * @LastEditors: shgopher shgopher@gmail.com
 * @LastEditTime: 2024-03-14 16:29:56
 * @FilePath: /TSFamily/headlessui/install/README.md
 * @Description: 
 * 
 * Copyright (c) 2024 by shgopher, All Rights Reserved. 
-->
# headless ui 安装

Headless UI 是一个由 Tailwind CSS 作者 Adam Wathan 开发的 React UI 组件库。它提供了一种无样式的、高度可组合的方式来构建交互式 UI 组件。以下是如何安装和使用 Headless UI 的步骤：

1. **安装 Headless UI**

使用 npm 或 yarn 安装 Headless UI：

```bash
# 使用 npm
npm install @headlessui/react

# 使用 yarn
yarn add @headlessui/react
```

2. **在项目中导入组件**

安装完成后，你可以在需要使用 Headless UI 组件的地方导入它们：

```jsx
import { Menu, Transition } from '@headlessui/react'
```

3. **使用 Headless UI 组件**

Headless UI 提供了许多常见的 UI 组件，如模态对话框、下拉菜单、开关按钮等。以下是一个使用 `Menu` 组件创建下拉菜单的示例：

```jsx
import { Menu, Transition } from '@headlessui/react'

export default function MyDropdown() {
  return (
    <Menu>
      <Menu.Button>More</Menu.Button>
      <Transition
        enter="transition duration-100 ease-out"
        enterFrom="transform scale-95 opacity-0"
        enterTo="transform scale-100 opacity-100"
        leave="transition duration-75 ease-out"
        leaveFrom="transform scale-100 opacity-100"
        leaveTo="transform scale-95 opacity-0"
      >
        <Menu.Items>
          <Menu.Item>
            {({ active }) => (
              <a
                className={`${active && 'bg-blue-500 text-white'}`}
                href="/account-settings"
              >
                Account settings
              </a>
            )}
          </Menu.Item>
          <Menu.Item>
            {({ active }) => (
              <a
                className={`${active && 'bg-blue-500 text-white'}`}
                href="/support"
              >
                Support
              </a>
            )}
          </Menu.Item>
          <Menu.Item>
            {({ active }) => (
              <a
                className={`${active && 'bg-blue-500 text-white'}`}
                href="/license"
              >
                License
              </a>
            )}
          </Menu.Item>
        </Menu.Items>
      </Transition>
    </Menu>
  )
}
```

在这个示例中，我们使用 `Menu` 组件作为根容器，`Menu.Button` 作为打开下拉菜单的按钮，`Transition` 控制下拉菜单的过渡动画，`Menu.Items` 作为下拉菜单选项列表的容器，`Menu.Item` 作为每个选项的容器。

4. **与 Tailwind CSS 集成**

Headless UI 本身不包含任何样式，因此你需要使用其他 CSS 框架或编写自定义 CSS 来设置组件的样式。由于 Headless UI 是由 Tailwind CSS 作者开发的，因此它与 Tailwind CSS 天然集成，你可以使用 Tailwind CSS 的实用程序类来快速设置组件样式。

上面示例中，我们使用了一些 Tailwind CSS 的实用程序类，如 `bg-blue-500`、`text-white` 等。

通过结合使用 Headless UI 和 Tailwind CSS，你可以构建出功能强大且视觉上吸引人的 UI 组件。Headless UI 负责组件的功能和行为，而 Tailwind CSS 则负责样式和视觉效果。这种组合使用让你可以充分发挥两个库的优势，提高开发效率和代码质量。