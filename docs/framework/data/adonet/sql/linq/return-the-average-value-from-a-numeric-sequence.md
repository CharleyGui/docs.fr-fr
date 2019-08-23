---
title: Retourner la valeur moyenne d'une séquence numérique
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee3b8673-a2e7-4b2d-9b5c-4972ff9e665d
ms.openlocfilehash: 56fe777a3bca1e2b54b61d1586f78a2df4fb475f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963824"
---
# <a name="return-the-average-value-from-a-numeric-sequence"></a>Retourner la valeur moyenne d'une séquence numérique
L'opérateur <xref:System.Linq.Enumerable.Average%2A> calcule la moyenne d'une séquence de valeurs numériques.  
  
> [!NOTE]
> La traduction [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] de la `Average` de valeurs entières est calculée comme un entier, non comme un double.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant retourne la moyenne de valeurs `Freight` dans la table `Orders`.  
  
 Les résultats de l'exemple de base de données Northwind seraient `78.2442`.  
  
 [!code-csharp[DLinqQueryExamples#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#1)]
 [!code-vb[DLinqQueryExamples#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#1)]  
  
## <a name="example"></a>Exemples  
 L'exemple suivant retourne le prix unitaire moyen de tous les produits (`Products`) dans la table `Products`.  
  
 Les résultats de l'exemple de base de données Northwind seraient `28.8663`.  
  
 [!code-csharp[DLinqQueryExamples#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#2)]
 [!code-vb[DLinqQueryExamples#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#2)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise l'opérateur `Average` pour rechercher ces `Products` dont le prix unitaire est plus élevé que le prix unitaire moyen de la catégorie à laquelle il appartient. L'exemple affiche ensuite les résultats par groupes.  
  
 Notez que cet exemple requiert l’utilisation du mot clé `var` en C#, car le type de retour est anonyme.  
  
 [!code-csharp[DLinqQueryExamples#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#3)]
 [!code-vb[DLinqQueryExamples#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#3)]  
  
 Si vous exécutez cette requête sur l'exemple de base de données Northwind, les résultats doivent se présenter comme suit :  
  
 `1`  
  
 `Côte de Blaye`  
  
 `Ipoh Coffee`  
  
 `2`  
  
 `Grandma's Boysenberry Spread`  
  
 `Northwoods Cranberry Sauce`  
  
 `Sirop d'érable`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `Gumbär Gummibärchen`  
  
 `Schoggi Schokolade`  
  
 `Tarte au sucre`  
  
 `4`  
  
 `Queso Manchego La Pastora`  
  
 `Mascarpone Fabioli`  
  
 `Raclette Courdavault`  
  
 `Camembert Pierrot`  
  
 `Gudbrandsdalsost`  
  
 `Mozzarella di Giovanni`  
  
 `5`  
  
 `Gustaf's Knäckebröd`  
  
 `Gnocchi di nonna Alice`  
  
 `Wimmers gute Semmelknödel`  
  
 `6`  
  
 `Mishi Kobe Niku`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Rössle Sauerkraut`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Ikura`  
  
 `Carnarvon Tigers`  
  
 `Nord-Ost Matjeshering`  
  
 `Gravad lax`  
  
## <a name="see-also"></a>Voir aussi

- [Requêtes d’agrégation](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
