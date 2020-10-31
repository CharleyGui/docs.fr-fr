---
ms.openlocfilehash: 188fef66444cd60f59a3cb9619c0d86efd155f99
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93136273"
---

### <a name="install-the-sdk"></a><span data-ttu-id="c296f-101">Installer le Kit de développement logiciel (SDK)</span><span class="sxs-lookup"><span data-stu-id="c296f-101">Install the SDK</span></span>

<span data-ttu-id="c296f-102">Kit SDK .NET Core vous permet de développer des applications avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c296f-102">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="c296f-103">Si vous installez kit SDK .NET Core, vous n’avez pas besoin d’installer le runtime correspondant.</span><span class="sxs-lookup"><span data-stu-id="c296f-103">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="c296f-104">Pour installer kit SDK .NET Core, exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="c296f-104">To install .NET Core SDK, run the following commands:</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-2.1
```

> [!IMPORTANT]
> <span data-ttu-id="c296f-105">Si vous recevez un message d’erreur semblable à **incapable de localiser le package dotnet-SDK-2,1** , consultez la section de [résolution des problèmes de apt](#apt-troubleshooting) .</span><span class="sxs-lookup"><span data-stu-id="c296f-105">If you receive an error message similar to **Unable to locate package dotnet-sdk-2.1** , see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="c296f-106">Installer le runtime</span><span class="sxs-lookup"><span data-stu-id="c296f-106">Install the runtime</span></span>

<span data-ttu-id="c296f-107">Le Runtime .NET Core vous permet d’exécuter des applications qui ont été créées avec .NET Core et qui ne comportent pas le Runtime.</span><span class="sxs-lookup"><span data-stu-id="c296f-107">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="c296f-108">Les commandes suivantes installent le runtime ASP.NET Core, qui est le runtime le plus compatible pour .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c296f-108">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="c296f-109">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="c296f-109">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-2.1
```

> [!IMPORTANT]
> <span data-ttu-id="c296f-110">Si vous recevez un message d’erreur semblable à **incapable de localiser le package aspnetcore-Runtime-2,1** , consultez la section de [résolution des problèmes de apt](#apt-troubleshooting) .</span><span class="sxs-lookup"><span data-stu-id="c296f-110">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-2.1** , see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

<span data-ttu-id="c296f-111">Comme alternative au runtime ASP.NET Core, vous pouvez installer le Runtime .NET Core qui n’inclut pas ASP.NET Core prise en charge : remplacez `aspnetcore-runtime-2.1` dans la commande précédente par `dotnet-runtime-2.1` .</span><span class="sxs-lookup"><span data-stu-id="c296f-111">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `aspnetcore-runtime-2.1` in the previous command with `dotnet-runtime-2.1`.</span></span>

```bash
sudo apt-get install -y dotnet-runtime-2.1
```
