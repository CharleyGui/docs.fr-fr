---
title: La variable '<variablename>'masque une variable dans un bloc englobant
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 474a920c9cfdfba7a8157320d9c88b8677958425
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406519"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a>La variable '\<variablename>'masque une variable dans un bloc englobant
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
