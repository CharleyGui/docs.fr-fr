---
title: Types références Nullables
description: Cet article fournit une vue d’ensemble des types de référence Nullable, ajoutés en C# 8,0. Vous allez découvrir comment la fonctionnalité offre une protection contre les exceptions de référence null pour les projets nouveaux ou existants.
ms.technology: csharp-null-safety
ms.date: 04/21/2020
ms.openlocfilehash: cb9438db6364b6dc5d34f3a776d3ed7ec2e9978b
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440391"
---
# <a name="nullable-reference-types"></a>Types références Nullables

C# 8.0 introduit des **types référence nullables** et des **types référence non nullables** qui vous permettent d’établir des instructions importantes sur les propriétés de variables de type référence :

- **Une référence ne doit pas être null**. Lorsque les variables ne sont pas censées être null, le compilateur applique des règles qui garantissent que le déréférencement de ces variables est sécurisé sans avoir d’abord vérifié qu’elle n’est pas NULL :
  - La variable doit être initialisée avec une valeur non null.
  - La variable ne peut jamais se voir attribuer la valeur `null`.
- **Une référence peut être null**. Lorsque les variables peuvent être null, le compilateur applique des règles différentes pour garantir que vous avez correctement vérifié une référence null :
  - La variable peut être déréférencée seulement si le compilateur peut garantir que la valeur n’est pas null.
  - Ces variables peuvent être initialisées avec la valeur `null` par défaut et peuvent se voir attribuer la valeur `null` dans un autre code.

Cette nouvelle fonctionnalité offre des avantages significatifs par rapport à la gestion des variables de référence dans les versions antérieures de C#, où l’intention de conception ne peut pas être déterminée à partir de la déclaration de la variable. Le compilateur ne protégeait pas des exceptions de référence null pour les types référence :

- **Une référence peut être null**. Le compilateur n’émet pas d’avertissements quand une variable de type référence est initialisée à `null` ou ultérieurement assignée `null` . Le compilateur émet des avertissements lorsque ces variables sont déréférencées sans contrôles null.
- **Une référence est censée ne pas être null**. Le compilateur ne génère aucun avertissement quand les types référence sont déréférencés. Le compilateur émet des avertissements si une variable est définie sur une expression qui peut être null.

Ces avertissements sont émis au moment de la compilation. Le compilateur n’ajoute pas de contrôles null ou autres constructions d’exécution dans un contexte Nullable. Au moment de l’exécution, une référence Nullable et une référence non Nullable sont équivalentes.

En ajoutant des types référence nullables, vous pouvez déclarer votre intention plus clairement. La valeur `null` est un bon moyen de représenter qu’une variable ne fait pas référence à une valeur. N’utilisez pas cette fonctionnalité pour supprimer toutes les valeurs `null` de votre code. Déclarez plutôt votre intention au compilateur et aux autres développeurs qui lisent votre code. Quand vous déclarez votre intention, le compilateur vous informe si vous écrivez du code qui n’est pas en phase avec cette intention.

Un **type de référence nullable** est inidqué avec la même syntaxe que celle des [types valeur nullable](language-reference/builtin-types/nullable-value-types.md) : un `?` est ajouté au type de la variable. Par exemple, la déclaration de variable suivante représente une variable de chaîne nullable, `name` :

```csharp
string? name;
```

Toute variable où `?` n’est pas ajouté au nom de type est un **type de référence non Nullable**. Cela comprend toutes les variables de type référence dans le code existant lorsque vous avez activé cette fonctionnalité.

Le compilateur utilise l’analyse statique pour déterminer si une référence nullable est connue pour être non null. Le compilateur vous avertit si vous déréférencez une référence nullable quand elle est susceptible d’être null. Vous pouvez remplacer ce comportement à l’aide de l' [opérateur null-indulgent avec](language-reference/operators/null-forgiving.md) à la `!` suite d’un nom de variable. Par exemple, si vous savez que la variable `name` n’est pas null alors que le compilateur génère un avertissement, vous pouvez écrire le code suivant pour remplacer l’analyse du compilateur :

```csharp
name!.Length;
```

## <a name="nullability-of-types"></a>Nullabilité des types

Tout type référence peut avoir l’une des quatre *nullabilités* , qui décrit quand des avertissements sont générés :

- Non *null* : aucune valeur NULL ne peut être assignée aux variables de ce type. Les variables de ce type n’ont pas besoin d’être vérifiées pour savoir si elles ont la valeur null avant d’être déréférencées.
- *Nullable* : la valeur NULL peut être assignée aux variables de ce type. Le déréférencement des variables de ce type sans vérifier `null` au préalable génère un avertissement.
- *Oublie* : oublie est l’état pré-C # 8,0. Les variables de ce type peuvent être déréférencées ou attribuées sans avertissement.
- *Inconnu* : inconnu est généralement utilisé pour les paramètres de type où les contraintes n’indiquent pas au compilateur que le type doit être *Nullable* ou ne peut pas être *null*.

La nullabilité d’un type dans une déclaration de variable est contrôlée par le *contexte nullable* dans lequel la variable est déclarée.

## <a name="nullable-contexts"></a>Contextes nullables

Les contextes nullables permettent de contrôler précisément comment le compilateur interprète les variables de type référence. Le **contexte d’annotation Nullable** d’une ligne source donnée est activé ou désactivé. Vous pouvez considérer le compilateur pre-C # 8,0 comme en compilant tout votre code dans un contexte Nullable désactivé : tout type de référence peut être null. Le **contexte d’avertissements Nullable** peut également être activé ou désactivé. Le contexte d’avertissements nullable spécifie les avertissements générés par le compilateur à l’aide de son analyse de flux.

Le contexte d’annotation Nullable et le contexte d’avertissement Nullable peuvent être définis pour un projet à l’aide de l' `Nullable` élément dans votre fichier *. csproj* . Cet élément configure comment le compilateur interprète la nullabilité des types et quels avertissements sont générés. Les paramètres valides sont :

- `enable`: Le contexte d’annotation Nullable est **activé**. Le contexte d’avertissement nullable est **activé**.
  - Les variables d’un type référence, `string` par exemple, sont non nullables.  Tous les avertissements de nullabilité sont activés.
- `warnings`: Le contexte d’annotation Nullable est **désactivé**. Le contexte d’avertissement nullable est **activé**.
  - Les variables d’un type référence sont oblivious. Tous les avertissements de nullabilité sont activés.
- `annotations`: Le contexte d’annotation Nullable est **activé**. Le contexte d’avertissement nullable est **désactivé**.
  - Les variables d’un type référence, String par exemple, ne sont pas nullables. Tous les avertissements de nullabilité sont désactivés.
- `disable`: Le contexte d’annotation Nullable est **désactivé**. Le contexte d’avertissement nullable est **désactivé**.
  - Les variables d’un type référence sont oblivious, comme dans les versions antérieures de C#. Tous les avertissements de nullabilité sont désactivés.

**Exemple**  :

```xml
<Nullable>enable</Nullable>
```

Vous pouvez aussi utiliser des directives pour définir ces mêmes contextes partout dans votre projet :

- `#nullable enable`: Définit le contexte d’annotation Nullable et le contexte d’avertissement Nullable sur **activé**.
- `#nullable disable`: Définit le contexte d’annotation Nullable et le contexte d’avertissement Nullable sur **désactivé**.
- `#nullable restore`: Restaure le contexte d’annotation Nullable et le contexte d’avertissement Nullable aux paramètres du projet.
- `#nullable disable warnings`: Affectez la valeur **désactivé** au contexte d’avertissement Nullable.
- `#nullable enable warnings`: Affectez la valeur **activé** au contexte d’avertissement Nullable.
- `#nullable restore warnings`: Restaure le contexte d’avertissement Nullable aux paramètres du projet.
- `#nullable disable annotations`: Affectez la valeur **désactivé** au contexte d’annotation Nullable.
- `#nullable enable annotations`: Affectez la valeur **activé** au contexte d’annotation Nullable.
- `#nullable restore annotations`: Restaure le contexte d’avertissement d’annotation aux paramètres du projet.

Par défaut, l’annotation Nullable et les contextes d’avertissement sont **désactivés** , y compris les nouveaux projets. Cela signifie que votre code existant est compilé sans modification et sans générer de nouveaux avertissements.

Ces options fournissent deux stratégies distinctes pour [mettre à jour une base de code existante](nullable-migration-strategies.md) afin d’utiliser des types de référence Nullable.

## <a name="nullable-annotation-context"></a>Contexte d’annotation nullable

Le compilateur utilise les règles suivantes dans un contexte d’annotation nullable désactivé :

- Vous ne pouvez pas déclarer de références nullables dans un contexte désactivé.
- Une valeur NULL peut être assignée à toutes les variables de référence.
- Aucun avertissement n’est généré lorsqu’une variable d’un type référence est déréférencée.
- L’opérateur null-forgiving ne peut pas être utilisé dans un contexte désactivé.

Le comportement est le même que dans les versions précédentes de C#.

Le compilateur utilise les règles suivantes dans un contexte d’annotation nullable activé :

- Toute variable d’un type référence est une **référence non nullable**.
- Toute référence non nullable peut être déréférencée sans problème.
- Tout type référence nullable (indiqué par `?` après le type dans la déclaration de variable) peut être null. L’analyse statique détermine si la valeur est connue pour être non null lorsqu’elle est déréférencée. Si ce n’est pas le cas, le compilateur vous avertit.
- Vous pouvez utiliser l’opérateur null-forgiving pour déclarer qu’une référence nullable n’est pas null.

Dans un contexte d’annotation nullable activé, le caractère `?` ajouté à un type référence déclare un **type référence nullable**. L' **opérateur null-indulgent avec** `!` peut être ajouté à une expression pour déclarer que l’expression n’est pas null.

## <a name="nullable-warning-context"></a>Contexte d’avertissement nullable

Le contexte d’avertissement nullable est différent du contexte d’annotation nullable. Des avertissements peuvent être activés, même lorsque les nouvelles annotations sont désactivées. Le compilateur utilise l’analyse de flux statique pour déterminer l’ **état null** de toutes les références. L’état null est **non null** ou **peut-être null** quand le *contexte d’avertissement nullable* n’est pas **désactivé**. Si vous déréférencez une référence quand le compilateur a déterminé qu’elle est **peut-être null** , le compilateur vous avertit. L’état d’une référence est **peut-être null** , sauf si le compilateur peut déterminer une des deux conditions :

1. Une valeur non null a été assignée définitivement à la variable.
1. La variable ou l’expression a été vérifiée pour savoir si sa valeur est null avant de la référencer.

Le compilateur génère des avertissements lorsque vous déréférencez une variable ou une expression qui est **peut-être null** dans un contexte d’avertissement Nullable. En outre, le compilateur génère des avertissements quand une variable de type référence non null reçoit une variable ou une expression de type **null** dans un contexte d’annotation Nullable activé.

## <a name="attributes-describe-apis"></a>Les attributs décrivent des API

Vous ajoutez des attributs aux API qui fournissent au compilateur plus d’informations sur le moment où les arguments ou les valeurs de retour peuvent ou ne peuvent pas être null. Vous pouvez en savoir plus sur ces attributs dans notre article dans la référence du langage couvrant les [attributs Nullable](language-reference/attributes/nullable-analysis.md). Ces attributs sont ajoutés aux bibliothèques .NET sur les versions actuelles et à venir. Les API les plus couramment utilisées sont mises à jour en premier.

## <a name="known-pitfalls"></a>Pièges connus

Les tableaux et les structs qui contiennent des types référence sont des pièges connus dans la fonctionnalité de types référence Nullable.

### <a name="structs"></a>Structures

Un struct qui contient des types référence n’acceptant pas les valeurs NULL permet de l’assigner `default` sans avertissement. Prenons l’exemple suivant :

```csharp
using System;

#nullable enable

public struct Student
{
    public string FirstName;
    public string? MiddleName;
    public string LastName;
}

public static class Program
{
    public static void PrintStudent(Student student)
    {
        Console.WriteLine($"First name: {student.FirstName.ToUpper()}");
        Console.WriteLine($"Middle name: {student.MiddleName.ToUpper()}");
        Console.WriteLine($"Last name: {student.LastName.ToUpper()}");
    }

    public static void Main() => PrintStudent(default);
}
```

Dans l’exemple précédent, il n’y a pas d’avertissement dans `PrintStudent(default)` tandis que les types de référence non Nullable `FirstName` et `LastName` sont null.

Un autre cas plus courant est lorsque vous traitez des structs génériques. Prenons l’exemple suivant :

```csharp
#nullable enable

public struct Foo<T>
{
    public T Bar { get; set; }
}

public static class Program
{
    public static void Main()
    {
        string s = default(Foo<string>).Bar;
    }
}
```

Dans l’exemple précédent, la propriété `Bar` va être `null` au moment de l’exécution et elle est assignée à une chaîne non Nullable sans avertissement.

### <a name="arrays"></a>Tableaux

Les tableaux sont également un piège connu dans les types de référence Nullable. Prenons l’exemple suivant qui ne génère pas d’avertissements :

```csharp
using System;

#nullable enable

public static class Program
{
    public static void Main()
    {
        string[] values = new string[10];
        string s = values[0];
        Console.WriteLine(s.ToUpper());
    }
}
```

Dans l’exemple précédent, la déclaration du tableau indique qu’elle contient des chaînes qui n’acceptent pas les valeurs NULL, tandis que ses éléments sont tous initialisés à la valeur null. Ensuite, `s` une valeur null est assignée à la variable (le premier élément du tableau). Enfin, la variable `s` est déréférencée et provoque une exception Runtime.

## <a name="see-also"></a>Voir aussi

- [Spécification des types de référence Nullable Draft](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)
- [Tutoriel d’introduction aux références nullables](tutorials/nullable-reference-types.md)
- [Migration d’une base de code existante vers des références nullables](tutorials/upgrade-to-nullable-references.md)
- [-Nullable (option du compilateur C#)](language-reference/compiler-options/nullable-compiler-option.md)
