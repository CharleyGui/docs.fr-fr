---
title: Types anonymes - Guide de programmation C#
description: Les types anonymes en C# encapsulent un jeu de propriétés en lecture seule dans un objet sans avoir à définir explicitement un type. Le compilateur génère un nom.
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#]
- C# Language, anonymous types
ms.assetid: 59c9d7a4-3b0e-475e-b620-0ab86c088e9b
ms.openlocfilehash: ccdee1a86ab0c292721e69346cb7cedb03d4c28b
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474499"
---
# <a name="anonymous-types-c-programming-guide"></a>Types anonymes (Guide de programmation C#)

Les types anonymes permettent d'encapsuler un ensemble de propriétés en lecture seule dans un unique objet sans avoir à définir explicitement un type. Le nom du type est généré par le compilateur et n'est pas disponible au niveau du code source. Le type de chaque propriété est déduit par le compilateur.  
  
 Vous créez des types anonymes en utilisant l’opérateur [new](../../language-reference/operators/new-operator.md) avec un initialiseur d’objet. Pour plus d’informations sur les initialiseurs d’objets, consultez [Initialiseurs d’objets et de collections](./object-and-collection-initializers.md).  
  
 L'exemple suivant montre un type anonyme qui est initialisé avec deux propriétés nommées `Amount` et `Message`.  
  
```csharp  
var v = new { Amount = 108, Message = "Hello" };  
  
// Rest the mouse pointer over v.Amount and v.Message in the following  
// statement to verify that their inferred types are int and string.  
Console.WriteLine(v.Amount + v.Message);  
```  
  
 Les types anonymes sont en règle générale utilisés dans la clause [select](../../language-reference/keywords/select-clause.md) d’une expression de requête pour retourner un sous-ensemble de propriétés de chaque objet dans la séquence source. Pour plus d’informations sur les requêtes, consultez [LINQ en C#](../../linq/index.md).  
  
 Les types anonymes contiennent une ou plusieurs propriétés en lecture seule publiques. Aucun autre type de membres de classe, tels que des méthodes ou des événements, n'est valide. L'expression qui est utilisée pour initialiser une propriété ne peut pas être `null`, une fonction anonyme ou un type pointeur.  
  
 Le scénario le plus courant consiste à initialiser un type anonyme avec les propriétés d'un autre type. Dans l'exemple suivant, une classe existe qui porte le nom `Product`. La classe `Product` comprend des propriétés `Color` et `Price`, ainsi que d'autres propriétés qui ne vous intéressent pas. La variable `products` est une collection d'objets `Product`. La déclaration de type anonyme commence par le mot clé `new`. La déclaration initialise un nouveau type qui utilise uniquement deux propriétés de `Product`. Une quantité réduite de données est ainsi retournée dans la requête.  
  
 Si vous n'indiquez pas les noms de membre dans le type anonyme, le compilateur attribue aux membres de type anonyme le même nom que celui de la propriété utilisée pour les initialiser. Vous devez fournir un nom pour une propriété qui est initialisée avec une expression, comme indiqué dans l'exemple précédent. Dans l'exemple suivant, les noms des propriétés du type anonyme sont `Color` et `Price`.  
  
 [!code-csharp[csRef30Features#81](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csRef30Features/CS/csref30.cs#81)]  
  
 Quand vous utilisez un type anonyme pour initialiser une variable, vous déclarez la variable en tant que variable locale implicitement typée en utilisant [var](../../language-reference/keywords/var.md). Le nom de type ne peut pas être spécifié dans la déclaration de variable, car seul le compilateur a accès au nom sous-jacent du type anonyme. Pour plus d’informations sur `var`, consultez [Variables locales implicitement typées](./implicitly-typed-local-variables.md).  
  
 Vous pouvez créer un tableau d'éléments typés anonymement en associant une variable locale implicitement typée et un tableau typé implicitement, comme indiqué dans l'exemple suivant.  
  
```csharp  
var anonArray = new[] { new { name = "apple", diam = 4 }, new { name = "grape", diam = 1 }};  
```  
  
## <a name="remarks"></a>Notes  
 Les types anonymes sont des types [class](../../language-reference/keywords/class.md) qui dérivent directement d’[object](../../language-reference/builtin-types/reference-types.md) et qui ne peuvent pas être castés en type à l’exception du type [object](../../language-reference/builtin-types/reference-types.md). Le compilateur fournit un nom pour chaque type anonyme, bien que votre application ne puisse pas y accéder. Du point de vue du CLR, un type anonyme n'est pas différent des autres types de référence.  
  
 Si plusieurs initialiseurs d'objet dans un assembly spécifient une séquence de propriétés dans le même ordre et qui sont du même type et portent le même nom, le compilateur traite les objets comme des instances du même type. Elles partagent les mêmes informations de type générées par le compilateur.  
  
 Vous ne pouvez pas déclarer un champ, une propriété, un événement ou le type de retour d'une méthode comme ayant un type anonyme. De même, vous ne pouvez pas déclarer un paramètre formel d'une méthode, d'une propriété, d'un constructeur ou d'un indexeur comme ayant un type anonyme. Pour passer un type anonyme, ou une collection qui contient des types anonymes, en tant qu'argument d'une méthode, vous pouvez déclarer le paramètre comme objet de type. Cependant, cela va à l'encontre de l'objectif du typage fort. Si vous devez stocker les résultats de requête ou les passer en dehors des limites de la méthode, utilisez un struct ordinaire ou une classe au lieu d'un type anonyme.  
  
 Dans la mesure où les méthodes <xref:System.Object.Equals%2A> et <xref:System.Object.GetHashCode%2A> dans les types anonymes sont définies selon les termes des méthodes `Equals` et `GetHashCode` des propriétés, deux instances du même type anonyme sont égales si toutes leurs propriétés sont égales.  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Initialiseurs d’objets et de collections](./object-and-collection-initializers.md)
- [Mise en route de LINQ en C#](../concepts/linq/index.md)
- [LINQ en C#](../../linq/index.md)
