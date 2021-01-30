---
title: Visite guidée du langage C# - Guide du langage C#
description: Novice en matière de langage C# ? Découvrez les principes de base du langage. Commencez par cette vue d’ensemble.
ms.date: 01/28/2021
ms.openlocfilehash: 016edf331d8cbdca2902cb033963b6aea11df513
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216640"
---
# <a name="a-tour-of-the-c-language"></a>Visite guidée du langage C#

C# (prononcé « voir Sharp ») est un langage de programmation moderne, orienté objet et de type sécurisé. C# permet aux développeurs de créer de nombreux types d’applications sécurisées et fiables qui s’exécutent dans l’écosystème .NET. C# prend sa source dans la famille de langages C et sera immédiatement reconnaissable aux programmeurs en C, C++, Java et JavaScript. Cette visite guidée fournit une vue d’ensemble des principaux composants du langage dans C# 8 et versions antérieures. Si vous souhaitez explorer le langage par le biais d’exemples interactifs, consultez la présentation des didacticiels [C#](../tutorials/intro-to-csharp/index.md) .

C# est un langage de programmation orienté objet et **orienté composant**. C# fournit des constructions de langage pour prendre en charge directement ces concepts, en faisant de C# un langage naturel dans lequel créer et utiliser des composants logiciels. Depuis son origine, C# a ajouté des fonctionnalités pour prendre en charge de nouvelles charges de travail et des pratiques de conception de logiciels émergentes.

Plusieurs fonctionnalités C# permettent de créer des applications robustes et durables. Le [_*_garbage collection_*_](../../standard/garbage-collection/index.md) libère automatiquement la mémoire occupée par des objets inutilisés inaccessibles. Les [_*_types Nullable_*_](../nullable-references.md) protègent les variables qui ne font pas référence aux objets alloués. La [_*_gestion des exceptions_*_](../programming-guide/exceptions/index.md) offre une approche structurée et extensible de la détection et de la récupération des erreurs. Les [_*_expressions lambda_*_](../language-reference/operators/lambda-expressions.md) prennent en charge les techniques de programmation fonctionnelle. La syntaxe [_*_LINQ (Language Integrated Query)_*_](../linq/index.md) crée un modèle commun pour l’utilisation des données de n’importe quelle source. La prise en charge linguistique pour les [_*_opérations asynchrones_*_](../programming-guide/concepts/async/index.md) fournit la syntaxe pour la création de systèmes distribués. C# possède un [_*_système de type unifié_*_](../programming-guide/types/index.md). Tous les types C#, y compris les types primitifs tels que `int` et `double`, héritent d’un seul type `object` racine. Tous les types partagent un ensemble d’opérations courantes. Les valeurs de n’importe quel type peuvent être stockées, transportées et exploitées de manière cohérente. En outre, C# prend en charge les [types référence](../language-reference/builtin-types/reference-types.md) définis par l’utilisateur et les [types valeur](../language-reference/builtin-types/value-types.md). C# permet l’allocation dynamique d’objets et le stockage en ligne de structures légères. C# prend en charge des méthodes et des types génériques, ce qui améliore la sécurité et les performances de type. C# fournit des itérateurs, qui permettent aux implémenteurs de classes de collection de définir des comportements personnalisés pour le code client.

C# met l’accent sur le contrôle de _*_version_*_ pour s’assurer que les programmes et les bibliothèques peuvent évoluer au fil du temps d’une manière compatible. Les aspects de la conception de C# qui ont été directement influencés par les considérations relatives à la gestion des versions incluent les `virtual` `override` modificateurs et séparés, les règles de résolution de surcharge de méthode et la prise en charge des déclarations de membres d’interface explicites.

## <a name="net-architecture"></a>Architecture .NET

Les programmes C# s’exécutent sur .NET, un système d’exécution virtuel appelé le common language runtime (CLR) et un ensemble de bibliothèques de classes. Le CLR est l’implémentation par Microsoft de l’infrastructure de langage commun (CLI), une norme internationale. L’interface CLI est la base de la création d’environnements d’exécution et de développement dans lesquels les langages et les bibliothèques fonctionnent ensemble de façon transparente.

Le code source écrit en C# est compilé dans un [langage intermédiaire (il)](../../standard/managed-code.md) conforme à la spécification CLI. Le code de langage intermédiaire et les ressources, telles que les bitmaps et les chaînes, sont stockés dans un assembly, en général avec une extension de _.dll *. Un assembly contient un manifeste qui fournit des informations sur les types, la version et la culture de l’assembly.

Lorsque le programme C# est exécuté, l’assembly est chargé dans le CLR. Le CLR effectue une compilation juste-à-temps (JIT) pour convertir le code de langage intermédiaire en instructions machine natives. Le CLR fournit d’autres services liés à la garbage collection automatique, à la gestion des exceptions et à la gestion des ressources. Le code exécuté par le CLR est parfois appelé « code managé », contrairement à « code non managé », qui est compilé dans un langage machine natif ciblant une plateforme spécifique.

L’interopérabilité des langages est une fonctionnalité clé de .NET. Le code de langage intermédiaire produit par le compilateur C# est conforme à la spécification de type commun (CTS). Le code de langage intermédiaire généré à partir de C# peut interagir avec le code généré à partir des versions .NET de F #, Visual Basic, C++ ou l’un des plus de 20 autres langages compatibles CTS. Un seul assembly peut contenir plusieurs modules écrits dans différents langages .NET, et les types peuvent se référencer mutuellement comme s’ils avaient été écrits dans le même langage.

Outre les services d’exécution, .NET comprend également des bibliothèques étendues. Ces bibliothèques prennent en charge de nombreuses charges de travail différentes. Elles sont organisées en espaces de noms qui fournissent un large éventail de fonctionnalités utiles pour tout, de l’entrée de fichier à la sortie de la manipulation de chaînes à l’analyse XML, aux infrastructures d’application Web pour Windows Forms contrôles. L’application C# classique utilise largement la bibliothèque de classes .NET pour gérer les tâches courantes de « plomberie ».

Pour plus d’informations sur .NET, consultez [vue d’ensemble de .net](../../core/introduction.md).

## <a name="hello-world"></a>Hello World

Le programme « Hello, World » est souvent utilisé pour présenter un langage de programmation. Le voici en C# :

:::code language="csharp" interactive="try-dotnet" source="./snippets/shared/HelloWorld.cs":::

Le programme « Hello, World » commence par une directive `using` qui fait référence à l’espace de noms `System`. Les espaces de noms représentent un moyen hiérarchique d’organiser les bibliothèques et les programmes C#. Les espaces de noms contiennent des types et d’autres espaces de noms ; par exemple, l’espace de noms `System` contient plusieurs types, notamment la classe `Console` référencée dans le programme, et d’autres espaces de noms, tels que `IO` et `Collections`. Une directive `using` qui fait référence à un espace de noms donné permet l’utilisation non qualifiée des types membres de cet espace de noms. En raison de la directive `using`, le programme peut utiliser `Console.WriteLine` comme raccourci pour `System.Console.WriteLine`.

La classe `Hello` déclarée par le programme « Hello, World » a un membre unique, la méthode nommée `Main`. La `Main` méthode est déclarée avec le `static` modificateur. Si les méthodes d’instance peuvent faire référence à une instance d’objet englobante particulière avec le mot clé `this`, les méthodes statiques fonctionnent sans référence à un objet particulier. Par Convention, une méthode statique nommée `Main` sert de point d’entrée d’un programme C#.

La sortie du programme est générée par la méthode `WriteLine` de la classe `Console` dans l’espace de noms `System`. Cette classe est fournie par les bibliothèques de classes standard, qui, par défaut, sont référencées automatiquement par le compilateur.

## <a name="types-and-variables"></a>Types et variables

Il existe deux genres de types en C# : les *types référence* et les *types valeur*. Les variables des types valeur contiennent directement leurs données. Les variables des types référence stockent des références à leurs données, qui sont les derniers appelés objets. Avec les types référence, il est possible que deux variables référencent le même objet et que les opérations sur une variable affectent l’objet référencé par l’autre variable. Avec les types valeur, les variables ont chacune leur propre copie des données, et il n’est pas possible pour les opérations sur l’une d’affecter l’autre (à l’exception des `ref` `out` variables de paramètre et).

Un ***identifier** _ est un nom de variable. Un identificateur est une séquence de caractères Unicode sans espace blanc. Un identificateur peut être un mot réservé C#, s’il est préfixé par `@` . L’utilisation d’un mot réservé comme identificateur peut être utile lors de l’interaction avec d’autres langages.

Les types valeur de C# sont divisés en _simple types *, *types ENUM*, types *struct*, *types valeur Nullable* et *types valeur de tuple*. Les types référence de C# sont encore divisés en *types classe*, *types interface*, *types tableau* et *types délégués*.

Le schéma suivant fournit une vue d’ensemble du système de type de C#.

- [Types de valeur](../language-reference/builtin-types/value-types.md)
  - [Types simples](../language-reference/builtin-types/value-types.md#built-in-value-types)
    - [Intégrale signé](../language-reference/builtin-types/integral-numeric-types.md): `sbyte` , `short` , `int` , `long`
    - [Entier non signé](../language-reference/builtin-types/integral-numeric-types.md): `byte` , `ushort` , `uint` , `ulong`
    - [Caractères Unicode](../../standard/base-types/character-encoding-introduction.md): `char` , qui représente une unité de code UTF-16
    - [Virgule flottante binaire IEEE](../language-reference/builtin-types/floating-point-numeric-types.md): `float` , `double`
    - Virgule [flottante décimale haute précision](../language-reference/builtin-types/floating-point-numeric-types.md):`decimal`
    - Boolean : `bool` , qui représente des valeurs booléennes, les valeurs qui sont `true` ou `false`
  - [Types ENUM](../language-reference/builtin-types/enum.md)
    - Types définis par l’utilisateur sous la forme `enum E {...}` . Un type `enum` est un type distinct avec des constantes nommées. Chaque type `enum` a un type sous-jacent qui doit être un des huit types intégraux. L’ensemble de valeurs d’un type `enum` est le même que l’ensemble de valeurs du type sous-jacent.
  - [Types struct](../language-reference/builtin-types/struct.md)
    - Types définis par l'utilisateur de la forme `struct S {...}`
  - [Types valeur Nullable](../language-reference/builtin-types/nullable-value-types.md)
    - Extensions de tous les autres types de valeurs avec une valeur `null`
  - [Types de valeur de Tuple](../language-reference/builtin-types/value-tuples.md)
    - Types définis par l'utilisateur de la forme `(T1, T2, ...)`
- [Types référence](../language-reference/keywords/reference-types.md)
  - [Types de classe](../language-reference/keywords/class.md)
    - Classe de base fondamentale de tous les autres types : `object`
    - [Chaînes Unicode](../../standard/base-types/character-encoding-introduction.md): `string` , qui représente une séquence d’unités de code UTF-16
    - Types définis par l'utilisateur de la forme `class C {...}`
  - [Types d'interface](../language-reference/keywords/interface.md)
    - Types définis par l'utilisateur de la forme `interface I {...}`
  - [Types tableau](../programming-guide/arrays/index.md)
    - Unidimensionnel, multidimensionnel et en escalier. Par exemple : `int[]` , `int[,]` et `int[][]`
  - [Types délégués](../language-reference/builtin-types/reference-types.md#the-delegate-type)
    - Types définis par l'utilisateur de la forme `delegate int D(...)`

Les programmes C# utilisent les *déclarations de type* pour créer de nouveaux types. Une déclaration de type spécifie le nom et les membres du nouveau type. Six des catégories de types C# sont définissables par l’utilisateur : types de classes, types struct, types interface, types ENUM, types délégués et types valeur de Tuple.

- Un type `class` définit une structure de données qui contient des données membres (champs) et des fonctions membres (méthodes, propriétés, etc.). Les types de classes prennent en charge l’héritage unique et le polymorphisme, des mécanismes par lesquels les classes dérivées peuvent étendre et spécialiser les classes de base.
- Un type `struct` est similaire à un type de classe dans la mesure où il représente une structure avec des membres de données et des membres de fonctions. Toutefois, contrairement aux classes, les structs sont des types valeur et ne nécessitent généralement pas d’allocation de tas. Les types struct ne prennent pas en charge l’héritage spécifié par l’utilisateur, et tous les types struct héritent implicitement du type `object` .
- Un `interface` type définit un contrat comme un jeu nommé de membres publics. Un `class` ou `struct` qui implémente un `interface` doit fournir des implémentations des membres de l’interface. Une `interface` peut hériter de plusieurs interfaces de base, et une `class` ou `struct` peut implémenter plusieurs interfaces.
- Un type `delegate` représente des références aux méthodes avec une liste de paramètres et un type de retour particuliers. Les délégués permettent de traiter les méthodes en tant qu’entités qui peuvent être affectées à des variables et passées comme paramètres. Les délégués sont semblables aux types de fonction fournis par les langages fonctionnels. Elles sont également similaires au concept de pointeurs de fonction qui se trouvent dans d’autres langages. Contrairement aux pointeurs de fonction, les délégués sont orientés objet et de type sécurisé.

Les `class` types,, `struct` `interface` et `delegate` prennent tous en charge les génériques, dans lesquels ils peuvent être paramétrés avec d’autres types.

C# prend en charge les tableaux unidimensionnels et multidimensionnels de tout type. Contrairement aux types indiqués ci-dessus, les types de tableau ne doivent pas nécessairement être déclarés avant de pouvoir être utilisés. Au lieu de cela, les types de tableaux sont construits en ajoutant des crochets à un nom de type. Par exemple, `int[]` est un tableau unidimensionnel de `int` , `int[,]` est un tableau à deux dimensions de `int` , et `int[][]` est un tableau unidimensionnel de tableaux unidimensionnels, ou un tableau en escalier, de `int` .

Les types Nullable ne nécessitent pas une définition distincte. Pour chaque type non Nullable `T` , il existe un type Nullable correspondant `T?` qui peut contenir une valeur supplémentaire, `null` . Par exemple, `int?` est un type qui peut contenir n’importe quel entier 32 bits ou la valeur `null` , et `string?` est un type qui peut contenir n’importe quelle `string` valeur ou `null` .

Le système de type C# est unifié de telle façon qu’une valeur de n’importe quel type peut être traitée comme un `object` . Chaque type dans C# dérive directement ou indirectement du type `object`, et `object` est la classe de base fondamentale de tous les types. Les valeurs des types référence sont considérées comme des objets simplement en affichant les valeurs en tant que type `object`. Les valeurs des types valeur sont considérées comme des objets en effectuant des opérations de *boxing* et *d’unboxing*. Dans l’exemple suivant, une valeur `int` est convertie en `object` et à nouveau en `int`.

:::code language="csharp" source="./snippets/shared/Program.cs" ID="boxing" :::

Quand une valeur d’un type de valeur est assignée à une `object` référence, un « Box » est alloué pour contenir la valeur. Cette zone est une instance d’un type référence, et la valeur est copiée dans cette zone. À l’inverse, lorsqu’une `object` référence est castée en un type valeur, une vérification est effectuée que le référencé `object` est une zone du type valeur correct. Si la vérification est réussie, la valeur dans la zone est copiée dans le type valeur.

Le système de type unifié de C# signifie que les types valeur sont traités comme `object` des références « à la demande ». En raison de l’unification, les bibliothèques à usage général qui utilisent le type `object` peuvent être utilisées avec tous les types qui dérivent de `object` , y compris les types référence et les types valeur.

Il existe plusieurs types de *variables* en C#, y compris les champs, les éléments de tableau, les variables locales et les paramètres. Les variables représentent des emplacements de stockage. Chaque variable a un type qui détermine les valeurs qui peuvent être stockées dans la variable, comme indiqué ci-dessous.

- Type de valeur n’acceptant pas Null
  - Une valeur de ce type exact
- Types valeur Nullable
  - Une valeur `null` ou une valeur de ce type exact
- objet
  - Une référence `null`, une référence à un objet de tout type référence ou une référence à une valeur boxed de n’importe quel type valeur
- Type de classe
  - Une référence `null`, une référence à une instance de ce type de classe ou une référence à une instance d’une classe dérivée de ce type de classe
- Type d'interface
  - Une référence `null`, une référence à une instance d’un type de classe qui implémente ce type d’interface ou une référence à une valeur boxed d’un type valeur qui implémente ce type d’interface
- Type tableau
  - Une référence `null`, une référence à une instance de ce type de tableau ou une instance d’un type de tableau compatible
- Type délégué
  - Une référence `null` ou une référence à une instance d’un type délégué compatible

## <a name="program-structure"></a>Structure du programme

Les concepts clés de l’organisation en C# sont les [ * **programmes** _](../programming-guide/inside-a-program/index.md), les [_*_espaces de noms_*_](../programming-guide/namespaces/index.md), les [_*_types_*_](../programming-guide/types/index.md), [_*_les membres_*_](../programming-guide/classes-and-structs/members.md)et les [_*_assemblys_*_](../../standard/assembly/index.md). Les programmes déclarent des types qui contiennent des membres et peuvent être organisés en espaces de noms. Les classes, les structs et les interfaces sont des exemples de types. Les champs, méthodes, propriétés et événements sont des exemples de membres. Lorsque les programmes C# sont compilés, ils sont empaquetés physiquement dans des assemblys. Les assemblys ont généralement l’extension de fichier `.exe` ou `.dll` , selon qu’ils implémentent des _*_applications_*_ ou des _*_bibliothèques_*_, respectivement.

Prenons l’exemple d’un assembly qui contient le code suivant :

:::code language="csharp" source="./snippets/shared/AcmeStack.cs":::

Le nom qualifié complet de cette classe est `Acme.Collections.Stack`. La classe contient plusieurs membres : un champ nommé `top`, deux méthodes nommées `Push` et `Pop`, et une classe imbriquée nommée `Entry`. La classe `Entry` contient trois membres en plus : un champ nommé `next`, un autre nommé `data` et un constructeur. `Stack`Est une classe _generic *. Il a un paramètre de type, `T` qui est remplacé par un type concret lorsqu’il est utilisé.

> [!NOTE]
> Une *pile* est une collection « First in-Last out » (Filo). De nouveaux éléments sont ajoutés en haut de la pile. Lorsqu’un élément est supprimé, il est supprimé du haut de la pile.

Les assemblys contiennent le code exécutable sous forme d’instructions de langage intermédiaire (IL) et des informations symboliques sous la forme de métadonnées. Avant son exécution, le compilateur juste-à-temps (JIT) du Common Language Runtime .NET convertit le code IL dans un assembly en code spécifique au processeur.

Étant donné qu’un assembly est une unité autodescriptive de fonctionnalité contenant à la fois du code et des métadonnées, il n’est pas nécessaire d’utiliser des `#include` directives et des fichiers d’en-tête en C#. Les membres et types publics contenus dans un assembly particulier sont disponibles dans un programme C# par simple référence à cet assembly lors de la compilation du programme. Par exemple, ce programme utilise la classe `Acme.Collections.Stack` à partir de l’assembly `acme.dll` :

:::code language="csharp" source="./snippets/shared/StackUsage.cs":::

Pour compiler ce programme, vous devez *référencer* l’assembly contenant la classe Stack définie dans l’exemple précédent.

Les programmes C# peuvent être stockés dans plusieurs fichiers sources. Lorsqu’un programme C# est compilé, tous les fichiers sources sont traités ensemble, et les fichiers sources peuvent se référencer librement. Conceptuellement, c’est comme si tous les fichiers sources étaient concaténés dans un fichier volumineux avant d’être traités. Les déclarations anticipées ne sont jamais nécessaires en C#, car, à quelques exceptions près, l’ordre de déclaration n’est pas significatif. C# ne limite pas un fichier source à la déclaration d’un seul type public et n’exige pas que le nom du fichier source corresponde à un type déclaré dans le fichier source.

D’autres Articles de cette présentation expliquent ces blocs organisationnels.

>[!div class="step-by-step"]
>[Next](types.md)
