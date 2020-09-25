---
title: Requêtes LINQ to SQL
ms.date: 03/30/2017
ms.assetid: f4897aaa-7f44-4c20-a471-b948c2971aae
ms.openlocfilehash: c49644a866a6e245c6be1f9a8e8f95d003fd0191
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175224"
---
# <a name="linq-to-sql-queries"></a>Requêtes LINQ to SQL

Vous définissez des requêtes à l' [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aide de la même syntaxe que dans LINQ. La seule différence est que les objets référencés dans vos requêtes sont mappés aux éléments d'une base de données. Pour plus d’informations, consultez [Introduction aux requêtes LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduit les requêtes que vous écrivez en requêtes SQL équivalentes et les envoie au serveur pour traitement. Plus spécifiquement, votre application utilise l'API [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour demander l'exécution de la requête. Le fournisseur [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] transforme ensuite la requête en texte SQL et délègue l'exécution au fournisseur ADO. Le fournisseur ADO retourne des résultats de la requête en tant que `DataReader`. Le [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fournisseur traduit les résultats ADO en une <xref:System.Linq.IQueryable> collection d’objets utilisateur.  
  
> [!NOTE]
> La plupart des méthodes et opérateurs sur .NET Framework types intégrés ont des traductions directes vers SQL. Ceux que LINQ ne peut pas traduire génèrent des exceptions au moment de l’exécution. Pour plus d’informations, consultez [mappage de type SQL-CLR](sql-clr-type-mapping.md).  
  
 Le tableau suivant présente les similitudes et les différences entre LINQ et les [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] éléments de requête.  
  
|Élément|Requête LINQ|[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Requête|  
|----------|----------------|----------------------------------------------------------------------|  
|Type de retour de la variable locale qui contient la requête (pour les requêtes qui retournent des séquences)|Generic <ph id="ph1">`IEnumerable`</ph>|Generic <ph id="ph1">`IQueryable`</ph>|  
|Spécification de la source de données|Utilise la `From` clause (Visual Basic) ou `from` (C#)|Identique|  
|Filtrage|Utilise la `Where` / `where` clause|Identique|  
|Regroupement|Utilise la `Group…By` / `groupby` clause|Identique|  
|Sélection (projection)|Utilise la `Select` / `select` clause|Identique|  
|Exécution différée / exécution immédiate|Consultez [Introduction aux requêtes LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)|Identique|  
|Implémentation de jointures|Utilise la `Join` / `join` clause|Peut utiliser la `Join` / `join` clause, mais utilise plus efficacement l' <xref:System.Data.Linq.Mapping.AssociationAttribute> attribut. Pour plus d’informations, consultez [interrogation des relations](querying-across-relationships.md).|  
|Exécution distante / exécution locale||Pour plus d’informations, consultez [exécution distante ou locale](remote-vs-local-execution.md).|  
|Transmission en continu / interrogation mise en cache|Non applicable dans un scénario de mémoire locale||  
  
## <a name="see-also"></a>Voir aussi

- [Introduction aux requêtes LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
- [Opérations de requête LINQ de base](../../../../../csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)
- [Relations des types dans des opérations de requête LINQ](../../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)
- [Concepts relatifs aux requêtes](query-concepts.md)
