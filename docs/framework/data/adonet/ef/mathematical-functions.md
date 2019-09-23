---
title: Fonctions mathématiques
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 5e5658e28c7d806f7fd38f941bfa7254e7806e11
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182486"
---
# <a name="mathematical-functions"></a>Fonctions mathématiques

Le fournisseur de données .NET Framework pour SQL Server (SqlClient) propose des fonctions mathématiques qui effectuent des calculs sur des valeurs d’entrée qui sont fournies comme arguments, et retournent une valeur numérique comme résultat. Ces fonctions se trouvent dans l'espace de noms SqlServer, lequel est disponible lorsque vous utilisez SqlClient. La propriété d’espace de noms d’un fournisseur permet à Entity Framework de découvrir le préfixe attribué par ce fournisseur à des constructions spécifiques, telles que des types et des fonctions. Le tableau suivant décrit les fonctions mathématiques SqlClient.  
  
## <a name="absexpression"></a>ABS (expression)

Effectue la fonction de valeur absolue.

**Arguments**

`expression`: ,, Ou`Decimal`. `Int32` `Int64` `Double`

**Valeur de retour**

Valeur absolue de l'expression spécifiée.

**Exemple**

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a>ACOS (expression)

Retourne la valeur d'arc cosinus de l'expression spécifiée.

**Arguments**

`expression`: `Double`

**Valeur de retour**

`Double`

**Exemple**

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a>ASIN (expression)

Retourne la valeur d'arcsinus de l'expression spécifiée.

**Arguments**

`expression`: `Double`

**Valeur de retour**

`Double`

**Exemple**

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a>ATAN (expression)

Retourne la valeur d'arctangente de l'expression numérique spécifiée.

**Arguments**

`expression`: `Double`

**Valeur de retour**

`Double`

**Exemple**

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a>ATN2 (expression, expression)

Retourne l'angle, en radians, dont la tangente est comprise entre les deux expressions numériques spécifiées.

**Arguments**

`expression`: `Double`

**Valeur de retour**

`Double`

**Exemple**

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a>CEILING (expression)

Convertit l'expression spécifiée en plus petit entier supérieur ou égal à cette expression.

**Arguments**

`expression`: ,, Ou`Decimal`. `Int32` `Int64` `Double`

**Valeur de retour**

,, Ou`Decimal`. `Int32` `Int64` `Double`

**Exemple** 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a>COS(expression)

Calcule le cosinus trigonométrique de l'angle spécifié, en radians. 

**Arguments** 

`expression`: `Double` 

**Valeur de retour** 

`Double` 

**Exemple** 

`SqlServer.COS(45)`

## <a name="cotexpression"></a>COT (expression)

Calcule la cotangente trigonométrique de l'angle spécifié, en radians. 

**Arguments** 

`expression`: `Double` 

**Valeur de retour** 

`Double` 

**Exemple** 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a>DEGRÉS (radians)

Retourne l'angle correspondant, en degrés. 

**Arguments** 

`expression`: ,, Ou`Decimal`. `Int32` `Int64` `Double` 

**Valeur de retour** 

,, Ou`Decimal`. `Int32` `Int64` `Double` 

**Exemple** 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a>EXP (expression)

Calcule la valeur exponentielle d'une expression numérique spécifiée. 

**Arguments** 

`expression`: `Double` 

**Valeur de retour** 

`Double` 

**Exemple**`SqlServer.EXP(1)`

## <a name="floorexpression"></a>FLOOR (expression)

Convertit l'expression spécifiée en plus grand entier inférieur ou égal à cette expression. 

**Arguments** 

`expression`: `Double` 

**Valeur de retour** 

`Double` 

**Exemple** 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a>LOG (expression)

Calcule le logarithme népérien de l'expression `float` spécifiée. 

**Arguments** 

`expression`: `Double` 

**Valeur de retour** 

`Double` 

**Exemple** 

`SqlServer.LOG(100)`

## <a name="log10expression"></a>LOG10 (expression)

Retourne le logarithme en base 10 de l'expression `Double` spécifiée. 

**Arguments** 

`expression`: `Double` 

**Valeur de retour** 

`Double` 

**Exemple** 

`SqlServer.LOG10(100)`

## <a name="pi"></a>PI()

Retourne la valeur constante de pi sous la forme d'une valeur `Double`. 

**Valeur de retour** 

`Double` 

**Exemple** 

`SqlServer.PI()`

## <a name="powernumeric_expression-power_expression"></a>PUISSANCE (expression_numérique, power_expression)

Calcule la valeur d'une expression donnée élevée à une puissance spécifiée.

**Arguments** 

|  |  |
|--|--|
|`numeric_expression`| ,, Ou`Decimal`. `Int32` `Int64` `Double`|
|`power_expression`| Qui représente la puissance à laquelle le `numeric_expression`doit être déclenché. `Double`| 

**Valeur de retour** 

Valeur du paramètre `numeric_expression` donné élevé à la puissance `power_expression` spécifiée. 

**Exemple** 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a>RADIANs (expression)

Convertit les degrés en radians. 

**Arguments** 

`expression`: ,, Ou`Decimal`. `Int32` `Int64` `Double` 

**Valeur de retour** 

,, Ou`Decimal`. `Int32` `Int64` `Double` 

**Exemple** 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a>RAND ([Seed])

Retourne une valeur aléatoire comprise entre 0 et 1. 

**Arguments** 

Valeur de départ en tant `Int32`que. Si la valeur initiale n'est pas spécifiée, le moteur de base de données SQL Server affecte une valeur initiale aléatoire. Pour une valeur initiale spécifiée, le résultat retourné est toujours le même.

**Valeur de retour** 

Valeur `Double` aléatoire comprise entre 0 et 1. 

**Exemple** 

`SqlServer.RAND()`
  
## <a name="roundnumeric_expression-lengthfunction"></a>ROUND (expression_numérique, longueur [, fonction])

Retourne une expression numérique, arrondie à la longueur ou à la précision spécifiée. 

**Arguments** 

|  |  |
|--|--|
|`numeric_expression`| ,, Ou`Decimal`. `Int32` `Int64` `Double` 
|`length`| `Int32` qui représente la précision selon laquelle arrondir `numeric_expression`. Lorsque `length` est un nombre positif, `numeric_expression` est arrondi au nombre de décimales indiqué par `length`. Lorsque `length` est un nombre négatif, `numeric_expression` est arrondi à gauche de la virgule décimale, selon l'indication fournie par `length`.|
|`function` | Optionnel. `Int32` Qui représente le type d’opération à effectuer. Quand la fonction est omise ou a la valeur 0 (valeur par défaut `numeric_expression` ), est arrondie. Lorsqu’une valeur autre que 0 est spécifiée, `numeric_expression` est tronqué. |

**Valeur de retour** 

Valeur du paramètre `numeric_expression` donné élevé à la puissance `power_expression` spécifiée.

**Exemple** 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a>SIGN (expression) 

Retourne le signe positif (+1), nul (0) ou négatif (-1) de l'expression spécifiée. 

**Arguments** 

`expression` : `Int32`, `Int64`, `Double` ou `Decimal` 

**Valeur de retour** 

,, Ou`Decimal`. `Int32` `Int64` `Double` 

**Exemple** 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a>SIN(expression)

Calcule le sinus trigonométrique de l'angle spécifié, en radians, et retourne une expression `Double`. 

**Arguments** 

`expression`: `Double` 

**Valeur de retour** 

`Double` 

**Exemple**`SqlServer.SIN(20)`

## <a name="sqrtexpression"></a>SQRT (expression)

Retourne la racine carrée de l'expression spécifiée. 

**Arguments** 

`expression`: `Double` 

**Valeur de retour** 

`Double` 

**Exemple**`SqlServer.SQRT(3600)`

## <a name="squareexpression"></a>SQUARE (expression)

Retourne le carré de l'expression spécifiée. 

**Arguments** 

`expression`: `Double` 

**Valeur de retour** 

`Double` 

**Exemple** 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a>TAN (expression)

Calcule la tangente d'une expression spécifiée.

**Arguments** 

`expression`: `Double` 

**Valeur de retour** 

`Double` 

**Exemple** 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a>Voir aussi

Pour plus d'informations sur les fonctions mathématiques prises en charge par SqlClient, consultez la documentation correspondant à la version de SQL Server que vous avez spécifiée dans le manifeste du fournisseur SqlClient :

- **SQL Server 2005 :** [Fonctions mathématiques (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))
- **SQL Server 2008 :** [Fonctions mathématiques (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))
- **SQL Server 2012 et versions ultérieures :** [Fonctions mathématiques (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql)

- [Fonctions SqlClient pour Entity Framework](sqlclient-for-ef-functions.md)
