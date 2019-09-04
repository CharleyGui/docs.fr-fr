---
title: TOP (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: 8b55519b7f95deb6463af4c0a6a2a53975e5b5a2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248970"
---
# <a name="top-entity-sql"></a>TOP (Entity SQL)

La clause SELECT peut avoir une sous-clause TOP facultative après le modificateur ALL/DISTINCT facultatif. La sous-clause TOP spécifie que seul le premier ensemble de lignes sera retourné à partir du résultat de la requête.

## <a name="syntax"></a>Syntaxe

```
[ TOP (n) ]
```

## <a name="arguments"></a>Arguments

`n`Expression numérique qui spécifie le nombre de lignes à retourner. `n` peut être un littéral numérique unique ou un paramètre unique.

## <a name="remarks"></a>Notes

L'expression TOP doit être un littéral numérique unique ou un paramètre unique. Si un littéral constant est utilisé, le type de littéral doit implicitement pouvoir être promu en Edm.Int64 (octet, int16, int32 ou int64 ou tout type de fournisseur correspondant à un type qui peut être promu en Edm.Int64) et sa valeur doit être supérieure ou égale au zéro. Dans le cas contraire, une exception est levée. Si un paramètre est utilisé comme expression, le type du paramètre doit aussi pouvoir être implicitement promu en Edm.Int64, mais la valeur réelle du paramètre ne pourra pas être validée au moment de la compilation, car les valeurs de paramètres sont liées tardivement.

L'exemple suivant est une expression TOP constante :

```sql
select distinct top(10) c.a1, c.a2 from T as a
```

Voici un exemple d’expression TOP paramétrable :

```sql
select distinct top(@topParam) c.a1, c.a2 from T as a
```

TOP n'est pas déterministe, à moins que la requête soit triée. Si vous avez besoin d'un résultat déterministe, utilisez les sous-clauses [SKIP](skip-entity-sql.md) et [LIMIT](limit-entity-sql.md) dans la clause [ORDER BY](order-by-entity-sql.md) . TOP et SKIP/LIMIT s'excluent mutuellement.

## <a name="example"></a>Exemples

La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] suivante utilise TOP pour spécifier la ligne supérieure à retourner à partir du résultat de la requête. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :

1. Suivez la procédure décrite [dans la rubrique Procédure : Exécutez une requête qui retourne les résultats](../how-to-execute-a-query-that-returns-structuraltype-results.md)de StructuralType.

2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :

    [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]

## <a name="see-also"></a>Voir aussi

- [SELECT](select-entity-sql.md)
- [SKIP](skip-entity-sql.md)
- [LIMIT](limit-entity-sql.md)
- [ORDER BY](order-by-entity-sql.md)
- [Référence Entity SQL](entity-sql-reference.md)
