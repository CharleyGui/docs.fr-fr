---
title: "'<membername>' est ambigu dans les interfaces héritées '<interfacename1>' et '<interfacename2>'"
ms.date: 07/20/2015
f1_keywords:
- vbc30685
- bc30685
helpviewer_keywords:
- BC30685
ms.assetid: 756add7a-23d5-4b4f-a48d-8297d6459c73
ms.openlocfilehash: f242db9e02a1983e731dce280be0e8f8a8b12712
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397270"
---
# <a name="membername-is-ambiguous-across-the-inherited-interfaces-interfacename1-and-interfacename2"></a>'\<membername>' est ambigu dans les interfaces héritées '\<interfacename1>' et '\<interfacename2>'
L’interface hérite de deux membres ou plus portant le même nom de plusieurs interfaces.  
  
 **ID d’erreur :** BC30685  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Effectuez un cast de la valeur vers l’interface de base que vous souhaitez utiliser. par exemple :  
  
    ```vb  
    Interface Left  
        Sub MySub()  
    End Interface  
  
    Interface Right  
        Sub MySub()  
    End Interface  
  
    Interface LeftRight  
        Inherits Left, Right  
    End Interface  
  
    Module test  
        Sub Main()  
            Dim x As LeftRight  
            ' x.MySub()  'x is ambiguous.  
            CType(x, Left).MySub() ' Cast to base type.  
            CType(x, Right).MySub() ' Call the other base type.  
        End Sub  
    End Module  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces](../../programming-guide/language-features/interfaces/index.md)
