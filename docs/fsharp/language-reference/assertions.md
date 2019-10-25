---
title: Assertions
description: Découvrez comment utiliser l’expression’Assert’en tant que fonctionnalité de débogage pour tester des expressions F# dans le langage de programmation.
ms.date: 10/22/2019
ms.openlocfilehash: 430db20e5ca307ba43a72e678a0424e03b0ac381
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799064"
---
# <a name="assertions"></a>Assertions

L’expression `assert` est une fonctionnalité de débogage que vous pouvez utiliser pour tester une expression. En cas d’échec en mode débogage, une assertion génère une boîte de dialogue d’erreur système.

## <a name="syntax"></a>Syntaxe

```fsharp
assert condition
```

## <a name="remarks"></a>Notes

L’expression `assert` a le type `bool -> unit`.

La fonction `assert` se résout en <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>. Cela signifie que son comportement est identique à l’appel de <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> directement.

La vérification des assertions n’est activée que lorsque vous compilez en mode débogage ; autrement dit, si la constante `DEBUG` est définie. Dans le système de projet, par défaut, la constante `DEBUG` est définie dans la configuration Debug, mais pas dans la configuration Release.

L’erreur d’échec d’assertion ne peut pas F# être interceptée à l’aide de la gestion des exceptions.

## <a name="example"></a>Exemple

L’exemple de code suivant illustre l’utilisation de l’expression `assert`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F#](index.md)
