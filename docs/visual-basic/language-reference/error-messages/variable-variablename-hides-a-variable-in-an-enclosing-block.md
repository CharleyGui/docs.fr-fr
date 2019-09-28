---
title: La variable '<variablename>'masque une variable dans un bloc englobant
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 4312abef83728f432e2f6a492e5acad3450719b1
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592060"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a>La variable' \<variablename > 'masque une variable dans un bloc englobant
Une variable comprise dans un bloc porte le même nom qu’une autre variable locale.  
  
 **ID d’erreur :** BC30616  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Renommez la variable dans le bloc délimité afin qu’elle ne soit pas la même que les autres variables locales. Exemple :  
  
    ```vb  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
- Une cause courante de cette erreur est l’utilisation de `Catch e As Exception` à l’intérieur d’un gestionnaire d’événements. Si c’est le cas, nommez la variable de bloc `Catch` `ex` au lieu de `e`.  
  
- Une autre source courante de cette erreur est une tentative d’accès à une variable locale déclarée dans un bloc `Try` dans un bloc `Catch` séparé. Pour corriger cela, déclarez la variable en dehors de la structure `Try...Catch...Finally`.  
  
## <a name="see-also"></a>Voir aussi

- [Try...Catch...Finally (instruction)](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Déclaration de variable](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
