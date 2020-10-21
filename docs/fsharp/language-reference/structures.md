---
title: Structures
description: 'En savoir plus sur la structure F #, un type d’objet compact est souvent plus efficace qu’une classe pour les types avec une petite quantité de données et un comportement simple.'
ms.date: 05/16/2016
ms.openlocfilehash: 1e9652cc4776e4d1d52eb20e41b6dd87a6c5ba05
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223821"
---
# <a name="structures"></a>Structures

Une *structure* est un type d’objet compact qui peut être plus efficace qu’une classe pour les types qui ont une petite quantité de données et un comportement simple.

## <a name="syntax"></a>Syntaxe

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    struct
        type-definition-elements-and-members
    end
// or
[ attributes ]
[<StructAttribute>]
type [accessibility-modifier] type-name =
    type-definition-elements-and-members
```

## <a name="remarks"></a>Notes

Les structures sont des *types valeur*, ce qui signifie qu’elles sont stockées directement sur la pile ou, lorsqu’elles sont utilisées en tant que champs ou éléments de tableau, inline dans le type parent. Contrairement aux classes et aux enregistrements, les structures ont une sémantique de passage par valeur. Cela signifie qu'elles sont principalement utilisées pour les petits volumes de données qui sont fréquemment sollicités et copiés.

Dans la syntaxe précédente, deux formes sont présentes. La première n'est pas la syntaxe simplifiée, mais elle est néanmoins fréquemment utilisée, car quand vous employez les mots clés `struct` et `end`, vous pouvez omettre l'attribut `StructAttribute` qui apparaît dans la seconde forme. Vous pouvez abréger `StructAttribute` en `Struct`.

Les *éléments Type-Definition-Elements-et-members* dans la syntaxe précédente représentent des déclarations et des définitions de membre. Les structures peuvent avoir des constructeurs et des champs modifiables et non modifiables, et peuvent déclarer des membres et des implémentations d'interface. Pour plus d’informations, consultez [membres](./members/index.md).

Les structures ne peuvent pas participer à l’héritage, ne peuvent pas contenir les liaisons `let` ou `do`, et ne peuvent pas comporter de manière récursive les champs de leur propre type (bien qu’elles puissent contenir des cellules de référence qui référencent leur propre type).

Étant donné que les structures n’autorisent pas les liaisons `let`, vous devez déclarer leurs champs à l’aide du mot clé `val`. Le mot clé `val` définit un champ et son type, mais n'autorise pas l'initialisation. À la place, les déclarations `val` sont initialisées à la valeur zéro ou null. Pour cette raison, les structures ayant un constructeur implicite (c’est-à-dire les paramètres qui sont fournis immédiatement après le nom de la structure dans la déclaration) requièrent que les déclarations `val` soient annotées avec l’attribut `DefaultValue`. Les structures ayant un constructeur défini prennent toujours en charge l'initialisation à zéro. Par conséquent, l'attribut `DefaultValue` est une déclaration selon laquelle une telle valeur égale à zéro est valide pour le champ. Les constructeurs implicites pour les structures n'exécutent aucune action, car les liaisons `let` et `do` ne sont pas autorisées sur le type, mais les valeurs de paramètre de constructeur implicite passées sont disponibles en tant que champs privés.

Les constructeurs explicites peuvent impliquer l'initialisation des valeurs de champ. Quand une structure a un constructeur explicite, elle prend toujours en charge l'initialisation à zéro ; toutefois, vous n'utilisez pas l'attribut `DefaultValue` sur les déclarations `val`, car il est en conflit avec le constructeur explicite. Pour plus d’informations sur `val` les déclarations, consultez [champs explicites : le `val` mot clé](./members/explicit-fields-the-val-keyword.md).

Les attributs et les modificateurs d'accessibilité sont autorisés sur les structures et suivent les mêmes règles que celles des autres types. Pour plus d’informations, consultez [attributs](attributes.md) et [Access Control](access-control.md).

Les exemples de code suivants illustrent des définitions de structure.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="byreflike-structs"></a>Structs ByRefLike

Vous pouvez définir vos propres structs qui peuvent adhérer à `byref` des sémantiques de type : pour plus d’informations, consultez [types ByRef](byrefs.md) . Cette opération s’effectue avec l' <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribut :

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike` n’implique pas `Struct` . Les deux doivent être présents sur le type.

Un `byref` struct « -like » en F # est un type valeur lié à la pile. Elle n’est jamais allouée sur le tas managé. Un `byref` struct de type like est utile pour la programmation hautes performances, car il est appliqué avec un ensemble de vérifications fortes sur la durée de vie et la non-capture. Les règles sont les suivantes :

- Elles peuvent être utilisées en tant que paramètres de fonction, paramètres de méthode, variables locales, retours de méthode.
- Ils ne peuvent pas être des membres statiques ou d’instance d’une classe ou d’un struct normal.
- Ils ne peuvent pas être capturés par une construction de fermeture ( `async` méthodes ou expressions lambda).
- Ils ne peuvent pas être utilisés comme paramètre générique.

Bien que ces règles restreignent fortement l’utilisation, elles le font pour garantir la promesse de l’informatique hautes performances de manière sûre.

## <a name="readonly-structs"></a>Structs en lecture seule

Vous pouvez annoter des structs avec l' <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> attribut. Par exemple :

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsReadOnly` n’implique pas `Struct` . Vous devez ajouter les deux pour avoir un `IsReadOnly` struct.

L’utilisation de cet attribut émet des métadonnées pour que F # et C# sachent le traiter comme `inref<'T>` et `in ref` , respectivement.

La définition d’une valeur mutable à l’intérieur d’un struct ReadOnly génère une erreur.

## <a name="struct-records-and-discriminated-unions"></a>Enregistrements de struct et unions discriminées

Vous pouvez représenter des [enregistrements](records.md) et des [unions discriminées](discriminated-unions.md) comme des structs avec l' `[<Struct>]` attribut.  Pour en savoir plus, consultez chaque article.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F #](index.md)
- [Classes](classes.md)
- [Enregistrements](records.md)
- [Members](./members/index.md) (Membres)
