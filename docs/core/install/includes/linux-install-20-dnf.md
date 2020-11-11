---
ms.openlocfilehash: bd0953697ee3a9e928d09c1f270a4af5606ee0d9
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507056"
---

### <a name="install-the-sdk"></a><span data-ttu-id="69d14-101">Installer le SDK</span><span class="sxs-lookup"><span data-stu-id="69d14-101">Install the SDK</span></span>

<span data-ttu-id="69d14-102">Le kit SDK .NET Core vous permet de développer des applications avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="69d14-102">The .NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="69d14-103">Si vous installez le kit SDK .NET Core, vous n’avez pas besoin d’installer le runtime correspondant.</span><span class="sxs-lookup"><span data-stu-id="69d14-103">If you install the .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="69d14-104">Pour installer le kit SDK .NET Core, exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="69d14-104">To install the .NET Core SDK, run the following commands:</span></span>

```bash
sudo dnf install dotnet-sdk-2.0
```

### <a name="install-the-runtime"></a><span data-ttu-id="69d14-105">Installer le runtime</span><span class="sxs-lookup"><span data-stu-id="69d14-105">Install the runtime</span></span>

<span data-ttu-id="69d14-106">Le Runtime .NET Core vous permet d’exécuter des applications qui ont été créées avec .NET Core et qui ne comportent pas le Runtime.</span><span class="sxs-lookup"><span data-stu-id="69d14-106">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="69d14-107">Les commandes suivantes installent le runtime ASP.NET Core, qui est le runtime le plus compatible pour .NET Core.</span><span class="sxs-lookup"><span data-stu-id="69d14-107">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="69d14-108">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="69d14-108">In your terminal, run the following commands.</span></span>

```bash
sudo dnf install aspnetcore-runtime-2.0
```

<span data-ttu-id="69d14-109">Comme alternative au runtime ASP.NET Core, vous pouvez installer le Runtime .NET Core, qui n’inclut pas ASP.NET Core prise en charge : remplacez `aspnetcore-runtime-2.0` dans la commande précédente par `dotnet-runtime-2.0` .</span><span class="sxs-lookup"><span data-stu-id="69d14-109">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime, which doesn't include ASP.NET Core support: replace `aspnetcore-runtime-2.0` in the previous command with `dotnet-runtime-2.0`.</span></span>

```bash
sudo dnf install dotnet-runtime-2.0
```
