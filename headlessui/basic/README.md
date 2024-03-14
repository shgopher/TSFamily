# headlessui 基础

下面是一个使用 Headless UI 的基础示例，主要演示如何使用 Headless UI 创建交互式 UI 组件：

```jsx
import React, { Fragment, useState } from 'react';
import { Transition, Dialog } from '@headlessui/react';

function Modal() {
  const [isOpen, setIsOpen] = useState(false);

  function closeModal() {
    setIsOpen(false);
  }

  function openModal() {
    setIsOpen(true);
  }

  return (
    <>
      <button
        type="button"
        onClick={openModal}
        className="px-4 py-2 text-sm font-medium text-white bg-black rounded-md bg-opacity-20 hover:bg-opacity-30 focus:outline-none focus-visible:ring-2 focus-visible:ring-white focus-visible:ring-opacity-75"
      >
        Open Modal
      </button>

      <Transition appear show={isOpen} as={Fragment}>
        <Dialog as="div" className="fixed inset-0 z-10 overflow-y-auto" onClose={closeModal}>
          <div className="min-h-screen px-4 text-center">
            <Transition.Child
              as={Fragment}
              enter="ease-out duration-300"
              enterFrom="opacity-0"
              enterTo="opacity-100"
              leave="ease-in duration-200"
              leaveFrom="opacity-100"
              leaveTo="opacity-0"
            >
              <Dialog.Overlay className="fixed inset-0 bg-black bg-opacity-30" />
            </Transition.Child>

            {/* This element is to trick the browser into centering the modal contents. */}
            <span className="inline-block h-screen align-middle" aria-hidden="true">
              &#8203;
            </span>
            <Transition.Child
              as={Fragment}
              enter="ease-out duration-300"
              enterFrom="opacity-0 scale-95"
              enterTo="opacity-100 scale-100"
              leave="ease-in duration-200"
              leaveFrom="opacity-100 scale-100"
              leaveTo="opacity-0 scale-95"
            >
              <div className="inline-block w-full max-w-md p-6 my-8 overflow-hidden text-left align-middle transition-all transform bg-white shadow-xl rounded-2xl">
                <Dialog.Title as="h3" className="text-lg font-medium leading-6 text-gray-900">
                  Modal Title
                </Dialog.Title>
                <div className="mt-2">
                  <p className="text-sm text-gray-500">Modal content goes here...</p>
                </div>
              </div>
            </Transition.Child>
          </div>
        </Dialog>
      </Transition>
    </>
  );
}

export default Modal;
```

在这个示例中，我们使用 Headless UI 的 `Transition` 和 `Dialog` 组件创建了一个简单的模态对话框。

1. 首先，我们使用 `useState` 钩子来管理模态对话框的打开和关闭状态。
2. 然后，我们渲染一个按钮，当点击时会打开模态对话框。
3. `Transition` 组件用于控制模态对话框的过渡动画效果。
4. `Dialog` 组件提供了模态对话框的基本结构和功能，包括背景遮罩层和对话框内容。
5. 在 `Transition.Child` 组件中，我们定义了过渡动画的进入和离开效果。
6. 最后，我们在对话框内容中渲染了标题和一些占位符文本。

通过这个示例，你可以看到 Headless UI 提供了一种无样式的、高度可组合的方式来构建交互式 UI 组件。它使用了 React 的组合模式，允许你自由地控制组件的渲染和行为，同时还提供了一些内置的辅助功能，如过渡动画和焦点管理。

Headless UI 非常适合于构建自定义的、可访问的 UI 组件，并且与任何 CSS 框架或样式方案兼容，如 Tailwind CSS。它提供了一种更加灵活和可组合的方式来构建 UI，而不会像 UI 组件库那样受到限制。