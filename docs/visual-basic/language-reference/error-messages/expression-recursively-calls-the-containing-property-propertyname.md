---
title: L'expression appelle de manière récursive la propriété conteneur '<propertyname>'
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: 42177f22e632e4a05b1f0b4d934f3e56ab9ff0f2
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698566"
---
# <a name="expression-recursively-calls-the-containing-property-propertyname"></a>L’expression appelle de manière récursive la propriété conteneur' \<propertyname > '
Une instruction dans la procédure `Set` d’une définition de propriété stocke une valeur dans le nom de la propriété.  
  
 L’approche recommandée pour conserver la valeur d’une propriété consiste à définir une variable `Private` dans le conteneur de la propriété et à l’utiliser à la fois dans les procédures `Get` et `Set`. La procédure `Set` doit ensuite stocker la valeur entrante dans cette variable `Private`.  
  
 La procédure `Get` se comporte comme une procédure `Function`, de sorte qu’elle peut attribuer une valeur au nom de la propriété et retourner le contrôle en rencontrant l’instruction `End Get`. Toutefois, l’approche recommandée consiste à inclure la variable `Private` comme valeur dans une [instruction return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 La procédure `Set` se comporte comme une procédure `Sub`, qui ne retourne pas de valeur. Par conséquent, le nom de la procédure ou de la propriété n’a aucune signification particulière dans une procédure `Set`, et vous ne pouvez pas y stocker de valeur.  
  
 L’exemple suivant illustre l’approche qui peut provoquer cette erreur, suivie de l’approche recommandée.  
  
```vb  
Public Class illustrateProperties  
' The code in the following property causes this error.  
    Public Property badProp() As Char  
        Get  
            Dim charValue As Char  
            ' Insert code to update charValue.  
            badProp = charValue  
        End Get  
        Set(ByVal Value As Char)  
            ' The following statement causes this error.  
            badProp = Value  
            ' The value stored in the local variable badProp  
            ' is not used by the Get procedure in this property.  
        End Set  
    End Property  
' The following code uses the recommended approach.  
    Private propValue As Char  
    Public Property goodProp() As Char  
        Get  
            ' Insert code to update propValue.  
            Return propValue  
        End Get  
        Set(ByVal Value As Char)  
            propValue = Value  
        End Set  
    End Property  
End Class  
```  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC42026  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Réécrivez la définition de la propriété pour utiliser l’approche recommandée, comme illustré dans l’exemple précédent.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures de propriété](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)
- [Set (instruction)](../../../visual-basic/language-reference/statements/set-statement.md)
