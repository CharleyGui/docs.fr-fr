---
title: 'Didacticiel : utiliser les attributs-C #'
description: Découvrez comment les attributs fonctionnent en C#.
author: mgroves
ms.technology: csharp-fundamentals
ms.date: 03/06/2017
ms.assetid: b152cf36-76e4-43a5-b805-1a1952e53b79
ms.openlocfilehash: 4e2c0126d0920df18271f8889d8e117cd374d979
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174184"
---
# <a name="use-attributes-in-c"></a>Utiliser des attributs en C\#

Les attributs fournissent un moyen permettant d’associer des informations au code de manière déclarative. Ils peuvent également fournir un élément réutilisable qui peut être appliqué à diverses cibles.

Considérez l’attribut `[Obsolete]`. Vous pouvez l’appliquer aux classes, structures, méthodes, constructeurs et bien plus encore. Il _déclare_ que l’élément est obsolète. Il revient ensuite au compilateur C# de rechercher cet attribut et d’effectuer des actions en réponse.

Dans ce didacticiel, vous allez voir comment ajouter des attributs à votre code, comment créer et utiliser vos propres attributs et comment utiliser des attributs qui sont intégrés à .NET Core.

## <a name="prerequisites"></a>Prérequis

Vous devez configurer votre ordinateur pour exécuter .NET core. Vous trouverez les instructions d’installation dans la page [téléchargements .net Core](https://dotnet.microsoft.com/download) .
Vous pouvez exécuter cette application sur Windows, Ubuntu Linux, Mac OS ou dans un conteneur Docker.
Vous devez installer l’éditeur de code de votre choix. Les descriptions ci-dessous utilisent [Visual Studio Code](https://code.visualstudio.com/), un éditeur open source et multiplateforme. Cependant, vous pouvez utiliser les outils avec lesquels vous êtes le plus à l’aise.

## <a name="create-the-application"></a>Création de l’application

Maintenant que vous avez installé tous les outils, créez une nouvelle application .NET Core. Pour utiliser le générateur de ligne de commande, exécutez la commande suivante dans votre interpréteur de commandes préféré :

`dotnet new console`

Cette commande permet de créer des fichiers de projet .NET Core. Vous devez exécuter `dotnet restore` pour restaurer les dépendances nécessaires à la compilation de ce projet.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Pour exécuter le programme, utilisez `dotnet run`. Vous devriez voir le résultat dans la « Hello, World » dans la console.

## <a name="how-to-add-attributes-to-code"></a>Guide pratique d’ajout d’attributs aux propriétés

En C#, les attributs sont des classes qui héritent de la classe de base `Attribute`. Toute classe qui hérite de `Attribute` peut être utilisée comme une sorte de « balise » sur les autres éléments de code.
Par exemple, il existe un attribut appelé `ObsoleteAttribute`. Il sert à signaler que le code est obsolète et ne doit pas être plus utilisé. Vous pouvez placer cet attribut sur une classe, par exemple en utilisant des crochets.

[!code-csharp[Obsolete attribute example](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample1)]

Notez que si la classe est nommée `ObsoleteAttribute`, il est seulement nécessaire d’utiliser `[Obsolete]` dans le code. Il s’agit d’une convention que C# respecte.
Vous pouvez utiliser le nom complet `[ObsoleteAttribute]` si vous le souhaitez.

Lorsque vous marquez une classe comme étant obsolète, il est judicieux de fournir des informations indiquant *pourquoi* elle est obsolète, et/ou *quelle classe* utiliser à la place. Faites cela en passant un paramètre de chaîne à l’attribut obsolète.

[!code-csharp[Obsolete attribute example with parameters](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample2)]

La chaîne est passée comme argument à un constructeur `ObsoleteAttribute`, comme si vous écriviez `var attr = new ObsoleteAttribute("some string")`.

Les paramètres à un constructeur d’attribut sont limités aux types simples/littéraux : `bool, int, double, string, Type, enums, etc` et les tableaux de ces types.
Vous ne pouvez pas utiliser une expression ou une variable. Vous êtes libre d’utiliser des paramètres positionnels ou nommés.

## <a name="how-to-create-your-own-attribute"></a>Guide pratique de création de votre propre attribut

La création d’un attribut est aussi simple que l’héritage de la classe de base `Attribute`.

[!code-csharp[Create your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample1)]

Avec les éléments ci-dessus, je peux maintenant utiliser `[MySpecial]` (ou `[MySpecialAttribute]`) en tant qu’attribut ailleurs dans la base de code.

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample2)]

Les attributs dans la bibliothèque de classes de base .NET, comme `ObsoleteAttribute`, déclenchent certains comportements au sein du compilateur. Toutefois, un attribut que vous créez agit uniquement comme métadonnées et ne produit pas de code dans la classe d’attributs en cours d’exécution. Il revient à vous d’agir sur ces métadonnées ailleurs dans votre code (plus loin dans ce didacticiel).

Il y a ici un « piège » à éviter. Comme mentionné ci-dessus, seuls certains types sont autorisés à être passés comme arguments lors de l’utilisation d’attributs. Toutefois, lorsque vous créez un type d’attribut, le compilateur C# ne vous empêche pas de créer ces paramètres. Dans l’exemple ci-dessous, j’ai créé un attribut avec un constructeur qui se compile correctement.

[!code-csharp[Valid constructor used in an attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGothca1)]

Toutefois, vous ne pourrez pas utiliser ce constructeur avec une syntaxe d’attribut.

[!code-csharp[Invalid attempt to use the attribute constructor](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGotcha2)]

L’exemple ci-dessus entraîne une erreur du compilateur, comme `Attribute constructor parameter 'myClass' has type 'Foo', which is not a valid attribute parameter type`

## <a name="how-to-restrict-attribute-usage"></a>Comment limiter l’utilisation d’attributs

Les attributs peuvent être utilisés sur plusieurs « cibles ». Les exemples ci-dessus les illustrent sur des classes, mais ils peuvent également être utilisés sur :

* Assembly
* Classe
* Constructeur
* Délégué
* Énumération
* Événement
* Champ
* GenericParameter
* Interface
* Méthode
* Module
* Paramètre
* Propriété
* ReturnValue
* Structure

Lorsque vous créez une classe d’attributs, par défaut, C# vous permettra d’utiliser cet attribut sur une des cibles d’attribut possibles. Si vous souhaitez limiter votre attribut à certaines cibles, vous pouvez le faire à l’aide de `AttributeUsageAttribute` sur votre classe d’attributs. C’est exact, un attribut sur un attribut !

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample1)]

Si vous tentez de placer l’attribut ci-dessus sur quelque chose qui n’est pas une classe ou un struct, vous obtiendrez une erreur du compilateur, comme `Attribute 'MyAttributeForClassAndStructOnly' is not valid on this declaration type. It is only valid on 'class, struct' declarations`

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample2)]

## <a name="how-to-use-attributes-attached-to-a-code-element"></a>Guide d’utilisation des attributs associés à un élément de code

Les attributs agissent comme métadonnées. Sans une certaine force extérieure, vous ne les verrez pas faire grand-chose.

Pour rechercher et agir sur des attributs, la [Réflexion](../programming-guide/concepts/reflection.md) est généralement nécessaire. Je n’aborderai pas la réflexion de façon approfondie dans ce didacticiel, mais l’idée fondamentale est que la réflexion vous permet d’écrire du code en C# qui examine un autre code.

Par exemple, vous pouvez utiliser la réflexion pour obtenir des informations sur une classe (ajoutez `using System.Reflection;` au début de votre code) :

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample1)]

Cela imprimera quelque chose comme : `The assembly qualified name of MyClass is ConsoleApplication.MyClass, attributes, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`

Une fois que vous avez un objet `TypeInfo` (ou `MemberInfo`, `FieldInfo`, etc.), vous pouvez utiliser la méthode `GetCustomAttributes`. Cette opération renvoie une collection d’objets `Attribute`.
Vous pouvez également utiliser `GetCustomAttribute` et spécifier un type d’attribut.

Voici un exemple d’utilisation de `GetCustomAttributes` sur une instance de `MemberInfo` pour `MyClass` (avec un attribut `[Obsolete]` associé, comme vu précédemment).

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample2)]

Cela imprimera ceci sur la console : `Attribute on MyClass: ObsoleteAttribute`. Essayez d’ajouter d’autres attributs à `MyClass`.

Il est important de noter que ces objets `Attribute` sont instanciés de manière différée. Autrement dit, ils ne sont pas instanciés jusqu'à ce que vous utilisiez `GetCustomAttribute` ou `GetCustomAttributes`.
Ils sont également instanciés chaque fois. Appeler `GetCustomAttributes` deux fois à la suite renverra deux instances différentes de `ObsoleteAttribute`.

## <a name="common-attributes-in-the-base-class-library-bcl"></a>Attributs communs dans la bibliothèque de classes de base (BCL)

Les attributs sont utilisés par de nombreux outils et frameworks. NUnit utilise des attributs tels que `[Test]` et `[TestFixture]`, qui sont utilisés par le Test Runner de NUnit. ASP.NET MVC utilise des attributs tels que `[Authorize]` et fournit un framework de filtres d’action pour traiter les problèmes transversaux sur les actions MVC. [PostSharp](https://www.postsharp.net) utilise la syntaxe d’attribut pour permettre la programmation orientée aspect en C#.

Voici quelques attributs importants générés dans les bibliothèques de classe de base de .NET Core :

* `[Obsolete]`. Celui-ci a été utilisé dans les exemples ci-dessus, et il se trouve dans l’espace de noms `System`. Il est utile de fournir des informations déclaratives sur une base de code changeante. Un message peut être fourni sous la forme d’une chaîne et un autre paramètre booléen peut servir à passer d’un avertissement du compilateur à une erreur du compilateur.

* `[Conditional]`. Cet attribut se trouve dans l'espace de noms `System.Diagnostics`. Cet attribut peut être appliqué aux méthodes (ou classes d’attributs). Vous devez transmettre une chaîne au constructeur.
Si cette chaîne ne correspond pas à une directive `#define`, les appels à cette méthode (mais pas la méthode proprement dite) sont supprimés par le compilateur C#. Cela est généralement utilisé pour le débogage (diagnostic).

* `[CallerMemberName]`. Cet attribut peut être utilisé sur les paramètres et se trouve dans l’espace de noms `System.Runtime.CompilerServices`. Il s’agit d’un attribut utilisé pour injecter le nom de la méthode qui appelle une autre méthode. Cela est généralement utilisé comme moyen d’éliminer les « chaînes magiques » lors de l’implémentation de INotifyPropertyChanged dans divers frameworks d’interface utilisateur. Par exemple :

[!code-csharp[Using CallerMemberName when implementing INotifyPropertyChanged](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CallerMemberName1)]

Dans le code ci-dessus, il est inutile d’avoir une chaîne littérale `"Name"`. Cela peut vous aider à éviter les bogues liés aux fautes de frappe et rend également plus simple la refactorisation/les changements de nom.

## <a name="summary"></a>Résumé

Si les attributs offrent à C# la puissance déclarative, ils constituent une forme de code de type métadonnées et n’agissent pas par eux-mêmes.
