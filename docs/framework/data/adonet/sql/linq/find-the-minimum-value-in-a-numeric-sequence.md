---
title: 'Comment : rechercher la valeur minimale dans une séquence numérique'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 78203093-f242-4572-9b31-9495b10926aa
ms.openlocfilehash: 2ffff8b69839d5c1e70e81f9fc6f3a97f57ac6c6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155976"
---
# <a name="find-the-minimum-value-in-a-numeric-sequence"></a>Comment : rechercher la valeur minimale dans une séquence numérique

Utilisez l'opérateur <xref:System.Linq.Enumerable.Min%2A> pour retourner la valeur minimale d'une séquence de valeurs numériques.  
  
## <a name="example"></a>Exemple  

 L'exemple suivant recherche le prix unitaire le plus bas parmi les produits.  
  
 Si vous exécutez cette requête sur l'exemple de base de données Northwind, vous obtenez le résultat suivant : `2.5000`.  
  
 [!code-csharp[DLinqQueryExamples#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#9)]
 [!code-vb[DLinqQueryExamples#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#9)]  
  
## <a name="example"></a>Exemple  

 L'exemple suivant recherche le montant de fret le plus bas parmi les commandes.  
  
 Si vous exécutez cette requête sur l'exemple de base de données Northwind, vous obtenez le résultat suivant : `0.0200`.  
  
 [!code-csharp[DLinqQueryExamples#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#10)]
 [!code-vb[DLinqQueryExamples#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#10)]  
  
## <a name="example"></a>Exemple  

 L'exemple suivant utilise Min pour trouver les `Products` qui ont le prix unitaire le plus bas dans chaque catégorie. La sortie est classée par catégorie.  
  
 [!code-csharp[DLinqQueryExamples#11](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#11)]
 [!code-vb[DLinqQueryExamples#11](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#11)]  
  
 Si vous exécutez la requête précédente sur l'exemple de base de données Northwind, les résultats se présenteront comme suit :  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Requêtes d'agrégation](aggregate-queries.md)
- [Téléchargement d’exemples de base de données](downloading-sample-databases.md)
