---
title: Tableaux
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: d4a1f379a88231654c710b1df7b505316377c915
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741807"
---
# <a name="arrays"></a><span data-ttu-id="fc222-102">Tableaux</span><span class="sxs-lookup"><span data-stu-id="fc222-102">Arrays</span></span>
<span data-ttu-id="fc222-103">✔️ préférez utiliser des collections sur des tableaux dans des API publiques.</span><span class="sxs-lookup"><span data-stu-id="fc222-103">✔️ DO prefer using collections over arrays in public APIs.</span></span> <span data-ttu-id="fc222-104">La section [Collections](../../../docs/standard/design-guidelines/guidelines-for-collections.md) fournit des détails sur la manière de choisir entre des collections et des tableaux.</span><span class="sxs-lookup"><span data-stu-id="fc222-104">The [Collections](../../../docs/standard/design-guidelines/guidelines-for-collections.md) section provides details about how to choose between collections and arrays.</span></span>

 <span data-ttu-id="fc222-105">❌ n’utilisez pas de champs de tableau en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="fc222-105">❌ DO NOT use read-only array fields.</span></span> <span data-ttu-id="fc222-106">Le champ lui-même est en lecture seule et ne peut pas être modifié, mais les éléments du tableau peuvent être modifiés.</span><span class="sxs-lookup"><span data-stu-id="fc222-106">The field itself is read-only and can't be changed, but elements in the array can be changed.</span></span>

 <span data-ttu-id="fc222-107">✔️ envisagez d’utiliser des tableaux en escalier à la place de tableaux multidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="fc222-107">✔️ CONSIDER using jagged arrays instead of multidimensional arrays.</span></span>

 <span data-ttu-id="fc222-108">Un tableau en escalier est un tableau avec des éléments qui sont également des tableaux.</span><span class="sxs-lookup"><span data-stu-id="fc222-108">A jagged array is an array with elements that are also arrays.</span></span> <span data-ttu-id="fc222-109">Les tableaux qui composent les éléments peuvent être de différentes tailles, ce qui permet d’obtenir un espace moins gaspillé pour certains jeux de données (par exemple, la matrice éparse) par rapport aux tableaux multidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="fc222-109">The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays.</span></span> <span data-ttu-id="fc222-110">En outre, le CLR optimise les opérations d’index sur les tableaux en escalier, de sorte qu’ils peuvent présenter de meilleures performances d’exécution dans certains scénarios.</span><span class="sxs-lookup"><span data-stu-id="fc222-110">Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.</span></span>

 <span data-ttu-id="fc222-111">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="fc222-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="fc222-112">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="fc222-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="fc222-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc222-113">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="fc222-114">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fc222-114">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="fc222-115">Indications relatives à l’utilisation</span><span class="sxs-lookup"><span data-stu-id="fc222-115">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
