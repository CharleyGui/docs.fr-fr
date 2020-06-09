---
ms.openlocfilehash: db89539982c1afe0df374027d54826f3265f0fee
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603012"
---

### <a name="install-the-sdk"></a><span data-ttu-id="903f6-101">Installer le Kit de développement logiciel (SDK)</span><span class="sxs-lookup"><span data-stu-id="903f6-101">Install the SDK</span></span>

<span data-ttu-id="903f6-102">Le kit SDK .NET Core vous permet de développer des applications avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="903f6-102">The .NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="903f6-103">Pour installer le kit SDK .NET Core, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="903f6-103">To install the .NET Core SDK, run the following commands.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

### <a name="install-the-runtime"></a><span data-ttu-id="903f6-104">Installer le runtime</span><span class="sxs-lookup"><span data-stu-id="903f6-104">Install the runtime</span></span>

<span data-ttu-id="903f6-105">Le Runtime .NET Core vous permet d’exécuter des applications qui ont été créées avec .NET Core et qui ne comportent pas le Runtime.</span><span class="sxs-lookup"><span data-stu-id="903f6-105">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="903f6-106">Les commandes ci-dessous installent le runtime ASP.NET Core, qui est le runtime le plus compatible pour .NET Core.</span><span class="sxs-lookup"><span data-stu-id="903f6-106">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="903f6-107">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="903f6-107">In your terminal, run the following commands.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

<span data-ttu-id="903f6-108">Comme alternative au runtime ASP.NET Core, vous pouvez installer le Runtime .NET Core qui n’inclut pas ASP.NET Core prise en charge : replace `aspnetcore-runtime-2.1` dans la commande ci-dessus avec `dotnet-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="903f6-108">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `aspnetcore-runtime-2.1` in the command above with `dotnet-runtime-3.1`.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```
