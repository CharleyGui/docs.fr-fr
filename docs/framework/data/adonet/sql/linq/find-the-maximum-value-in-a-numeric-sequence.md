---
title: 'Comment : rechercher la valeur maximale dans une séquence numérique'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70d7c058-0280-4815-a008-6f290093591a
ms.openlocfilehash: b70b94338ca7bdbb600bac697d3a36ff117d757e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156002"
---
# <a name="find-the-maximum-value-in-a-numeric-sequence"></a>Comment : rechercher la valeur maximale dans une séquence numérique

Utilisez l'opérateur <xref:System.Linq.Enumerable.Max%2A> pour rechercher la valeur la plus élevée dans une séquence de valeurs numériques.  
  
## <a name="example"></a>Exemple  

 L'exemple suivant recherche la date la plus récente d'embauche parmi tous les employés.  
  
 Si vous exécutez cette requête sur l'exemple de base de données Northwind, vous obtenez le résultat suivant : `11/15/1994 12:00:00 AM`.  
  
 [!code-csharp[DLinqQueryExamples#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#6)]
 [!code-vb[DLinqQueryExamples#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#6)]  
  
## <a name="example"></a>Exemple  

 L'exemple suivant recherche les unités dont le stock est le plus élevé parmi tous les produits.  
  
 Si vous exécutez cette requête sur l'exemple de base de données Northwind, vous obtenez le résultat suivant : `125`.  
  
 [!code-csharp[DLinqQueryExamples#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#7)]
 [!code-vb[DLinqQueryExamples#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#7)]  
  
## <a name="example"></a>Exemple  

 L'exemple suivant utilise Max pour rechercher les `Products` dont le prix unitaire est le plus élevé dans chaque catégorie. Les résultats sont ensuite répertoriés par catégorie.  
  
 [!code-csharp[DLinqQueryExamples#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#8)]
 [!code-vb[DLinqQueryExamples#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#8)]  
  
 Si vous exécutez la requête précédente sur l'exemple de base de données Northwind, les résultats se présenteront comme suit :  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Requêtes d'agrégation](aggregate-queries.md)
- [Téléchargement d’exemples de base de données](downloading-sample-databases.md)
