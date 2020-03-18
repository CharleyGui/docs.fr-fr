---
title: Initialiseurs d’objet et de collection - Guide de programmation C#
ms.date: 12/19/2018
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: ae8741e2f29db0a470ad8d3b121375fbdeaff0d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170193"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a>Initialiseurs d’objet et de collection (Guide de programmation C#)

C# vous permet d’instancier un objet ou une collection et d’effectuer des affectations de membres dans une seule instruction.

## <a name="object-initializers"></a>Initialiseurs d’objet

Les initialiseurs d'objet vous permettent d'affecter des valeurs aux champs ou propriétés accessibles d'un objet, au moment de sa création, sans devoir appeler un constructeur suivi de ses lignes d'instructions d'assignation. La syntaxe de l'initialiseur de l'objet vous permet de spécifier les arguments d'un constructeur ou de les omettre (et la syntaxe de parenthèses).  L'exemple suivant montre comment utiliser l'initialiseur de l'objet de type nommé, `Cat`, et comment appeler le constructeur sans paramètre. Notez l'utilisation de propriétés implémentées automatiquement dans la classe `Cat`. Pour plus d’informations, consultez [Propriétés implémentées automatiquement](auto-implemented-properties.md).  
  
[!code-csharp[ObjectInitializer1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#CatDeclaration)]  
[!code-csharp[ObjectInitializer1a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ObjectPropertyInitialization)]  

La syntaxe des initialiseurs d’objet vous permet de créer une instance qui assigne l’objet nouvellement créé, avec ses propriétés, à la variable dans l’assignation.

À compter de C# 6, les initialiseurs d’objet peuvent, en plus d’affecter des champs et des propriétés, définir des indexeurs. Prenez l’exemple de cette classe `Matrix` de base :

[!code-csharp[ObjectInitializer2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixDeclaration)]  

Vous pouvez initialiser la matrice identity avec le code suivant :

[!code-csharp[ObjectInitializer2a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixInitialization)]  

Tout indexeur accessible qui contient un setter accessible peut être utilisé comme l’une des expressions d’un initialiseur d’objet, indépendamment du nombre ou des types d’arguments. Les arguments d’index forment le côté gauche de l’affectation, et la valeur le côté droit de l’expression.  Par exemple, les éléments suivants sont tous valides si `IndexersExample` a les indexeurs appropriés :

```csharp
var thing = new IndexersExample {
    name = "object one",
    [1] = '1',
    [2] = '4',
    [3] = '9',
    Size = Math.PI,
    ['C',4] = "Middle C"
}
```

Pour le code précédent à compiler, le type `IndexersExample` doit avoir les membres suivants :

```csharp
public string name;
public double Size { set { ... }; }
public char this[int i] { set { ... }; }
public string this[char c, int i] {  set { ... }; }
```

## <a name="object-initializers-with-anonymous-types"></a>Initialiseurs d'objet avec des types anonymes

Bien que les initialisateurs d’objets puissent être utilisés dans n’importe quel contexte, ils sont particulièrement utiles dans les expressions de requête linQ. Les expressions de requête utilisent souvent des [types anonymes](./anonymous-types.md), qui peuvent uniquement être initialisés à l’aide d’un initialiseur d’objet, comme indiqué dans la déclaration suivante.  

```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```

Les types `select` anonymes permettent à la clause d’une expression de requête LINQ de transformer des objets de la séquence originale en objets dont la valeur et la forme peuvent différer de l’original. Cela s'avère utile si vous souhaitez stocker uniquement une partie des informations de chaque objet d'une séquence. Dans l'exemple suivant, supposons qu'un objet de produit (`p`) contient de nombreux champs et méthodes et que vous souhaitez uniquement créer une séquence d'objets qui contiennent le nom de produit et le prix unitaire.  
  
[!code-csharp[ObjectInitializer3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#AnonymousUse)]  

Lorsque cette requête est exécutée, la variable `productInfos` contient une séquence d'objets qui sont accessibles dans une instruction `foreach` comme indiqué dans cet exemple :  

```csharp
foreach(var p in productInfos){...}  
```

Chaque objet dans le nouveau type anonyme a deux propriétés publiques qui reçoivent les mêmes noms que les propriétés ou champs de l’objet d’origine. Vous pouvez également renommer un champ lorsque vous créez un type anonyme. L'exemple suivant renomme le champ `UnitPrice` en `Price`.  

```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```

## <a name="collection-initializers"></a>Initialiseurs de collection

Les initialiseurs de collection vous permettent de spécifier un ou plusieurs initialiseurs d’élément quand vous initialisez un type de collection qui implémente <xref:System.Collections.IEnumerable> et qui utilise `Add` comme méthode d’instance ou méthode d’extension avec la signature appropriée. Les initialiseurs d’élément peuvent être une valeur simple, une expression ou un initialiseur d’objet. En utilisant un initialiseur de collection, il n’est pas nécessaire de spécifier plusieurs appels ; le compilateur les ajoute automatiquement.  
  
L’exemple suivant montre deux initialiseurs de collection simples :  

```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```

L'initialiseur de collection suivant utilise des initialiseurs d'objets pour initialiser les objets de la classe `Cat` définis dans un exemple précédent. Notez que les initialiseurs d'objets individuels sont placés entre accolades et séparés par une virgule.  
  
[!code-csharp[ListInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitializer)]  
  
Vous pouvez spécifier [Null](../../language-reference/keywords/null.md) comme élément dans un initialiseur de collection si la méthode `Add` de la collection l’autorise.  
  
[!code-csharp[ListInitializerNull](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitialerWithNull)]  
  
 Vous pouvez spécifier des éléments indexés si la collection prend en charge l’indexation en lecture/écriture.
  
[!code-csharp[DictionaryInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryIndexerInitializer)]  

L’exemple précédent génère du code qui appelle <xref:System.Collections.Generic.Dictionary%602.Item(%600)> pour définir les valeurs. Avant le numéro 6, vous pouvez initialiser les dictionnaires et autres contenants associatifs à l’aide de la syntaxe suivante. Notez que la syntaxe de l’indexeur, avec des parenthèses et une affectation, est remplacée par un objet avec plusieurs valeurs :

[!code-csharp[DictionaryAddInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryAddInitializer)]  

Cet exemple d’initialiseur appelle <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> pour ajouter les trois éléments dans le dictionnaire. Ces deux manières d’initialiser les collections associatives ont un comportement légèrement différent en raison des appels de méthode générés par le compilateur. Les deux variantes fonctionnent avec la classe `Dictionary`. D’autres types peuvent uniquement prendre en charge l’une ou l’autre en fonction de leur API publique.

## <a name="examples"></a>Exemples

L’exemple suivant combine les concepts d’initialiseurs d’objet et de collection.

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullExample)]  

L’exemple suivant montre un objet qui implémente <xref:System.Collections.IEnumerable> et qui contient une méthode `Add` avec plusieurs paramètres. Il utilise un initialiseur de collection avec plusieurs éléments dans la liste correspondant à la signature de la méthode `Add`.

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullListExample)]  

Les méthodes `Add` peuvent utiliser le mot clé `params` pour sélectionner un nombre variable d’arguments, comme indiqué dans l’exemple suivant. Cet exemple montre également l’implémentation personnalisée d’un indexeur pour initialiser une collection à l’aide d’index.

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullDictionaryInitializer)]  

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [LINQ en C#](../../linq/index.md)
- [Types anonymes](anonymous-types.md)
