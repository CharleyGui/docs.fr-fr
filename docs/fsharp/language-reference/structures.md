---
title: Structures
description: Renseignez-vous sur la structure F, un type d’objet compact souvent plus efficace qu’une classe pour les types avec une petite quantité de données et un comportement simple.
ms.date: 05/16/2016
ms.openlocfilehash: 1e9652cc4776e4d1d52eb20e41b6dd87a6c5ba05
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400280"
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

Les structures sont *des types de valeur,* ce qui signifie qu’elles sont stockées directement sur la pile ou, lorsqu’elles sont utilisées comme champs ou éléments de tableau, en ligne dans le type parent. Contrairement aux classes et aux enregistrements, les structures ont une sémantique de passage par valeur. Cela signifie qu'elles sont principalement utilisées pour les petits volumes de données qui sont fréquemment sollicités et copiés.

Dans la syntaxe précédente, deux formes sont présentes. La première n'est pas la syntaxe simplifiée, mais elle est néanmoins fréquemment utilisée, car quand vous employez les mots clés `struct` et `end`, vous pouvez omettre l'attribut `StructAttribute` qui apparaît dans la seconde forme. Vous pouvez abréger `StructAttribute` en `Struct`.

La *définition type-éléments-éléments-et-membres* de la syntaxe précédente représente les déclarations et les définitions des membres. Les structures peuvent avoir des constructeurs et des champs modifiables et non modifiables, et peuvent déclarer des membres et des implémentations d'interface. Pour plus d’informations, voir [Membres](./members/index.md).

Les structures ne peuvent pas participer à l’héritage, ne peuvent pas contenir les liaisons `let` ou `do`, et ne peuvent pas comporter de manière récursive les champs de leur propre type (bien qu’elles puissent contenir des cellules de référence qui référencent leur propre type).

Étant donné que les structures n’autorisent pas les liaisons `let`, vous devez déclarer leurs champs à l’aide du mot clé `val`. Le mot clé `val` définit un champ et son type, mais n'autorise pas l'initialisation. À la place, les déclarations `val` sont initialisées à la valeur zéro ou null. Pour cette raison, les structures ayant un constructeur implicite (c’est-à-dire les paramètres qui sont fournis immédiatement après le nom de la structure dans la déclaration) requièrent que les déclarations `val` soient annotées avec l’attribut `DefaultValue`. Les structures ayant un constructeur défini prennent toujours en charge l'initialisation à zéro. Par conséquent, l'attribut `DefaultValue` est une déclaration selon laquelle une telle valeur égale à zéro est valide pour le champ. Les constructeurs implicites pour les structures n'exécutent aucune action, car les liaisons `let` et `do` ne sont pas autorisées sur le type, mais les valeurs de paramètre de constructeur implicite passées sont disponibles en tant que champs privés.

Les constructeurs explicites peuvent impliquer l'initialisation des valeurs de champ. Quand une structure a un constructeur explicite, elle prend toujours en charge l'initialisation à zéro ; toutefois, vous n'utilisez pas l'attribut `DefaultValue` sur les déclarations `val`, car il est en conflit avec le constructeur explicite. Pour plus `val` d’informations sur les déclarations, voir [Champs explicites: `val` Le mot clé](./members/explicit-fields-the-val-keyword.md).

Les attributs et les modificateurs d'accessibilité sont autorisés sur les structures et suivent les mêmes règles que celles des autres types. Pour plus d’informations, voir [Attributs](attributes.md) et [contrôle d’accès](access-control.md).

Les exemples de code suivants illustrent des définitions de structure.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="byreflike-structs"></a>ByRefLike structs

Vous pouvez définir vos propres structs qui peuvent adhérer à `byref`-comme la sémantique: voir [Byrefs](byrefs.md) pour plus d’informations. Ceci est fait <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> avec l’attribut:

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike`n’implique `Struct`pas . Les deux doivent être présents sur le type.

Une`byref`struction «-comme » dans le F est un type de valeur lié à la pile. Il n’est jamais alloué sur le tas géré. Une `byref`structure comme est utile pour la programmation haute performance, car elle est appliquée avec un ensemble de contrôles forts sur la durée de vie et la non-capture. Les règles sont les suivante :

- Ils peuvent être utilisés comme paramètres de fonction, paramètres de méthode, variables locales, retours de méthode.
- Ils ne peuvent pas être statiques ou des membres d’instance d’une classe ou d’une struct normale.
- Ils ne peuvent pas être`async` capturés par une construction de fermeture (méthodes ou expressions lambda).
- Ils ne peuvent pas être utilisés comme paramètre générique.

Bien que ces règles restreignent très fortement l’utilisation, elles le font pour remplir la promesse de l’informatique de haute performance d’une manière sûre.

## <a name="readonly-structs"></a>LireLees structs

Vous pouvez annoter les <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> structs avec l’attribut. Par exemple :

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsReadOnly`n’implique `Struct`pas . Vous devez ajouter les `IsReadOnly` deux pour avoir une struct.

L’utilisation de cet attribut émet des métadonnées permettant `inref<'T>` `in ref`à F et CMD de savoir le traiter comme et, respectivement.

Définir une valeur mutable à l’intérieur d’une struction lisale produit une erreur.

## <a name="struct-records-and-discriminated-unions"></a>Struct Records et Discriminated Unions

Vous pouvez représenter [les documents](records.md) et les `[<Struct>]` unions [discriminées](discriminated-unions.md) comme structs avec l’attribut.  Voir chaque article pour en savoir plus.

## <a name="see-also"></a>Voir aussi

- [Référence linguistique F](index.md)
- [Classes](classes.md)
- [Dossiers](records.md)
- [Membres](./members/index.md)
