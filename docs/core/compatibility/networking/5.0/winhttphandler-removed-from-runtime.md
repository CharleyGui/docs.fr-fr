---
title: 'Modification avec rupture : WinHttpHandler supprimé du Runtime .NET'
description: Découvrez la modification avec rupture dans .NET 5,0 où WinHttpHandler a été supprimé du Runtime .NET.
ms.date: 10/18/2020
ms.openlocfilehash: f8b9910ade8d459133791a23704d624a91cc5dff
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760923"
---
# <a name="winhttphandler-removed-from-net-runtime"></a><span data-ttu-id="e995d-103">WinHttpHandler supprimé du Runtime .NET</span><span class="sxs-lookup"><span data-stu-id="e995d-103">WinHttpHandler removed from .NET runtime</span></span>

<span data-ttu-id="e995d-104">La `WinHttpHandler` classe a été supprimée de l’assembly *System.Net.Http.dll* .</span><span class="sxs-lookup"><span data-stu-id="e995d-104">The `WinHttpHandler` class was removed from the *System.Net.Http.dll* assembly.</span></span> <span data-ttu-id="e995d-105">Il est désormais disponible uniquement en tant que [package NuGet](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)hors-bande (OOB).</span><span class="sxs-lookup"><span data-stu-id="e995d-105">It's now available only as an out-of-band (OOB) [NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="e995d-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="e995d-106">Version introduced</span></span>

<span data-ttu-id="e995d-107">5.0</span><span class="sxs-lookup"><span data-stu-id="e995d-107">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="e995d-108">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="e995d-108">Change description</span></span>

<span data-ttu-id="e995d-109">Dans les versions précédentes de .NET, la <xref:System.Net.Http.WinHttpHandler> classe est disponible dans le cadre des bibliothèques .net de base.</span><span class="sxs-lookup"><span data-stu-id="e995d-109">In previous .NET versions, the <xref:System.Net.Http.WinHttpHandler> class is available as part of the core .NET libraries.</span></span> <span data-ttu-id="e995d-110">À compter de .NET 5,0, la <xref:System.Net.Http.WinHttpHandler> classe est uniquement disponible en tant que [package NuGet](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)installé séparément.</span><span class="sxs-lookup"><span data-stu-id="e995d-110">Starting in .NET 5.0, the <xref:System.Net.Http.WinHttpHandler> class is only available as a separately installed [NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span>

## <a name="recommended-action"></a><span data-ttu-id="e995d-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="e995d-111">Recommended action</span></span>

<span data-ttu-id="e995d-112">Installez le [package NuGet System .net. http. WinHttpHandler](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span><span class="sxs-lookup"><span data-stu-id="e995d-112">Install the [System.Net.Http.WinHttpHandler NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span> <span data-ttu-id="e995d-113">Ou, si vous n’avez pas besoin de fonctionnalités spécifiques à WinHTTP, utilisez à la <xref:System.Net.Http.SocketsHttpHandler> place.</span><span class="sxs-lookup"><span data-stu-id="e995d-113">Or, if you don't require WinHTTP-specific features, use <xref:System.Net.Http.SocketsHttpHandler> instead.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="e995d-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="e995d-114">Affected APIs</span></span>

- <xref:System.Net.Http.WinHttpHandler?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Net.Http.WinHttpHandler`

### Category

Networking

-->
