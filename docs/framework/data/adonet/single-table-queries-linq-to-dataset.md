---
title: Requêtes d'analyse unique (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b74bcf8-3f87-449f-bff7-6bcb0d69d212
ms.openlocfilehash: 87a2f6853136b4b3e622968327bde01c9862bfdf
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504632"
---
# <a name="single-table-queries-linq-to-dataset"></a>Requêtes d'analyse unique (LINQ to DataSet)
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] les requêtes fonctionnent sur des sources de données qui implémentent le <xref:System.Collections.Generic.IEnumerable%601> interface ou le <xref:System.Linq.IQueryable%601> interface. Le <xref:System.Data.DataTable> classe n’implémente pas ces deux interfaces, vous devez appeler la <xref:System.Data.DataTableExtensions.AsEnumerable%2A> méthode si vous souhaitez utiliser le <xref:System.Data.DataTable> en tant que source dans le `From` clause d’une [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] requête.  
  
 L'exemple ci-dessous obtient toutes les commandes en ligne de la table SalesOrderHeader et affiche l'ID de commande, la date de commande et le numéro de commande sur la console.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)] 
  
 La requête de variable locale est initialisée avec une expression de requête qui opère sur une ou plusieurs sources d’informations en appliquant un ou plusieurs opérateurs de requête parmi les opérateurs de requête standard ou, dans le cas de LINQ to DataSet, d’opérateurs spécifiques à la <xref:System.Data.DataSet>classe. L'expression de requête de l'exemple précédent utilise deux des opérateurs de requête standard : `Where` et `Select`.  
  
 La clause `Where` filtre la séquence en fonction d'une condition : dans ce cas, que l'indicateur `OnlineOrderFlag` soit défini sur `true`. L'opérateur `Select` alloue et retourne un objet énumérable qui capture les arguments transmis à l'opérateur. Dans l'exemple ci-dessus, un type anonyme est créé avec trois propriétés : `SalesOrderID`, `OrderDate` et `SalesOrderNumber`. Les valeurs de ces trois propriétés sont définies selon les valeurs des colonnes `SalesOrderID`, `OrderDate` et `SalesOrderNumber` de la table `SalesOrderHeader`.  
  
 La boucle `foreach` énumère ensuite l'objet énumérable retourné par `Select` puis génère les résultats de la requête. Parce que la requête est du type <xref:System.Linq.Enumerable>, qui implémente <xref:System.Collections.Generic.IEnumerable%601>, l'évaluation de la requête est différée jusqu'à ce que la variable de requête soit itérée au sein de la boucle `foreach`. L'évaluation de requête différée permet de conserver les requêtes en tant que valeurs qui peuvent être évaluées plusieurs fois, produisant chaque fois des résultats potentiellement différents.  
  
 La méthode <xref:System.Data.DataRowExtensions.Field%2A> fournit l'accès aux valeurs de colonne d'un <xref:System.Data.DataRow> et le <xref:System.Data.DataRowExtensions.SetField%2A> (non illustré dans l'exemple précédent) définit les valeurs de colonne dans un <xref:System.Data.DataRow>. Les deux méthodes <xref:System.Data.DataRowExtensions.Field%2A> et <xref:System.Data.DataRowExtensions.SetField%2A> gèrent des types Nullable, ce qui fait que vous n'avez pas à vérifier explicitement les valeurs Null. Les deux méthodes sont également des méthodes génériques, ce qui veut dire que vous n’avez pas à effectuer un cast du type de retour. Vous pourriez utiliser l’accesseur de colonne existant dans <xref:System.Data.DataRow> (par exemple, `o["OrderDate"]`), mais il vous faudrait alors effectuer un cast de l’objet de retour vers le type approprié.  Si la colonne est Nullable, vous devez vérifier si la valeur est Null à l'aide de la méthode <xref:System.Data.DataRow.IsNull%2A>. Pour plus d’informations, consultez [méthodes génériques Field et SetField](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md).  
  
 Notez que le type de données spécifié dans le paramètre générique `T` de la méthode <xref:System.Data.DataRowExtensions.Field%2A> et de la méthode <xref:System.Data.DataRowExtensions.SetField%2A> doit correspondre au type de la valeur sous-jacente, sinon une <xref:System.InvalidCastException> est levée. Le nom de la colonne spécifiée doit également correspondre à celui de la colonne dans le <xref:System.Data.DataSet>, sinon une <xref:System.ArgumentException> est levée. Dans les deux cas, l'exception est levée au moment de l'exécution de l'énumération des données lorsque la requête est exécutée.  
  
## <a name="see-also"></a>Voir aussi

- [Requêtes de table croisée](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)
- [Interrogation de DataSets typés](../../../../docs/framework/data/adonet/querying-typed-datasets.md)
- [Méthodes génériques Field et SetField](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)
