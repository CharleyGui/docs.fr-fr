---
title: Requêtes LINQ to SQL
ms.date: 03/30/2017
ms.assetid: f4897aaa-7f44-4c20-a471-b948c2971aae
ms.openlocfilehash: 478138d26d6cdf656b2487c637a5eb13784126e9
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634378"
---
# <a name="linq-to-sql-queries"></a>Requêtes LINQ to SQL
Vous définissez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] requêtes à l’aide de la même syntaxe que dans LINQ. La seule différence est que les objets référencés dans vos requêtes sont mappés aux éléments d'une base de données. Pour plus d’informations, consultez [Introduction aux requêtes LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduit les requêtes que vous écrivez en requêtes SQL équivalentes et les envoie au serveur pour traitement. Plus spécifiquement, votre application utilise l'API [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour demander l'exécution de la requête. Le fournisseur [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] transforme ensuite la requête en texte SQL et délègue l'exécution au fournisseur ADO. Le fournisseur ADO retourne des résultats de la requête en tant que `DataReader`. Le fournisseur [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduit les résultats ADO en une collection <xref:System.Linq.IQueryable> d’objets utilisateur.  
  
> [!NOTE]
> La plupart des méthodes et opérateurs sur .NET Framework types intégrés ont des traductions directes vers SQL. Ceux que LINQ ne peut pas traduire génèrent des exceptions au moment de l’exécution. Pour plus d’informations, consultez [mappage de type SQL-CLR](sql-clr-type-mapping.md).  
  
 Le tableau suivant présente les similitudes et les différences entre les éléments de requête LINQ et [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
|Élément|Requête LINQ|Requête [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
|----------|----------------|----------------------------------------------------------------------|  
|Type de retour de la variable locale qui contient la requête (pour les requêtes qui retournent des séquences)|`IEnumerable` générique|`IQueryable` générique|  
|Spécification de la source de données|Utilise la clause `From` (Visual Basic) ou `from`C#()|Identique|  
|Filtrage|Utilise la clause `Where`/`where`|Identique|  
|Regroupement|Utilise la clause `Group…By`/`groupby`|Identique|  
|Sélection (projection)|Utilise la clause `Select`/`select`|Identique|  
|Exécution différée / exécution immédiate|Consultez [Introduction aux requêtes LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)|Identique|  
|Implémentation de jointures|Utilise la clause `Join`/`join`|Peut utiliser la clause `Join`/`join`, mais utilise l’attribut <xref:System.Data.Linq.Mapping.AssociationAttribute> de manière plus efficace. Pour plus d’informations, consultez [interrogation des relations](querying-across-relationships.md).|  
|Exécution distante / exécution locale||Pour plus d’informations, consultez [Remote vs. ](remote-vs-local-execution.md)d’exécution locale.|  
|Transmission en continu / interrogation mise en cache|Non applicable dans un scénario de mémoire locale||  
  
## <a name="see-also"></a>Voir aussi

- [Introduction aux requêtes LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
- [Opérations de requête LINQ de base](../../../../../csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)
- [Relations des types dans des opérations de requête LINQ](../../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)
- [Concepts relatifs aux requêtes](query-concepts.md)
