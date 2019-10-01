---
title: Les paramètres optionnels doivent spécifier une valeur par défaut
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: b32c150f0faf4a9dcec3cec7620c3a9c050f6f20
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696882"
---
# <a name="optional-parameters-must-specify-a-default-value"></a>Les paramètres optionnels doivent spécifier une valeur par défaut
Les paramètres facultatifs doivent fournir des valeurs par défaut qui peuvent être utilisées si aucun paramètre n’est fourni par une procédure appelante.  
  
 **ID d’erreur :** BC30812  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Spécifiez les valeurs par défaut des paramètres facultatifs. par exemple :  
  
    ```vb  
    Sub Proc1(ByVal X As Integer,   
          Optional ByVal Y As String = "Default Value")  
       MsgBox("Default argument is: " & Y)  
    End Sub  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Facultatif](../../../visual-basic/language-reference/modifiers/optional.md)
