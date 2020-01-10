---
title: Dernières modifications-.NET Framework à .NET Core
description: Répertorie les modifications avec rupture d' .NET Framework à .NET Core.
ms.date: 12/18/2019
ms.openlocfilehash: e01ca522b7ec29e2f6db8a5a0c2fcdfc30a38168
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740902"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a><span data-ttu-id="42ebe-103">Dernières modifications pour la migration de .NET Framework vers .NET Core</span><span class="sxs-lookup"><span data-stu-id="42ebe-103">Breaking changes for migration from .NET Framework to .NET Core</span></span>

<span data-ttu-id="42ebe-104">Si vous migrez une application à partir de .NET Framework vers .NET Core, les modifications avec rupture mentionnées dans cet article peuvent vous affecter.</span><span class="sxs-lookup"><span data-stu-id="42ebe-104">If you're migrating an app from .NET Framework to .NET Core, the breaking changes listed in this article may affect you.</span></span> <span data-ttu-id="42ebe-105">En outre, l’article sur les [technologies .NET Framework non disponibles sur .net Core](../porting/net-framework-tech-unavailable.md) fournit des informations sur les technologies qui ne sont pas prises en charge sur .net Core, par exemple, les domaines d’application et .NET Remoting.</span><span class="sxs-lookup"><span data-stu-id="42ebe-105">In addition, the [.NET Framework technologies unavailable on .NET Core](../porting/net-framework-tech-unavailable.md) article provides information about technologies that aren't supported on .NET Core, for example, application domains and .NET remoting.</span></span>

<span data-ttu-id="42ebe-106">Les modifications avec rupture sont regroupées par catégorie.</span><span class="sxs-lookup"><span data-stu-id="42ebe-106">Breaking changes are grouped by category.</span></span>

> [!NOTE]
> <span data-ttu-id="42ebe-107">Cet article n’est pas une liste complète des modifications avec rupture entre .NET Framework et .NET Core.</span><span class="sxs-lookup"><span data-stu-id="42ebe-107">This article is not a complete list of breaking changes between .NET Framework and .NET Core.</span></span> <span data-ttu-id="42ebe-108">Les modifications critiques les plus importantes sont ajoutées ici, car nous en avons conscience.</span><span class="sxs-lookup"><span data-stu-id="42ebe-108">The most important breaking changes are added here as we become aware of them.</span></span>

## <a name="corefx"></a><span data-ttu-id="42ebe-109">CoreFx</span><span class="sxs-lookup"><span data-stu-id="42ebe-109">CoreFx</span></span>

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

## <a name="windows-forms"></a><span data-ttu-id="42ebe-110">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="42ebe-110">Windows Forms</span></span>

<span data-ttu-id="42ebe-111">Pour plus d’informations sur les modifications avec rupture quand vous migrez une application Windows Forms de .NET Framework vers .NET Core 3,0 ou version ultérieure, consultez [modifications avec rupture dans Windows Forms (.NET Framework à .net Core)](../porting/winforms-breaking-changes.md).</span><span class="sxs-lookup"><span data-stu-id="42ebe-111">For information about breaking changes when you migrate a Windows Forms app from .NET Framework to .NET Core 3.0 or later, see [Breaking changes in Windows Forms (.NET Framework to .NET Core)](../porting/winforms-breaking-changes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="42ebe-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42ebe-112">See also</span></span>

- [<span data-ttu-id="42ebe-113">Technologies de .NET Framework indisponibles sur .NET Core</span><span class="sxs-lookup"><span data-stu-id="42ebe-113">.NET Framework technologies unavailable on .NET Core</span></span>](../porting/net-framework-tech-unavailable.md)
