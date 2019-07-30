---
title: Assertions
description: Découvrez comment utiliser l’expression’Assert’en tant que fonctionnalité de débogage pour tester des expressions F# dans le langage de programmation.
ms.date: 05/16/2016
ms.openlocfilehash: b8b7e9662143b432d650f87515d4af31cced4149
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630028"
---
# <a name="assertions"></a>Assertions

L' `assert` expression est une fonctionnalité de débogage que vous pouvez utiliser pour tester une expression. En cas d’échec en mode débogage, une assertion génère une boîte de dialogue d’erreur système.

## <a name="syntax"></a>Syntaxe

```fsharp
assert condition
```

## <a name="remarks"></a>Notes

L' `assert` expression a le `bool -> unit`type.

Dans la syntaxe précédente, *condition* représente une expression booléenne qui doit être testée. Si l’expression prend la valeur `true`, l’exécution ne se poursuit pas. Si la valeur `false`est, une boîte de dialogue d’erreur système est générée. La boîte de dialogue d’erreur contient une légende qui indique que l’assertion de chaîne **a échoué**. La boîte de dialogue contient une trace de la pile qui indique où l’échec de l’assertion s’est produit.

La vérification des assertions n’est activée que lorsque vous compilez en mode débogage; autrement dit, si la constante `DEBUG` est définie. Dans le système de projet, par défaut, `DEBUG` la constante est définie dans la configuration Debug, mais pas dans la configuration Release.

L’erreur d’échec d’assertion ne peut pas F# être interceptée à l’aide de la gestion des exceptions.

> [!NOTE]
> La `assert` fonction est résolue en <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.

## <a name="example"></a>Exemples

L’exemple de code suivant illustre l’utilisation de l' `assert` expression.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)
