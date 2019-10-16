---
title: NAVIGATE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 09128a367a02e1f9b206a9cc068987166c76381b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319551"
---
# <a name="navigate-entity-sql"></a>NAVIGATE (Entity SQL)

Parcourt la relation établie entre des entités.

## <a name="syntax"></a>Syntaxe

```sql
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a>Arguments

`instance-expression` instance d’une entité.

`relationship-type` nom de type de la relation, à partir du fichier Conceptual Schema Definition Language (CSDL). La `relationship-type` est qualifiée de \<namespace >. \<relationship nom de type >.

`to` la fin de la relation.

`from` le début de la relation.

## <a name="return-value"></a>Valeur de retour

Si la cardinalité de la terminaison To est 1, la valeur retournée est `Ref<T>`. Si la cardinalité de la terminaison To est n, la valeur retournée est `Collection<Ref<T>>`.

## <a name="remarks"></a>Notes

Les relations sont des constructions de première classe dans le Entity Data Model (EDM). Elles peuvent être établies entre plusieurs types d'entités et les utilisateurs peuvent les parcourir d'une terminaison (entité) à l'autre. `from` et `to` sont facultatifs à la condition qu'il n'existe aucune ambiguïté au niveau de la résolution des noms dans la relation.

NAVIGATE est valide dans l'espace O et C.

Une construction de navigation se présente généralement sous la forme suivante :

navigate(`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ] ] )

Exemple :

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

Où OrderCustomer est le `relationship`, et Client et Order sont les terminaisons `to-end` (customer) et `from-end` (order) de la relation. Si OrderCustomer était une relation n :1, le type de résultat de l’expression de navigation est Ref @ no__t-0Customer >.

Voici la même expression sous une forme plus simple :

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

De même, dans une requête de la forme suivante, l’expression de navigation produirait une collection < Ref @ no__t-0Order > >.

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

L'expression d'instance doit être un type entity/ref.

## <a name="example"></a>Exemple

La requête Entity SQL suivante utilise l'opérateur NAVIGATE pour parcourir la relation établie entre les types d'entités Address et SalesOrderHeader. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :

1. Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).

2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :

 [!code-sql[DP EntityServices Concepts#NAVIGATE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#navigate)]

## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
- [Comment : naviguer parmi les relations avec l’opérateur Navigate](navigate-entity-sql.md)
