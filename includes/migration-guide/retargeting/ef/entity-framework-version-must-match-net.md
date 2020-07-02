---
ms.openlocfilehash: 863e7035827537e0f943af05c2f0232029b99db8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617190"
---
### <a name="entity-framework-version-must-match-the-net-framework-version"></a><span data-ttu-id="f5717-101">La version d’Entity Framework doit correspondre à la version du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f5717-101">Entity Framework version must match the .NET Framework version</span></span>

#### <a name="details"></a><span data-ttu-id="f5717-102">Détails</span><span class="sxs-lookup"><span data-stu-id="f5717-102">Details</span></span>

<span data-ttu-id="f5717-103">La version d’Entity Framework (EF) doit être mise en correspondance avec la version de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f5717-103">The Entity Framework (EF) version should be matched with the .NET Framework version.</span></span> <span data-ttu-id="f5717-104">Entity Framework 5 est recommandé pour .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="f5717-104">Entity Framework 5 is recommended for .NET Framework 4.5.</span></span> <span data-ttu-id="f5717-105">Il existe certains problèmes connus avec EF 4.x dans un projet .NET Framework 4.5 concernant <xref:System.ComponentModel.DataAnnotations>.</span><span class="sxs-lookup"><span data-stu-id="f5717-105">There are some known issues with EF 4.x in a .NET Framework 4.5 project around <xref:System.ComponentModel.DataAnnotations>.</span></span> <span data-ttu-id="f5717-106">Dans .NET Framework 4,5, ceux-ci ont été déplacés vers un autre assembly, ce qui signifie qu’il existe des problèmes pour déterminer les annotations à utiliser.</span><span class="sxs-lookup"><span data-stu-id="f5717-106">In .NET Framework 4.5, these were moved to a different assembly, so there are issues determining which annotations to use.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f5717-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="f5717-107">Suggestion</span></span>

<span data-ttu-id="f5717-108">Mise à niveau vers Entity Framework 5 pour .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="f5717-108">Upgrade to Entity Framework 5 for .NET Framework 4.5</span></span>

| <span data-ttu-id="f5717-109">Nom</span><span class="sxs-lookup"><span data-stu-id="f5717-109">Name</span></span>    | <span data-ttu-id="f5717-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="f5717-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f5717-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="f5717-111">Scope</span></span>   | <span data-ttu-id="f5717-112">Majeure</span><span class="sxs-lookup"><span data-stu-id="f5717-112">Major</span></span>       |
| <span data-ttu-id="f5717-113">Version</span><span class="sxs-lookup"><span data-stu-id="f5717-113">Version</span></span> | <span data-ttu-id="f5717-114">4,5</span><span class="sxs-lookup"><span data-stu-id="f5717-114">4.5</span></span>         |
| <span data-ttu-id="f5717-115">Type</span><span class="sxs-lookup"><span data-stu-id="f5717-115">Type</span></span>    | <span data-ttu-id="f5717-116">Reciblage</span><span class="sxs-lookup"><span data-stu-id="f5717-116">Retargeting</span></span> |
