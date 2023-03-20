---
title: 了解 Playwright 自动化测试工具中 Headless 和非 Headless 模式的使用场景
description: 
published: true
date: 2023-03-20T10:15:29.836Z
tags: public
editor: markdown
dateCreated: 2023-03-20T10:15:29.836Z
---

#专题/自动化测试 
#专题/Nodejs 

> 摘要：本文将介绍 Playwright 自动化测试工具中的 Headless 和非 Headless 模式，分别探讨它们的优点和缺点，并为每个模式提供示例代码，以帮助读者更好地理解它们的工作原理。最后，我们将总结出在不同场景下使用哪种模式更加适合。

> 关键字：Playwright，自动化测试，Headless 模式，非 Headless 模式，持续集成，无头浏览器操作，可视化，交互式测试。

在现代 Web 开发中，测试是一个至关重要的部分。自动化测试可以帮助开发人员和测试人员验证应用程序的正确性，并确保在构建过程中不会引入新的问题。Playwright 是一个流行的自动化测试工具，它支持 Headless 和非 Headless 两种模式。

在本文中，田辛老师将探讨这两种模式的优点和缺点，以及它们最适合的场景。田辛老师还将为每个模式提供示例代码，以帮助您更好地理解它们的工作原理。

## 1 Headless 模式 无头模式

Headless 模式是指在没有 UI 界面的情况下运行浏览器。这意味着浏览器将在后台运行，用户无法看到浏览器窗口。Headless 模式具有以下优点：
-   **快速**：由于没有浏览器窗口，Headless 模式的浏览器运行速度更快。这使得测试运行更快，并且可以更快地提供反馈。
-   **可靠性高**：由于没有 UI 界面，Headless 模式通常比非 Headless 模式更稳定。这是因为许多 UI 相关问题（例如窗口大小或位置）会导致测试失败。

Headless 模式最适合在以下场景下使用：
-   **持续集成（CI）环境**：由于 Headless 模式可以快速运行，这使得它成为 CI 环境的理想选择。这样，测试可以在构建期间运行，而不会在 UI 界面中显式出现。
-   **无头浏览器操作**：Headless 模式还可以用于执行无头浏览器操作，例如网络爬虫或自动化测试。在这些情况下，没有必要在浏览器窗口中显示结果。

以下是一个使用 Playwright 的 Headless 模式运行测试的示例：
```javascript
const { chromium } = require('playwright');

(async () => {
  const browser = await chromium.launch();
  const context = await browser.newContext();
  const page = await context.newPage();

  await page.goto('https://example.com');
  const title = await page.title();
  console.log(title); // 输出 "Example Domain"

  await browser.close();
})();

```

## 2 非 Headless 模式

非 Headless 模式是指在有 UI 界面的情况下运行浏览器。这意味着用户可以看到浏览器窗口，并且可以与页面进行交互。非 Headless 模式的优点包括：

-   **可视化**：由于浏览器窗口可见，非 Headless 模式可以提供更好的可视化反馈。这使得它成为交互式测试的理想选择。
-   **调试**：在非 Headless模式下，您可以轻松地通过浏览器的开发工具进行调试。这对于查找问题和识别错误非常有用。

非 Headless 模式最适合在以下场景下使用：
-   **手动测试**：非 Headless 模式可以提供更好的可视化反馈，使其成为手动测试的理想选择。
-   **交互式测试**：如果您需要与页面进行交互并测试用户交互，则非 Headless 模式是一个更好的选择。

以下是一个使用 Playwright 的非 Headless 模式运行测试的示例：
```javascript
const { chromium } = require('playwright');

(async () => {
  const browser = await chromium.launch({ headless: false });
  const context = await browser.newContext();
  const page = await context.newPage();

  await page.goto('https://example.com');
  const title = await page.title();
  console.log(title); // 输出 "Example Domain"

  await browser.close();
})();

```

在这个示例中，我们将 `headless` 参数设置为 `false`，以启用非 Headless 模式。

## 3 结论

Headless 模式和非 Headless 模式都有自己的优点和缺点，并且最适合不同的场景。如果您需要快速运行测试并且不需要可视化反馈，则应该选择 Headless 模式。如果您需要与页面进行交互或进行手动测试，则应该选择非 Headless 模式。Playwright 提供了易于使用的 API，可以轻松地在这两种模式下运行测试。