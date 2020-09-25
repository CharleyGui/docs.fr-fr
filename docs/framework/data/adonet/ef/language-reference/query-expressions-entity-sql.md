---
title: Expressions de requête (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: ca6b79b4b3d3326a74780345decf58367596adb0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175601"
---
# <a name="query-expressions-entity-sql"></a>Expressions de requête (Entity SQL)

Une expression de requête combine un grand nombre d'opérateurs de requête différents dans une syntaxe unique. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fournit différents genres d’expressions, notamment les [littéraux](literals-entity-sql.md), les [paramètres](parameters-entity-sql.md), les [variables](variables-entity-sql.md), les opérateurs, les [fonctions](functions-entity-sql.md), les opérateurs de jeu, etc. Pour plus d’informations, consultez [Entity SQL référence](entity-sql-reference.md).  
  
## <a name="clauses"></a>Clauses  

 Une expression de requête est constituée d’une série de clauses qui appliquent des opérations successives à une collection d’objets. Elles sont basées sur les mêmes clauses dans une instruction SQL SELECT standard : [Select](select-entity-sql.md), [from](from-entity-sql.md), [Where](where-entity-sql.md), [Group by](group-by-entity-sql.md), [having](having-entity-sql.md)et [order by](order-by-entity-sql.md).  
  
## <a name="scope"></a>Étendue  

 Les noms définis dans la clause FROM sont introduits dans l'étendue FROM dans l'ordre de leur apparition, de gauche à droite. Dans la liste JOIN, les expressions peuvent faire référence aux noms définis précédemment dans la liste. Les propriétés publiques des éléments identifiés dans la clause FROM ne sont pas ajoutées à l'étendue FROM : elles doivent toujours être référencées par le biais du nom qualifié par un alias. Normalement, toutes les parties de l'expression select sont considérées comme faisant partie de l'étendue FROM.  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
