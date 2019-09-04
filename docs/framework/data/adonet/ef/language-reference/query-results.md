---
title: Résultats de requête
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bcd7b699-4e50-4523-8c33-2f54a103d94e
ms.openlocfilehash: d43ec0cdf5b5bb03854dffc7132dddb4c9ae76fd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249259"
---
# <a name="query-results"></a>Résultats de requête
Une fois qu’une requête de LINQ to Entities est convertie en arborescences de commandes et exécutée, les résultats de la requête sont généralement retournés comme suit :  
  
- une collection de zéro, un ou plusieurs objets entité typés ou une projection de types complexes dans le modèle conceptuel ;  
  
- des types CLR pris en charge par le modèle conceptuel ;  
  
- Collections inline.  
  
- Types anonymes.  
  
 Lorsque la requête a été exécutée sur la source de données, les résultats sont matérialisés en types CLR et retournés au client. La matérialisation d'objets est entièrement assurée par [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Les erreurs qui résultent d'une impossibilité d'effectuer un mappage entre [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] et le CLR provoquent la levée d'exceptions pendant la matérialisation d'objets.  
  
 Si l'exécution de la requête retourne des types de modèle conceptuel primitifs, les résultats se composent de types CLR autonomes et déconnectés d'[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Toutefois, si la requête retourne une collection d’objets entité typés, représentée par <xref:System.Data.Objects.ObjectQuery%601>, ces types sont suivis par le contexte d’objet. Tous les comportements d’objet (tels que les collections enfants/parents, le suivi des modifications, le polymorphisme, etc [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].) sont définis dans le. Ces fonctionnalités peuvent être utilisées en leur qualité, comme défini dans l'[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Pour plus d’informations, consultez [utilisation des objets](../working-with-objects.md).  
  
 Les types Struct retournés par les requêtes (tels que les types anonymes et les types complexes Nullable) peuvent être de valeur `null`. Une propriété <xref:System.Data.Objects.DataClasses.EntityCollection%601> d'une entité retournée peut également être de valeur `null`. Cela peut être le résultat de la projection de la propriété de collection d'une entité de valeur `null`, par exemple, en cas d'appel de <xref:System.Linq.Queryable.FirstOrDefault%2A> sur un objet <xref:System.Data.Objects.ObjectQuery%601> qui n'a pas d'éléments.  
  
 Dans certains cas, une requête peut sembler générer un résultat matérialisé pendant son exécution, mais il s'avère qu'elle est exécutée sur le serveur et que l'objet entité n'est jamais matérialisé dans le CLR. Cela peut être la cause de problèmes si vous êtes dépendant des effets secondaires de la matérialisation d'objets.  
  
 L'exemple suivant contient une classe personnalisée, `MyContact`, avec une propriété `LastName`. Lorsque la propriété `LastName` est définie, une variable `count` est incrémentée. Si vous exécutez les deux requêtes suivantes, la première incrémente `count` mais pas la deuxième. Cela est dû au fait que dans la deuxième requête, la propriété `LastName` est projetée à partir des résultats et que la classe `MyContact` n'est jamais créée, car elle n'est pas utile à l'exécution de la requête sur le magasin.  
  
 [!code-csharp[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#materializationsideeffects)]
 [!code-vb[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#materializationsideeffects)]  
  
 [!code-csharp[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#mycontactclass)]
 [!code-vb[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#mycontactclass)]
