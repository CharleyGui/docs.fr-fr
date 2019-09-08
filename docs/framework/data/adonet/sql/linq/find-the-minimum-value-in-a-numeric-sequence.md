---
title: 'Comment : rechercher la valeur minimale dans une séquence numérique'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 78203093-f242-4572-9b31-9495b10926aa
ms.openlocfilehash: d8aee43f13ec92f649b4df20505ac56c336fe07a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793835"
---
# <a name="find-the-minimum-value-in-a-numeric-sequence"></a><span data-ttu-id="11d57-102">Comment : rechercher la valeur minimale dans une séquence numérique</span><span class="sxs-lookup"><span data-stu-id="11d57-102">Find the Minimum Value in a Numeric Sequence</span></span>
<span data-ttu-id="11d57-103">Utilisez l'opérateur <xref:System.Linq.Enumerable.Min%2A> pour retourner la valeur minimale d'une séquence de valeurs numériques.</span><span class="sxs-lookup"><span data-stu-id="11d57-103">Use the <xref:System.Linq.Enumerable.Min%2A> operator to return the minimum value from a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11d57-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="11d57-104">Example</span></span>  
 <span data-ttu-id="11d57-105">L'exemple suivant recherche le prix unitaire le plus bas parmi les produits.</span><span class="sxs-lookup"><span data-stu-id="11d57-105">The following example finds the lowest unit price of any product.</span></span>  
  
 <span data-ttu-id="11d57-106">Si vous exécutez cette requête sur l'exemple de base de données Northwind, vous obtenez le résultat suivant : `2.5000`.</span><span class="sxs-lookup"><span data-stu-id="11d57-106">If you run this query against the Northwind sample database, the output is: `2.5000`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#9)]
 [!code-vb[DLinqQueryExamples#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="11d57-107">Exemples</span><span class="sxs-lookup"><span data-stu-id="11d57-107">Example</span></span>  
 <span data-ttu-id="11d57-108">L'exemple suivant recherche le montant de fret le plus bas parmi les commandes.</span><span class="sxs-lookup"><span data-stu-id="11d57-108">The following example finds the lowest freight amount for any order.</span></span>  
  
 <span data-ttu-id="11d57-109">Si vous exécutez cette requête sur l'exemple de base de données Northwind, vous obtenez le résultat suivant : `0.0200`.</span><span class="sxs-lookup"><span data-stu-id="11d57-109">If you run this query against the Northwind sample database, the output is: `0.0200`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#10)]
 [!code-vb[DLinqQueryExamples#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="11d57-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="11d57-110">Example</span></span>  
 <span data-ttu-id="11d57-111">L'exemple suivant utilise Min pour trouver les `Products` qui ont le prix unitaire le plus bas dans chaque catégorie.</span><span class="sxs-lookup"><span data-stu-id="11d57-111">The following example uses Min to find the `Products` that have the lowest unit price in each category.</span></span> <span data-ttu-id="11d57-112">La sortie est classée par catégorie.</span><span class="sxs-lookup"><span data-stu-id="11d57-112">The output is arranged by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#11](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#11)]
 [!code-vb[DLinqQueryExamples#11](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#11)]  
  
 <span data-ttu-id="11d57-113">Si vous exécutez la requête précédente sur l'exemple de base de données Northwind, les résultats se présenteront comme suit :</span><span class="sxs-lookup"><span data-stu-id="11d57-113">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
 `1`  
  
 `Guaraná Fantástica`  
  
 `2`  
  
 `Aniseed Syrup`  
  
 `3`  
  
 `Teatime Chocolate Biscuits`  
  
 `4`  
  
 `Geitost`  
  
 `5`  
  
 `Filo Mix`  
  
 `6`  
  
 `Tourtière`  
  
 `7`  
  
 `Longlife Tofu`  
  
 `8`  
  
 `Konbu`  
  
## <a name="see-also"></a><span data-ttu-id="11d57-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11d57-114">See also</span></span>

- [<span data-ttu-id="11d57-115">Requêtes d’agrégation</span><span class="sxs-lookup"><span data-stu-id="11d57-115">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="11d57-116">Téléchargement d’exemples de base de données</span><span class="sxs-lookup"><span data-stu-id="11d57-116">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
