---
title: Fonctions mathématiques
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 4512aaa2eeb3e715a1d6f7a8655912eb15162124
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149763"
---
# <a name="mathematical-functions"></a>Fonctions mathématiques

Le fournisseur de données .NET Framework pour SQL Server (SqlClient) propose des fonctions mathématiques qui effectuent des calculs sur des valeurs d’entrée qui sont fournies comme arguments, et retournent une valeur numérique comme résultat. Ces fonctions se trouvent dans l'espace de noms SqlServer, lequel est disponible lorsque vous utilisez SqlClient. La propriété d’espace de noms d’un fournisseur permet à Entity Framework de découvrir le préfixe attribué par ce fournisseur à des constructions spécifiques, telles que des types et des fonctions. Le tableau suivant décrit les fonctions mathématiques SqlClient.  
  
## <a name="absexpression"></a>ABS (expression)

Effectue la fonction de valeur absolue.

**Arguments**

`expression` :`Int32`,`Int64`, `Double` ou `Decimal`.

**Valeur de rendement**

Valeur absolue de l'expression spécifiée.

**Exemple**

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a>ACOS (expression)

Retourne la valeur d'arc cosinus de l'expression spécifiée.

**Arguments**

`expression` : une `Double`.

**Valeur de rendement**

`Double`.

**Exemple**

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a>ASIN (expression)

Retourne la valeur d'arcsinus de l'expression spécifiée.

**Arguments**

`expression` : une `Double`.

**Valeur de rendement**

`Double`.

**Exemple**

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a>ATAN(expression)

Retourne la valeur d'arctangente de l'expression numérique spécifiée.

**Arguments**

`expression` : une `Double`.

**Valeur de rendement**

`Double`.

**Exemple**

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a>ATN2 (expression, expression)

Retourne l'angle, en radians, dont la tangente est comprise entre les deux expressions numériques spécifiées.

**Arguments**

`expression` : une `Double`.

**Valeur de rendement**

`Double`.

**Exemple**

`SqlServer.ATN2(9, 8)`

## <a name="ceilingexpression"></a>CEILING(expression)

Convertit l'expression spécifiée en plus petit entier supérieur ou égal à cette expression.

**Arguments**

`expression` :`Int32`,`Int64`, `Double` ou `Decimal`.

**Valeur de rendement**

Un `Int32` `Int64`, `Double`, `Decimal`, ou .

**Exemple**

[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a>COS (expression)

Calcule le cosinus trigonométrique de l'angle spécifié, en radians.

**Arguments**

`expression` : une `Double`.

**Valeur de rendement**

`Double`.

**Exemple**

`SqlServer.COS(45)`

## <a name="cotexpression"></a>COT (expression)

Calcule la cotangente trigonométrique de l'angle spécifié, en radians.

**Arguments**

`expression` : une `Double`.

**Valeur de rendement**

`Double`.

**Exemple**

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a>DEGREES (radians)

Retourne l'angle correspondant, en degrés.

**Arguments**

`expression` :`Int32`,`Int64`, `Double` ou `Decimal`.

**Valeur de rendement**

Un `Int32` `Int64`, `Double`, `Decimal`, ou .

**Exemple**

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a>EXP (expression)

Calcule la valeur exponentielle d'une expression numérique spécifiée.

**Arguments**

`expression` : une `Double`.

**Valeur de rendement**

`Double`.

**Exemple**`SqlServer.EXP(1)`

## <a name="floorexpression"></a>FLOOR (expression)

Convertit l'expression spécifiée en plus grand entier inférieur ou égal à cette expression.

**Arguments**

`expression` : une `Double`.

**Valeur de rendement**

`Double`.

**Exemple**

[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a>LOG(expression)

Calcule le logarithme népérien de l'expression `float` spécifiée.

**Arguments**

`expression` : une `Double`.

**Valeur de rendement**

`Double`.

**Exemple**

`SqlServer.LOG(100)`

## <a name="log10expression"></a>LOG10 (expression)

Retourne le logarithme en base 10 de l'expression `Double` spécifiée.

**Arguments**

`expression` : une `Double`.

**Valeur de rendement**

`Double`.

**Exemple**

`SqlServer.LOG10(100)`

## <a name="pi"></a>PI()

Retourne la valeur constante de pi sous la forme d'une valeur `Double`.

**Valeur de rendement**

`Double`.

**Exemple**

`SqlServer.PI()`

## <a name="powernumeric_expression-power_expression"></a>POWER (numeric_expression, power_expression)

Calcule la valeur d'une expression donnée élevée à une puissance spécifiée.

**Arguments**

|  |  |
|--|--|
|`numeric_expression`| Un `Int32` `Int64`, `Double`, `Decimal`, ou .|
|`power_expression`| Un `Double` qui représente le pouvoir `numeric_expression`auquel élever le .|

**Valeur de rendement**

Valeur du paramètre `numeric_expression` donné élevé à la puissance `power_expression` spécifiée.

**Exemple**

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a>RADIANS(expression)

Convertit les degrés en radians.

**Arguments**

`expression` :`Int32`,`Int64`, `Double` ou `Decimal`.

**Valeur de rendement**

Un `Int32` `Int64`, `Double`, `Decimal`, ou .

**Exemple**

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a>RAND ([semences])

Retourne une valeur aléatoire comprise entre 0 et 1.

**Arguments**

La valeur de `Int32`graine comme un . Si la valeur initiale n'est pas spécifiée, le moteur de base de données SQL Server affecte une valeur initiale aléatoire. Pour une valeur de départ spécifiée, le résultat retourné est toujours le même.

**Valeur de rendement**

Valeur `Double` aléatoire comprise entre 0 et 1.

**Exemple**

`SqlServer.RAND()`
  
## <a name="roundnumeric_expression-lengthfunction"></a>ROUND (numeric_expression, longueur[,fonction])

Retourne une expression numérique, arrondie à la longueur ou à la précision spécifiée.

**Arguments**

|  |  |
|--|--|
|`numeric_expression`| Un `Int32` `Int64`, `Double`, `Decimal`, ou .
|`length`| `Int32` qui représente la précision selon laquelle arrondir `numeric_expression`. Lorsque `length` est un nombre positif, `numeric_expression` est arrondi au nombre de décimales indiqué par `length`. Lorsque `length` est un nombre négatif, `numeric_expression` est arrondi à gauche de la virgule décimale, selon l'indication fournie par `length`.|
|`function` | facultatif. Un `Int32` qui représente le type d’opération à effectuer. Lorsque la fonction est omise ou a `numeric_expression` une valeur de 0 (par défaut), est arrondie. Lorsqu’une valeur autre que `numeric_expression` 0 est spécifiée, est tronquée. |

**Valeur de rendement**

Valeur du paramètre `numeric_expression` donné élevé à la puissance `power_expression` spécifiée.

**Exemple**

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a>SIGN(expression)

Renvoie le chiffre positif (+1), zéro (0) ou négatif (-1) de l'expression spécifiée.

**Arguments**

`expression` : `Int32`, `Int64`, `Double` ou `Decimal`

**Valeur de rendement**

Un `Int32` `Int64`, `Double`, `Decimal`, ou .

**Exemple**

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a>SIN(expression)

Calcule le sinus trigonométrique de l'angle spécifié, en radians, et retourne une expression `Double`.

**Arguments**

`expression` : une `Double`.

**Valeur de rendement**

`Double`.

**Exemple**`SqlServer.SIN(20)`

## <a name="sqrtexpression"></a>SQRT(expression)

Retourne la racine carrée de l'expression spécifiée.

**Arguments**

`expression` : une `Double`.

**Valeur de rendement**

`Double`.

**Exemple**`SqlServer.SQRT(3600)`

## <a name="squareexpression"></a>SQUARE (expression)

Retourne le carré de l'expression spécifiée.

**Arguments**

`expression` : une `Double`.

**Valeur de rendement**

`Double`.

**Exemple**

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a>TAN (expression)

Calcule la tangente d'une expression spécifiée.

**Arguments**

`expression`: `Double`

**Valeur de rendement**

`Double`

**Exemple**

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a>Voir aussi

- [Fonctions mathématiques (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql)
- [Fonctions SqlClient pour Entity Framework](sqlclient-for-ef-functions.md)
