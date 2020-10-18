---
title: La variable '<variablename>'masque une variable dans un bloc englobant
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 408acaafd5e266266b5191313611b94b72a5c270
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161346"
---
# <a name="bc30616-variable-variablename-hides-a-variable-in-an-enclosing-block"></a>BC30616 : la variable' \<variablename> 'masque une variable dans un bloc englobant

Une variable comprise dans un bloc porte le même nom qu’une autre variable locale.

 **ID d’erreur :** BC30616

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Renommez la variable dans le bloc délimité afin qu’elle ne soit pas la même que les autres variables locales. Par exemple :

    ```vb
    Dim a, b, x As Integer
    If a = b Then
       Dim y As Integer = 20 ' Uniquely named block variable.
    End If
    ```

- Une cause courante de cette erreur est l’utilisation de `Catch e As Exception` dans un gestionnaire d’événements. Si c’est le cas, nommez la `Catch` variable de bloc `ex` plutôt que `e` .

- Une autre source courante de cette erreur est une tentative d’accès à une variable locale déclarée dans un `Try` bloc dans un `Catch` bloc séparé. Pour corriger cela, déclarez la variable en dehors de la `Try...Catch...Finally` structure.

## <a name="see-also"></a>Voir aussi

- [Try...Catch...Finally (instruction)](../statements/try-catch-finally-statement.md)
- [Déclaration de variable](../../programming-guide/language-features/variables/variable-declaration.md)
