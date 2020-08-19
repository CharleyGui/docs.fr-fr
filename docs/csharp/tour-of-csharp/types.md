---
title: 'Définir des types et leurs membres-visite guidée de C #'
description: Les blocs de construction des programmes sont des types. Découvrez comment créer des classes, des structs, des interfaces, etc. en C#.
ms.date: 08/06/2020
ms.openlocfilehash: efd353fe8c1e6a57952bcb2586a05ad38ecd52b9
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559113"
---
# <a name="types-and-members"></a>Types et membres

## <a name="classes-and-objects"></a>Classes et objets

Les *Classes* sont le type le plus fondamental de C#. Une classe est une structure de données qui combine l’état (champs) et les actions (méthodes et autres fonctions membres) en une seule unité. Une classe fournit une définition pour les *instances* de la classe, également appelées *objets*. Les classes prennent en charge *l’héritage* et le *polymorphisme*, des mécanismes par lesquels les *classes dérivées* peuvent étendre et spécialiser les *classes de base*.

Les nouvelles classes sont créées à l’aide des déclarations de classe. Une déclaration de classe commence par un en-tête. L’en-tête spécifie :

- Attributs et modificateurs de la classe
- Nom de la classe.
- Classe de base (en cas d’héritage d’une [classe de base](#base-classes))
- Interfaces implémentées par la classe.

L’en-tête est suivi par le corps de la classe, qui se compose d’une liste de déclarations de membres écrites entre les délimiteurs `{` et `}`.

Le code suivant illustre une déclaration d’une classe simple nommée `Point` :

:::code language="csharp" source="./snippets/shared/Types.cs" ID="PointClass":::

Les instances de classes sont créées à l’aide de l’opérateur `new`, qui alloue la mémoire pour une nouvelle instance, appelle un constructeur pour initialiser l’instance et retourne une référence à l’instance. Les instructions suivantes créent deux `Point` objets et stockent les références à ces objets dans deux variables :

:::code language="csharp" source="./snippets/shared/Types.cs" ID="CreatePoints":::

La mémoire occupée par un objet est automatiquement libérée lorsque l’objet n’est plus accessible. Il n’est ni nécessaire ni possible de libérer explicitement des objets en C#.

### <a name="type-parameters"></a>Paramètres de type

Les classes génériques définissent les [***paramètres de type***](../programming-guide/generics/index.md). Les paramètres de type sont une liste de noms de paramètre de type entre crochets pointus. Les paramètres de type suivent le nom de la classe. Les paramètres de type peuvent ensuite être utilisés dans le corps des déclarations de classe pour définir les membres de la classe. Dans l’exemple suivant, les paramètres de type de `Pair` sont `TFirst` et `TSecond` :

:::code language="csharp" source="./snippets/shared/Types.cs" ID="DefinePairClass":::

Un type de classe déclaré pour prendre des paramètres de type est appelé un *type de classe générique*. Les types struct, interface et Delegate peuvent également être génériques.
Lorsque la classe générique est utilisée, des arguments de type doivent être fournis pour chacun des paramètres de type :

:::code language="csharp" source="./snippets/shared/Types.cs" ID="CreatePairObject":::

Un type générique avec des arguments de type fournis, comme `Pair<int,string>` ci-dessus, est appelé un *type construit*.

### <a name="base-classes"></a>Classes de base

Une déclaration de classe peut spécifier une classe de base. Suivez les paramètres Name et type de la classe avec le signe deux-points et le nom de la classe de base. L’omission d’une spécification de classe de base revient à dériver du type `object`. Dans l’exemple suivant, la classe de base de `Point3D` est `Point` . Dans le premier exemple, la classe de base de `Point` est `object` :

:::code language="csharp" source="./snippets/shared/Types.cs" ID="Create3DPoint":::

Une classe hérite des membres de sa classe de base. L’héritage signifie qu’une classe contient implicitement tous les membres de sa classe de base. Une classe n’hérite pas de l’instance et des constructeurs statiques, et du finaliseur. Une classe dérivée peut ajouter de nouveaux membres aux membres qu’elle hérite, mais elle ne peut pas supprimer la définition d’un membre hérité. Dans l’exemple précédent, `Point3D` hérite des `X` `Y` membres et de `Point` , et chaque `Point3D` instance contient trois propriétés, `X` , `Y` et `Z` .

Il existe une conversion implicite d’un type de classe vers un de ses types de classe de base. Une variable d’un type de classe peut référencer une instance de cette classe ou une instance de toute classe dérivée. Par exemple, pour les déclarations de classe précédentes, une variable de type `Point` peut faire référence à un objet `Point` ou `Point3D` :

:::code language="csharp" source="./snippets/shared/Types.cs" ID="ImplicitCastToBase":::

## <a name="structs"></a>Structures

Les classes définissent des types qui prennent en charge l’héritage et le polymorphisme. Elles vous permettent de créer des comportements sophistiqués basés sur des hiérarchies de classes dérivées. En revanche, les types [***struct***](../language-reference/builtin-types/struct.md) sont des types plus simples dont l’objectif principal est de stocker des valeurs de données. Les structs ne peuvent pas déclarer un type de base ; ils dérivent implicitement de <xref:System.ValueType?displayProperty=nameWithType> . Vous ne pouvez pas dériver `struct` d’autres types à partir d’un `struct` type. Ils sont implicitement sealed.

:::code language="csharp" source="./snippets/shared/Types.cs" ID="PointStruct":::

## <a name="interfaces"></a>Interfaces

Une [***interface***](../programming-guide/interfaces/index.md) définit un contrat qui peut être implémenté par des classes et des structs. Une interface peut contenir des méthodes, des propriétés, des événements et des indexeurs. En général, une interface ne fournit pas d’implémentations des membres qu’elle définit. elle spécifie simplement les membres qui doivent être fournis par les classes ou les structs qui implémentent l’interface.

Les interfaces peuvent utiliser ***l’héritage multiple***. Dans l’exemple suivant, l’interface `IComboBox` hérite à la fois de `ITextBox` et `IListBox`.

:::code language="csharp" source="./snippets/shared/Types.cs" ID="FirstInterfaces":::

Les classes et les structs peuvent implémenter plusieurs interfaces. Dans l’exemple suivant, la classe `EditBox` implémente à la fois `IControl` et `IDataBound`.

:::code language="csharp" source="./snippets/shared/Types.cs" ID="ImplementInterfaces":::

Lorsqu’une classe ou un struct implémente une interface spécifique, les instances de cette classe ou struct peuvent être converties implicitement en ce type d’interface. Par exemple

:::code language="csharp" source="./snippets/shared/Types.cs" ID="UseInterfaces":::

## <a name="enums"></a>Énumérations

Un type [***enum***](../language-reference/builtin-types/enum.md) définit un ensemble de valeurs constantes. L’exemple suivant `enum` déclare des constantes qui définissent des légumes racines différents :

:::code language="csharp" source="./snippets/shared/Types.cs" ID="EnumDeclaration":::

Vous pouvez également définir un `enum` à utiliser en combinaison comme indicateurs. La déclaration suivante déclare un jeu d’indicateurs pour les quatre saisons. Toute combinaison de saisons peut être appliquée, y compris une `All` valeur qui inclut toutes les saisons :

:::code language="csharp" source="./snippets/shared/Types.cs" ID="FlagsEnumDeclaration":::

L’exemple suivant montre des déclarations des deux énumérations précédentes :

:::code language="csharp" source="./snippets/shared/Types.cs" ID="UsingEnums":::

## <a name="nullable-types"></a>Types Nullable

Les variables de tout type peuvent être déclarées comme n' ***acceptant pas les valeurs NULL*** ou ***null***. Une variable Nullable peut contenir une `null` valeur supplémentaire, ce qui n’indique aucune valeur. Les types valeur Nullable (structs ou enums) sont représentés par <xref:System.Nullable%601?displayProperty=nameWithType> . Les types référence non Nullable et Nullable sont représentés par le type référence sous-jacent. La distinction est représentée par les métadonnées lues par le compilateur et certaines bibliothèques. Le compilateur fournit des avertissements quand des références Nullable sont déréférencées sans avoir d’abord vérifié leur valeur par rapport à `null` . Le compilateur fournit également des avertissements lorsque des références non Nullable se voient affecter une valeur qui peut être `null` . L’exemple suivant déclare un ***entier Nullable***, en l’initialisant à `null` . Ensuite, il définit la valeur sur `5` . Il illustre le même concept avec une ***chaîne Nullable***. Pour plus d’informations, consultez [types valeur Nullable](../language-reference/builtin-types/nullable-value-types.md) et [types référence Nullable](../nullable-references.md).

:::code language="csharp" source="./snippets/shared/Types.cs" ID="DeclareNullable":::

## <a name="tuples"></a>Tuples

C# prend en charge les [***tuples***](../language-reference/builtin-types/value-tuples.md), qui fournit une syntaxe concise pour regrouper plusieurs éléments de données dans une structure de données légère. Vous instanciez un tuple en déclarant les types et les noms des membres entre `(` et `)` , comme indiqué dans l’exemple suivant :

:::code language="csharp" source="./snippets/shared/Types.cs" ID="DeclareTuples":::

Les tuples offrent une alternative à la structure de données avec plusieurs membres, sans utiliser les blocs de construction décrits dans l’article suivant.

>[!div class="step-by-step"]
>[Précédent](index.md) 
> [Suivant](program-building-blocks.md)
