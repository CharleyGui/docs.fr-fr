---
title: 'Comment : calculer la somme de valeurs dans une séquence numérique'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
ms.openlocfilehash: 978b02e9363a89c5bd007afc1960bd2a2d0ca0d2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592551"
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a><span data-ttu-id="c93f5-102">Comment : calculer la somme de valeurs dans une séquence numérique</span><span class="sxs-lookup"><span data-stu-id="c93f5-102">Compute the Sum of Values in a Numeric Sequence</span></span>
<span data-ttu-id="c93f5-103">Utilisez l'opérateur <xref:System.Linq.Enumerable.Sum%2A> pour calculer la somme des valeurs numériques dans une séquence.</span><span class="sxs-lookup"><span data-stu-id="c93f5-103">Use the <xref:System.Linq.Enumerable.Sum%2A> operator to compute the sum of numeric values in a sequence.</span></span>  
  
 <span data-ttu-id="c93f5-104">Notez les caractéristiques suivantes de l'opérateur `Sum` dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="c93f5-104">Note the following characteristics of the `Sum` operator in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
- <span data-ttu-id="c93f5-105">L'opérateur d'agrégation (opérateur de requête standard) `Sum` prend la valeur zéro pour une séquence vide ou contenant uniquement des valeurs null.</span><span class="sxs-lookup"><span data-stu-id="c93f5-105">The Standard Query Operator aggregate operator `Sum` evaluates to zero for an empty sequence or a sequence that contains only nulls.</span></span> <span data-ttu-id="c93f5-106">Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], la sémantique de SQL reste inchangée.</span><span class="sxs-lookup"><span data-stu-id="c93f5-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged.</span></span> <span data-ttu-id="c93f5-107">`Sum` prend donc la valeur null plutôt que la valeur zéro pour une séquence vide ou contenant uniquement des valeurs null.</span><span class="sxs-lookup"><span data-stu-id="c93f5-107">For this reason, `Sum` evaluates to null instead of to zero for an empty sequence or for a sequence that contains only nulls.</span></span>  
  
- <span data-ttu-id="c93f5-108">Les limitations SQL sur les résultats intermédiaires s'appliquent aux agrégats dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c93f5-108">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="c93f5-109">Somme des quantités d’entier 32 bits n’est pas calculée à l’aide des résultats 64 bits et de dépassement de capacité peut se produire pour le [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduction de `Sum`.</span><span class="sxs-lookup"><span data-stu-id="c93f5-109">Sum of 32-bit integer quantities is not computed by using 64-bit results, and overflow can occur for the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of `Sum`.</span></span> <span data-ttu-id="c93f5-110">Ce risque existe même si l'implémentation de l'opérateur de requête standard n'entraîne pas de dépassement de capacité pour la séquence en mémoire correspondante.</span><span class="sxs-lookup"><span data-stu-id="c93f5-110">This possibility exists even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c93f5-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="c93f5-111">Example</span></span>  
 <span data-ttu-id="c93f5-112">L'exemple suivant recherche les frais de transport totaux pour toutes les commandes de la table `Order`.</span><span class="sxs-lookup"><span data-stu-id="c93f5-112">The following example finds the total freight of all orders in the `Order` table.</span></span>  
  
 <span data-ttu-id="c93f5-113">Si vous exécutez cette requête sur l'exemple de base de données Northwind, vous obtenez le résultat suivant : `64942.6900`.</span><span class="sxs-lookup"><span data-stu-id="c93f5-113">If you run this query against the Northwind sample database, the output is: `64942.6900`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="c93f5-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="c93f5-114">Example</span></span>  
 <span data-ttu-id="c93f5-115">L'exemple suivant recherche le nombre total d'unités commandées pour tous les produits.</span><span class="sxs-lookup"><span data-stu-id="c93f5-115">The following example finds the total number of units on order for all products.</span></span>  
  
 <span data-ttu-id="c93f5-116">Si vous exécutez cette requête sur l'exemple de base de données Northwind, vous obtenez le résultat suivant : `780`.</span><span class="sxs-lookup"><span data-stu-id="c93f5-116">If you run this query against the Northwind sample database, the output is: `780`.</span></span>  
  
 <span data-ttu-id="c93f5-117">Notez que vous devez effectuer un cast des types `short` (par exemple, `UnitsOnOrder`) car `Sum` n'a aucune surcharge pour les types courts.</span><span class="sxs-lookup"><span data-stu-id="c93f5-117">Note that you must cast `short` types (for example, `UnitsOnOrder`) because `Sum` has no overload for short types.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="c93f5-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c93f5-118">See also</span></span>

- [<span data-ttu-id="c93f5-119">Requêtes d’agrégation</span><span class="sxs-lookup"><span data-stu-id="c93f5-119">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
- [<span data-ttu-id="c93f5-120">Téléchargement d’exemples de base de données</span><span class="sxs-lookup"><span data-stu-id="c93f5-120">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
