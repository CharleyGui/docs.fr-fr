---
ms.openlocfilehash: be1fad236dd3eed047b010e93285aec8bc607b61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394330"
---
### <a name="hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced"></a><span data-ttu-id="66f2f-101">Hébergement : types IHostingEnvironment et IApplicationLifetime marqués comme obsolètes et remplacés</span><span class="sxs-lookup"><span data-stu-id="66f2f-101">Hosting: IHostingEnvironment and IApplicationLifetime types marked obsolete and replaced</span></span>

<span data-ttu-id="66f2f-102">De nouveaux types ont été introduits pour `IHostingEnvironment` remplacer `IApplicationLifetime` les types et existants.</span><span class="sxs-lookup"><span data-stu-id="66f2f-102">New types have been introduced to replace existing `IHostingEnvironment` and `IApplicationLifetime` types.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="66f2f-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="66f2f-103">Version introduced</span></span>

<span data-ttu-id="66f2f-104">3.0</span><span class="sxs-lookup"><span data-stu-id="66f2f-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="66f2f-105">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="66f2f-105">Old behavior</span></span>

<span data-ttu-id="66f2f-106">Il existe deux types `IHostingEnvironment` différents `IApplicationLifetime` et de `Microsoft.Extensions.Hosting` et `Microsoft.AspNetCore.Hosting`.</span><span class="sxs-lookup"><span data-stu-id="66f2f-106">There were two different `IHostingEnvironment` and `IApplicationLifetime` types from `Microsoft.Extensions.Hosting` and `Microsoft.AspNetCore.Hosting`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="66f2f-107">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="66f2f-107">New behavior</span></span>

<span data-ttu-id="66f2f-108">Les anciens types ont été marqués comme obsolètes et remplacés par de nouveaux types.</span><span class="sxs-lookup"><span data-stu-id="66f2f-108">The old types have been marked as obsolete and replaced with new types.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="66f2f-109">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="66f2f-109">Reason for change</span></span>

<span data-ttu-id="66f2f-110">Quand `Microsoft.Extensions.Hosting` a été introduit dans ASP.net Core 2,1, certains types `IHostingEnvironment` comme `IApplicationLifetime` et ont été `Microsoft.AspNetCore.Hosting`copiés à partir de.</span><span class="sxs-lookup"><span data-stu-id="66f2f-110">When `Microsoft.Extensions.Hosting` was introduced in ASP.NET Core 2.1, some types like `IHostingEnvironment` and `IApplicationLifetime` were copied from `Microsoft.AspNetCore.Hosting`.</span></span> <span data-ttu-id="66f2f-111">Certaines modifications de l’ASP.NET Core 3,0 entraînent l’inclusion `Microsoft.Extensions.Hosting` des `Microsoft.AspNetCore.Hosting` espaces de noms et dans les applications.</span><span class="sxs-lookup"><span data-stu-id="66f2f-111">Some ASP.NET Core 3.0 changes cause apps to include both the `Microsoft.Extensions.Hosting` and `Microsoft.AspNetCore.Hosting` namespaces.</span></span> <span data-ttu-id="66f2f-112">Toute utilisation de ces types dupliqués provoque une erreur du compilateur « référence ambiguë » lorsque les deux espaces de noms sont référencés.</span><span class="sxs-lookup"><span data-stu-id="66f2f-112">Any use of those duplicate types causes an "ambiguous reference" compiler error when both namespaces are referenced.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="66f2f-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="66f2f-113">Recommended action</span></span>

<span data-ttu-id="66f2f-114">Remplacement des utilisations des anciens types par les types nouvellement introduits comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="66f2f-114">Replaced any usages of the old types with the newly introduced types as below:</span></span>

<span data-ttu-id="66f2f-115">**Types obsolètes (avertissement) :**</span><span class="sxs-lookup"><span data-stu-id="66f2f-115">**Obsolete types (warning):**</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>

<span data-ttu-id="66f2f-116">**Nouveaux types :**</span><span class="sxs-lookup"><span data-stu-id="66f2f-116">**New types:**</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment?displayProperty=nameWithType>
- `Microsoft.AspNetCore.Hosting.IWebHostEnvironment : IHostEnvironment`
- <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.Environments?displayProperty=nameWithType>

<span data-ttu-id="66f2f-117">Les nouvelles `IHostEnvironment` `IsDevelopment` méthodes `IsProduction` et les méthodes d’extension `Microsoft.Extensions.Hosting` se trouvent dans l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="66f2f-117">The new `IHostEnvironment` `IsDevelopment` and `IsProduction` extension methods are in the `Microsoft.Extensions.Hosting` namespace.</span></span> <span data-ttu-id="66f2f-118">Cet espace de noms devra peut-être être ajouté à votre projet.</span><span class="sxs-lookup"><span data-stu-id="66f2f-118">That namespace may need to be added to your project.</span></span>

#### <a name="category"></a><span data-ttu-id="66f2f-119">Category</span><span class="sxs-lookup"><span data-stu-id="66f2f-119">Category</span></span>

<span data-ttu-id="66f2f-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="66f2f-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="66f2f-121">API affectées</span><span class="sxs-lookup"><span data-stu-id="66f2f-121">Affected APIs</span></span>

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
