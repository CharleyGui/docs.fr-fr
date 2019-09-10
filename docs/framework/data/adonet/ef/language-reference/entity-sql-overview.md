---
title: Vue d'ensemble d'Entity SQL
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: 8f40a34f361669d2b8d89b63b3187cae6bf705d2
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854485"
---
# <a name="entity-sql-overview"></a>Vue d'ensemble d'Entity SQL
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]est un langage de type SQL qui vous permet d’interroger des modèles conceptuels dans le Entity Framework. Les modèles conceptuels représentent des données sous forme d' [!INCLUDE[esql](../../../../../../includes/esql-md.md)] entités et de relations, et vous permettent d’interroger ces entités et relations dans un format familier à ceux qui ont utilisé SQL.  
      
 Le Entity Framework fonctionne avec les fournisseurs de données spécifiques au stockage pour [!INCLUDE[esql](../../../../../../includes/esql-md.md)] traduire le générique en requêtes spécifiques au stockage. Le fournisseur EntityClient fournit une méthode pour exécuter une commande [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sur un modèle d'entité et retourner des types de données enrichis, y compris des résultats scalaires, des jeux de résultats et des graphiques d'objets. Lorsque vous construisez des objets <xref:System.Data.EntityClient.EntityCommand>, vous pouvez spécifier un nom de procédure stockée ou le texte d'une requête en assignant une chaîne de requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] à sa propriété <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType>. <xref:System.Data.EntityClient.EntityDataReader> expose les résultats de l'exécution d'un <xref:System.Data.EntityClient.EntityCommand> sur un modèle EDM. Pour exécuter la commande qui retourne l'objet <xref:System.Data.EntityClient.EntityDataReader>, appelez la méthode <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.  
  
 Outre le fournisseur EntityClient, le Entity Framework vous permet d’utiliser [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pour exécuter des requêtes sur un modèle conceptuel et retourner des données sous forme d’objets CLR fortement typés qui sont des instances de types d’entité. Pour plus d’informations, consultez [utilisation des objets](../working-with-objects.md).  
  
 Cette section fournit des informations conceptuelles sur [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 [Différences entre Entity SQL et Transact-SQL](how-entity-sql-differs-from-transact-sql.md)  
  
 [Aide-mémoire Entity SQL](entity-sql-quick-reference.md)  
  
 [Système de type](type-system-entity-sql.md)  
  
 [Définitions de type](type-definitions-entity-sql.md)  
  
 [Construction de types](constructing-types-entity-sql.md)  
  
 [Mise en cache d’un plan de requête](query-plan-caching-entity-sql.md)  
  
 [Espaces de noms](namespaces-entity-sql.md)  
  
 [Identificateurs](identifiers-entity-sql.md)  
  
 [Paramètres](parameters-entity-sql.md)  
  
 [Variables](variables-entity-sql.md)  
  
 [Expressions non prises en charge](unsupported-expressions-entity-sql.md)  
  
 [Littéraux](literals-entity-sql.md)  
  
 [Littéraux null et inférence de type](null-literals-and-type-inference-entity-sql.md)  
  
 [Jeu de caractères en entrée](input-character-set-entity-sql.md)  
  
 [Expressions de requête](query-expressions-entity-sql.md)  
  
 [Fonctions](functions-entity-sql.md)  
  
 [Priorité des opérateurs](operator-precedence-entity-sql.md)  
  
 [Pagination](paging-entity-sql.md)  
  
 [Sémantique de comparaison](comparison-semantics-entity-sql.md)  
  
 [Composition de requêtes Entity SQL imbriquées](composing-nested-entity-sql-queries.md)  
  
 [Types structurés autorisant la valeur null](nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
- [Langage Entity SQL](entity-sql-language.md)
- [Spécifications CSDL, SSDL et MSL](csdl-ssdl-and-msl-specifications.md)
