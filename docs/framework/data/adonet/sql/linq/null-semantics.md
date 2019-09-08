---
title: Sémantique Null
ms.date: 03/30/2017
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
ms.openlocfilehash: d0b18c0a699840d11f5e4add05147672f9bb69e9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792980"
---
# <a name="null-semantics"></a><span data-ttu-id="18057-102">Sémantique Null</span><span class="sxs-lookup"><span data-stu-id="18057-102">Null Semantics</span></span>
<span data-ttu-id="18057-103">Le tableau suivant fournit des liens vers différentes parties de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] la documentation `null` ,`Nothing` où les problèmes (dans Visual Basic) sont abordés.</span><span class="sxs-lookup"><span data-stu-id="18057-103">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in Visual Basic) issues are discussed.</span></span>  
  
|<span data-ttu-id="18057-104">Rubrique</span><span class="sxs-lookup"><span data-stu-id="18057-104">Topic</span></span>|<span data-ttu-id="18057-105">Description</span><span class="sxs-lookup"><span data-stu-id="18057-105">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="18057-106">Incompatibilité entre types SQL-CLR</span><span class="sxs-lookup"><span data-stu-id="18057-106">SQL-CLR Type Mismatches</span></span>](sql-clr-type-mismatches.md)|<span data-ttu-id="18057-107">La section « sémantique null » de cette rubrique présente la description de la valeur booléenne SQL à trois États par rapport à la Common Language Runtime à deux États <xref:System.Boolean>(CLR) `Nothing` , le littéral ( `null` Visual BasicC#) et (), ainsi que d’autres liés.</span><span class="sxs-lookup"><span data-stu-id="18057-107">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` (Visual Basic) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="18057-108">Traduction des opérateurs de requête standard</span><span class="sxs-lookup"><span data-stu-id="18057-108">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)|<span data-ttu-id="18057-109">La section « Sémantique Null » de cette rubrique décrit la sémantique de comparaison Null dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="18057-109">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="18057-110">System.String, méthodes</span><span class="sxs-lookup"><span data-stu-id="18057-110">System.String Methods</span></span>](system-string-methods.md)|<span data-ttu-id="18057-111">La section « Différences par rapport à .NET » de cette rubrique décrit comment un retour de 0 de <xref:System.String.LastIndexOf%2A> peut signifier que la chaîne a la valeur null ou que la position trouvée est 0.</span><span class="sxs-lookup"><span data-stu-id="18057-111">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="18057-112">Calculer la somme de valeurs dans une séquence numérique</span><span class="sxs-lookup"><span data-stu-id="18057-112">Compute the Sum of Values in a Numeric Sequence</span></span>](compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="18057-113">Décrit comment l' <xref:System.Linq.Enumerable.Sum%2A> opérateur prend `null` la valeur (`Nothing` dans Visual Basic) au lieu de 0 pour une séquence qui contient uniquement des valeurs null ou pour une séquence vide.</span><span class="sxs-lookup"><span data-stu-id="18057-113">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in Visual Basic) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="18057-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18057-114">See also</span></span>

- [<span data-ttu-id="18057-115">Fonctions et types de données</span><span class="sxs-lookup"><span data-stu-id="18057-115">Data Types and Functions</span></span>](data-types-and-functions.md)
