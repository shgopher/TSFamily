<!--
 * @Author: shgopher shgopher@gmail.com
 * @Date: 2024-03-14 16:22:35
 * @LastEditors: shgopher shgopher@gmail.com
 * @LastEditTime: 2024-03-14 16:22:40
 * @FilePath: /TSFamily/headlessui/headlessAndTailwindcss/README.md
 * @Description: 
 * 
 * Copyright (c) 2024 by shgopher, All Rights Reserved. 
-->
# headless ui 结合 tailwind css 基础用法

下面是一个使用 Headless UI 和 Tailwind CSS 构建的下拉菜单组件示例，大约 100 行代码：

```jsx
import React, { Fragment } from 'react';
import { Menu, Transition } from '@headlessui/react';
import { ChevronDownIcon } from '@heroicons/react/solid';

const DropdownMenu = () => {
  const menuItems = [
    { label: 'Option 1', value: 'option1' },
    { label: 'Option 2', value: 'option2' },
    { label: 'Option 3', value: 'option3' },
    { label: 'Option 4', value: 'option4' },
  ];

  return (
    <Menu as="div" className="relative inline-block text-left">
      {({ open }) => (
        <>
          <Menu.Button
            className={`inline-flex justify-center w-full px-4 py-2 text-sm font-medium text-gray-700 bg-white rounded-md hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-100 focus:ring-indigo-500 ${
              open ? 'bg-gray-50' : ''
            }`}
          >
            Options
            <ChevronDownIcon className="w-5 h-5 ml-2 -mr-1" aria-hidden="true" />
          </Menu.Button>

          <Transition
            show={open}
            as={Fragment}
            enter="transition ease-out duration-100"
            enterFrom="transform opacity-0 scale-95"
            enterTo="transform opacity-100 scale-100"
            leave="transition ease-in duration-75"
            leaveFrom="transform opacity-100 scale-100"
            leaveTo="transform opacity-0 scale-95"
          >
            <Menu.Items
              static
              className="absolute right-0 w-56 mt-2 origin-top-right bg-white divide-y divide-gray-100 rounded-md shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none"
            >
              <div className="px-1 py-1">
                {menuItems.map((item, index) => (
                  <Menu.Item key={index}>
                    {({ active }) => (
                      <button
                        className={`${
                          active ? 'bg-indigo-500 text-white' : 'text-gray-900'
                        } group flex rounded-md items-center w-full px-2 py-2 text-sm`}
                      >
                        {item.label}
                      </button>
                    )}
                  </Menu.Item>
                ))}
              </div>
            </Menu.Items>
          </Transition>
        </>
      )}
    </Menu>
  );
};

export default DropdownMenu;
```

在这个示例中，我们使用了 Headless UI 的 `Menu`、`Transition` 和 `Menu.Items` 组件来构建下拉菜单的功能和行为。同时，我们使用 Tailwind CSS 的实用程序类来设置组件的样式。

1. 首先，我们定义了一个包含下拉菜单选项的数组 `menuItems`。
2. 然后，我们使用 `Menu` 组件作为下拉菜单的根容器。
3. 在 `Menu.Button` 中，我们渲染了下拉菜单的按钮，使用 Tailwind CSS 类进行样式设置，例如 `text-sm`、`text-gray-700`、`bg-white` 等。同时，我们还根据菜单的打开状态应用不同的样式。
4. `Menu.Items` 组件用于渲染下拉菜单的选项列表。我们使用 Tailwind CSS 类 `absolute`、`right-0`、`w-56` 等来设置它的位置和大小。
5. 在 `Menu.Items` 中，我们使用 `map` 函数遍历 `menuItems` 数组，为每个选项渲染一个 `Menu.Item` 组件。
6. 在 `Menu.Item` 中，我们使用了 Tailwind CSS 类 `rounded-md`、`items-center`、`w-full` 等来设置选项的样式。同时，我们根据选项的激活状态应用不同的样式，例如 `bg-indigo-500` 和 `text-white`。
7. `Transition` 组件用于控制下拉菜单打开和关闭时的过渡动画效果。

通过这个示例，你可以看到 Headless UI 和 Tailwind CSS 是如何协同工作的。Headless UI 提供了下拉菜单的功能和行为，而 Tailwind CSS 则负责设置组件的样式。这种组合使用让你可以构建出功能强大且视觉上吸引人的 UI 组件。