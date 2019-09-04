---
title: NAVIGATE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 2c6c2ae4c593da1d5fe8cdf3015eb0e31e4b12b5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249940"
---
# <a name="navigate-entity-sql"></a>NAVIGATE (Entity SQL)

Parcourt la relation établie entre des entités.

## <a name="syntax"></a>Syntaxe

```
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a>Arguments

`instance-expression`Instance d’une entité.

`relationship-type`Nom de type de la relation, à partir du fichier Conceptual Schema Definition Language (CSDL). Est qualifié en tant \<qu’espace de noms >.\< `relationship-type` nom du type de relation >.

`to`Fin de la relation.

`from`Début de la relation.

## <a name="return-value"></a>Valeur de retour

Si la cardinalité de la terminaison To est 1, la valeur retournée est `Ref<T>`. Si la cardinalité de la terminaison To est n, la valeur retournée est `Collection<Ref<T>>`.

## <a name="remarks"></a>Notes

Les relations sont des constructions de première classe dans le Entity Data Model (EDM). Elles peuvent être établies entre plusieurs types d'entités et les utilisateurs peuvent les parcourir d'une terminaison (entité) à l'autre. `from` et `to` sont facultatifs à la condition qu'il n'existe aucune ambiguïté au niveau de la résolution des noms dans la relation.

NAVIGATE est valide dans l'espace O et C.

Une construction de navigation se présente généralement sous la forme suivante :

navigate(`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ] ] )

Par exemple :

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

Où OrderCustomer est le `relationship`, et Client et Order sont les terminaisons `to-end` (customer) et `from-end` (order) de la relation. Si OrderCustomer était une relation n :1, le type de résultat de l’expression de navigation est\<Ref client >.

Voici la même expression sous une forme plus simple :

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

De même, dans une requête de la forme suivante, l’expression de navigation produirait une collection <\<ordre de référence > >.

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

L'expression d'instance doit être un type entity/ref.

## <a name="example"></a>Exemple

La requête Entity SQL suivante utilise l'opérateur NAVIGATE pour parcourir la relation établie entre les types d'entités Address et SalesOrderHeader. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :

1. Suivez la procédure décrite [dans la rubrique Procédure : Exécutez une requête qui retourne les résultats](../how-to-execute-a-query-that-returns-structuraltype-results.md)de StructuralType.

2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :

 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]

## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
- [Guide pratique : Naviguer parmi les relations avec l’opérateur Navigate](navigate-entity-sql.md)
