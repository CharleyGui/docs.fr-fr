---
title: Requêtes d'analyse croisée (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
ms.openlocfilehash: ed860b60add288899ac6f97429b2f01577ee392a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504068"
---
# <a name="cross-table-queries-linq-to-dataset"></a>Requêtes d'analyse croisée (LINQ to DataSet)
Outre l’interrogation d’une table unique, vous pouvez également effectuer des requêtes à tables croisées dans LINQ to DataSet. Cela en utilisant un *jointure*. Une jointure est l'association d'objets d'une source de données avec des objets qui partagent un attribut commun dans une autre source de données, comme un produit ou un ID de contact. Dans la programmation orientée objets, les relations entre les objets sont relativement faciles à explorer car chaque objet possède un membre faisant référence à un autre objet. Dans les tables de base de données externe, toutefois, l'exploration des relations n'est pas aussi simple. Les tables de base de données ne contiennent pas de relations intégrées. Dans ces cas particuliers, l'opération de jointure peut servir à faire correspondre des éléments de chaque source. Par exemple, avec deux tables qui contiennent des informations sur les produits et des informations sur les ventes, vous pourriez utiliser une opération de jointure pour faire correspondre les informations sur les ventes et les produits pour la même commande.  
  
 L'infrastructure [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] fournit deux opérateurs de jointure, <xref:System.Linq.Enumerable.Join%2A> et <xref:System.Linq.Enumerable.GroupJoin%2A>. Ces opérateurs effectuent *équijointures*: autrement dit, des jointures qui correspondent aux données de deux sources uniquement lorsque leurs clés sont identiques. (En revanche, prend en charge de Transact-SQL opérateurs de jointure autres que `equals`, telles que le `less than` opérateur.)  
  
 En termes de base de données relationnelle, <xref:System.Linq.Enumerable.Join%2A> implémente une jointure interne. Une jointure interne est un type de jointure dans lequel seuls les objets qui ont une correspondance dans le data set opposé sont retournés.  
  
 Le <xref:System.Linq.Enumerable.GroupJoin%2A> opérateurs n’ont aucun équivalent direct en termes de base de données relationnelle ; ils implémentent un sur-ensemble de jointures internes et de jointures externes gauches. Une jointure externe gauche est une jointure qui retourne chaque élément de la première collection (gauche), même si elle n'a pas d'éléments corrélés dans la seconde collection.  
  
 Pour plus d’informations sur les jointures, consultez [opérations de jointure](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120)).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant effectue une jointure traditionnelle des tables `SalesOrderHeader` et `SalesOrderDetail` de l'exemple de base de données AdventureWorks pour obtenir les commandes en ligne du mois d'août.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a>Voir aussi

- [Interrogation de DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [Requêtes de table unique](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
- [Interrogation de DataSets typés](../../../../docs/framework/data/adonet/querying-typed-datasets.md)
- [Opérations de jointure](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120))
- [Exemples LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
