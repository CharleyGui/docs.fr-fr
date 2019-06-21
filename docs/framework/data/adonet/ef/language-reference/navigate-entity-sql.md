---
title: NAVIGATE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 6ce88cecf210d8b3cf541fe7e870e19a59e344ec
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307332"
---
# <a name="navigate-entity-sql"></a>NAVIGATE (Entity SQL)

Parcourt la relation établie entre des entités.

## <a name="syntax"></a>Syntaxe

```
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a>Arguments

`instance-expression` Une instance d’une entité.

`relationship-type` Le nom de type de la relation, à partir du fichier conceptual schema definition language (CSDL). Le `relationship-type` est qualifié en tant que \<espace de noms >.\< nom de type de relation >.

`to` La fin de la relation.

`from` Début de la relation.

## <a name="return-value"></a>Valeur de retour

Si la cardinalité de la terminaison To est 1, la valeur retournée est `Ref<T>`. Si la cardinalité de la terminaison To est n, la valeur retournée est `Collection<Ref<T>>`.

## <a name="remarks"></a>Notes

Les relations sont des constructions de première classe dans le modèle EDM (Entity Data Model). Elles peuvent être établies entre plusieurs types d'entités et les utilisateurs peuvent les parcourir d'une terminaison (entité) à l'autre. `from` et `to` sont facultatifs à la condition qu'il n'existe aucune ambiguïté au niveau de la résolution des noms dans la relation.

NAVIGATE est valide dans l'espace O et C.

Une construction de navigation se présente généralement sous la forme suivante :

navigate(`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ] ] )

Exemple :

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

Où OrderCustomer est le `relationship`, et Client et Order sont les terminaisons `to-end` (customer) et `from-end` (order) de la relation. Si OrderCustomer était une relation de type n : 1, le type de résultat de l’expression de navigation est Ref\<client >.

Voici la même expression sous une forme plus simple :

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

De même, dans une requête sous la forme suivante, l’expression de navigation produirait le résultat Collection < Ref\<ordre >>.

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

L'expression d'instance doit être un type entity/ref.

## <a name="example"></a>Exemple

La requête Entity SQL suivante utilise l'opérateur NAVIGATE pour parcourir la relation établie entre les types d'entités Address et SalesOrderHeader. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :

1. Suivez la procédure décrite dans [Comment : Exécuter une requête qui retourne des résultats StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).

2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :

 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]

## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Guide pratique pour Parcourir les relations avec l’opérateur Navigate](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)
