---
title: Fonctions mathématiques canoniques
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 9417ff9836912017c9d88bb24a18849aaac2836a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250308"
---
# <a name="math-canonical-functions"></a>Fonctions mathématiques canoniques

Entity SQL comprend les fonctions canoniques mathématiques suivantes :
  
## <a name="absvalue"></a>Abs(valeur)

Retourne la valeur absolue de `value`.

**Arguments**

`Int16` ,,`Double`, ,,`Decimal`Et. `Byte` `Int32` `Int64` `Single`

**Valeur de retour**

Type d'élément `value`.

**Exemple**

`Abs(-2)`

## <a name="ceilingvalue"></a>Ceiling(valeur)

Retourne le plus petit entier qui n'est pas inférieur à `value`.

**Arguments**

`Single` ,`Double`Et .`Decimal`

**Valeur de retour**

Type d'élément `value`.

**Exemple**

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a>Floor(valeur)

Retourne le plus grand entier qui n'est pas supérieur à `value`.

**Arguments**

`Single` ,`Double`Et .`Decimal`

**Valeur de retour**

Type d'élément `value`.

**Exemple**

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a>Power(valeur, exposant)

Retourne le résultat de `value` à l'exposant `exponent` spécifié.

**Arguments**

|  |  |
|--|--|
|`value` | `Int32, Int64, Double`, Ou`Decimal`. |
|`exponent` | `Int64` ,`Double`Ou .`Decimal` |

**Valeur de retour**

Type d'élément `value`.

**Exemple**

`Power(748.58,2)`

## <a name="roundvalue"></a>Round(valeur)

Retourne la partie entière de `value`, arrondie à l'entier le plus proche.

**Arguments**

`Single` ,`Double`Et .`Decimal`

**Valeur de retour**

Type d'élément `value`.

**Exemple**

`Round(748.58)`

## <a name="roundvalue-digits"></a>Round(valeur, chiffres)

Retourne `value`, arrondi aux `digits` spécifiés les plus proches.

**Arguments**

|  |  |
|--|--|
|`value`|`Double` ou `Decimal`.|
|`digits`|`Int16` ou `Int32`.|

**Valeur de retour**

Type d'élément `value`.

**Exemple**

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a>Truncate(valeur, chiffres)

Retourne `value`, tronqué aux `digits` spécifiés les plus proches.

**Arguments**

|  |  |
|--|--|
|`value`|`Double` ou `Decimal`.|
|`digits`|`Int16` ou `Int32`.|

**Valeur de retour**

Type d'élément `value`.

**Exemple**

`Truncate(748.58,1)`  
  
 Ces fonctions retournent `null` si une entrée de valeur `null` est fournie.  
  
 Des fonctionnalités équivalentes sont disponibles dans le fournisseur managé Client Microsoft SQL. Pour plus d’informations, consultez [SqlClient pour les fonctions de Entity Framework](../sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions canoniques](canonical-functions.md)
