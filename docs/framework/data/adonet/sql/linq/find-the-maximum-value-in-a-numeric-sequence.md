---
title: 'Comment : rechercher la valeur maximale dans une séquence numérique'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70d7c058-0280-4815-a008-6f290093591a
ms.openlocfilehash: ebef8cb373da4021fd68fd7ce38de8cb06eb81ec
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782170"
---
# <a name="find-the-maximum-value-in-a-numeric-sequence"></a><span data-ttu-id="26552-102">Comment : rechercher la valeur maximale dans une séquence numérique</span><span class="sxs-lookup"><span data-stu-id="26552-102">Find the Maximum Value in a Numeric Sequence</span></span>
<span data-ttu-id="26552-103">Utilisez l'opérateur <xref:System.Linq.Enumerable.Max%2A> pour rechercher la valeur la plus élevée dans une séquence de valeurs numériques.</span><span class="sxs-lookup"><span data-stu-id="26552-103">Use the <xref:System.Linq.Enumerable.Max%2A> operator to find the highest value in a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26552-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="26552-104">Example</span></span>  
 <span data-ttu-id="26552-105">L'exemple suivant recherche la date la plus récente d'embauche parmi tous les employés.</span><span class="sxs-lookup"><span data-stu-id="26552-105">The following example finds the latest date of hire for any employee.</span></span>  
  
 <span data-ttu-id="26552-106">Si vous exécutez cette requête sur l'exemple de base de données Northwind, vous obtenez le résultat suivant : `11/15/1994 12:00:00 AM`.</span><span class="sxs-lookup"><span data-stu-id="26552-106">If you run this query against the sample Northwind database, the output is: `11/15/1994 12:00:00 AM`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#6)]
 [!code-vb[DLinqQueryExamples#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="26552-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="26552-107">Example</span></span>  
 <span data-ttu-id="26552-108">L'exemple suivant recherche les unités dont le stock est le plus élevé parmi tous les produits.</span><span class="sxs-lookup"><span data-stu-id="26552-108">The following example finds the most units in stock for any product.</span></span>  
  
 <span data-ttu-id="26552-109">Si vous exécutez cette requête sur l'exemple de base de données Northwind, vous obtenez le résultat suivant : `125`.</span><span class="sxs-lookup"><span data-stu-id="26552-109">If you run this example against the sample Northwind database, the output is: `125`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#7)]
 [!code-vb[DLinqQueryExamples#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#7)]  
  
## <a name="example"></a><span data-ttu-id="26552-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="26552-110">Example</span></span>  
 <span data-ttu-id="26552-111">L'exemple suivant utilise Max pour rechercher les `Products` dont le prix unitaire est le plus élevé dans chaque catégorie.</span><span class="sxs-lookup"><span data-stu-id="26552-111">The following example uses Max to find the `Products` that have the highest unit price in each category.</span></span> <span data-ttu-id="26552-112">Les résultats sont ensuite répertoriés par catégorie.</span><span class="sxs-lookup"><span data-stu-id="26552-112">The output then lists the results by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#8)]
 [!code-vb[DLinqQueryExamples#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#8)]  
  
 <span data-ttu-id="26552-113">Si vous exécutez la requête précédente sur l'exemple de base de données Northwind, les résultats se présenteront comme suit :</span><span class="sxs-lookup"><span data-stu-id="26552-113">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
 `1`  
  
 `Côte de Blaye`  
  
 `2`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `4`  
  
 `Raclette Courdavault`  
  
 `5`  
  
 `Gnocchi di nonna Alice`  
  
 `6`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Carnarvon Tigers`  
  
## <a name="see-also"></a><span data-ttu-id="26552-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26552-114">See also</span></span>

- [<span data-ttu-id="26552-115">Requêtes d’agrégation</span><span class="sxs-lookup"><span data-stu-id="26552-115">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="26552-116">Téléchargement d’exemples de base de données</span><span class="sxs-lookup"><span data-stu-id="26552-116">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
