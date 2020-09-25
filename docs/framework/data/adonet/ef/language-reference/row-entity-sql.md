---
title: ROW (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: 2ab91d0c6d3c3ed3f88a7f0ddbf3a6c2f36d8b04
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202251"
---
# <a name="row-entity-sql"></a>ROW (Entity SQL)

Construit des enregistrements anonymes structurellement typés à partir d'une ou plusieurs valeurs.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a>Arguments  

 `expression`  
 Toute expression de requête valide qui retourne une valeur à construire dans un type de ligne.  
  
 `alias`  
 Spécifie un alias pour la valeur spécifiée dans un type de ligne. Si aucun alias n'est fourni, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] essaie de générer un alias en fonction des règles de génération d'alias [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .  
  
## <a name="return-value"></a>Valeur renvoyée  

 Type de ligne.  
  
## <a name="remarks"></a>Notes  

 Les constructeurs de ligne s'avèrent utiles dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pour construire des enregistrements anonymes structurellement types à partir d'une ou plusieurs valeurs. Le type de résultat d'un constructeur de ligne est un type de ligne dont les types de champ correspondent aux types des valeurs qui ont servi à construire la ligne. Par exemple, l'expression suivante construit une valeur de type `Record(a int, b string, c int)`.  
  
```sql  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 Si vous ne fournissez pas d'alias pour une expression contenue dans un constructeur de ligne, Entity Framework essaie d'en générer un. Pour plus d'informations, voir la section « Règles d'alias » de la rubrique [Identificateurs](identifiers-entity-sql.md) .  
  
 Les règles suivantes s'appliquent à l'utilisation d'alias dans les expressions d'un constructeur de ligne :  
  
- les expressions contenues dans un constructeur de ligne ne peuvent pas faire référence aux autres alias du même constructeur ;  
  
- deux expressions contenues dans un même constructeur de ligne ne peuvent pas avoir le même alias.  
  
 Pour plus d’informations sur les constructeurs de requête, consultez [construction de types](constructing-types-entity-sql.md).  
  
## <a name="example"></a>Exemple  

 La requête Entity SQL ci-dessous utilise l'opérateur ROW pour construire des enregistrements anonymes structurellement typés. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-sql[DP EntityServices Concepts#ROW](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#row)]  
  
## <a name="see-also"></a>Voir aussi

- [Construction de types](constructing-types-entity-sql.md)
- [Référence Entity SQL](entity-sql-reference.md)
- [Définitions de types](type-definitions-entity-sql.md)
