---
ms.openlocfilehash: c1a2d76b4e596acc395da6cefed008078e57a336
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858602"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a><span data-ttu-id="336da-101">Les valeurs de fusion Null ne sont pas visibles dans le débogueur jusqu’à une étape ultérieure</span><span class="sxs-lookup"><span data-stu-id="336da-101">Null coalescer values are not visible in debugger until one step later</span></span>

|   |   |
|---|---|
|<span data-ttu-id="336da-102">Détails</span><span class="sxs-lookup"><span data-stu-id="336da-102">Details</span></span>|<span data-ttu-id="336da-103">Un bogue dans.NET Framework 4.5 empêche de voir les valeurs définies via une opération de fusion Null dans le débogueur immédiatement après le déroulement de l’opération d’assignation lors de l’exécution de la version 64 bits du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="336da-103">A bug in the .NET Framework 4.5 causes values set via a null coalescing operation to not be visible in the debugger immediately after the assignment operation is executed when running on the 64-bit version of the Framework.</span></span>|
|<span data-ttu-id="336da-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="336da-104">Suggestion</span></span>|<span data-ttu-id="336da-105">Une nouvelle exécution pas à pas dans le débogueur entraînera la mise à jour correcte de la valeur locale/du champ.</span><span class="sxs-lookup"><span data-stu-id="336da-105">Stepping one additional time in the debugger will cause the local/field's value to be correctly updated.</span></span> <span data-ttu-id="336da-106">Par ailleurs, ce problème a été corrigé dans .NET Framework 4.6 et vous pouvez le résoudre en effectuant la mise à niveau vers cette version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="336da-106">Also, this issue has been fixed in the .NET Framework 4.6; upgrading to that version of the Framework should solve the issue.</span></span>|
|<span data-ttu-id="336da-107">Portée</span><span class="sxs-lookup"><span data-stu-id="336da-107">Scope</span></span>|<span data-ttu-id="336da-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="336da-108">Edge</span></span>|
|<span data-ttu-id="336da-109">Version</span><span class="sxs-lookup"><span data-stu-id="336da-109">Version</span></span>|<span data-ttu-id="336da-110">4.5</span><span class="sxs-lookup"><span data-stu-id="336da-110">4.5</span></span>|
|<span data-ttu-id="336da-111">Type</span><span class="sxs-lookup"><span data-stu-id="336da-111">Type</span></span>|<span data-ttu-id="336da-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="336da-112">Runtime</span></span>|

