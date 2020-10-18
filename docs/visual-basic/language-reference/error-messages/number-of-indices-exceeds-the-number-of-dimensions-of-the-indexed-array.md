---
title: Le nombre d'indices est supérieur au nombre de dimensions du tableau indexé
ms.date: 07/20/2015
f1_keywords:
- bc30106
- vbc30106
helpviewer_keywords:
- BC30106
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
ms.openlocfilehash: 9a191ff7ec3ad6a607e6509cc143c359f64f21ea
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159909"
---
# <a name="bc30106-number-of-indices-exceeds-the-number-of-dimensions-of-the-indexed-array"></a>BC30106 : le nombre d’index dépasse le nombre de dimensions du tableau indexé

Le nombre d’index utilisés pour accéder à un élément de tableau doit être rigoureusement identique au rang du tableau, c’est-à-dire au nombre de dimensions déclarées pour celui-ci.

 **ID d’erreur :** BC30106

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Supprimez les indices de la référence de tableau jusqu’à ce que le nombre total d’indices soit égal au rang du tableau. Par exemple :

    ```vb
    Dim gameBoard(3, 3) As String

    ' Incorrect code. The array has two dimensions.
    gameBoard(1, 1, 1) = "X"
    gameBoard(2, 1, 1) = "O"

    ' Correct code.
    gameBoard(0, 0) = "X"
    gameBoard(1, 0) = "O"
    ```

## <a name="see-also"></a>Voir aussi

- [Tableaux](../../programming-guide/language-features/arrays/index.md)
