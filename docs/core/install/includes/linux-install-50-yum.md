---
ms.openlocfilehash: cc394741e399f4fc54dd67f1736f7027badf4c7d
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507094"
---

### <a name="install-the-sdk"></a><span data-ttu-id="0f87d-101">Installer le SDK</span><span class="sxs-lookup"><span data-stu-id="0f87d-101">Install the SDK</span></span>

<span data-ttu-id="0f87d-102">Le kit de développement logiciel (SDK) .NET vous permet de développer des applications avec .NET.</span><span class="sxs-lookup"><span data-stu-id="0f87d-102">The .NET SDK allows you to develop apps with .NET.</span></span> <span data-ttu-id="0f87d-103">Si vous installez le kit de développement logiciel (SDK) .NET, vous n’avez pas besoin d’installer le runtime correspondant.</span><span class="sxs-lookup"><span data-stu-id="0f87d-103">If you install the .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="0f87d-104">Pour installer le kit de développement logiciel (SDK) .NET, exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="0f87d-104">To install the .NET SDK, run the following commands:</span></span>

```bash
sudo yum install dotnet-sdk-5.0
```

### <a name="install-the-runtime"></a><span data-ttu-id="0f87d-105">Installer le runtime</span><span class="sxs-lookup"><span data-stu-id="0f87d-105">Install the runtime</span></span>

<span data-ttu-id="0f87d-106">Le runtime ASP.NET Core vous permet d’exécuter des applications qui ont été créées avec .NET et qui n’ont pas fourni le Runtime.</span><span class="sxs-lookup"><span data-stu-id="0f87d-106">The ASP.NET Core Runtime allows you to run apps that were made with .NET that didn't provide the runtime.</span></span> <span data-ttu-id="0f87d-107">Les commandes suivantes installent le runtime ASP.NET Core, qui est le runtime le plus compatible pour .NET.</span><span class="sxs-lookup"><span data-stu-id="0f87d-107">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET.</span></span> <span data-ttu-id="0f87d-108">Sur votre terminal, exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="0f87d-108">In your terminal, run the following commands:</span></span>

```bash
sudo yum install aspnetcore-runtime-5.0
```

<span data-ttu-id="0f87d-109">Comme alternative au runtime ASP.NET Core, vous pouvez installer le Runtime .NET, qui n’inclut pas ASP.NET Core prise en charge : remplacer `aspnetcore-runtime-5.0` dans la commande précédente par `dotnet-runtime-5.0` :</span><span class="sxs-lookup"><span data-stu-id="0f87d-109">As an alternative to the ASP.NET Core Runtime, you can install the .NET Runtime, which doesn't include ASP.NET Core support: replace `aspnetcore-runtime-5.0` in the previous command with `dotnet-runtime-5.0`:</span></span>

```bash
sudo yum install dotnet-runtime-5.0
```
