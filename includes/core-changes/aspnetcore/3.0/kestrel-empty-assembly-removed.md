---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032585"
---
### <a name="kestrel-empty-https-assembly-removed"></a><span data-ttu-id="7d0ee-101">Kestrel : un assembly HTTPs vide a été supprimé</span><span class="sxs-lookup"><span data-stu-id="7d0ee-101">Kestrel: Empty HTTPS assembly removed</span></span>

<span data-ttu-id="7d0ee-102">L’assembly <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="7d0ee-102">The assembly <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> has been removed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7d0ee-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="7d0ee-103">Version introduced</span></span>

<span data-ttu-id="7d0ee-104">3.0</span><span class="sxs-lookup"><span data-stu-id="7d0ee-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7d0ee-105">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="7d0ee-105">Reason for change</span></span>

<span data-ttu-id="7d0ee-106">Dans ASP.NET Core 2,1, le contenu de `Microsoft.AspNetCore.Server.Kestrel.Https` a été déplacé vers <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="7d0ee-106">In ASP.NET Core 2.1, the contents of `Microsoft.AspNetCore.Server.Kestrel.Https` were moved to <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>.</span></span> <span data-ttu-id="7d0ee-107">Cette modification a été effectuée de manière non-critique à l’aide d' `[TypeForwardedTo]` attributs.</span><span class="sxs-lookup"><span data-stu-id="7d0ee-107">This change was done in a non-breaking way using `[TypeForwardedTo]` attributes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7d0ee-108">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="7d0ee-108">Recommended action</span></span>

- <span data-ttu-id="7d0ee-109">Les bibliothèques référençant `Microsoft.AspNetCore.Server.Kestrel.Https` 2,0 doivent mettre à jour toutes les dépendances de ASP.net core à 2,1 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="7d0ee-109">Libraries referencing `Microsoft.AspNetCore.Server.Kestrel.Https` 2.0 should update all ASP.NET Core dependencies to 2.1 or later.</span></span> <span data-ttu-id="7d0ee-110">Dans le cas contraire, ils peuvent s’arrêter lorsqu’ils sont chargés dans une application ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="7d0ee-110">Otherwise, they may break when loaded into an ASP.NET Core 3.0 app.</span></span>
- <span data-ttu-id="7d0ee-111">Les applications et les bibliothèques qui ciblent ASP.NET Core 2,1 et versions ultérieures doivent supprimer toutes les références directes au `Microsoft.AspNetCore.Server.Kestrel.Https` package NuGet.</span><span class="sxs-lookup"><span data-stu-id="7d0ee-111">Apps and libraries targeting ASP.NET Core 2.1 and later should remove any direct references to the `Microsoft.AspNetCore.Server.Kestrel.Https` NuGet package.</span></span>

#### <a name="category"></a><span data-ttu-id="7d0ee-112">Category</span><span class="sxs-lookup"><span data-stu-id="7d0ee-112">Category</span></span>

<span data-ttu-id="7d0ee-113">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7d0ee-113">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7d0ee-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="7d0ee-114">Affected APIs</span></span>

<span data-ttu-id="7d0ee-115">None</span><span class="sxs-lookup"><span data-stu-id="7d0ee-115">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
