---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394381"
---
### <a name="kestrel-empty-https-assembly-removed"></a><span data-ttu-id="30136-101">Kestrel : un assembly HTTPs vide a été supprimé</span><span class="sxs-lookup"><span data-stu-id="30136-101">Kestrel: Empty HTTPS assembly removed</span></span>

<span data-ttu-id="30136-102">L’assembly <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="30136-102">The assembly <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> has been removed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="30136-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="30136-103">Version introduced</span></span>

<span data-ttu-id="30136-104">3,0</span><span class="sxs-lookup"><span data-stu-id="30136-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="30136-105">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="30136-105">Reason for change</span></span>

<span data-ttu-id="30136-106">Dans ASP.NET Core 2,1, le contenu de `Microsoft.AspNetCore.Server.Kestrel.Https` a été déplacé vers <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="30136-106">In ASP.NET Core 2.1, the contents of `Microsoft.AspNetCore.Server.Kestrel.Https` were moved to <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>.</span></span> <span data-ttu-id="30136-107">Cette modification a été effectuée de manière non-simple à l’aide d’attributs `[TypeForwardedTo]`.</span><span class="sxs-lookup"><span data-stu-id="30136-107">This change was done in a non-breaking way using `[TypeForwardedTo]` attributes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="30136-108">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="30136-108">Recommended action</span></span>

- <span data-ttu-id="30136-109">Les bibliothèques référençant `Microsoft.AspNetCore.Server.Kestrel.Https` 2,0 doivent mettre à jour toutes les dépendances de ASP.NET Core à 2,1 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="30136-109">Libraries referencing `Microsoft.AspNetCore.Server.Kestrel.Https` 2.0 should update all ASP.NET Core dependencies to 2.1 or later.</span></span> <span data-ttu-id="30136-110">Dans le cas contraire, ils peuvent s’arrêter lorsqu’ils sont chargés dans une application ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="30136-110">Otherwise, they may break when loaded into an ASP.NET Core 3.0 app.</span></span>
- <span data-ttu-id="30136-111">Les applications et les bibliothèques qui ciblent ASP.NET Core 2,1 et versions ultérieures doivent supprimer toutes les références directes au package NuGet `Microsoft.AspNetCore.Server.Kestrel.Https`.</span><span class="sxs-lookup"><span data-stu-id="30136-111">Apps and libraries targeting ASP.NET Core 2.1 and later should remove any direct references to the `Microsoft.AspNetCore.Server.Kestrel.Https` NuGet package.</span></span>

#### <a name="category"></a><span data-ttu-id="30136-112">Category</span><span class="sxs-lookup"><span data-stu-id="30136-112">Category</span></span>

<span data-ttu-id="30136-113">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="30136-113">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="30136-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="30136-114">Affected APIs</span></span>

<span data-ttu-id="30136-115">aucune.</span><span class="sxs-lookup"><span data-stu-id="30136-115">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
