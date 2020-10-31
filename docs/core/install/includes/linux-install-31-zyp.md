---
ms.openlocfilehash: 36f1ee26def82d426b6637ae96f382fc89791a2f
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93136106"
---

### <a name="install-the-sdk"></a><span data-ttu-id="3e099-101">Installer le Kit de développement logiciel (SDK)</span><span class="sxs-lookup"><span data-stu-id="3e099-101">Install the SDK</span></span>

<span data-ttu-id="3e099-102">Le kit SDK .NET Core vous permet de développer des applications avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3e099-102">The .NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="3e099-103">Pour installer le kit SDK .NET Core, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="3e099-103">To install the .NET Core SDK, run the following commands.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

### <a name="install-the-runtime"></a><span data-ttu-id="3e099-104">Installer le runtime</span><span class="sxs-lookup"><span data-stu-id="3e099-104">Install the runtime</span></span>

<span data-ttu-id="3e099-105">Le Runtime .NET Core vous permet d’exécuter des applications qui ont été créées avec .NET Core et qui ne comportent pas le Runtime.</span><span class="sxs-lookup"><span data-stu-id="3e099-105">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="3e099-106">Les commandes suivantes installent le runtime ASP.NET Core, qui est le runtime le plus compatible pour .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3e099-106">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="3e099-107">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="3e099-107">In your terminal, run the following commands.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

<span data-ttu-id="3e099-108">Comme alternative au runtime ASP.NET Core, vous pouvez installer le Runtime .NET Core qui n’inclut pas ASP.NET Core prise en charge : remplacez `aspnetcore-runtime-2.1` dans la commande précédente par `dotnet-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="3e099-108">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `aspnetcore-runtime-2.1` in the previous command with `dotnet-runtime-3.1`.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```
