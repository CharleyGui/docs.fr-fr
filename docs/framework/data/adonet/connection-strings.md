---
title: Chaînes de connexion dans ADO.NET
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 02fe8d984f1287673477bb142b3f9626e248898e
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363751"
---
# <a name="connection-strings-in-adonet"></a>Chaînes de connexion dans ADO.NET

Une chaîne de connexion contient des informations d'initialisation qui sont passées en tant que paramètre d'un fournisseur de données à une source de données. Le fournisseur de données reçoit la chaîne de connexion en tant que <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> valeur de la propriété. Le fournisseur analyse la chaîne de connexion et s’assure que la syntaxe est correcte et que les mots clés sont pris en charge. La <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> méthode transmet ensuite les paramètres de connexion analysés à la source de données. La source de données effectue une validation supplémentaire et établit une connexion.

## <a name="connection-string-syntax"></a>Syntaxe de chaîne de connexion

Une chaîne de connexion est une liste délimitée par des points-virgules de paires de paramètres clé/valeur:

```
keyword1=value; keyword2=value;
```

Les mots clés ne respectent pas la casse. Toutefois, les valeurs peuvent respecter la casse, en fonction de la source de données. Les mots clés et les valeurs peuvent contenir des [espaces blancs](https://en.wikipedia.org/wiki/Whitespace_character#Unicode). Les espaces blancs de début et de fin sont ignorés dans les mots clés et les valeurs sans guillemets.

Si une valeur contient le point-virgule, les [caractères de contrôle Unicode](https://en.wikipedia.org/wiki/Unicode_control_characters)ou les espaces blancs de début ou de fin, elle doit être placée entre guillemets simples ou doubles. Par exemple :

```
Keyword=" whitespace  ";
Keyword='special;character';
```

Le caractère englobant peut ne pas se trouver dans la valeur qu’il englobe. Par conséquent, une valeur contenant des guillemets simples peut être placée entre guillemets doubles, et vice versa:

```
Keyword='double"quotation;mark';
Keyword="single'quotation;mark";
```

Vous pouvez également échapper le caractère englobant à l’aide de deux d’entre eux:

```
Keyword="double""quotation";
Keyword='single''quotation';
```

Les guillemets eux-mêmes, ainsi que le signe égal, ne nécessitent pas d’échappement, donc les chaînes de connexion suivantes sont valides:

```
Keyword=no "escaping" 'required';
Keyword=a=b=c
```

Étant donné que chaque valeur est lue jusqu’au point-virgule suivant ou jusqu’à la fin de la chaîne, `a=b=c`la valeur dans le dernier exemple est, et le point-virgule final est facultatif.

Toutes les chaînes de connexion partagent la même syntaxe de base décrite ci-dessus. Toutefois, l’ensemble des mots clés reconnus dépend du fournisseur et a évolué au fil des années à partir des API antérieures telles que *ODBC*. Le fournisseur de données *.NET Framework* pour *SQL Server* (`SqlClient`) prend en charge de nombreux mots clés d’anciennes API, mais il est généralement plus flexible et accepte des synonymes pour un grand nombre des mots clés de chaîne de connexion courants.

Les erreurs de frappe peuvent entraîner des erreurs. Par exemple, `Integrated Security=true` est valide, mais `IntegratedSecurity=true` génère une erreur.

Les chaînes de connexion construites manuellement au moment de l’exécution à partir d’une entrée utilisateur non validée sont vulnérables aux attaques par injection de chaîne et mettent en péril la sécurité au niveau de la source de données. Pour résoudre ces problèmes, *ADO.NET* 2,0 a introduit les générateurs de [chaînes de connexion](../../../../docs/framework/data/adonet/connection-string-builders.md) pour chaque fournisseur de données *.NET Framework* . Ces générateurs de chaînes de connexion exposent des paramètres en tant que propriétés fortement typées et permettent de valider la chaîne de connexion avant qu’elle ne soit envoyée à la source de données.

## <a name="in-this-section"></a>Dans cette section

[Générateurs de chaînes de connexion](../../../../docs/framework/data/adonet/connection-string-builders.md)\
Montre comment utiliser les classes `ConnectionStringBuilder` pour générer des chaînes de connexion valides au moment de l'exécution.

[Chaînes de connexion et fichiers de configuration](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)\
Montre comment stocker et extraire des chaînes de connexion dans des fichiers de configuration.

[Syntaxe de chaîne de connexion](../../../../docs/framework/data/adonet/connection-string-syntax.md)\
Décrit comment configurer des chaînes de connexion spécifiques au fournisseur pour `SqlClient`, `OracleClient`, `OleDb` et `Odbc`.

[Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md)\
Montre des techniques pour la protection des informations utilisées pour la connexion à une source de données.

## <a name="see-also"></a>Voir aussi

- [Connexion à une source de données](/cpp/data/odbc/connecting-to-a-data-source)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
