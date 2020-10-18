---
title: L'expression appelle de manière récursive la propriété conteneur '<propertyname>'
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: f5b8b226d46afa0555559de0930f20025ba27f2b
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162763"
---
# <a name="bc42026-expression-recursively-calls-the-containing-property-propertyname"></a>BC42026 : l’expression appelle de manière récursive la propriété conteneur' \<propertyname> '

Une instruction dans la `Set` procédure d’une définition de propriété stocke une valeur dans le nom de la propriété.

 L’approche recommandée pour conserver la valeur d’une propriété consiste à définir une `Private` variable dans le conteneur de la propriété et à l’utiliser dans `Get` les `Set` procédures et. La `Set` procédure doit ensuite stocker la valeur entrante dans cette `Private` variable.

 La `Get` procédure se comporte comme une `Function` procédure. elle peut donc assigner une valeur au nom de la propriété et retourner le contrôle en rencontrant l' `End Get` instruction. Toutefois, l’approche recommandée consiste à inclure la `Private` variable en tant que valeur dans une [instruction return](../statements/return-statement.md).

 La `Set` procédure se comporte comme une `Sub` procédure, qui ne retourne pas de valeur. Par conséquent, le nom de la procédure ou de la propriété n’a aucune signification particulière dans une `Set` procédure, et vous ne pouvez pas y stocker de valeur.

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

- [Procédures Property](../../programming-guide/language-features/procedures/property-procedures.md)
- [Property Statement](../statements/property-statement.md)
- [Instruction Set](../statements/set-statement.md)
