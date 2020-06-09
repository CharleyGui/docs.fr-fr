---
ms.openlocfilehash: 0d29407896145bc3b2ed8284c839ae8f2f0521b2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602949"
---

<span data-ttu-id="24ee4-101">Les [scripts dotnet-install](../../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du **Kit de développement logiciel (SDK)**.</span><span class="sxs-lookup"><span data-stu-id="24ee4-101">The [dotnet-install scripts](../../tools/dotnet-install-script.md) are used for automation and non-admin installs of the **SDK**.</span></span> <span data-ttu-id="24ee4-102">Vous pouvez télécharger le script depuis <https://dot.net/v1/dotnet-install.sh>.</span><span class="sxs-lookup"><span data-stu-id="24ee4-102">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="24ee4-103">Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="24ee4-103">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="24ee4-104">Pour installer la version actuelle, qui ne peut pas être une version (LTS), utilisez le `-c Current` paramètre.</span><span class="sxs-lookup"><span data-stu-id="24ee4-104">To install the current release, which may not be an (LTS) version, use the `-c Current` parameter.</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="24ee4-105">Pour installer le Runtime .NET Core au lieu du kit de développement logiciel (SDK), utilisez le `--runtime` paramètre.</span><span class="sxs-lookup"><span data-stu-id="24ee4-105">To install .NET Core Runtime instead of the SDK, use the `--runtime` parameter.</span></span>

```bash
./dotnet-install.sh -c Current --runtime
```

<span data-ttu-id="24ee4-106">Vous pouvez installer une version spécifique en modifiant le `-c` paramètre pour indiquer la version spécifique.</span><span class="sxs-lookup"><span data-stu-id="24ee4-106">You can install a specific version by altering the `-c` parameter to indicate the specific version.</span></span> <span data-ttu-id="24ee4-107">La commande suivante installe kit SDK .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="24ee4-107">The following command installs .NET Core SDK 3.1.</span></span>

```bash
./dotnet-install.sh -c 3.1
```

<span data-ttu-id="24ee4-108">Pour plus d’informations, consultez informations de référence sur les [scripts dotnet-install](../../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="24ee4-108">For more information, see [dotnet-install scripts reference](../../tools/dotnet-install-script.md).</span></span>
