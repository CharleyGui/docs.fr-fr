---
title: Types - Guide de programmation C#
description: En savoir plus sur les types en programmation C#, tels que les types intégrés, les types personnalisés, les types valeur et les types référence.
ms.date: 11/19/2020
helpviewer_keywords:
- value types [C#]
- reference types [C#]
- types [C#]
- C# language, data types
- common type system [C#]
- data types [C#]
- C# language, types
- strong typing [C#]
ms.assetid: f782d7cc-035e-4500-b1b1-36a9881130ad
ms.openlocfilehash: 6a1a5b230e427a4991162a702245f1a87352784d
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190245"
---
# <a name="types-c-programming-guide"></a>Types (Guide de programmation C#)

## <a name="types-variables-and-values"></a>Types, variables et valeurs

C# est un langage fortement typé. Chaque variable et chaque constante ont un type, tout comme chaque expression qui fournit une valeur. Chaque déclaration de méthode spécifie un nom, un nombre de paramètres, ainsi que le type et le type (valeur, référence ou sortie) pour chaque paramètre d’entrée et pour la valeur de retour. La bibliothèque de classes .NET définit un ensemble de types numériques intégrés et des types plus complexes qui représentent un large éventail de constructions logiques, telles que le système de fichiers, les connexions réseau, les collections et les tableaux d’objets, ainsi que les dates. Un programme C# classique utilise des types de la bibliothèque de classes et des types définis par l’utilisateur qui modélisent les concepts propres au domaine du problème du programme.

Les informations stockées dans un type peuvent inclure les éléments suivants :

- Espace de stockage nécessaire pour une variable du type.
- Valeurs minimale et maximale que le type peut représenter.
- Membres (méthodes, champs, événements, etc.) que le type contient.
- Type de base dont le type est hérité.
- Interface (s) qu’il implémente.
- Emplacement où sera allouée la mémoire pour les variables au moment de l’exécution.
- Sortes d’opérations autorisées.

Le compilateur utilise les informations de type pour s’assurer que toutes les opérations effectuées dans votre code sont de *type sécurisé*. Par exemple, si vous déclarez une variable de type [int](../../language-reference/builtin-types/integral-numeric-types.md), le compilateur vous permet d’utiliser la variable dans des opérations d’addition et de soustraction. Si vous essayez d’effectuer ces mêmes opérations avec une variable de type [bool](../../language-reference/builtin-types/bool.md), le compilateur génère une erreur, comme illustré dans l’exemple suivant :

:::code language="csharp" source="snippets/index/Program.cs" id="TypeSafeExample":::

> [!NOTE]
> Développeurs C et C++ : notez que dans C#, [bool](../../language-reference/builtin-types/bool.md) n’est pas convertible en [int](../../language-reference/builtin-types/integral-numeric-types.md).

Le compilateur incorpore les informations de type dans le fichier exécutable sous forme de métadonnées. Le common language runtime (CLR) utilise ces métadonnées au moment de l’exécution pour garantir que le type est sécurisé lorsqu’il alloue et libère de la mémoire.

### <a name="specifying-types-in-variable-declarations"></a>Spécification de types dans les déclarations de variable

Lorsque vous déclarez une variable ou une constante dans un programme, vous devez spécifier son type ou utiliser le mot clé [var](../../language-reference/keywords/var.md) pour permettre au compilateur de déduire le type. L’exemple suivant montre des déclarations de variable qui utilisent des types numériques intégrés et des types complexes définis par l’utilisateur :

:::code language="csharp" source="snippets/index/Program.cs" id="Declarations":::

Les types de paramètres de méthode et de valeurs de retour sont spécifiés dans la déclaration de méthode. La signature suivante présente une méthode qui requiert [int](../../language-reference/builtin-types/integral-numeric-types.md) comme argument d’entrée et retourne une chaîne :

:::code language="csharp" source="snippets/index/Program.cs" id="GetName":::

Une fois que vous avez déclaré une variable, vous ne pouvez pas la redéclarer avec un nouveau type et vous ne pouvez pas assigner une valeur qui n’est pas compatible avec son type déclaré. Par exemple, vous ne pouvez pas déclarer un [int](../../language-reference/builtin-types/integral-numeric-types.md) et lui assigner une valeur booléenne `true` . Toutefois, les valeurs peuvent être converties en d’autres types, par exemple quand elles sont assignées à de nouvelles variables ou passées en tant qu’arguments de méthode. Une *conversion de type* qui n’entraîne pas de perte de données est effectuée automatiquement par le compilateur. Une conversion susceptible de causer la perte de données exige une variable *cast* dans le code source.

Pour plus d’informations, consultez [Cast et conversions de types](./casting-and-type-conversions.md).

## <a name="built-in-types"></a>Types intégrés

C# fournit un jeu standard de types intégrés pour représenter les entiers, les valeurs à virgule flottante, les expressions booléennes, les caractères de texte, les valeurs décimales et d’autres types de données. Il existe également des types `string` et `object` intégrés. Ces types peuvent être utilisés dans n’importe quel programme C#. Pour obtenir la liste complète des types intégrés, consultez [types intégrés](../../language-reference/builtin-types/built-in-types.md).

## <a name="custom-types"></a>Types personnalisés

Vous utilisez les constructions [struct](../../language-reference/builtin-types/struct.md), [classe](../../language-reference/keywords/class.md), [interface](../../language-reference/keywords/interface.md) et [enum](../../language-reference/builtin-types/enum.md) pour créer vos propres types personnalisés. La bibliothèque de classes .NET est une collection de types personnalisés fournie par Microsoft que vous pouvez utiliser dans vos propres applications. Par défaut, les types les plus fréquemment utilisés dans la bibliothèque de classes sont disponibles dans tous les programmes C#. D’autres deviennent disponibles uniquement lorsque vous ajoutez explicitement une référence de projet à l’assembly dans lequel elles sont définies. Une fois que le compilateur a une référence à l’assembly, vous pouvez déclarer des variables (et des constantes) des types déclarés dans cet assembly dans le code source. Pour plus d’informations, consultez [Bibliothèque de classes .NET](../../../standard/class-library-overview.md).

## <a name="the-common-type-system"></a>Système de type commun

Il est important de comprendre deux points fondamentaux concernant le système de type dans .NET :

- Il prend en charge le principe d’héritage. Les types peuvent dériver d’autres types, appelés *types de base*. Le type dérivé hérite (avec certaines restrictions) des méthodes, des propriétés et des autres membres du type de base. Le type de base peut à son tour dériver d’un autre type, auquel cas le type dérivé hérite des membres des deux types de base dans sa hiérarchie d’héritage. Tous les types, notamment les types numériques intégrés comme <xref:System.Int32?displayProperty=nameWithType> (mot clé C# : [int](../../language-reference/builtin-types/integral-numeric-types.md)), dérivent au final d’un seul type de base, qui est <xref:System.Object?displayProperty=nameWithType> (mot clé C# : [object](../../language-reference/builtin-types/reference-types.md)). Cette hiérarchie de types unifiée est appelée [Système de type commun](../../../standard/base-types/common-type-system.md) (CTS). Pour plus d’informations sur l’héritage dans C#, consultez [Héritage](../classes-and-structs/inheritance.md).
- Chaque type du CTS est défini comme *type valeur* ou *type référence*. Ces types incluent tous les types personnalisés dans la bibliothèque de classes .NET et également vos propres types définis par l’utilisateur. Les types que vous définissez à l’aide du mot clé [struct](../../language-reference/builtin-types/struct.md) sont des types valeur ; tous les types numériques intégrés sont `structs`. Les types que vous définissez à l’aide du mot clé [class](../../language-reference/keywords/class.md) sont des types référence. Les types référence et les types valeur ne suivent pas les mêmes règles de compilation et ont un comportement différent au moment de l’exécution.

L’illustration suivante montre la relation entre les types valeur et les types référence dans le CTS.

![Capture d’écran montrant des types valeur et des types référence dans CTS.](./media/index/value-reference-types-common-type-system.png)

> [!NOTE]
> Vous pouvez voir que les types couramment utilisés sont tous organisés dans l’espace de noms <xref:System>. Toutefois, l’espace de noms qui contient un type n’a aucune incidence sur le fait qu’il s’agisse d’un type valeur ou d’un type référence.

### <a name="value-types"></a>Types de valeur

Les types valeur dérivent de <xref:System.ValueType?displayProperty=nameWithType>, qui dérive de <xref:System.Object?displayProperty=nameWithType>. Les types qui dérivent de <xref:System.ValueType?displayProperty=nameWithType> ont un comportement spécial dans le CLR. Les variables de type valeur contiennent directement leurs valeurs, ce qui signifie que la mémoire est allouée inline dans le contexte où la variable est déclarée. Il n’existe pas d’allocation de tas ou de charge de garbage collection distincte pour les variables de type valeur.

Il existe deux catégories de types valeur : [struct](../../language-reference/builtin-types/struct.md) et [enum](../../language-reference/builtin-types/enum.md).

Les types numériques intégrés sont des structs et ont des champs et des méthodes auxquels vous pouvez accéder :

:::code language="csharp" source="snippets/index/Program.cs" id="ConstantByte":::

Mais vous les déclarez et leur assignez des valeurs comme s’il s’agissait de types non agrégés simples :

:::code language="csharp" source="snippets/index/Program.cs" id="NonAggregateTypes":::

Les types valeur sont *sealed*, ce qui signifie que vous ne pouvez pas dériver un type de n’importe quel type valeur, par exemple <xref:System.Int32?displayProperty=nameWithType> . Vous ne pouvez pas définir un struct pour hériter d’une classe ou d’un struct défini par l’utilisateur, car un struct peut uniquement hériter de <xref:System.ValueType?displayProperty=nameWithType> . Toutefois, un struct peut implémenter une ou plusieurs interfaces. Vous pouvez effectuer un cast d’un type struct en n’importe quel type d’interface qu’il implémente ; ce Cast entraîne une opération de *boxing* pour encapsuler le struct à l’intérieur d’un objet de type référence sur le tas managé. Les opérations de boxing se produisent quand vous passez un type valeur à une méthode qui prend un <xref:System.Object?displayProperty=nameWithType> ou tout type d’interface comme paramètre d’entrée. Pour plus d’informations, consultez [Conversion boxing et unboxing](./boxing-and-unboxing.md).

Vous utilisez le mot clé [struct](../../language-reference/builtin-types/struct.md) pour créer vos propres types valeur personnalisés. En règle générale, un struct est utilisé comme conteneur pour un petit jeu de variables connexes, comme le montre l'exemple suivant :

:::code language="csharp" source="snippets/index/Program.cs" id="Coords":::

Pour plus d’informations sur les structs, consultez [types structure](../../language-reference/builtin-types/struct.md). Pour plus d’informations sur les types valeur, consultez [types valeur](../../language-reference/builtin-types/value-types.md).

L’autre catégorie de types valeur est [enum](../../language-reference/builtin-types/enum.md). Un enum définit un jeu de constantes intégrales nommées. Par exemple l’énumération <xref:System.IO.FileMode?displayProperty=nameWithType> dans la bibliothèque de classes du .NET contient un ensemble d’entiers constants nommés qui spécifient comment un fichier doit être ouvert. Il est défini comme indiqué dans l’exemple suivant :

:::code language="csharp" source="snippets/index/Program.cs" id="EnumFileMode":::

La constante `System.IO.FileMode.Create` a la valeur 2. Toutefois, le nom est bien plus explicite pour les êtres humains qui lisent le code source. pour cette raison, il est préférable d’utiliser des énumérations au lieu de nombres littéraux constants. Pour plus d'informations, consultez <xref:System.IO.FileMode?displayProperty=nameWithType>.

Toutes les énumérations héritent de <xref:System.Enum?displayProperty=nameWithType>, qui hérite de <xref:System.ValueType?displayProperty=nameWithType>. Toutes les règles qui s’appliquent aux structs s’appliquent également aux enums. Pour plus d’informations sur les enums, consultez [types énumération](../../language-reference/builtin-types/enum.md).

### <a name="reference-types"></a>Types référence

Un type qui est défini comme une [classe](../../language-reference/keywords/class.md), un [délégué](../../language-reference/builtin-types/reference-types.md), un tableau ou une [interface](../../language-reference/keywords/interface.md) est un *type référence*. Au moment de l’exécution, quand vous déclarez une variable de type référence, celle-ci contient la valeur [null](../../language-reference/keywords/null.md) tant que vous n’avez pas explicitement créé un objet à l’aide de l’opérateur [new](../../language-reference/operators/new-operator.md) ou que vous ne lui avez pas assigné un objet créé ailleurs à l’aide de `new`, comme indiqué dans l’exemple suivant :

:::code language="csharp" source="snippets/index/Program.cs" id="DeclarationAndAssignment":::

Une interface doit être initialisée avec un objet de classe qui l’implémente. Si `MyClass` implémente `IMyInterface`, vous créez une instance de `IMyInterface` comme indiqué dans l’exemple suivant :

:::code language="csharp" source="snippets/index/Program.cs" id="InterfaceDeclaration":::

Quand l’objet est créé, la mémoire est allouée sur le tas managé et la variable contient uniquement une référence à l’emplacement de l’objet. Les types sur le tas managé nécessitent une surcharge lorsqu’ils sont alloués et lorsqu’ils sont récupérés par la fonctionnalité de gestion automatique de la mémoire du CLR, appelée *garbage collection*. Toutefois, garbage collection est également hautement optimisé et, dans la plupart des scénarios, il ne crée pas de problème de performances. Pour plus d’informations sur le garbage collection, consultez [Gestion automatique de la mémoire](../../../standard/automatic-memory-management.md).

Tous les tableaux sont des types référence, même si leurs éléments sont des types valeur. Les tableaux dérivent implicitement de la classe <xref:System.Array?displayProperty=nameWithType>, mais vous les déclarez et vous les utilisez avec la syntaxe simplifiée fournie par C#, comme illustré dans l’exemple suivant :

:::code language="csharp" source="snippets/index/Program.cs" id="ArrayDeclaration":::

Les types référence prennent en charge l’héritage. Lorsque vous créez une classe, vous pouvez hériter de toute autre interface ou classe qui n’est pas définie comme [sealed](../../language-reference/keywords/sealed.md), et d’autres classes peuvent hériter de votre classe et substituer vos méthodes virtuelles. Pour plus d’informations sur la création de vos propres classes, consultez [Classes et structures](../classes-and-structs/index.md). Pour plus d’informations sur l’héritage et les méthodes virtuelles, consultez [Héritage](../classes-and-structs/inheritance.md).

## <a name="types-of-literal-values"></a>Types de valeurs littérales

Dans C#, les valeurs littérales reçoivent un type du compilateur. Vous pouvez spécifier la façon dont un littéral numérique doit être typé en ajoutant une lettre à la fin du nombre. Par exemple, pour spécifier que la valeur 4,56 doit être traitée comme une valeur float, ajoutez « f » ou « F » après le nombre : `4.56f`. Si aucune lettre n’est ajoutée, le compilateur déduit un type pour le littéral. Pour plus d’informations sur les types qui peuvent être spécifiés avec des suffixes de lettres, consultez [types numériques intégraux](../../language-reference/builtin-types/integral-numeric-types.md) et [types numériques à virgule flottante](../../language-reference/builtin-types/floating-point-numeric-types.md).

Étant donné que les littéraux sont typés et que tous les types dérivent en fin de compte <xref:System.Object?displayProperty=nameWithType> , vous pouvez écrire et compiler du code tel que le code suivant :

:::code language="csharp" source="snippets/index/Program.cs" id="ConvertTypes":::

## <a name="generic-types"></a>Types génériques

Un type peut être déclaré avec un ou plusieurs *paramètres de type* qui servent d’espace réservé pour le type réel (le *type concret*) que le code client fournit lorsqu’il crée une instance du type. Ces types sont appelés *types génériques*. Par exemple, le type .NET <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> a un paramètre de type qui, par Convention, porte le nom *T*. Lorsque vous créez une instance du type, vous spécifiez le type des objets que la liste doit contenir, par exemple String :

:::code language="csharp" source="snippets/index/Program.cs" id="GenericType":::

L’utilisation du paramètre de type rend possible la réutilisation de la même classe pour contenir tout type d’élément, sans avoir à convertir chaque élément en [object](../../language-reference/builtin-types/reference-types.md). Les classes de collection génériques sont appelées *collections fortement typées* , car le compilateur connaît le type spécifique des éléments de la collection et peut déclencher une erreur au moment de la compilation si, par exemple, vous tentez d’ajouter un entier à l' `stringList` objet dans l’exemple précédent. Pour plus d’informations, consultez [Génériques](../generics/index.md).

## <a name="implicit-types-anonymous-types-and-nullable-value-types"></a>Types implicites, types anonymes et types valeur Nullable

Comme indiqué précédemment, vous pouvez attribuer implicitement un type à une variable locale (mais pas les membres de la classe) à l’aide du mot clé [var](../../language-reference/keywords/var.md). La variable reçoit toujours un type au moment de la compilation, mais le type est fourni par le compilateur. Pour plus d’informations, consultez [Variables locales implicitement typées](../classes-and-structs/implicitly-typed-local-variables.md).

Il peut être difficile de créer un type nommé pour des ensembles simples de valeurs associées que vous ne souhaitez pas stocker ou passer en dehors des limites de la méthode. Vous pouvez alors créer des *types anonymes*. Pour plus d’informations, consultez [types anonymes](../classes-and-structs/anonymous-types.md).

Les types valeur ordinaires ne peuvent pas avoir une valeur [null](../../language-reference/keywords/null.md). Toutefois, vous pouvez créer des types valeur Nullable en ajoutant un `?` après le type. Par exemple, `int?` est un type `int` qui peut également avoir la valeur [null](../../language-reference/keywords/null.md). Les types valeur Nullable sont des instances du type struct générique <xref:System.Nullable%601?displayProperty=nameWithType> . Les types valeur Nullable sont particulièrement utiles lorsque vous passez des données vers et à partir de bases de données dans lesquelles les valeurs numériques peuvent être null. Pour plus d’informations, consultez [types valeur Nullable](../../language-reference/builtin-types/nullable-value-types.md).

## <a name="compile-time-type-and-runtime-type"></a>Type au moment de la compilation et type d’exécution

Une variable peut avoir différents types au moment de la compilation et au moment de l’exécution. Le *type au moment* de la compilation est le type déclaré ou déduit de la variable dans le code source. Le *type au moment* de l’exécution est le type de l’instance référencée par cette variable. Ces deux types sont souvent les mêmes, comme dans l’exemple suivant :

:::code language="csharp" source="snippets/index/Program.cs" id="CompileTimeType":::

Dans d’autres cas, le type au moment de la compilation est différent, comme indiqué dans les deux exemples suivants :

:::code language="csharp" source="snippets/index/Program.cs" id="RuntimeTypes":::

Dans les deux exemples précédents, le type au moment de l’exécution est un `string` . Le type au moment de la compilation est `object` sur la première ligne et `IEnumerable<char>` dans la seconde.

Si les deux types sont différents pour une variable, il est important de comprendre quand le type au moment de la compilation et le type au moment de l’exécution s’appliquent. Le type au moment de la compilation détermine toutes les actions effectuées par le compilateur. Ces actions du compilateur incluent la résolution de l’appel de méthode, la résolution de surcharge et les casts implicites et explicites disponibles. Le type au moment de l’exécution détermine toutes les actions qui sont résolues au moment de l’exécution. Ces actions au moment de l’exécution incluent la répartition des appels de méthode virtuelle, l’évaluation `is` et les `switch` expressions, ainsi que d’autres API de test de type. Pour mieux comprendre comment votre code interagit avec les types, identifiez l’action qui s’applique à ce type.

## <a name="related-sections"></a>Sections connexes

Pour plus d’informations, consultez les articles suivants :

- [Cast et conversions de types](./casting-and-type-conversions.md)
- [Boxing et unboxing](./boxing-and-unboxing.md)
- [Utilisation du type dynamic](./using-type-dynamic.md)
- [Types valeur](../../language-reference/builtin-types/value-types.md)
- [Types référence](../../language-reference/keywords/reference-types.md)
- [Classes et structs](../classes-and-structs/index.md)
- [Types anonymes](../classes-and-structs/anonymous-types.md)
- [Génériques](../generics/index.md)

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C#](../../language-reference/index.md)
- [Guide de programmation C#](../index.md)
- [Conversion des types de données XML](../../../standard/data/xml/conversion-of-xml-data-types.md)
- [Types intégraux](../../language-reference/builtin-types/integral-numeric-types.md)
