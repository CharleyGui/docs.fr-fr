---
title: Sémantique Null
ms.date: 03/30/2017
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
ms.openlocfilehash: 739ee95be45d7d64a4ad1678837b9706a533f07d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147539"
---
# <a name="null-semantics"></a><span data-ttu-id="76ada-102">Sémantique Null</span><span class="sxs-lookup"><span data-stu-id="76ada-102">Null Semantics</span></span>

<span data-ttu-id="76ada-103">Le tableau suivant fournit des liens vers différentes parties de la [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation `null` , où les `Nothing` problèmes (dans Visual Basic) sont abordés.</span><span class="sxs-lookup"><span data-stu-id="76ada-103">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in Visual Basic) issues are discussed.</span></span>  
  
|<span data-ttu-id="76ada-104">Rubrique</span><span class="sxs-lookup"><span data-stu-id="76ada-104">Topic</span></span>|<span data-ttu-id="76ada-105">Description</span><span class="sxs-lookup"><span data-stu-id="76ada-105">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="76ada-106">Incompatibilité entre types SQL-CLR</span><span class="sxs-lookup"><span data-stu-id="76ada-106">SQL-CLR Type Mismatches</span></span>](sql-clr-type-mismatches.md)|<span data-ttu-id="76ada-107">La section « sémantique null » de cette rubrique présente la description de la valeur booléenne SQL à trois États par rapport à la common language runtime à deux États (CLR) <xref:System.Boolean> , le littéral `Nothing` (Visual Basic) et `null` (C#), ainsi que d’autres problèmes similaires.</span><span class="sxs-lookup"><span data-stu-id="76ada-107">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` (Visual Basic) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="76ada-108">Traduction des opérateurs de requête standard</span><span class="sxs-lookup"><span data-stu-id="76ada-108">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)|<span data-ttu-id="76ada-109">La section « Sémantique Null » de cette rubrique décrit la sémantique de comparaison Null dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="76ada-109">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="76ada-110">System.String, méthodes</span><span class="sxs-lookup"><span data-stu-id="76ada-110">System.String Methods</span></span>](system-string-methods.md)|<span data-ttu-id="76ada-111">La section « Différences par rapport à .NET » de cette rubrique décrit comment un retour de 0 de <xref:System.String.LastIndexOf%2A> peut signifier que la chaîne a la valeur null ou que la position trouvée est 0.</span><span class="sxs-lookup"><span data-stu-id="76ada-111">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="76ada-112">Comment : calculer la somme de valeurs dans une séquence numérique</span><span class="sxs-lookup"><span data-stu-id="76ada-112">Compute the Sum of Values in a Numeric Sequence</span></span>](compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="76ada-113">Décrit comment l' <xref:System.Linq.Enumerable.Sum%2A> opérateur prend la valeur `null` ( `Nothing` dans Visual Basic) au lieu de 0 pour une séquence qui contient uniquement des valeurs null ou pour une séquence vide.</span><span class="sxs-lookup"><span data-stu-id="76ada-113">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in Visual Basic) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="76ada-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76ada-114">See also</span></span>

- [<span data-ttu-id="76ada-115">Fonctions et types de données</span><span class="sxs-lookup"><span data-stu-id="76ada-115">Data Types and Functions</span></span>](data-types-and-functions.md)
