---
title: Utiliser des indexeurs - Guide de programmation C#
description: Découvrez comment déclarer et utiliser un indexeur pour une classe, un struct ou une interface en C#. Cet article comprend un exemple de code.
ms.date: 07/15/2020
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: a8a9e05c1d2e44841177a924c6ff51c6c9e6a05a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301864"
---
# <a name="using-indexers-c-programming-guide"></a>Utiliser des indexeurs (Guide de programmation C#)

Les indexeurs sont une pratique syntaxique qui vous permet de créer une [classe](../../language-reference/keywords/class.md), un [struct](../../language-reference/builtin-types/struct.md)ou une [interface](../../language-reference/keywords/interface.md) que les applications clientes peuvent accéder en tant que tableau. Le compilateur génère une `Item` propriété (ou une propriété autre que nommée si <xref:System.Runtime.CompilerServices.IndexerNameAttribute> est présent) et les méthodes d’accesseur appropriées. Le plus souvent, les indexeurs sont implémentés dans les types dont l’objectif premier est d’encapsuler une collection ou un tableau interne. Par exemple, supposons que vous ayez une classe `TempRecord` qui représente la température en degrés Fahrenheit enregistrée à 10 heures différentes pendant une période de 24 heures. La classe contient un `temps` tableau de type `float[]` pour stocker les valeurs de température. En implémentant un indexeur dans cette classe, les clients peuvent accéder aux températures dans une instance `TempRecord` sous la forme `float temp = tempRecord[4]` et non sous la forme `float temp = tempRecord.temps[4]`. La notation de l’indexeur simplifie non seulement la syntaxe des applications clientes ; elle rend également la classe et son objectif plus intuitifs à comprendre pour d’autres développeurs.

Pour déclarer un indexeur sur une classe ou un struct, utilisez le mot clé [this](../../language-reference/keywords/this.md), comme dans l’exemple suivant :

```csharp
// Indexer declaration
public int this[int index]
{
    // get and set accessors
}
```

> [!IMPORTANT]
> La déclaration d’un indexeur génère automatiquement une propriété nommée `Item` sur l’objet. La `Item` propriété n’est pas directement accessible à partir de l' [expression d’accès au membre](../../language-reference/operators/member-access-operators.md#member-access-expression-)d’instance. En outre, si vous ajoutez votre propre `Item` propriété à un objet avec un indexeur, vous obtiendrez une [Erreur du compilateur CS0102](../../misc/cs0102.md). Pour éviter cette erreur, utilisez l' <xref:System.Runtime.CompilerServices.IndexerNameAttribute> indexeur renommez-le comme indiqué ci-dessous.

## <a name="remarks"></a>Notes

Le type d’un indexeur et le type de ses paramètres doivent être au moins aussi accessibles que l’indexeur lui-même. Pour plus d’informations sur les niveaux d’accessibilité, consultez [Modificateurs d’accès](../../language-reference/keywords/access-modifiers.md).

Pour plus d’informations sur l’utilisation d’indexeurs avec une interface, consultez [Indexeurs d’interface](./indexers-in-interfaces.md).

La signature d’un indexeur est composée du nombre et des types de ses paramètres formels. Elle ne comporte ni le type de l’indexeur ni le nom des paramètres formels. Si vous déclarez plusieurs indexeurs dans la même classe, ils doivent avoir des signatures différentes.

Une valeur d’indexeur n’est pas classée comme variable ; vous ne pouvez donc pas la passer comme paramètre [ref](../../language-reference/keywords/ref.md) ou [out](../../language-reference/keywords/out-parameter-modifier.md).

Pour affecter à l’indexeur un nom exploitable dans d’autres langages, utilisez <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, comme dans l’exemple suivant :

```csharp
// Indexer declaration
[System.Runtime.CompilerServices.IndexerName("TheItem")]
public int this[int index]
{
    // get and set accessors
}
```

Cet indexeur porte le nom `TheItem` , car il est substitué par l’attribut de nom de l’indexeur. Par défaut, le nom de l’indexeur est `Item` .

## <a name="example-1"></a>Exemple 1

L’exemple suivant montre comment déclarer un champ de tableau privé `temps`, et un indexeur. L’indexeur permet d’accéder directement à l’instance `tempRecord[i]`. Comme alternative à l’utilisation de l’indexeur, vous pouvez déclarer le tableau comme membre [public](../../language-reference/keywords/public.md) et accéder directement à ses membres, `tempRecord.temps[i]`.

:::code language="csharp" source="snippets/Temperatures/TempRecord.cs":::

Notez que quand l’accès à un indexeur est évalué, par exemple dans une instruction `Console.Write`, l’accesseur [get](../../language-reference/keywords/get.md) est appelé. C’est pourquoi une erreur de compilation se produit s’il n’existe aucun accesseur `get`.

:::code language="csharp" source="snippets/Temperatures/Program.cs":::

## <a name="indexing-using-other-values"></a>Indexation avec d’autres valeurs

C# ne limite pas le type de paramètre d’indexeur au type entier. Par exemple, il peut être utile d’utiliser une chaîne avec un indexeur. Il est possible d’implémenter un tel indexeur en recherchant la chaîne dans la collection et en retournant la valeur appropriée. Comme les accesseurs peuvent être surchargés, les versions de chaîne et d’entier peuvent coexister.

## <a name="example-2"></a>Exemple 2

L’exemple suivant déclare une classe qui stocke les jours de la semaine. Un accesseur `get` prend une chaîne, le nom d’un jour, et retourne l’entier correspondant. Par exemple, « Sunday » retourne 0, « Monday » retourne 1 et ainsi de suite.

:::code language="csharp" source="snippets/StringIndexers/DayCollection.cs":::

### <a name="consuming-example-2"></a>Utilisation de l’exemple 2

:::code language="csharp" source="snippets/StringIndexers/Program.cs":::

## <a name="example-3"></a>Exemple 3

L’exemple suivant déclare une classe qui stocke les jours de la semaine à l’aide de l' <xref:System.DayOfWeek?displayProperty=fullName> énumération. Un `get` accesseur prend un `DayOfWeek` , la valeur d’un jour et retourne l’entier correspondant. Par exemple, `DayOfWeek.Sunday` retourne 0, `DayOfWeek.Monday` retourne 1, et ainsi de suite.

:::code language="csharp" source="snippets/DayOfWeekIndexers/DayOfWeekCollection.cs":::

### <a name="consuming-example-3"></a>Utilisation de l’exemple 3

:::code language="csharp" source="snippets/DayOfWeekIndexers/Program.cs":::

## <a name="robust-programming"></a>Programmation fiable

La sécurité et la fiabilité des indexeurs peuvent être améliorées de deux manières principales :

- N’oubliez pas d’incorporer une stratégie de gestion des erreurs au cas où le code client passerait une valeur d’index non valide. Dans le premier exemple décrit plus haut dans cette rubrique, la classe TempRecord fournit une propriété Length qui permet au code client de vérifier l’entrée avant de la passer à l’indexeur. Vous pouvez également placer le code de gestion des erreurs à l’intérieur de l’indexeur lui-même. N’oubliez pas d’indiquer aux utilisateurs toutes les exceptions que vous levez dans un accesseur d’indexeur.

- Définissez pour les accesseurs [get](../../language-reference/keywords/get.md) et [set](../../language-reference/keywords/set.md) une accessibilité aussi restrictive que possible. Cela est particulièrement important dans le cas de l’accesseur `set`. Pour plus d’informations, consultez [Restriction d’accessibilité de l’accesseur](../classes-and-structs/restricting-accessor-accessibility.md).

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Indexeurs](./index.md)
- [Propriétés](../classes-and-structs/properties.md)
