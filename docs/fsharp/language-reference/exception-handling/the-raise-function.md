---
title: 'Exceptions : fonction raise'
description: Découvrez comment la F# fonction «Raise» est utilisée pour indiquer qu’une erreur ou une condition exceptionnelle s’est produite.
ms.date: 05/16/2016
ms.openlocfilehash: e0cc8da8310203c537b8081af8a225671bd8c6a3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630288"
---
# <a name="exceptions-the-raise-function"></a>Exceptions : fonction raise

La `raise` fonction est utilisée pour indiquer qu’une erreur ou une condition exceptionnelle s’est produite. Les informations sur l’erreur sont capturées dans un objet exception.

## <a name="syntax"></a>Syntaxe

```fsharp
raise (expression)
```

## <a name="remarks"></a>Notes

La `raise` fonction génère un objet exception et lance un processus de déroulement de pile. Le processus de déroulement de la pile étant géré par le common language runtime (CLR), le comportement de ce processus est le même que dans tout autre langage .NET. Le processus de déroulement de la pile est une recherche d’un gestionnaire d’exceptions qui correspond à l’exception générée. La recherche démarre dans l’expression `try...with` actuelle, s’il en existe une. Chaque modèle du bloc `with` est vérifié, dans l’ordre. Lorsqu’un gestionnaire d’exceptions correspondant est trouvé, l’exception est considérée comme gérée; dans le cas contraire, la pile est `with` déroulée et les blocs de la chaîne d’appel sont vérifiés jusqu’à ce qu’un gestionnaire correspondant soit trouvé. Tous `finally` les blocs qui sont rencontrés dans la chaîne d’appel sont également exécutés dans l’ordre où la pile se déroule.

La `raise` fonction est l’équivalent de `throw` dans C# ou C++. Utilisez `reraise` dans un gestionnaire catch pour propager la même exception en haut de la chaîne d’appel.

Les exemples de code suivants illustrent l’utilisation `raise` de la fonction pour générer une exception.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

La `raise` fonction peut également être utilisée pour déclencher des exceptions .net, comme illustré dans l’exemple suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]

## <a name="see-also"></a>Voir aussi

- [Gestion des exceptions](index.md)
- [Types d'exceptions](exception-types.md)
- [Exceptions : L' `try...with` expression](the-try-with-expression.md)
- [Exceptions : L' `try...finally` expression](the-try-finally-expression.md)
- [Exceptions : La `failwith` fonction](the-failwith-function.md)
- [Exceptions : La `invalidArg` fonction](the-invalidArg-function.md)
