---
title: Point d'entrée
description: Découvrez comment définir le point d’entrée sur un F# programme compilé comme fichier exécutable, où l’exécution démarre formellement.
ms.date: 05/16/2016
ms.openlocfilehash: 5e13416131d4dfd22583439fedf51f18f7a461da
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630520"
---
# <a name="entry-point"></a>Point d'entrée

Cette rubrique décrit la méthode que vous utilisez pour définir le point d’entrée sur F# un programme.

## <a name="syntax"></a>Syntaxe

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a>Notes

Dans la syntaxe précédente, *let-function-binding* est la définition d’une fonction dans `let` une liaison.

Le point d’entrée d’un programme compilé comme fichier exécutable est l’emplacement où l’exécution démarre formellement. Vous spécifiez le point d’entrée F# d’une application en `EntryPoint` appliquant l’attribut à `main` la fonction du programme. Cette fonction (créée à l’aide `let` d’une liaison) doit être la dernière fonction du dernier fichier compilé. Le dernier fichier compilé est le dernier fichier du projet ou le dernier fichier passé à la ligne de commande.

La fonction de point d’entrée `string array -> int`a le type. Les arguments fournis sur la ligne de commande sont passés à `main` la fonction dans le tableau de chaînes. Le premier élément du tableau est le premier argument; le nom du fichier exécutable n’est pas inclus dans le tableau, comme c’est le cas dans d’autres langages. La valeur de retour est utilisée comme code de sortie pour le processus. Zéro indique généralement une réussite; une valeur différente de zéro indique une erreur. Il n’existe aucune convention pour la signification spécifique des codes de retour autres que zéro; les significations des codes de retour sont spécifiques à l’application.

L’exemple suivant illustre une fonction simple `main` .

[!code-fsharp[Main](~/samples/snippets/fsharp/entry-point/snippet501.fs)]

Lorsque ce code est exécuté avec la ligne `EntryPoint.exe 1 2 3`de commande, la sortie est la suivante.

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a>Point d’entrée implicite

Lorsqu’un programme n’a pas d’attribut **entryPoint** qui indique explicitement le point d’entrée, les liaisons de niveau supérieur dans le dernier fichier à compiler sont utilisées comme point d’entrée.

## <a name="see-also"></a>Voir aussi

- [Fonctions](index.md)
- [Liaisons let](let-bindings.md)
