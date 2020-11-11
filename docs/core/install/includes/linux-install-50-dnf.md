---
ms.openlocfilehash: 2cd5459ab7f2c8c96638bf27dd30980282036925
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506925"
---

### <a name="install-the-sdk"></a><span data-ttu-id="cdede-101">Installer le SDK</span><span class="sxs-lookup"><span data-stu-id="cdede-101">Install the SDK</span></span>

<span data-ttu-id="cdede-102">Le kit de développement logiciel (SDK) .NET vous permet de développer des applications avec .NET.</span><span class="sxs-lookup"><span data-stu-id="cdede-102">The .NET SDK allows you to develop apps with .NET.</span></span> <span data-ttu-id="cdede-103">Si vous installez le kit de développement logiciel (SDK) .NET, vous n’avez pas besoin d’installer le runtime correspondant.</span><span class="sxs-lookup"><span data-stu-id="cdede-103">If you install the .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="cdede-104">Pour installer le kit de développement logiciel (SDK) .NET, exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="cdede-104">To install the .NET SDK, run the following commands:</span></span>

```bash
sudo dnf install dotnet-sdk-5.0
```

### <a name="install-the-runtime"></a><span data-ttu-id="cdede-105">Installer le runtime</span><span class="sxs-lookup"><span data-stu-id="cdede-105">Install the runtime</span></span>

<span data-ttu-id="cdede-106">Le runtime ASP.NET Core vous permet d’exécuter des applications qui ont été créées avec .NET et qui n’ont pas fourni le Runtime.</span><span class="sxs-lookup"><span data-stu-id="cdede-106">The ASP.NET Core Runtime allows you to run apps that were made with .NET that didn't provide the runtime.</span></span> <span data-ttu-id="cdede-107">Les commandes suivantes installent le runtime ASP.NET Core, qui est le runtime le plus compatible pour .NET.</span><span class="sxs-lookup"><span data-stu-id="cdede-107">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET.</span></span> <span data-ttu-id="cdede-108">Sur votre terminal, exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="cdede-108">In your terminal, run the following commands:</span></span>

```bash
sudo dnf install aspnetcore-runtime-5.0
```

<span data-ttu-id="cdede-109">Comme alternative au runtime ASP.NET Core, vous pouvez installer le Runtime .NET, qui n’inclut pas ASP.NET Core prise en charge : remplacer `aspnetcore-runtime-5.0` dans la commande précédente par `dotnet-runtime-5.0` :</span><span class="sxs-lookup"><span data-stu-id="cdede-109">As an alternative to the ASP.NET Core Runtime, you can install the .NET Runtime, which doesn't include ASP.NET Core support: replace `aspnetcore-runtime-5.0` in the previous command with `dotnet-runtime-5.0`:</span></span>

```bash
sudo dnf install dotnet-runtime-5.0
```
