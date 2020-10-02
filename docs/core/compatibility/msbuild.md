---
title: Modifications avec rupture MSBuild
description: Répertorie les modifications avec rupture dans MSBuild pour .NET Core.
ms.date: 02/10/2020
ms.openlocfilehash: b57c70d21e061c59f26b11a025d4d05ce3b8ca99
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654733"
---
# <a name="msbuild-breaking-changes"></a><span data-ttu-id="20bf9-103">Modifications avec rupture MSBuild</span><span class="sxs-lookup"><span data-stu-id="20bf9-103">MSBuild breaking changes</span></span>

<span data-ttu-id="20bf9-104">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="20bf9-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="20bf9-105">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="20bf9-105">Breaking change</span></span> | <span data-ttu-id="20bf9-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="20bf9-106">Version introduced</span></span> |
| - | - |
| [<span data-ttu-id="20bf9-107">NETCOREAPP3_1 symbole de préprocesseur n’est pas défini lors du ciblage de .NET 5</span><span class="sxs-lookup"><span data-stu-id="20bf9-107">NETCOREAPP3_1 preprocessor symbol is not defined when targeting .NET 5</span></span>](#netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5) | <span data-ttu-id="20bf9-108">5.0</span><span class="sxs-lookup"><span data-stu-id="20bf9-108">5.0</span></span> |
| [<span data-ttu-id="20bf9-109">Changement de comportement de PublishDepsFilePath</span><span class="sxs-lookup"><span data-stu-id="20bf9-109">PublishDepsFilePath behavior change</span></span>](#publishdepsfilepath-behavior-change) | <span data-ttu-id="20bf9-110">5.0</span><span class="sxs-lookup"><span data-stu-id="20bf9-110">5.0</span></span> |
| [<span data-ttu-id="20bf9-111">Les fichiers Directory. Packages. props sont importés par défaut</span><span class="sxs-lookup"><span data-stu-id="20bf9-111">Directory.Packages.props files is imported by default</span></span>](#directorypackagesprops-files-is-imported-by-default) | <span data-ttu-id="20bf9-112">5.0</span><span class="sxs-lookup"><span data-stu-id="20bf9-112">5.0</span></span> |
| [<span data-ttu-id="20bf9-113">Changement de nom de fichier manifeste de ressource</span><span class="sxs-lookup"><span data-stu-id="20bf9-113">Resource manifest file name change</span></span>](#resource-manifest-file-name-change) | <span data-ttu-id="20bf9-114">3.0</span><span class="sxs-lookup"><span data-stu-id="20bf9-114">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="20bf9-115">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="20bf9-115">.NET 5.0</span></span>

[!INCLUDE [netcoreapp3_1-preprocessor-symbol-not-defined](../../../includes/core-changes/msbuild/5.0/netcoreapp3_1-preprocessor-symbol-not-defined.md)]

***

[!INCLUDE [publishdepsfilepath-behavior-change](../../../includes/core-changes/msbuild/5.0/publishdepsfilepath-behavior-change.md)]

***

[!INCLUDE [directory-packages-props-imported-by-default](../../../includes/core-changes/msbuild/5.0/directory-packages-props-imported-by-default.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="20bf9-116">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="20bf9-116">.NET Core 3.0</span></span>

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***
