---
ms.openlocfilehash: 907c4aa5573c392a68afad0a4d937eadcd556440
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620009"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a><span data-ttu-id="18197-101">Les valeurs de fusion Null ne sont pas visibles dans le débogueur jusqu’à une étape ultérieure</span><span class="sxs-lookup"><span data-stu-id="18197-101">Null coalescer values are not visible in debugger until one step later</span></span>

#### <a name="details"></a><span data-ttu-id="18197-102">Détails</span><span class="sxs-lookup"><span data-stu-id="18197-102">Details</span></span>

<span data-ttu-id="18197-103">Un bogue dans.NET Framework 4.5 empêche de voir les valeurs définies via une opération de fusion Null dans le débogueur immédiatement après le déroulement de l’opération d’assignation lors de l’exécution de la version 64 bits du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="18197-103">A bug in the .NET Framework 4.5 causes values set via a null coalescing operation to not be visible in the debugger immediately after the assignment operation is executed when running on the 64-bit version of the Framework.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="18197-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="18197-104">Suggestion</span></span>

<span data-ttu-id="18197-105">Une nouvelle exécution pas à pas dans le débogueur entraînera la mise à jour correcte de la valeur locale/du champ.</span><span class="sxs-lookup"><span data-stu-id="18197-105">Stepping one additional time in the debugger will cause the local/field's value to be correctly updated.</span></span> <span data-ttu-id="18197-106">Par ailleurs, ce problème a été corrigé dans .NET Framework 4.6 et vous pouvez le résoudre en effectuant la mise à niveau vers cette version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="18197-106">Also, this issue has been fixed in the .NET Framework 4.6; upgrading to that version of the Framework should solve the issue.</span></span>

| <span data-ttu-id="18197-107">Nom</span><span class="sxs-lookup"><span data-stu-id="18197-107">Name</span></span>    | <span data-ttu-id="18197-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="18197-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="18197-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="18197-109">Scope</span></span>   |<span data-ttu-id="18197-110">Edge</span><span class="sxs-lookup"><span data-stu-id="18197-110">Edge</span></span>|
|<span data-ttu-id="18197-111">Version</span><span class="sxs-lookup"><span data-stu-id="18197-111">Version</span></span>|<span data-ttu-id="18197-112">4,5</span><span class="sxs-lookup"><span data-stu-id="18197-112">4.5</span></span>|
|<span data-ttu-id="18197-113">Type</span><span class="sxs-lookup"><span data-stu-id="18197-113">Type</span></span>|<span data-ttu-id="18197-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="18197-114">Runtime</span></span>|
