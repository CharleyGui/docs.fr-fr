---
title: Requêtes LINQ to SQL
ms.date: 03/30/2017
ms.assetid: f4897aaa-7f44-4c20-a471-b948c2971aae
ms.openlocfilehash: 534da029664af0babc3dff6226ff095b7222c34d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915837"
---
# <a name="linq-to-sql-queries"></a>Requêtes LINQ to SQL
Vous définissez des requêtes [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] en utilisant la même syntaxe que dans [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]. La seule différence est que les objets référencés dans vos requêtes sont mappés aux éléments d'une base de données. Pour plus d’informations, consultez [Introduction aux requêtes LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduit les requêtes que vous écrivez en requêtes SQL équivalentes et les envoie au serveur pour traitement. Plus spécifiquement, votre application utilise l'API [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour demander l'exécution de la requête. Le fournisseur [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] transforme ensuite la requête en texte SQL et délègue l'exécution au fournisseur ADO. Le fournisseur ADO retourne des résultats de la requête en tant que `DataReader`. Le [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fournisseur traduit les résultats ADO en une <xref:System.Linq.IQueryable> collection d’objets utilisateur.  
  
> [!NOTE]
> La plupart des méthodes et opérateurs sur .NET Framework types intégrés ont des traductions directes vers SQL. Ceux que [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] ne peut pas traduire génèrent des exceptions runtime. Pour plus d’informations, consultez [mappage de type SQL-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
 Le tableau suivant affiche les ressemblances et différences entre les éléments de requête [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] et [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
|Item|Requête LINQ|Requête [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
|----------|----------------|----------------------------------------------------------------------|  
|Type de retour de la variable locale qui contient la requête (pour les requêtes qui retournent des séquences)|`IEnumerable` générique|`IQueryable` générique|  
|Spécification de la source de données|Utilise la `From` clause (Visual Basic) `from` ouC#()|Identique|  
|Filtrage|Utilise la `Where`clause / `where`|Identique|  
|Regroupement|Utilise la `Group…By`clause / `groupby`|Identique|  
|Sélection (projection)|Utilise la `Select`clause / `select`|Identique|  
|Exécution différée / exécution immédiate|Consultez [Introduction aux requêtes LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)|Identique|  
|Implémentation de jointures|Utilise la `Join`clause / `join`|Peut utiliser la `Join` / <xref:System.Data.Linq.Mapping.AssociationAttribute> clause, mais utilise plus efficacement l’attribut. `join` Pour plus d’informations, consultez interrogation des [relations](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).|  
|Exécution distante / exécution locale||Pour plus d’informations, [consultez Remote vs. Exécution](../../../../../../docs/framework/data/adonet/sql/linq/remote-vs-local-execution.md)locale.|  
|Transmission en continu / interrogation mise en cache|Non applicable dans un scénario de mémoire locale||  
  
## <a name="see-also"></a>Voir aussi

- [Introduction aux requêtes LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
- [Opérations de requête LINQ de base](../../../../../csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)
- [Relations des types dans des opérations de requête LINQ](../../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)
- [Concepts relatifs aux requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
