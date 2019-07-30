---
title: Tuples
description: En savoir plus F# sur le tuple, un regroupement de valeurs sans nom, mais ordonnées, peut-être de types différents.
ms.date: 05/16/2016
ms.openlocfilehash: 7a15d7e0c6c9b42118dd75066f02cbb2e05335fc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630242"
---
# <a name="tuples"></a>Tuples

Un *Tuple* est un regroupement de valeurs sans nom, mais ordonnées, peut-être de types différents.  Les tuples peuvent être des types référence ou des structs.

## <a name="syntax"></a>Syntaxe

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a>Notes

Chaque *élément* de la syntaxe précédente peut être n’importe F# quelle expression valide.

## <a name="examples"></a>Exemples

Les exemples de tuples incluent des paires, des triples, etc., du même type ou de types différents. Quelques exemples sont illustrés dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a>Obtention de valeurs individuelles

Vous pouvez utiliser des critères spéciaux pour accéder et assigner des noms pour les éléments de tuple, comme indiqué dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

Vous pouvez également déconstruire un tuple via des critères spéciaux en dehors `match` d’une `let` expression via la liaison:

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

Vous pouvez aussi répéter les correspondances sur les tuples en tant qu’entrées dans les fonctions:

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

Si vous n’avez besoin que d’un seul élément du tuple, le caractère générique (le trait de soulignement) peut être utilisé pour éviter de créer un nouveau nom pour une valeur dont vous n’avez pas besoin.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

La copie d’éléments d’un tuple de référence dans un tuple de struct est également simple:

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

Les fonctions `fst` et `snd` (tuples de référence uniquement) retournent respectivement le premier et le deuxième élément d’un tuple.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

Il n’existe aucune fonction intégrée qui retourne le troisième élément d’un triple, mais vous pouvez facilement en écrire un comme suit.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

En règle générale, il est préférable d’utiliser des critères spéciaux pour accéder à des éléments de tuple individuels.

## <a name="using-tuples"></a>Utilisation de tuples

Les tuples offrent un moyen pratique de retourner plusieurs valeurs à partir d’une fonction, comme illustré dans l’exemple suivant. Cet exemple exécute une division d’entier et retourne le résultat arrondi de l’opération en tant que premier membre d’une paire de tuples et le reste comme deuxième membre de la paire.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

Les tuples peuvent également être utilisés en tant qu’arguments de fonction lorsque vous souhaitez éviter la curryfication implicite des arguments de fonction qui est impliquée par la syntaxe de fonction habituelle.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

La syntaxe habituelle pour définir la fonction `let sum a b = a + b` vous permet de définir une fonction qui est l’application partielle du premier argument de la fonction, comme indiqué dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

L’utilisation d’un tuple comme paramètre désactive la curryfication. Pour plus d’informations, consultez «application partielle d’arguments» dans les [fonctions](./functions/index.md).

## <a name="names-of-tuple-types"></a>Noms de types de tuples

Lorsque vous écrivez le nom d’un type qui est un tuple, vous utilisez le `*` symbole pour séparer les éléments. Pour un tuple qui se compose d' `int`un, `float`d’un et `string`d’un, `(10, 10.0, "ten")`tel que, le type serait écrit comme suit.

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a>Interopérabilité avec C# les tuples

C#7,0 a introduit des tuples dans le langage.  Les tuples C# dans sont des structs et sont équivalents aux tuples F#de struct dans.  Si vous devez interagir avec, vous C#devez utiliser des tuples de struct.

C’est facile à faire.  Par exemple, imaginez que vous devez passer un tuple à une C# classe, puis utiliser son résultat, qui est également un tuple:

```csharp
namespace CSharpTupleInterop
{
    public static class Example
    {
        public static (int, int) AddOneToXAndY((int x, int y) a) =>
            (a.x + 1, a.y + 1);
    }
}
```

Dans votre F# code, vous pouvez ensuite passer un tuple de struct comme paramètre et utiliser le résultat comme un tuple de struct.

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a>Conversion entre les tuples de référence et les tuples de struct

Étant donné que les tuples de référence et les tuples de struct ont une représentation sous-jacente complètement différente, ils ne sont pas implicitement convertibles.  Autrement dit, le code, tel que le suivant, n’est pas compilé:

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

Vous devez créer un modèle de correspondance sur un tuple et construire l’autre avec les parties constituantes.  Exemple :

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a>Forme compilée de tuples de référence

Cette section explique la forme des tuples lorsqu’elles sont compilées.  Les informations ici ne sont pas nécessaires pour la lecture, sauf si vous ciblez .NET Framework 3,5 ou une valeur inférieure.

Les tuples sont compilés dans des objets de l’un des différents types `System.Tuple`génériques, tous nommés, qui sont surchargés sur l’arité, ou le nombre de paramètres de type. Les types de tuples apparaissent dans ce formulaire lorsque vous les affichez à partir C# d’un autre langage, tel que ou Visual Basic, ou lorsque vous utilisez un F# outil qui n’est pas informé des constructions. Les `Tuple` types ont été introduits dans .NET Framework 4. Si vous ciblez une version antérieure du .NET Framework, le compilateur utilise les versions de [System. Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) de la version 2,0 de la F# bibliothèque principale. Les types de cette bibliothèque sont utilisés uniquement pour les applications qui ciblent les versions 2,0, 3,0 et 3,5 du .NET Framework. Le transfert de type est utilisé pour garantir la compatibilité binaire entre les composants .NET Framework F# 2,0 et .NET Framework 4.

### <a name="compiled-form-of-struct-tuples"></a>Forme compilée de tuples de struct

Les tuples de struct (par `struct (x, y)`exemple,), sont fondamentalement différents des tuples de référence.  Ils sont compilés dans <xref:System.ValueTuple> le type, surchargé par l’arité, ou le nombre de paramètres de type.  Ils sont équivalents aux [ C# tuples 7,0](../../csharp/tuples.md) et [Visual Basic 2017](../../visual-basic/programming-guide/language-features/data-types/tuples.md), et interagissent de manière bidirectionnelle.

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)
- [Types F#](fsharp-types.md)
