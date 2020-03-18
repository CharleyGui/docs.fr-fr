---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394381"
---
### <a name="kestrel-empty-https-assembly-removed"></a><span data-ttu-id="fe2d1-101">Kestrel: L’assemblage HTTPS vide supprimé</span><span class="sxs-lookup"><span data-stu-id="fe2d1-101">Kestrel: Empty HTTPS assembly removed</span></span>

<span data-ttu-id="fe2d1-102">L’assemblage <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="fe2d1-102">The assembly <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> has been removed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fe2d1-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="fe2d1-103">Version introduced</span></span>

<span data-ttu-id="fe2d1-104">3.0</span><span class="sxs-lookup"><span data-stu-id="fe2d1-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="fe2d1-105">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="fe2d1-105">Reason for change</span></span>

<span data-ttu-id="fe2d1-106">Dans ASP.NET Core 2.1, le `Microsoft.AspNetCore.Server.Kestrel.Https` contenu de <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>ont été déplacés à .</span><span class="sxs-lookup"><span data-stu-id="fe2d1-106">In ASP.NET Core 2.1, the contents of `Microsoft.AspNetCore.Server.Kestrel.Https` were moved to <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>.</span></span> <span data-ttu-id="fe2d1-107">Ce changement a été fait d’une manière non-rupture en utilisant des `[TypeForwardedTo]` attributs.</span><span class="sxs-lookup"><span data-stu-id="fe2d1-107">This change was done in a non-breaking way using `[TypeForwardedTo]` attributes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fe2d1-108">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="fe2d1-108">Recommended action</span></span>

- <span data-ttu-id="fe2d1-109">Les bibliothèques `Microsoft.AspNetCore.Server.Kestrel.Https` faisant référence à 2.0 devraient mettre à jour toutes les dépendances ASP.NET Core à 2,1 ou plus tard.</span><span class="sxs-lookup"><span data-stu-id="fe2d1-109">Libraries referencing `Microsoft.AspNetCore.Server.Kestrel.Https` 2.0 should update all ASP.NET Core dependencies to 2.1 or later.</span></span> <span data-ttu-id="fe2d1-110">Sinon, ils peuvent se briser lorsqu’ils sont chargés dans une application ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="fe2d1-110">Otherwise, they may break when loaded into an ASP.NET Core 3.0 app.</span></span>
- <span data-ttu-id="fe2d1-111">Les applications et les bibliothèques ciblant ASP.NET Core 2.1 et `Microsoft.AspNetCore.Server.Kestrel.Https` ultérieurement devraient supprimer toute référence directe au paquet NuGet.</span><span class="sxs-lookup"><span data-stu-id="fe2d1-111">Apps and libraries targeting ASP.NET Core 2.1 and later should remove any direct references to the `Microsoft.AspNetCore.Server.Kestrel.Https` NuGet package.</span></span>

#### <a name="category"></a><span data-ttu-id="fe2d1-112">Category</span><span class="sxs-lookup"><span data-stu-id="fe2d1-112">Category</span></span>

<span data-ttu-id="fe2d1-113">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fe2d1-113">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fe2d1-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="fe2d1-114">Affected APIs</span></span>

<span data-ttu-id="fe2d1-115">None</span><span class="sxs-lookup"><span data-stu-id="fe2d1-115">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
