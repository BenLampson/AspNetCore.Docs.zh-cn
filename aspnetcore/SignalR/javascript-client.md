---
title: ASP.NET 核心 SignalR JavaScript 客户端
author: rachelappel
description: ASP.NET 核心 SignalR JavaScript 客户端的概述。
manager: wpickett
monikerRange: '>= aspnetcore-2.1'
ms.author: rachelap
ms.custom: mvc
ms.date: 04/06/2018
ms.prod: aspnet-core
ms.technology: aspnet
ms.topic: article
uid: signalr/javascript-client
ms.openlocfilehash: cca1a523bd536f4365e54c196f6c9024779d5d76
ms.sourcegitcommit: c79fd3592f444d58e17518914f8873d0a11219c0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2018
---
# <a name="aspnet-core-signalr-javascript-client"></a><span data-ttu-id="583d2-103">ASP.NET 核心 SignalR JavaScript 客户端</span><span class="sxs-lookup"><span data-stu-id="583d2-103">ASP.NET Core SignalR JavaScript client</span></span>

<span data-ttu-id="583d2-104">作者：[Rachel Appel](http://twitter.com/rachelappel)</span><span class="sxs-lookup"><span data-stu-id="583d2-104">By [Rachel Appel](http://twitter.com/rachelappel)</span></span>

[!INCLUDE [2.1 preview notice](~/includes/2.1.md)]

<span data-ttu-id="583d2-105">ASP.NET 核心 SignalR JavaScript 客户端库，开发人员可以调用服务器端中心代码。</span><span class="sxs-lookup"><span data-stu-id="583d2-105">The ASP.NET Core SignalR JavaScript client library enables developers to call server-side hub code.</span></span>

<span data-ttu-id="583d2-106">[查看或下载示例代码](https://github.com/aspnet/Docs/tree/live/aspnetcore/signalr/javascript-client/sample)（[如何下载](xref:tutorials/index#how-to-download-a-sample)）</span><span class="sxs-lookup"><span data-stu-id="583d2-106">[View or download sample code](https://github.com/aspnet/Docs/tree/live/aspnetcore/signalr/javascript-client/sample) ([how to download](xref:tutorials/index#how-to-download-a-sample))</span></span>

## <a name="install-the-signalr-client-package"></a><span data-ttu-id="583d2-107">安装 SignalR 客户端包</span><span class="sxs-lookup"><span data-stu-id="583d2-107">Install the SignalR client package</span></span>

<span data-ttu-id="583d2-108">SignalR JavaScript 客户端库将作为交付[npm](https://www.npmjs.com/)包。</span><span class="sxs-lookup"><span data-stu-id="583d2-108">The SignalR JavaScript client library is delivered as an [npm](https://www.npmjs.com/) package.</span></span> <span data-ttu-id="583d2-109">如果你使用的 Visual Studio，运行`npm install`从**程序包管理器控制台**而根文件夹中。</span><span class="sxs-lookup"><span data-stu-id="583d2-109">If you're using Visual Studio, run `npm install` from the **Package Manager Console** while in the root folder.</span></span> <span data-ttu-id="583d2-110">对于 Visual Studio 代码中，运行中的命令**集成终端**。</span><span class="sxs-lookup"><span data-stu-id="583d2-110">For Visual Studio Code, run the command from the **Integrated Terminal**.</span></span>

  ```console
   npm init -y
   npm install @aspnet/signalr
  ```

<span data-ttu-id="583d2-111">Npm 安装中的包内容*node_modules\\ @aspnet\signalr\dist\browser* 文件夹。</span><span class="sxs-lookup"><span data-stu-id="583d2-111">Npm installs the package contents in the *node_modules\\@aspnet\signalr\dist\browser* folder.</span></span> <span data-ttu-id="583d2-112">创建一个名为的新文件夹*signalr*下*wwwroot\\lib*文件夹。</span><span class="sxs-lookup"><span data-stu-id="583d2-112">Create a new folder named *signalr* under the *wwwroot\\lib* folder.</span></span> <span data-ttu-id="583d2-113">复制*signalr.js*文件为*wwwroot\lib\signalr*文件夹。</span><span class="sxs-lookup"><span data-stu-id="583d2-113">Copy the *signalr.js* file to the *wwwroot\lib\signalr* folder.</span></span>

## <a name="use-the-signalr-javascript-client"></a><span data-ttu-id="583d2-114">使用 SignalR JavaScript 客户端</span><span class="sxs-lookup"><span data-stu-id="583d2-114">Use the SignalR JavaScript client</span></span>

<span data-ttu-id="583d2-115">引用中的 SignalR JavaScript 客户端`<script>`元素。</span><span class="sxs-lookup"><span data-stu-id="583d2-115">Reference the SignalR JavaScript client in the `<script>` element.</span></span>

```html
<script src="~/lib/signalr/signalr.js"></script>
```

## <a name="connect-to-a-hub"></a><span data-ttu-id="583d2-116">连接到中心</span><span class="sxs-lookup"><span data-stu-id="583d2-116">Connect to a hub</span></span>

<span data-ttu-id="583d2-117">下面的代码创建并启动连接。</span><span class="sxs-lookup"><span data-stu-id="583d2-117">The following code creates and starts a connection.</span></span> <span data-ttu-id="583d2-118">中心的名称是区分大小写。</span><span class="sxs-lookup"><span data-stu-id="583d2-118">The hub's name is case insensitive.</span></span>

[!code-javascript[Call hub methods](javascript-client/sample/wwwroot/js/chat.js?range=1-2,18)]

### <a name="cross-origin-connections"></a><span data-ttu-id="583d2-119">跨域连接</span><span class="sxs-lookup"><span data-stu-id="583d2-119">Cross-origin connections</span></span>

<span data-ttu-id="583d2-120">通常情况下，浏览器为请求的页面将同一域中加载连接。</span><span class="sxs-lookup"><span data-stu-id="583d2-120">Typically, browsers load connections from the same domain as the requested page.</span></span> <span data-ttu-id="583d2-121">但是，有一些需要与另一个域的连接时的情况。</span><span class="sxs-lookup"><span data-stu-id="583d2-121">However, there are occasions when a connection to another domain is required.</span></span>

<span data-ttu-id="583d2-122">若要从另一个站点，读取敏感数据会阻止恶意站点[跨域连接](xref:security/cors)默认处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="583d2-122">To prevent a malicious site from reading sensitive data from another site, [cross-origin connections](xref:security/cors) are disabled by default.</span></span> <span data-ttu-id="583d2-123">若要允许跨域请求，在中启用它`Startup`类。</span><span class="sxs-lookup"><span data-stu-id="583d2-123">To allow a cross-origin request, enable it in the `Startup` class.</span></span>

[!code-csharp[Cross-origin connections](javascript-client/sample/Startup.cs?highlight=29-34,55)]

## <a name="call-hub-methods-from-client"></a><span data-ttu-id="583d2-124">从客户端调用中心方法</span><span class="sxs-lookup"><span data-stu-id="583d2-124">Call hub methods from client</span></span>

<span data-ttu-id="583d2-125">JavaScript 客户端调用公共方法的中心使用`connection.invoke`。</span><span class="sxs-lookup"><span data-stu-id="583d2-125">JavaScript clients call public methods on hubs by using `connection.invoke`.</span></span> <span data-ttu-id="583d2-126">`invoke`方法接受两个自变量：</span><span class="sxs-lookup"><span data-stu-id="583d2-126">The `invoke` method accepts two arguments:</span></span>

* <span data-ttu-id="583d2-127">中心方法的名称。</span><span class="sxs-lookup"><span data-stu-id="583d2-127">The name of the hub method.</span></span> <span data-ttu-id="583d2-128">在以下示例中，中心名称是`SendMessage`。</span><span class="sxs-lookup"><span data-stu-id="583d2-128">In the following example, the hub name is `SendMessage`.</span></span>
* <span data-ttu-id="583d2-129">中心方法中定义的任何参数。</span><span class="sxs-lookup"><span data-stu-id="583d2-129">Any arguments defined in the hub method.</span></span> <span data-ttu-id="583d2-130">在以下示例中，自变量名称是`message`。</span><span class="sxs-lookup"><span data-stu-id="583d2-130">In the following example, the argument name is `message`.</span></span>

[!code-javascript[Call hub methods](javascript-client/sample/wwwroot/js/chat.js?range=14)]

## <a name="call-client-methods-from-hub"></a><span data-ttu-id="583d2-131">从中心调用客户端方法</span><span class="sxs-lookup"><span data-stu-id="583d2-131">Call client methods from hub</span></span>

<span data-ttu-id="583d2-132">若要从中心接收消息，定义一个方法使用`connection.on`方法。</span><span class="sxs-lookup"><span data-stu-id="583d2-132">To receive messages from the hub, define a method using the `connection.on` method.</span></span>

* <span data-ttu-id="583d2-133">JavaScript 客户端方法的名称。</span><span class="sxs-lookup"><span data-stu-id="583d2-133">The name of the JavaScript client method.</span></span> <span data-ttu-id="583d2-134">在下面的示例中，该方法将`ReceiveMessage`。</span><span class="sxs-lookup"><span data-stu-id="583d2-134">In the following example, the method name is `ReceiveMessage`.</span></span>
* <span data-ttu-id="583d2-135">中心将传递给方法的自变量。</span><span class="sxs-lookup"><span data-stu-id="583d2-135">Arguments the hub passes to the method.</span></span> <span data-ttu-id="583d2-136">在以下示例中，自变量值是`message`。</span><span class="sxs-lookup"><span data-stu-id="583d2-136">In the following example, the argument value is `message`.</span></span>

[!code-javascript[Receive calls from hub](javascript-client/sample/wwwroot/js/chat.js?range=4-9)]

<span data-ttu-id="583d2-137">在前面的代码`connection.on`运行时服务器端代码将调用它使用`SendAsync`方法。</span><span class="sxs-lookup"><span data-stu-id="583d2-137">The preceding code in `connection.on` runs when server-side code calls it using the `SendAsync` method.</span></span>

[!code-javascript[Call client-side](javascript-client/sample/hubs/chathub.cs?range=8-11)]

<span data-ttu-id="583d2-138">SignalR 确定要调用的方法名称匹配的客户端方法并在中定义的自变量`SendAsync`和`connection.on`。</span><span class="sxs-lookup"><span data-stu-id="583d2-138">SignalR determines which client method to call by matching the method name and arguments defined in `SendAsync` and `connection.on`.</span></span>

> [!NOTE]
> <span data-ttu-id="583d2-139">作为最佳做法是，调用`connection.start`后`connection.on`以便接收任何消息之前注册您的处理程序。</span><span class="sxs-lookup"><span data-stu-id="583d2-139">As a best practice, call `connection.start` after `connection.on` so your handlers are registered before any messages are received.</span></span>

## <a name="error-handling-and-logging"></a><span data-ttu-id="583d2-140">错误处理和日志记录</span><span class="sxs-lookup"><span data-stu-id="583d2-140">Error handling and logging</span></span>

<span data-ttu-id="583d2-141">链`catch`方法的末尾`connection.start`方法以处理客户端错误。</span><span class="sxs-lookup"><span data-stu-id="583d2-141">Chain a `catch` method to the end of the `connection.start` method to handle client-side errors.</span></span> <span data-ttu-id="583d2-142">使用`console.error`输出错误给浏览器的控制台。</span><span class="sxs-lookup"><span data-stu-id="583d2-142">Use `console.error` to output errors to the browser's console.</span></span>

[!code-javascript[Error handling](javascript-client/sample/wwwroot/js/chat.js?range=18)]

<span data-ttu-id="583d2-143">通过传递要建立连接时记录的记录器和事件类型的安装程序客户端日志跟踪。</span><span class="sxs-lookup"><span data-stu-id="583d2-143">Setup client-side log tracing by passing a logger and type of event to log when the connection is made.</span></span> <span data-ttu-id="583d2-144">使用指定的日志级别和更高版本记录的消息。</span><span class="sxs-lookup"><span data-stu-id="583d2-144">Messages are logged with the specified log level and higher.</span></span> <span data-ttu-id="583d2-145">可用的日志级别如下所示：</span><span class="sxs-lookup"><span data-stu-id="583d2-145">Available log levels are as follows:</span></span>

* <span data-ttu-id="583d2-146">`signalR.LogLevel.Error` ： 错误消息。</span><span class="sxs-lookup"><span data-stu-id="583d2-146">`signalR.LogLevel.Error` : Error messages.</span></span> <span data-ttu-id="583d2-147">日志`Error`仅消息。</span><span class="sxs-lookup"><span data-stu-id="583d2-147">Logs `Error` messages only.</span></span>
* <span data-ttu-id="583d2-148">`signalR.LogLevel.Warning` ： 有关潜在的错误警告消息。</span><span class="sxs-lookup"><span data-stu-id="583d2-148">`signalR.LogLevel.Warning` : Warning messages about potential errors.</span></span> <span data-ttu-id="583d2-149">日志`Warning`，和`Error`消息。</span><span class="sxs-lookup"><span data-stu-id="583d2-149">Logs `Warning`, and `Error` messages.</span></span>
* <span data-ttu-id="583d2-150">`signalR.LogLevel.Information` ： 未出现错误状态消息。</span><span class="sxs-lookup"><span data-stu-id="583d2-150">`signalR.LogLevel.Information` : Status messages without errors.</span></span> <span data-ttu-id="583d2-151">日志`Information`， `Warning`，和`Error`消息。</span><span class="sxs-lookup"><span data-stu-id="583d2-151">Logs `Information`, `Warning`, and `Error` messages.</span></span>
* <span data-ttu-id="583d2-152">`signalR.LogLevel.Trace` ： 跟踪消息。</span><span class="sxs-lookup"><span data-stu-id="583d2-152">`signalR.LogLevel.Trace` : Trace messages.</span></span> <span data-ttu-id="583d2-153">记录所有内容，包括数据中心和客户端之间传输。</span><span class="sxs-lookup"><span data-stu-id="583d2-153">Logs everything, including data transported between hub and client.</span></span>

<span data-ttu-id="583d2-154">将记录器传递给要启动日志记录的连接。</span><span class="sxs-lookup"><span data-stu-id="583d2-154">Pass the logger to the connection to start logging.</span></span> <span data-ttu-id="583d2-155">浏览器开发人员工具通常包含显示的消息的控制台。</span><span class="sxs-lookup"><span data-stu-id="583d2-155">Browser developer tools typically contain a console that displays the messages.</span></span>

[!code-javascript[Logging levels](javascript-client/sample/wwwroot/js/chat.js?range=1-2)]

## <a name="related-resources"></a><span data-ttu-id="583d2-156">相关资源</span><span class="sxs-lookup"><span data-stu-id="583d2-156">Related resources</span></span>

* [<span data-ttu-id="583d2-157">ASP.NET 核心 SignalR 集线器</span><span class="sxs-lookup"><span data-stu-id="583d2-157">ASP.NET Core SignalR Hubs</span></span>](xref:signalr/hubs)
* [<span data-ttu-id="583d2-158">启用 ASP.NET Core 中的跨源请求 (CORS)</span><span class="sxs-lookup"><span data-stu-id="583d2-158">Enable Cross-Origin Requests (CORS) in ASP.NET Core</span></span>](xref:security/cors)