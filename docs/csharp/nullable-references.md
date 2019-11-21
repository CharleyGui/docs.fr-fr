---
title: Types références Nullables
description: Cet article fournit une vue d’ensemble des types de référence Nullable C# , ajoutés dans 8,0. Vous allez découvrir comment la fonctionnalité offre une protection contre les exceptions de référence null pour les projets nouveaux ou existants.
ms.technology: csharp-null-safety
ms.date: 02/19/2019
ms.openlocfilehash: ded7234ecb746ba03ba59505b7189272886f1cbf
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737839"
---
# <a name="nullable-reference-types"></a>Types références Nullables

C# 8.0 introduit des **types référence nullables** et des **types référence non nullables** qui vous permettent d’établir des instructions importantes sur les propriétés de variables de type référence :

- **Une référence n’est pas censée être null**. Lorsque les variables ne sont pas censées être null, le compilateur applique des règles qui garantissent que vous pouvez sans problème déréférencer ces variables sans avoir d’abord à vérifier qu’elles ne sont pas null :
  - La variable doit être initialisée avec une valeur non null.
  - La variable ne peut jamais se voir attribuer la valeur `null`.
- **Une référence peut être null**. Lorsque les variables peuvent être null, le compilateur applique des règles différentes pour garantir que vous avez correctement vérifié une référence null :
  - La variable peut être déréférencée seulement si le compilateur peut garantir que la valeur n’est pas null.
  - Ces variables peuvent être initialisées avec la valeur `null` par défaut et peuvent se voir attribuer la valeur `null` dans un autre code.

Cette nouvelle fonctionnalité fournit des avantages significatifs sur la gestion des variables de référence dans les versions antérieures de C# où l’intention de conception ne pouvait pas être déterminée à partir de la déclaration de variable. Le compilateur ne protégeait pas des exceptions de référence null pour les types référence :

- **Une référence peut être null**. Aucun avertissement n’est généré quand un type référence est initialisé avec la valeur null ou se voit attribuer la valeur null par la suite.
- **Une référence est censée ne pas être null**. Le compilateur ne génère aucun avertissement quand les types référence sont déréférencés. (Avec des références nullables, le compilateur génère des avertissements si vous déréférencez une variable susceptible d’être null).

En ajoutant des types référence nullables, vous pouvez déclarer votre intention plus clairement. La valeur `null` est un bon moyen de représenter qu’une variable ne fait pas référence à une valeur. N’utilisez pas cette fonctionnalité pour supprimer toutes les valeurs `null` de votre code. Déclarez plutôt votre intention au compilateur et aux autres développeurs qui lisent votre code. Quand vous déclarez votre intention, le compilateur vous informe si vous écrivez du code qui n’est pas en phase avec cette intention.

Un **type de référence nullable** est indiqué avec la même syntaxe que celle des [types valeur nullable](language-reference/builtin-types/nullable-value-types.md) : un `?` est ajouté au type de la variable. Par exemple, la déclaration de variable suivante représente une variable de chaîne nullable, `name` :

```csharp
string? name;
```

Toute variable où `?` n’est pas ajouté au nom de type est un **type référence non nullable**. Cela comprend toutes les variables de type référence du code existant si vous avez activé cette fonctionnalité.

Le compilateur utilise l’analyse statique pour déterminer si une référence nullable est connue pour être non null. Le compilateur vous avertit si vous déréférencez une référence nullable quand elle est susceptible d’être null. Vous pouvez remplacer ce comportement à l’aide de l' [opérateur null-indulgent avec](language-reference/operators/null-forgiving.md) `!` à la suite d’un nom de variable. Par exemple, si vous savez que la variable `name` n’est pas null alors que le compilateur génère un avertissement, vous pouvez écrire le code suivant pour remplacer l’analyse du compilateur :

```csharp
name!.Length;
```

## <a name="nullability-of-types"></a>Nullabilité des types

Tout type référence peut avoir l’une des quatre *nullabilités*, qui décrit quand des avertissements sont générés :

- Non *null*: aucune valeur NULL ne peut être assignée aux variables de ce type. Les variables de ce type n’ont pas besoin d’être vérifiées pour savoir si elles ont la valeur null avant d’être déréférencées.
- *Nullable*: la valeur NULL peut être assignée aux variables de ce type. Le déréférencement des variables de ce type sans vérifier `null` au préalable génère un avertissement.
- *Oublie*: il s’agit de l'C# état antérieur à 8,0. Les variables de ce type peuvent être déréférencées ou attribuées sans avertissement.
- *Inconnu*: c’est généralement le cas pour les paramètres de type où les contraintes n’indiquent pas au compilateur que le type doit être *Nullable* ou ne peut pas être *null*.

La nullabilité d’un type dans une déclaration de variable est contrôlée par le *contexte nullable* dans lequel la variable est déclarée.

## <a name="nullable-contexts"></a>Contextes nullables

Les contextes nullables permettent de contrôler précisément comment le compilateur interprète les variables de type référence. Le **contexte d’annotation Nullable** d’une ligne source donnée est activé ou désactivé. Vous pouvez considérer le compilateur antérieur àC# 8,0 comme en compilant tout votre code dans un contexte Nullable désactivé : tout type de référence peut avoir la valeur null. Le **contexte d’avertissements Nullable** peut également être activé ou désactivé. Le contexte d’avertissements nullable spécifie les avertissements générés par le compilateur à l’aide de son analyse de flux.

Le contexte d’annotation Nullable et le contexte d’avertissement Nullable peuvent être définis pour un projet à l’aide de l’élément `Nullable` dans votre fichier *. csproj* . Cet élément configure comment le compilateur interprète la nullabilité des types et quels avertissements sont générés. Les paramètres valides sont :

- `enable` : le contexte d’annotation Nullable est **activé**. Le contexte d’avertissement nullable est **activé**.
  - Les variables d’un type référence, `string` par exemple, sont non nullables.  Tous les avertissements de nullabilité sont activés.
- `warnings` : le contexte d’annotation Nullable est **désactivé**. Le contexte d’avertissement nullable est **activé**.
  - Les variables d’un type référence sont oblivious. Tous les avertissements de nullabilité sont activés.
- `annotations` : le contexte d’annotation Nullable est **activé**. Le contexte d’avertissement nullable est **désactivé**.
  - Les variables d’un type référence, String par exemple, ne sont pas nullables. Tous les avertissements de nullabilité sont désactivés.
- `disable` : le contexte d’annotation Nullable est **désactivé**. Le contexte d’avertissement nullable est **désactivé**.
  - Les variables d’un type référence sont oblivious, comme dans les versions antérieures de C#. Tous les avertissements de nullabilité sont désactivés.

**Exemple** :

```xml
<Nullable>enable</Nullable>
```

Vous pouvez aussi utiliser des directives pour définir ces mêmes contextes partout dans votre projet :

- `#nullable enable` : définit le contexte d’annotation Nullable et le contexte d’avertissement Nullable sur **activé**.
- `#nullable disable` : définit le contexte d’annotation Nullable et le contexte d’avertissement Nullable sur **désactivé**.
- `#nullable restore` : restaure le contexte d’annotation Nullable et le contexte d’avertissement Nullable aux paramètres du projet.
- `#nullable disable warnings` : définissez le contexte d’avertissement Nullable sur **désactivé**.
- `#nullable enable warnings` : définissez le contexte d’avertissement Nullable sur **activé**.
- `#nullable restore warnings` : restaure le contexte d’avertissement Nullable aux paramètres du projet.
- `#nullable disable annotations` : définissez le contexte d’annotation Nullable sur **désactivé**.
- `#nullable enable annotations` : définissez le contexte d’annotation Nullable sur **activé**.
- `#nullable restore annotations` : restaure le contexte d’avertissement d’annotation sur les paramètres du projet.

Par défaut, l’annotation Nullable et les contextes d’avertissement sont **désactivés**. Cela signifie que votre code existant est compilé sans modification et sans générer de nouveaux avertissements.

## <a name="nullable-annotation-context"></a>Contexte d’annotation nullable

Le compilateur utilise les règles suivantes dans un contexte d’annotation nullable désactivé :

- Vous ne pouvez pas déclarer de références nullables dans un contexte désactivé.
- Toutes les variables de référence peuvent se voir attribuer la valeur null.
- Aucun avertissement n’est généré lorsqu’une variable d’un type référence est déréférencée.
- L’opérateur null-forgiving ne peut pas être utilisé dans un contexte désactivé.

Le comportement est le même que dans les versions précédentes de C#.

Le compilateur utilise les règles suivantes dans un contexte d’annotation nullable activé :

- Toute variable d’un type référence est une **référence non nullable**.
- Toute référence non nullable peut être déréférencée sans problème.
- Tout type référence nullable (indiqué par `?` après le type dans la déclaration de variable) peut être null. L’analyse statique détermine si la valeur est connue pour être non null quand elle est déréférencée. Si ce n’est pas le cas, le compilateur vous avertit.
- Vous pouvez utiliser l’opérateur null-forgiving pour déclarer qu’une référence nullable n’est pas null.

Dans un contexte d’annotation nullable activé, le caractère `?` ajouté à un type référence déclare un **type référence nullable**. L' **opérateur null-indulgent avec** `!` peut être ajouté à une expression pour déclarer que l’expression n’a pas la valeur null.

## <a name="nullable-warning-context"></a>Contexte d’avertissement nullable

Le contexte d’avertissement nullable est différent du contexte d’annotation nullable. Des avertissements peuvent être activés, même lorsque les nouvelles annotations sont désactivées. Le compilateur utilise l’analyse de flux statique pour déterminer l’**état null** de toutes les références. L’état null est **non null** ou **peut-être null** quand le *contexte d’avertissement nullable* n’est pas **désactivé**. Si vous déréférencez une référence quand le compilateur a déterminé qu’elle est **peut-être null**, le compilateur vous avertit. L’état d’une référence est **peut-être null**, sauf si le compilateur peut déterminer une des deux conditions :

1. La variable s’est vu définitivement attribuer une valeur non null.
1. La variable ou l’expression a été vérifiée pour savoir si sa valeur est null avant de la référencer.

Le compilateur génère des avertissements chaque fois que vous déréférencez une variable ou une expression dans un état **peut-être null** lorsque le contexte d’avertissement Nullable est activé. En outre, des avertissements sont générés quand une variable ou une expression **null peut être** assignée à un type référence non null dans un contexte d’annotation activé pour la valeur null.

## <a name="see-also"></a>Voir aussi

- [Spécification des types de référence Nullable Draft](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)
- [Tutoriel d’introduction aux références nullables](tutorials/nullable-reference-types.md)
- [Migration d’une base de code existante vers des références nullables](tutorials/upgrade-to-nullable-references.md)
