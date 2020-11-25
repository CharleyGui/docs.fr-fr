---
ms.openlocfilehash: 540eebd957ce8ce0928db2bd8317cb220cba30bb
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031758"
---

<span data-ttu-id="4c99f-101">Les [scripts dotnet-install](../../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du **Kit de développement logiciel (SDK)** et du **Runtime**.</span><span class="sxs-lookup"><span data-stu-id="4c99f-101">The [dotnet-install scripts](../../tools/dotnet-install-script.md) are used for automation and non-admin installs of the **SDK** and **Runtime**.</span></span> <span data-ttu-id="4c99f-102">Vous pouvez télécharger le script depuis <https://dot.net/v1/dotnet-install.sh>.</span><span class="sxs-lookup"><span data-stu-id="4c99f-102">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="4c99f-103">Par défaut, le script installe la version la plus récente du kit de développement logiciel [(SDK) LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="4c99f-103">The script defaults to installing the latest SDK [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="4c99f-104">Pour installer la version actuelle, qui ne peut pas être une version (LTS), utilisez le `-c Current` paramètre.</span><span class="sxs-lookup"><span data-stu-id="4c99f-104">To install the current release, which may not be an (LTS) version, use the `-c Current` parameter.</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="4c99f-105">Pour installer le Runtime .NET au lieu du kit de développement logiciel (SDK), utilisez le `--runtime` paramètre.</span><span class="sxs-lookup"><span data-stu-id="4c99f-105">To install .NET Runtime instead of the SDK, use the `--runtime` parameter.</span></span>

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

<span data-ttu-id="4c99f-106">Vous pouvez installer une version spécifique en modifiant le `-c` paramètre pour indiquer la version spécifique.</span><span class="sxs-lookup"><span data-stu-id="4c99f-106">You can install a specific version by altering the `-c` parameter to indicate the specific version.</span></span> <span data-ttu-id="4c99f-107">La commande suivante installe le kit de développement logiciel (SDK) .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="4c99f-107">The following command installs .NET SDK 5.0.</span></span>

```bash
./dotnet-install.sh -c 5.0
```

<span data-ttu-id="4c99f-108">Pour plus d’informations, consultez informations de référence sur les [scripts dotnet-install](../../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="4c99f-108">For more information, see [dotnet-install scripts reference](../../tools/dotnet-install-script.md).</span></span>
