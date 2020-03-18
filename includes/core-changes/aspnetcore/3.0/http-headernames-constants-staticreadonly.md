---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901909"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a><span data-ttu-id="ff504-101">HTTP: HeaderNames constantes changé à statique readonly</span><span class="sxs-lookup"><span data-stu-id="ff504-101">HTTP: HeaderNames constants changed to static readonly</span></span>

<span data-ttu-id="ff504-102">À partir de ASP.NET Core 3.0 Aperçu 5, `const` `static readonly`les champs dans <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> changé de .</span><span class="sxs-lookup"><span data-stu-id="ff504-102">Starting in ASP.NET Core 3.0 Preview 5, the fields in <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> changed from `const` to `static readonly`.</span></span>

<span data-ttu-id="ff504-103">Pour discussion, voir [dotnet/aspnetcore 9514](https://github.com/dotnet/aspnetcore/issues/9514).</span><span class="sxs-lookup"><span data-stu-id="ff504-103">For discussion, see [dotnet/aspnetcore#9514](https://github.com/dotnet/aspnetcore/issues/9514).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ff504-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ff504-104">Version introduced</span></span>

<span data-ttu-id="ff504-105">3.0</span><span class="sxs-lookup"><span data-stu-id="ff504-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ff504-106">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="ff504-106">Old behavior</span></span>

<span data-ttu-id="ff504-107">Ces champs étaient `const`autrefois .</span><span class="sxs-lookup"><span data-stu-id="ff504-107">These fields used to be `const`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="ff504-108">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="ff504-108">New behavior</span></span>

<span data-ttu-id="ff504-109">Ces champs `static readonly`sont maintenant .</span><span class="sxs-lookup"><span data-stu-id="ff504-109">These fields are now `static readonly`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ff504-110">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="ff504-110">Reason for change</span></span>

<span data-ttu-id="ff504-111">Le changement:</span><span class="sxs-lookup"><span data-stu-id="ff504-111">The change:</span></span>

* <span data-ttu-id="ff504-112">Empêche les valeurs d’être intégrées au-delà des limites de l’assemblage, ce qui permet des corrections de valeur au besoin.</span><span class="sxs-lookup"><span data-stu-id="ff504-112">Prevents the values from being embedded across assembly boundaries, allowing for value corrections as needed.</span></span>
* <span data-ttu-id="ff504-113">Permet des contrôles plus rapides de l’égalité des références.</span><span class="sxs-lookup"><span data-stu-id="ff504-113">Enables faster reference equality checks.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ff504-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="ff504-114">Recommended action</span></span>

<span data-ttu-id="ff504-115">Recomplez contre 3.0.</span><span class="sxs-lookup"><span data-stu-id="ff504-115">Recompile against 3.0.</span></span> <span data-ttu-id="ff504-116">Le code source utilisant ces champs de la manière suivante ne peut plus le faire :</span><span class="sxs-lookup"><span data-stu-id="ff504-116">Source code using these fields in the following ways can no longer do so:</span></span>

* <span data-ttu-id="ff504-117">Comme argument d’attribut</span><span class="sxs-lookup"><span data-stu-id="ff504-117">As an attribute argument</span></span>
* <span data-ttu-id="ff504-118">Comme `case` un `switch` dans une déclaration</span><span class="sxs-lookup"><span data-stu-id="ff504-118">As a `case` in a `switch` statement</span></span>
* <span data-ttu-id="ff504-119">Lors de la définition d’un autre`const`</span><span class="sxs-lookup"><span data-stu-id="ff504-119">When defining another `const`</span></span>

<span data-ttu-id="ff504-120">Pour contourner le changement de rupture, passez à l’utilisation de constantes de noms d’en-tête auto-définies ou de littérals de cordes.</span><span class="sxs-lookup"><span data-stu-id="ff504-120">To work around the breaking change, switch to using self-defined header name constants or string literals.</span></span>

#### <a name="category"></a><span data-ttu-id="ff504-121">Category</span><span class="sxs-lookup"><span data-stu-id="ff504-121">Category</span></span>

<span data-ttu-id="ff504-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ff504-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ff504-123">API affectées</span><span class="sxs-lookup"><span data-stu-id="ff504-123">Affected APIs</span></span>

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
