---
title: 'Exceptions : fonction raise'
description: Découvrez comment la F# 'raise' (fonction) est utilisée pour indiquer qu’une erreur ou une condition exceptionnelle s’est produite.
ms.date: 05/16/2016
ms.openlocfilehash: 9e2515ad7b85c1025bc3aa0aa2a6929a8d35436d
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641964"
---
# <a name="exceptions-the-raise-function"></a>Exceptions : fonction raise

Le `raise` fonction est utilisée pour indiquer qu’une erreur ou une condition exceptionnelle s’est produite. Informations sur l’erreur sont capturées dans un objet d’exception.

## <a name="syntax"></a>Syntaxe

```fsharp
raise (expression)
```

## <a name="remarks"></a>Notes

Le `raise` fonction génère un objet d’exception et lance une processus de déroulement de la pile. Le processus de déroulement de pile est géré par le common language runtime (CLR), donc le comportement de ce processus est le même comme dans tout autre langage .NET. Le processus de déroulement de pile est une recherche pour un gestionnaire d’exceptions qui correspond à l’exception générée. La recherche commence dans le courant `try...with` expression, le cas échéant. Chaque modèle dans le `with` bloc est activé, dans l’ordre. Quand un gestionnaire d’exceptions correspondant est trouvé, l’exception est considérée comme gérée ; Sinon, la pile est déroulée et `with` blocs de la chaîne d’appel sont vérifiées jusqu'à ce qu’un gestionnaire correspondant est trouvé. N’importe quel `finally` blocs qui sont produisent dans la chaîne d’appel sont également exécutées en séquence comme la pile se déroule.

Le `raise` fonction est l’équivalent de `throw` en c# ou C++. Utilisez `reraise` dans un gestionnaire catch pour propager la même exception en haut de la chaîne d’appel.

Les exemples de code suivants illustrent l’utilisation de la `raise` fonction permettant de générer une exception.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

Le `raise` fonction peut également être utilisée pour lever des exceptions .NET, comme illustré dans l’exemple suivant.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]

## <a name="see-also"></a>Voir aussi

- [Gestion des exceptions](index.md)
- [Types d'exceptions](exception-types.md)
- [Exceptions : Le `try...with` Expression](the-try-with-expression.md)
- [Exceptions : Le `try...finally` Expression](the-try-finally-expression.md)
- [Exceptions : Le `failwith` (fonction)](the-failwith-function.md)
- [Exceptions : Le `invalidArg` (fonction)](the-invalidArg-function.md)
