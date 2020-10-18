---
title: Modifications avec rupture MSBuild
description: Répertorie les modifications avec rupture dans MSBuild pour .NET Core.
ms.date: 02/10/2020
ms.openlocfilehash: 9b0fba30c8955a6099bde0dc95b4df65a151d9e6
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159484"
---
# <a name="msbuild-breaking-changes"></a><span data-ttu-id="fc2ea-103">Modifications avec rupture MSBuild</span><span class="sxs-lookup"><span data-stu-id="fc2ea-103">MSBuild breaking changes</span></span>

<span data-ttu-id="fc2ea-104">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="fc2ea-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="fc2ea-105">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="fc2ea-105">Breaking change</span></span> | <span data-ttu-id="fc2ea-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="fc2ea-106">Version introduced</span></span> |
| - | - |
| [<span data-ttu-id="fc2ea-107">Modification de TargetFramework de netcoreapp en net</span><span class="sxs-lookup"><span data-stu-id="fc2ea-107">TargetFramework change from netcoreapp to net</span></span>](#targetframework-change-from-netcoreapp-to-net) | <span data-ttu-id="fc2ea-108">5.0</span><span class="sxs-lookup"><span data-stu-id="fc2ea-108">5.0</span></span> |
| [<span data-ttu-id="fc2ea-109">NETCOREAPP3_1 symbole de préprocesseur n’est pas défini lors du ciblage de .NET 5</span><span class="sxs-lookup"><span data-stu-id="fc2ea-109">NETCOREAPP3_1 preprocessor symbol is not defined when targeting .NET 5</span></span>](#netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5) | <span data-ttu-id="fc2ea-110">5.0</span><span class="sxs-lookup"><span data-stu-id="fc2ea-110">5.0</span></span> |
| [<span data-ttu-id="fc2ea-111">Changement de comportement de PublishDepsFilePath</span><span class="sxs-lookup"><span data-stu-id="fc2ea-111">PublishDepsFilePath behavior change</span></span>](#publishdepsfilepath-behavior-change) | <span data-ttu-id="fc2ea-112">5.0</span><span class="sxs-lookup"><span data-stu-id="fc2ea-112">5.0</span></span> |
| [<span data-ttu-id="fc2ea-113">Les fichiers Directory. Packages. props sont importés par défaut</span><span class="sxs-lookup"><span data-stu-id="fc2ea-113">Directory.Packages.props files is imported by default</span></span>](#directorypackagesprops-files-is-imported-by-default) | <span data-ttu-id="fc2ea-114">5.0</span><span class="sxs-lookup"><span data-stu-id="fc2ea-114">5.0</span></span> |
| [<span data-ttu-id="fc2ea-115">Changement de nom de fichier manifeste de ressource</span><span class="sxs-lookup"><span data-stu-id="fc2ea-115">Resource manifest file name change</span></span>](#resource-manifest-file-name-change) | <span data-ttu-id="fc2ea-116">3.0</span><span class="sxs-lookup"><span data-stu-id="fc2ea-116">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="fc2ea-117">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="fc2ea-117">.NET 5.0</span></span>

[!INCLUDE [targetframework-name-change](../../../includes/core-changes/msbuild/5.0/targetframework-name-change.md)]

***

[!INCLUDE [netcoreapp3_1-preprocessor-symbol-not-defined](../../../includes/core-changes/msbuild/5.0/netcoreapp3_1-preprocessor-symbol-not-defined.md)]

***

[!INCLUDE [publishdepsfilepath-behavior-change](../../../includes/core-changes/msbuild/5.0/publishdepsfilepath-behavior-change.md)]

***

[!INCLUDE [directory-packages-props-imported-by-default](../../../includes/core-changes/msbuild/5.0/directory-packages-props-imported-by-default.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="fc2ea-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="fc2ea-118">.NET Core 3.0</span></span>

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***
