---
title: La variable '<variablename>'masque une variable dans un bloc englobant
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 36fe543dd4546c6fe930f259a55cea856917370f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662667"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a>Variable '\<nom_variable >' masque une variable dans un bloc englobant
Une variable dans un bloc a le même nom qu’une autre variable locale.  
  
 **ID d’erreur :** BC30616  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Renommez la variable du bloc englobé afin qu’il ne soit pas identique à toutes les variables locales. Exemple :  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
- Une cause courante de cette erreur est l’utilisation de `Catch e As Exception` à l’intérieur d’un gestionnaire d’événements. Si c’est le cas, nommez le `Catch` variable bloc `ex` plutôt que `e`.  
  
- Une autre source courante de cette erreur est une tentative d’accès d’une variable locale déclarée dans un `Try` bloquer dans une fonction `Catch` bloc. Pour corriger ce problème, déclarez la variable en dehors de la `Try...Catch...Finally` structure.  
  
## <a name="see-also"></a>Voir aussi

- [Try...Catch...Finally (instruction)](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Déclaration de variable](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
