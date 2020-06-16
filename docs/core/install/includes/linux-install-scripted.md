---
ms.openlocfilehash: fb78e1439a680a8dbb9fc0eb8afdeee3efef7ead
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768393"
---

<span data-ttu-id="9e5bd-101">Les [scripts dotnet-install](../../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du **Kit de développement logiciel (SDK)** et du **Runtime**.</span><span class="sxs-lookup"><span data-stu-id="9e5bd-101">The [dotnet-install scripts](../../tools/dotnet-install-script.md) are used for automation and non-admin installs of the **SDK** and **Runtime**.</span></span> <span data-ttu-id="9e5bd-102">Vous pouvez télécharger le script depuis <https://dot.net/v1/dotnet-install.sh>.</span><span class="sxs-lookup"><span data-stu-id="9e5bd-102">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="9e5bd-103">Par défaut, le script installe la version la plus récente du kit de développement logiciel [(SDK) LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="9e5bd-103">The script defaults to installing the latest SDK [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="9e5bd-104">Pour installer la version actuelle, qui ne peut pas être une version (LTS), utilisez le `-c Current` paramètre.</span><span class="sxs-lookup"><span data-stu-id="9e5bd-104">To install the current release, which may not be an (LTS) version, use the `-c Current` parameter.</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="9e5bd-105">Pour installer le Runtime .NET Core au lieu du kit de développement logiciel (SDK), utilisez le `--runtime` paramètre.</span><span class="sxs-lookup"><span data-stu-id="9e5bd-105">To install .NET Core Runtime instead of the SDK, use the `--runtime` parameter.</span></span>

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

<span data-ttu-id="9e5bd-106">Vous pouvez installer une version spécifique en modifiant le `-c` paramètre pour indiquer la version spécifique.</span><span class="sxs-lookup"><span data-stu-id="9e5bd-106">You can install a specific version by altering the `-c` parameter to indicate the specific version.</span></span> <span data-ttu-id="9e5bd-107">La commande suivante installe kit SDK .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="9e5bd-107">The following command installs .NET Core SDK 3.1.</span></span>

```bash
./dotnet-install.sh -c 3.1
```

<span data-ttu-id="9e5bd-108">Pour plus d’informations, consultez informations de référence sur les [scripts dotnet-install](../../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="9e5bd-108">For more information, see [dotnet-install scripts reference](../../tools/dotnet-install-script.md).</span></span>
