---
title: Requêtes d'analyse croisée (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
ms.openlocfilehash: 4ab8eb9988995b4a142b1c02e82476f45285c3b8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785618"
---
# <a name="cross-table-queries-linq-to-dataset"></a>Requêtes d'analyse croisée (LINQ to DataSet)
Outre l’interrogation d’une table unique, vous pouvez également effectuer des requêtes entre tables dans LINQ to DataSet. Pour ce faire, vous utilisez une *jointure*. Une jointure est l'association d'objets d'une source de données avec des objets qui partagent un attribut commun dans une autre source de données, comme un produit ou un ID de contact. Dans la programmation orientée objets, les relations entre les objets sont relativement faciles à explorer car chaque objet possède un membre faisant référence à un autre objet. Dans les tables de base de données externe, toutefois, l'exploration des relations n'est pas aussi simple. Les tables de base de données ne contiennent pas de relations intégrées. Dans ces cas particuliers, l'opération de jointure peut servir à faire correspondre des éléments de chaque source. Par exemple, avec deux tables qui contiennent des informations sur les produits et des informations sur les ventes, vous pourriez utiliser une opération de jointure pour faire correspondre les informations sur les ventes et les produits pour la même commande.  
  
 L'infrastructure [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] fournit deux opérateurs de jointure, <xref:System.Linq.Enumerable.Join%2A> et <xref:System.Linq.Enumerable.GroupJoin%2A>. Ces opérateurs effectuent *des jointures*d’opérateur : c’est-à-dire des jointures qui correspondent à deux sources de données uniquement lorsque leurs clés sont égales. (En revanche, Transact-SQL prend en charge les opérateurs `equals`de jointure autres que `less than` , tels que l’opérateur.)  
  
 En termes de base de données relationnelle, <xref:System.Linq.Enumerable.Join%2A> implémente une jointure interne. Une jointure interne est un type de jointure dans lequel seuls les objets qui ont une correspondance dans le data set opposé sont retournés.  
  
 Les <xref:System.Linq.Enumerable.GroupJoin%2A> opérateurs n’ont pas d’équivalent direct dans les termes de base de données relationnelle ; ils implémentent un sur-ensemble de jointures internes et de jointures externes gauches. Une jointure externe gauche est une jointure qui retourne chaque élément de la première collection (gauche), même si elle n'a pas d'éléments corrélés dans la seconde collection.  
  
 Pour plus d’informations sur les jointures, consultez [opérations de jointure](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120)).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant effectue une jointure traditionnelle des tables `SalesOrderHeader` et `SalesOrderDetail` de l'exemple de base de données AdventureWorks pour obtenir les commandes en ligne du mois d'août.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a>Voir aussi

- [Interrogation de DataSets](querying-datasets-linq-to-dataset.md)
- [Requêtes de table unique](single-table-queries-linq-to-dataset.md)
- [Interrogation de DataSets typés](querying-typed-datasets.md)
- [Opérations de jointure](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120))
- [Exemples LINQ to DataSet](linq-to-dataset-examples.md)
