---
title: Modifications avec rupture MSBuild
description: Répertorie les modifications avec rupture dans MSBuild pour .NET Core 3,0-3,1.
ms.date: 12/14/2020
ms.openlocfilehash: 1ed5878845406fa7727c644f1e196d63a860646a
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97593446"
---
# <a name="msbuild-breaking-changes-in-net-core-30---31"></a><span data-ttu-id="ad5c5-103">Modifications importantes de MSBuild dans .NET Core 3,0-3,1</span><span class="sxs-lookup"><span data-stu-id="ad5c5-103">MSBuild breaking changes in .NET Core 3.0 - 3.1</span></span>

<span data-ttu-id="ad5c5-104">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="ad5c5-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="ad5c5-105">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="ad5c5-105">Breaking change</span></span> | <span data-ttu-id="ad5c5-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ad5c5-106">Version introduced</span></span> |
| - | - |
| [<span data-ttu-id="ad5c5-107">Les builds au moment du design ne retournent que les références de package de niveau supérieur</span><span class="sxs-lookup"><span data-stu-id="ad5c5-107">Design-time builds only return top-level package references</span></span>](#design-time-builds-only-return-top-level-package-references) | <span data-ttu-id="ad5c5-108">3.1</span><span class="sxs-lookup"><span data-stu-id="ad5c5-108">3.1</span></span> |
| [<span data-ttu-id="ad5c5-109">Changement de nom de fichier manifeste de ressource</span><span class="sxs-lookup"><span data-stu-id="ad5c5-109">Resource manifest file name change</span></span>](#resource-manifest-file-name-change) | <span data-ttu-id="ad5c5-110">3.0</span><span class="sxs-lookup"><span data-stu-id="ad5c5-110">3.0</span></span> |

## <a name="net-core-31"></a><span data-ttu-id="ad5c5-111">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="ad5c5-111">.NET Core 3.1</span></span>

[!INCLUDE [design-time-builds-return-top-level-package-refs](../../../includes/core-changes/msbuild/3.1/design-time-builds-return-top-level-package-refs.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="ad5c5-112">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ad5c5-112">.NET Core 3.0</span></span>

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***
