---
title: Tableaux
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: c3545c609b6544e6528bbae08889d0ef20473802
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821604"
---
# <a name="arrays"></a><span data-ttu-id="782f1-102">Tableaux</span><span class="sxs-lookup"><span data-stu-id="782f1-102">Arrays</span></span>
<span data-ttu-id="782f1-103">✔️ préférez utiliser des collections sur des tableaux dans des API publiques.</span><span class="sxs-lookup"><span data-stu-id="782f1-103">✔️ DO prefer using collections over arrays in public APIs.</span></span> <span data-ttu-id="782f1-104">La section [Collections](guidelines-for-collections.md) fournit des détails sur la manière de choisir entre des collections et des tableaux.</span><span class="sxs-lookup"><span data-stu-id="782f1-104">The [Collections](guidelines-for-collections.md) section provides details about how to choose between collections and arrays.</span></span>

 <span data-ttu-id="782f1-105">❌ N’utilisez pas de champs de tableau en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="782f1-105">❌ DO NOT use read-only array fields.</span></span> <span data-ttu-id="782f1-106">Le champ lui-même est en lecture seule et ne peut pas être modifié, mais les éléments du tableau peuvent être modifiés.</span><span class="sxs-lookup"><span data-stu-id="782f1-106">The field itself is read-only and can't be changed, but elements in the array can be changed.</span></span>

 <span data-ttu-id="782f1-107">✔️ envisagez d’utiliser des tableaux en escalier à la place de tableaux multidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="782f1-107">✔️ CONSIDER using jagged arrays instead of multidimensional arrays.</span></span>

 <span data-ttu-id="782f1-108">Un tableau en escalier est un tableau avec des éléments qui sont également des tableaux.</span><span class="sxs-lookup"><span data-stu-id="782f1-108">A jagged array is an array with elements that are also arrays.</span></span> <span data-ttu-id="782f1-109">Les tableaux qui composent les éléments peuvent être de différentes tailles, ce qui permet d’obtenir un espace moins gaspillé pour certains jeux de données (par exemple, la matrice éparse) par rapport aux tableaux multidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="782f1-109">The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays.</span></span> <span data-ttu-id="782f1-110">En outre, le CLR optimise les opérations d’index sur les tableaux en escalier, de sorte qu’ils peuvent présenter de meilleures performances d’exécution dans certains scénarios.</span><span class="sxs-lookup"><span data-stu-id="782f1-110">Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.</span></span>

 <span data-ttu-id="782f1-111">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="782f1-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="782f1-112">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="782f1-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="782f1-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="782f1-113">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="782f1-114">Directives de conception d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="782f1-114">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="782f1-115">Instructions d’utilisation</span><span class="sxs-lookup"><span data-stu-id="782f1-115">Usage Guidelines</span></span>](usage-guidelines.md)
