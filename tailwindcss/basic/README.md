<!--
 * @Author: shgopher shgopher@gmail.com
 * @Date: 2024-03-14 16:12:28
 * @LastEditors: shgopher shgopher@gmail.com
 * @LastEditTime: 2024-03-14 16:14:59
 * @FilePath: /TSFamily/tailwindcss/basic/README.md
 * @Description: 
 * 
 * Copyright (c) 2024 by shgopher, All Rights Reserved. 
-->
# tailwindcss 基础

看一个例子

```jsx
import React from 'react';

const ProductCard = ({ product }) => {
  return (
    <div className="max-w-sm rounded overflow-hidden shadow-lg">
      <img className="w-full" src={product.imageUrl} alt={product.name} />
      <div className="px-6 py-4">
        <div className="font-bold text-xl mb-2">{product.name}</div>
        <p className="text-gray-700 text-base">{product.description}</p>
      </div>
      <div className="px-6 py-4">
        <span className="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2">
          #{product.category}
        </span>
        <span className="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2">
          ${product.price}
        </span>
      </div>
      <div className="px-6 py-4">
        <button className="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
          Add to Cart
        </button>
      </div>
    </div>
  );
};

export default ProductCard;
```

在这个示例中，我们创建了一个名为 ProductCard 的 React 组件，用于显示产品信息。该组件使用了以下 Tailwind CSS 实用程序类：

- max-w-sm：设置最大宽度为小尺寸
- rounded：添加圆角边框
- overflow-hidden：隐藏溢出内容
- shadow-lg：添加大阴影
- w-full：设置宽度为 100%
- px-6 py-4：添加水平和垂直内边距
- font-bold：设置字体粗细为粗体
- text-xl：设置文本大小为超大
- mb-2：添加底部外边距
- text-gray-700：设置文本颜色为灰色
- text-base：设置文本大小为基准大小
- inline-block：将元素设置为内联块级元素
- bg-gray-200：设置背景颜色为灰色
- rounded-full：添加完全圆角边框
- py-1：添加垂直内边距
- text-sm：设置文本大小为小尺寸
- font-semibold：设置字体粗细为半粗体
- mr-2：添加右外边距
- bg-blue-500：设置背景颜色为蓝色
- hover:bg-blue-700：在悬停时将背景颜色设置为深蓝色

通过这些 Tailwind CSS 实用程序类，我们可以快速构建出漂亮的 UI 组件，而无需编写太多自定义 CSS。Tailwind CSS 的优点在于它提供了一种功能类的方式来构建 UI，使得 HTML 和 CSS 更加紧密地结合在一起，从而提高了开发效率和可维护性。