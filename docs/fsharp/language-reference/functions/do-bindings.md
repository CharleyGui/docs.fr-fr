---
title: Liaisons do
description: Découvrez comment une F# liaison’do’est utilisée pour exécuter du code sans définir une fonction ou une valeur.
ms.date: 05/16/2016
ms.openlocfilehash: f98f523296bfaceeda35d4861eafbfeaa5a60c32
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630538"
---
# <a name="do-bindings"></a>Liaisons do

Une `do` liaison est utilisée pour exécuter du code sans définir une fonction ou une valeur. En outre, les liaisons peuvent être utilisées dans les classes, consultez [ `do` liaisons dans les classes](../members/do-bindings-in-classes.md).

## <a name="syntax"></a>Syntaxe

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a>Notes

Utilisez une `do` liaison lorsque vous souhaitez exécuter du code indépendamment d’une définition de fonction ou de valeur. L’expression dans une `do` liaison doit retourner `unit`. Le code d’une liaison de `do` niveau supérieur est exécuté lors de l’initialisation du module. Le mot `do` clé est facultatif.

Les attributs peuvent être appliqués à une liaison de `do` niveau supérieur. Par exemple, si votre programme utilise COM Interop, vous souhaiterez peut-être `STAThread` appliquer l’attribut à votre programme. Pour ce faire, vous pouvez utiliser un attribut sur `do` une liaison, comme illustré dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](../index.md)
- [Fonctions](index.md)
