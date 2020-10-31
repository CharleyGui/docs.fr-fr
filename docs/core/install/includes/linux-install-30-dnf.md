---
ms.openlocfilehash: 68b55eb40d86ac3c92853acbb17ad622704b1336
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93135710"
---

### <a name="install-the-sdk"></a><span data-ttu-id="3541b-101">Installer le Kit de développement logiciel (SDK)</span><span class="sxs-lookup"><span data-stu-id="3541b-101">Install the SDK</span></span>

<span data-ttu-id="3541b-102">Kit SDK .NET Core vous permet de développer des applications avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3541b-102">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="3541b-103">Si vous installez kit SDK .NET Core, vous n’avez pas besoin d’installer le runtime correspondant.</span><span class="sxs-lookup"><span data-stu-id="3541b-103">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="3541b-104">Pour installer kit SDK .NET Core, exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="3541b-104">To install .NET Core SDK, run the following commands:</span></span>

```bash
sudo dnf install dotnet-sdk-3.0
```

### <a name="install-the-runtime"></a><span data-ttu-id="3541b-105">Installer le runtime</span><span class="sxs-lookup"><span data-stu-id="3541b-105">Install the runtime</span></span>

<span data-ttu-id="3541b-106">Le Runtime .NET Core vous permet d’exécuter des applications qui ont été créées avec .NET Core et qui ne comportent pas le Runtime.</span><span class="sxs-lookup"><span data-stu-id="3541b-106">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="3541b-107">Les commandes suivantes installent le runtime ASP.NET Core, qui est le runtime le plus compatible pour .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3541b-107">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="3541b-108">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="3541b-108">In your terminal, run the following commands.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.0
```

<span data-ttu-id="3541b-109">Comme alternative au runtime ASP.NET Core, vous pouvez installer le Runtime .NET Core qui n’inclut pas ASP.NET Core prise en charge : remplacez `aspnetcore-runtime-3.0` dans la commande précédente par `dotnet-runtime-3.0` .</span><span class="sxs-lookup"><span data-stu-id="3541b-109">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `aspnetcore-runtime-3.0` in the previous command with `dotnet-runtime-3.0`.</span></span>

```bash
sudo dnf install dotnet-runtime-3.0
```
