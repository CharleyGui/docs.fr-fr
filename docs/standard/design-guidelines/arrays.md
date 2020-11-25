---
title: Tableaux
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: 11c1d23af4cf599ba632144634947520a1647ae7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701391"
---
# <a name="arrays"></a><span data-ttu-id="9abe4-102">Tableaux</span><span class="sxs-lookup"><span data-stu-id="9abe4-102">Arrays</span></span>

<span data-ttu-id="9abe4-103">✔️ préférez utiliser des collections sur des tableaux dans des API publiques.</span><span class="sxs-lookup"><span data-stu-id="9abe4-103">✔️ DO prefer using collections over arrays in public APIs.</span></span> <span data-ttu-id="9abe4-104">La section [Collections](guidelines-for-collections.md) fournit des détails sur la manière de choisir entre des collections et des tableaux.</span><span class="sxs-lookup"><span data-stu-id="9abe4-104">The [Collections](guidelines-for-collections.md) section provides details about how to choose between collections and arrays.</span></span>

 <span data-ttu-id="9abe4-105">❌ N’utilisez pas de champs de tableau en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="9abe4-105">❌ DO NOT use read-only array fields.</span></span> <span data-ttu-id="9abe4-106">Le champ lui-même est en lecture seule et ne peut pas être modifié, mais les éléments du tableau peuvent être modifiés.</span><span class="sxs-lookup"><span data-stu-id="9abe4-106">The field itself is read-only and can't be changed, but elements in the array can be changed.</span></span>

 <span data-ttu-id="9abe4-107">✔️ envisagez d’utiliser des tableaux en escalier à la place de tableaux multidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="9abe4-107">✔️ CONSIDER using jagged arrays instead of multidimensional arrays.</span></span>

 <span data-ttu-id="9abe4-108">Un tableau en escalier est un tableau avec des éléments qui sont également des tableaux.</span><span class="sxs-lookup"><span data-stu-id="9abe4-108">A jagged array is an array with elements that are also arrays.</span></span> <span data-ttu-id="9abe4-109">Les tableaux qui composent les éléments peuvent être de différentes tailles, ce qui permet d’obtenir un espace moins gaspillé pour certains jeux de données (par exemple, la matrice éparse) par rapport aux tableaux multidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="9abe4-109">The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays.</span></span> <span data-ttu-id="9abe4-110">En outre, le CLR optimise les opérations d’index sur les tableaux en escalier, de sorte qu’ils peuvent présenter de meilleures performances d’exécution dans certains scénarios.</span><span class="sxs-lookup"><span data-stu-id="9abe4-110">Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.</span></span>

 <span data-ttu-id="9abe4-111">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="9abe4-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="9abe4-112">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="9abe4-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="9abe4-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9abe4-113">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="9abe4-114">Directives de conception d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="9abe4-114">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="9abe4-115">Instructions d’utilisation</span><span class="sxs-lookup"><span data-stu-id="9abe4-115">Usage Guidelines</span></span>](usage-guidelines.md)
