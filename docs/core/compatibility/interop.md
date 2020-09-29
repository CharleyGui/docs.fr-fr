---
title: Modifications avec rupture d’interopérabilité
description: Répertorie les dernières modifications apportées à l’interopérabilité dans .NET Core et .NET 5,0 et versions ultérieures.
ms.date: 06/23/2020
ms.openlocfilehash: a38fb1837e565be33f8ae1119480c8f1ae848ab0
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91438036"
---
# <a name="interop-breaking-changes"></a><span data-ttu-id="a01e2-103">Modifications avec rupture d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="a01e2-103">Interop breaking changes</span></span>

<span data-ttu-id="a01e2-104">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="a01e2-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="a01e2-105">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="a01e2-105">Breaking change</span></span> | <span data-ttu-id="a01e2-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="a01e2-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="a01e2-107">La conversion du wrapper RCW en `InterfaceIsIInspectable` interface lève PlatformNotSupportedException</span><span class="sxs-lookup"><span data-stu-id="a01e2-107">Casting RCW to an `InterfaceIsIInspectable` interface throws PlatformNotSupportedException</span></span>](#casting-rcw-to-an-interfaceisiinspectable-interface-throws-platformnotsupportedexception) | <span data-ttu-id="a01e2-108">5.0</span><span class="sxs-lookup"><span data-stu-id="a01e2-108">5.0</span></span> |
| [<span data-ttu-id="a01e2-109">Pas de détection de suffixe A/W sur les plateformes non-Windows</span><span class="sxs-lookup"><span data-stu-id="a01e2-109">No A/W suffix probing on non-Windows platforms</span></span>](#no-aw-suffix-probing-on-non-windows-platforms) | <span data-ttu-id="a01e2-110">5.0</span><span class="sxs-lookup"><span data-stu-id="a01e2-110">5.0</span></span> |
| [<span data-ttu-id="a01e2-111">La prise en charge intégrée de WinRT est supprimée de .NET</span><span class="sxs-lookup"><span data-stu-id="a01e2-111">Built-in support for WinRT is removed from .NET</span></span>](#built-in-support-for-winrt-is-removed-from-net) | <span data-ttu-id="a01e2-112">5.0</span><span class="sxs-lookup"><span data-stu-id="a01e2-112">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="a01e2-113">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="a01e2-113">.NET 5.0</span></span>

[!INCLUDE [casting-rcw-to-inspectable-interface-throws-exception](../../../includes/core-changes/interop/5.0/casting-rcw-to-inspectable-interface-throws-exception.md)]

***

[!INCLUDE [function-suffix-pinvoke](../../../includes/core-changes/interop/5.0/function-suffix-pinvoke.md)]

***

[!INCLUDE [built-in-support-for-winrt-removed](~/includes/core-changes/interop/5.0/built-in-support-for-winrt-removed.md)]

***
