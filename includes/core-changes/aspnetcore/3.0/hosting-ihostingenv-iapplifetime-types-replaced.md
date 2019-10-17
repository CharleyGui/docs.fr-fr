---
ms.openlocfilehash: be1fad236dd3eed047b010e93285aec8bc607b61
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394330"
---
### <a name="hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced"></a><span data-ttu-id="d6a75-101">Hébergement : types IHostingEnvironment et IApplicationLifetime marqués comme obsolètes et remplacés</span><span class="sxs-lookup"><span data-stu-id="d6a75-101">Hosting: IHostingEnvironment and IApplicationLifetime types marked obsolete and replaced</span></span>

<span data-ttu-id="d6a75-102">De nouveaux types ont été introduits pour remplacer les types `IHostingEnvironment` et `IApplicationLifetime` existants.</span><span class="sxs-lookup"><span data-stu-id="d6a75-102">New types have been introduced to replace existing `IHostingEnvironment` and `IApplicationLifetime` types.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d6a75-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="d6a75-103">Version introduced</span></span>

<span data-ttu-id="d6a75-104">3,0</span><span class="sxs-lookup"><span data-stu-id="d6a75-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d6a75-105">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="d6a75-105">Old behavior</span></span>

<span data-ttu-id="d6a75-106">Il existe deux types `IHostingEnvironment` et `IApplicationLifetime` différents de `Microsoft.Extensions.Hosting` et `Microsoft.AspNetCore.Hosting`.</span><span class="sxs-lookup"><span data-stu-id="d6a75-106">There were two different `IHostingEnvironment` and `IApplicationLifetime` types from `Microsoft.Extensions.Hosting` and `Microsoft.AspNetCore.Hosting`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d6a75-107">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="d6a75-107">New behavior</span></span>

<span data-ttu-id="d6a75-108">Les anciens types ont été marqués comme obsolètes et remplacés par de nouveaux types.</span><span class="sxs-lookup"><span data-stu-id="d6a75-108">The old types have been marked as obsolete and replaced with new types.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d6a75-109">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="d6a75-109">Reason for change</span></span>

<span data-ttu-id="d6a75-110">Lorsque `Microsoft.Extensions.Hosting` a été introduite dans ASP.NET Core 2,1, certains types, comme `IHostingEnvironment` et `IApplicationLifetime`, ont été copiés à partir de `Microsoft.AspNetCore.Hosting`.</span><span class="sxs-lookup"><span data-stu-id="d6a75-110">When `Microsoft.Extensions.Hosting` was introduced in ASP.NET Core 2.1, some types like `IHostingEnvironment` and `IApplicationLifetime` were copied from `Microsoft.AspNetCore.Hosting`.</span></span> <span data-ttu-id="d6a75-111">Certaines modifications de l’ASP.NET Core 3,0 entraînent l’inclusion à la fois des espaces de noms `Microsoft.Extensions.Hosting` et `Microsoft.AspNetCore.Hosting` dans les applications.</span><span class="sxs-lookup"><span data-stu-id="d6a75-111">Some ASP.NET Core 3.0 changes cause apps to include both the `Microsoft.Extensions.Hosting` and `Microsoft.AspNetCore.Hosting` namespaces.</span></span> <span data-ttu-id="d6a75-112">Toute utilisation de ces types dupliqués provoque une erreur du compilateur « référence ambiguë » lorsque les deux espaces de noms sont référencés.</span><span class="sxs-lookup"><span data-stu-id="d6a75-112">Any use of those duplicate types causes an "ambiguous reference" compiler error when both namespaces are referenced.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d6a75-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="d6a75-113">Recommended action</span></span>

<span data-ttu-id="d6a75-114">Remplacement des utilisations des anciens types par les types nouvellement introduits comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="d6a75-114">Replaced any usages of the old types with the newly introduced types as below:</span></span>

<span data-ttu-id="d6a75-115">**Types obsolètes (avertissement) :**</span><span class="sxs-lookup"><span data-stu-id="d6a75-115">**Obsolete types (warning):**</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>

<span data-ttu-id="d6a75-116">**Nouveaux types :**</span><span class="sxs-lookup"><span data-stu-id="d6a75-116">**New types:**</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment?displayProperty=nameWithType>
- `Microsoft.AspNetCore.Hosting.IWebHostEnvironment : IHostEnvironment`
- <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.Environments?displayProperty=nameWithType>

<span data-ttu-id="d6a75-117">Les nouvelles méthodes d’extension `IHostEnvironment` `IsDevelopment` et `IsProduction` se trouvent dans l’espace de noms `Microsoft.Extensions.Hosting`.</span><span class="sxs-lookup"><span data-stu-id="d6a75-117">The new `IHostEnvironment` `IsDevelopment` and `IsProduction` extension methods are in the `Microsoft.Extensions.Hosting` namespace.</span></span> <span data-ttu-id="d6a75-118">Cet espace de noms devra peut-être être ajouté à votre projet.</span><span class="sxs-lookup"><span data-stu-id="d6a75-118">That namespace may need to be added to your project.</span></span>

#### <a name="category"></a><span data-ttu-id="d6a75-119">Category</span><span class="sxs-lookup"><span data-stu-id="d6a75-119">Category</span></span>

<span data-ttu-id="d6a75-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d6a75-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d6a75-121">API affectées</span><span class="sxs-lookup"><span data-stu-id="d6a75-121">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Hosting.EnvironmentName`
- `T:Microsoft.AspNetCore.Hosting.IApplicationLifetime`
- `T:Microsoft.AspNetCore.Hosting.IHostingEnvironment`
- `T:Microsoft.Extensions.Hosting.EnvironmentName`
- `T:Microsoft.Extensions.Hosting.IApplicationLifetime`
- `T:Microsoft.Extensions.Hosting.IHostingEnvironment`

-->
