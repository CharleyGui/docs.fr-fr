---
title: Vue d'ensemble d'Entity SQL
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: 880b81f2b6d4c4b893d28c919490f88dfb2a42e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150374"
---
# <a name="entity-sql-overview"></a>Vue d'ensemble d'Entity SQL
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]est un langage de la SQL qui vous permet d’interroger des modèles conceptuels dans le Cadre d’entité. Les modèles conceptuels représentent les [!INCLUDE[esql](../../../../../../includes/esql-md.md)] données en tant qu’entités et relations, et vous permettent d’interroger ces entités et les relations dans un format qui est familier à ceux qui ont utilisé SQL.  

 Le Cadre d’entité travaille avec des [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fournisseurs de données spécifiques au stockage pour traduire les génériques en requêtes spécifiques au stockage. Le fournisseur EntityClient fournit une méthode pour exécuter une commande [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sur un modèle d'entité et retourner des types de données enrichis, y compris des résultats scalaires, des jeux de résultats et des graphiques d'objets. Lorsque vous construisez des objets <xref:System.Data.EntityClient.EntityCommand>, vous pouvez spécifier un nom de procédure stockée ou le texte d'une requête en assignant une chaîne de requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] à sa propriété <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType>. <xref:System.Data.EntityClient.EntityDataReader> expose les résultats de l'exécution d'un <xref:System.Data.EntityClient.EntityCommand> sur un modèle EDM. Pour exécuter la commande qui retourne l'objet <xref:System.Data.EntityClient.EntityDataReader>, appelez la méthode <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.  
  
 En plus du fournisseur EntityClient, le cadre [!INCLUDE[esql](../../../../../../includes/esql-md.md)] d’entité vous permet d’utiliser pour exécuter des requêtes contre un modèle conceptuel et retourner les données comme des objets CLR fortement typés qui sont des cas de types d’entités. Pour plus d’informations, voir [Travailler avec des objets](../working-with-objects.md).  
  
 Cette section fournit des informations conceptuelles sur [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 [Différences entre Entity SQL et Transact-SQL](how-entity-sql-differs-from-transact-sql.md)  
  
 [Aide-mémoire Entity SQL](entity-sql-quick-reference.md)  
  
 [Système de types](type-system-entity-sql.md)  
  
 [Définitions de types](type-definitions-entity-sql.md)  
  
 [Construction de types](constructing-types-entity-sql.md)  
  
 [Mise en cache d’un plan de requête](query-plan-caching-entity-sql.md)  
  
 [Espaces de noms](namespaces-entity-sql.md)  
  
 [Identificateurs](identifiers-entity-sql.md)  
  
 [Paramètres](parameters-entity-sql.md)  
  
 [Variables](variables-entity-sql.md)  
  
 [Expressions non prises en charge](unsupported-expressions-entity-sql.md)  
  
 [Littéraux](literals-entity-sql.md)  
  
 [Littéraux null et inférence de type](null-literals-and-type-inference-entity-sql.md)  
  
 [Jeu de caractères d’entrée](input-character-set-entity-sql.md)  
  
 [Expressions de requête](query-expressions-entity-sql.md)  
  
 [Fonctions](functions-entity-sql.md)  
  
 [Priorité des opérateurs](operator-precedence-entity-sql.md)  
  
 [Pagination](paging-entity-sql.md)  
  
 [Sémantique de comparaison](comparison-semantics-entity-sql.md)  
  
 [Composition de requêtes Entity SQL imbriquées](composing-nested-entity-sql-queries.md)  
  
 [Types structurés Nullable](nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
- [Langage d'Entity SQL](entity-sql-language.md)
- [Spécifications CSDL, SSDL et MSL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
