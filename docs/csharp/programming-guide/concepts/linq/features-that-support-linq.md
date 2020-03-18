---
title: Fonctionnalités C# qui prennent en charge LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: 9fc8adaa49d02f8b69c2db6e94a28b9fab36b3b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635793"
---
# <a name="c-features-that-support-linq"></a>Fonctionnalités C# qui prennent en charge LINQ

La section suivante présente de nouvelles constructions de langage qui sont apparues avec C# 3.0. Bien que ces nouvelles fonctionnalités soient toutes utilisées dans une certaine mesure avec les requêtes LINQ, elles ne se limitent pas à LINQ et peuvent être utilisées dans n’importe quel contexte où vous les trouvez utiles.

## <a name="query-expressions"></a>Expressions de requête

Les expressions de requête utilisent une syntaxe déclarative similaire à SQL ou XQuery pour interroger les collections IEnumerable. À l’heure de compilation, la syntaxe de requête est convertie en appels de méthode à la mise en œuvre par un fournisseur de LINQ des méthodes standard d’extension de l’opérateur de requête. Les applications contrôlent les opérateurs de requête standard qui se trouvent dans la portée en spécifiant l’espace de noms approprié avec une directive `using`. L’expression de requête suivante accepte un tableau de chaînes, regroupe les chaînes qui commencent par le même caractère, puis trie ces groupes de chaînes.

```csharp
var query = from str in stringArray
            group str by str[0] into stringGroup
            orderby stringGroup.Key
            select stringGroup;
```

Pour plus d’informations, consultez [Expressions de requête LINQ](../../../linq/index.md).

## <a name="implicitly-typed-variables-var"></a>Variables implicitement typées (var)

Au lieu de spécifier explicitement un type lorsque vous déclarez et initialisez une variable, vous pouvez utiliser le modificateur [var](../../../language-reference/keywords/var.md) pour indiquer au compilateur qu’il doit déduire et assigner le type, comme illustré ici :

```csharp
var number = 5;
var name = "Virginia";
var query = from str in stringArray
            where str[0] == 'm'
            select str;
```

Les variables déclarées comme `var` sont aussi fortement typées que les variables dont vous spécifiez explicitement le type. `var` permet de créer des types anonymes, mais peut être utilisé uniquement pour les variables locales. Les tableaux peuvent également être déclarés avec un typage implicite.

Pour plus d’informations, consultez [Variables locales implicitement typées](../../classes-and-structs/implicitly-typed-local-variables.md).

## <a name="object-and-collection-initializers"></a>Initialiseurs d’objets et de collections

Les initialiseurs d’objets et de collections permettent d’initialiser un objet sans appeler explicitement un constructeur pour cet objet. Les initialiseurs sont généralement utilisés dans les expressions de requête pour projeter la source de données en un nouveau type de données. En supposant une classe nommée `Customer` avec les propriétés publiques `Name` et `Phone`, l’initialiseur d’objet peut être utilisé, comme dans le code suivant :

```csharp
var cust = new Customer { Name = "Mike", Phone = "555-1212" };
```

Si l’on reprend notre classe `Customer`, supposons qu’il existe une source de données appelée `IncomingOrders` et que, pour chaque commande caractérisée par un grand `OrderSize`, nous souhaitons créer un nouveau `Customer` basé sur cette commande. Une requête LINQ peut être exécutée sur cette source de données et utiliser l’initialisation d’objets pour remplir une collection :

```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```

La source de données peut avoir plus de propriétés sous-jacentes que la classe `Customer`, par exemple, `OrderSize` ; cependant, avec l’initialisation d’objets, les données retournées par la requête sont moulées dans le type de données souhaité ; nous choisissons les données correspondant à notre classe. Par conséquent, nous disposons désormais d’un `IEnumerable` contenant les nouveaux `Customer` que nous voulions. La requête ci-dessus peut également s’écrire avec la syntaxe de méthode LINQ :

```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```

Pour plus d'informations, consultez les pages suivantes :

- [Initialiseurs d’objets et de collections](../../classes-and-structs/object-and-collection-initializers.md)

- [Syntaxe des expressions de requête pour les opérateurs de requête standard](./query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a>Types anonymes

Un type anonyme est construit par le compilateur et le nom du type est uniquement disponible pour le compilateur. Les types anonymes permettent de regrouper facilement des propriétés de manière temporaire dans un résultat de requête, sans avoir à définir un type nommé distinct. Les types anonymes sont initialisés avec une nouvelle expression et un initialiseur d’objet, comme indiqué ici :

```csharp
select new {name = cust.Name, phone = cust.Phone};
```

Pour plus d’informations, voir [Anonymous Types](../../classes-and-structs/anonymous-types.md).

## <a name="extension-methods"></a>Méthodes d’extension

Une méthode d’extension est une méthode statique qui peut être associée à un type, de manière à être appelée comme une méthode d’instance de ce type. Cette fonctionnalité permet d’ajouter de nouvelles méthodes aux types existants sans les modifier. Les opérateurs de requête standard sont un ensemble de méthodes d’extension qui <xref:System.Collections.Generic.IEnumerable%601>fournissent la fonctionnalité de requête LINQ pour n’importe quel type qui implémente.

Pour plus d’informations, consultez [Méthodes d’extension](../../classes-and-structs/extension-methods.md).

## <a name="lambda-expressions"></a>Expressions lambda

Une expression lambda est une fonction inline qui utilise l’opérateur => pour séparer les paramètres d’entrée du corps de la fonction, et qui peut être convertie au moment de la compilation en un délégué ou une arborescence d’expressions. Dans la programmation LINQ, vous rencontrerez des expressions lambda lorsque vous faites des appels de méthode directe aux opérateurs de requête standard.

Pour plus d'informations, consultez les pages suivantes :

- [Fonctions anonymes](../../statements-expressions-operators/anonymous-functions.md)

- [Expressions lambda](../../statements-expressions-operators/lambda-expressions.md)

- [Arborescences d’expressions (C#)](../expression-trees/index.md)

## <a name="see-also"></a>Voir aussi

- [LINQ (Language-Integrated Query) (C#)](./index.md)
