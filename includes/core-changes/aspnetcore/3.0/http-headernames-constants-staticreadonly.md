---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032534"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a><span data-ttu-id="7034a-101">HTTP : les constantes HeaderNames ont été modifiées en ReadOnly statique</span><span class="sxs-lookup"><span data-stu-id="7034a-101">HTTP: HeaderNames constants changed to static readonly</span></span>

<span data-ttu-id="7034a-102">À partir de ASP.NET Core 3,0 Preview 5, les champs de <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> ont été remplacés par `const` `static readonly` .</span><span class="sxs-lookup"><span data-stu-id="7034a-102">Starting in ASP.NET Core 3.0 Preview 5, the fields in <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> changed from `const` to `static readonly`.</span></span>

<span data-ttu-id="7034a-103">Pour plus d’informations, consultez [dotnet/aspnetcore # 9514](https://github.com/dotnet/aspnetcore/issues/9514).</span><span class="sxs-lookup"><span data-stu-id="7034a-103">For discussion, see [dotnet/aspnetcore#9514](https://github.com/dotnet/aspnetcore/issues/9514).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7034a-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="7034a-104">Version introduced</span></span>

<span data-ttu-id="7034a-105">3.0</span><span class="sxs-lookup"><span data-stu-id="7034a-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="7034a-106">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="7034a-106">Old behavior</span></span>

<span data-ttu-id="7034a-107">Ces champs sont utilisés comme `const` .</span><span class="sxs-lookup"><span data-stu-id="7034a-107">These fields used to be `const`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="7034a-108">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="7034a-108">New behavior</span></span>

<span data-ttu-id="7034a-109">Ces champs sont maintenant `static readonly` .</span><span class="sxs-lookup"><span data-stu-id="7034a-109">These fields are now `static readonly`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7034a-110">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="7034a-110">Reason for change</span></span>

<span data-ttu-id="7034a-111">La modification :</span><span class="sxs-lookup"><span data-stu-id="7034a-111">The change:</span></span>

* <span data-ttu-id="7034a-112">Empêche l’incorporation des valeurs dans les limites de l’assembly, ce qui permet d’obtenir des corrections de valeurs en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="7034a-112">Prevents the values from being embedded across assembly boundaries, allowing for value corrections as needed.</span></span>
* <span data-ttu-id="7034a-113">Active les vérifications d’égalité de référence plus rapides.</span><span class="sxs-lookup"><span data-stu-id="7034a-113">Enables faster reference equality checks.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7034a-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="7034a-114">Recommended action</span></span>

<span data-ttu-id="7034a-115">Recompilation sur 3,0.</span><span class="sxs-lookup"><span data-stu-id="7034a-115">Recompile against 3.0.</span></span> <span data-ttu-id="7034a-116">Le code source qui utilise ces champs de la manière suivante ne peut plus le faire :</span><span class="sxs-lookup"><span data-stu-id="7034a-116">Source code using these fields in the following ways can no longer do so:</span></span>

* <span data-ttu-id="7034a-117">En tant qu’argument d’attribut</span><span class="sxs-lookup"><span data-stu-id="7034a-117">As an attribute argument</span></span>
* <span data-ttu-id="7034a-118">En tant que `case` dans une `switch` instruction</span><span class="sxs-lookup"><span data-stu-id="7034a-118">As a `case` in a `switch` statement</span></span>
* <span data-ttu-id="7034a-119">Lors de la définition d’un autre `const`</span><span class="sxs-lookup"><span data-stu-id="7034a-119">When defining another `const`</span></span>

<span data-ttu-id="7034a-120">Pour contourner la modification avec rupture, basculez vers à l’aide de constantes de nom d’en-tête ou de littéraux de chaîne définis automatiquement.</span><span class="sxs-lookup"><span data-stu-id="7034a-120">To work around the breaking change, switch to using self-defined header name constants or string literals.</span></span>

#### <a name="category"></a><span data-ttu-id="7034a-121">Category</span><span class="sxs-lookup"><span data-stu-id="7034a-121">Category</span></span>

<span data-ttu-id="7034a-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7034a-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7034a-123">API affectées</span><span class="sxs-lookup"><span data-stu-id="7034a-123">Affected APIs</span></span>

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
