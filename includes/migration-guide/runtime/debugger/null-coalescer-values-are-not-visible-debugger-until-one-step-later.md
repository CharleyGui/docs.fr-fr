---
ms.openlocfilehash: 22f8e3bb1ba72379b3f5fc87a077e5fe57f89bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858602"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a><span data-ttu-id="17817-101">Les valeurs de fusion Null ne sont pas visibles dans le débogueur jusqu’à une étape ultérieure</span><span class="sxs-lookup"><span data-stu-id="17817-101">Null coalescer values are not visible in debugger until one step later</span></span>

|   |   |
|---|---|
|<span data-ttu-id="17817-102">Détails</span><span class="sxs-lookup"><span data-stu-id="17817-102">Details</span></span>|<span data-ttu-id="17817-103">Un bogue dans.NET Framework 4.5 empêche de voir les valeurs définies via une opération de fusion Null dans le débogueur immédiatement après le déroulement de l’opération d’assignation lors de l’exécution de la version 64 bits du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="17817-103">A bug in the .NET Framework 4.5 causes values set via a null coalescing operation to not be visible in the debugger immediately after the assignment operation is executed when running on the 64-bit version of the Framework.</span></span>|
|<span data-ttu-id="17817-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="17817-104">Suggestion</span></span>|<span data-ttu-id="17817-105">Une nouvelle exécution pas à pas dans le débogueur entraînera la mise à jour correcte de la valeur locale/du champ.</span><span class="sxs-lookup"><span data-stu-id="17817-105">Stepping one additional time in the debugger will cause the local/field's value to be correctly updated.</span></span> <span data-ttu-id="17817-106">Par ailleurs, ce problème a été corrigé dans .NET Framework 4.6 et vous pouvez le résoudre en effectuant la mise à niveau vers cette version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="17817-106">Also, this issue has been fixed in the .NET Framework 4.6; upgrading to that version of the Framework should solve the issue.</span></span>|
|<span data-ttu-id="17817-107">Étendue</span><span class="sxs-lookup"><span data-stu-id="17817-107">Scope</span></span>|<span data-ttu-id="17817-108">Edge</span><span class="sxs-lookup"><span data-stu-id="17817-108">Edge</span></span>|
|<span data-ttu-id="17817-109">Version</span><span class="sxs-lookup"><span data-stu-id="17817-109">Version</span></span>|<span data-ttu-id="17817-110">4.5</span><span class="sxs-lookup"><span data-stu-id="17817-110">4.5</span></span>|
|<span data-ttu-id="17817-111">Type</span><span class="sxs-lookup"><span data-stu-id="17817-111">Type</span></span>|<span data-ttu-id="17817-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="17817-112">Runtime</span></span>|
