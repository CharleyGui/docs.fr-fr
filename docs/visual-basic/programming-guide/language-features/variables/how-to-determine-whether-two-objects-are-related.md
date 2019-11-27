---
title: 'Comment : déterminer si deux objets sont liés'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: b3f5fc017166ba9cf28359db5de850c81b73bd69
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348628"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>Comment : déterminer si deux objets sont liés (Visual Basic)

Vous pouvez comparer deux objets pour déterminer la relation, le cas échéant, entre les classes à partir desquelles elles sont créées. La méthode <xref:System.Type.IsInstanceOfType%2A> de la classe <xref:System.Type?displayProperty=nameWithType> retourne `True` si la classe spécifiée hérite de la classe actuelle, ou si le type actuel est une interface prise en charge par la classe spécifiée.

### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>Pour déterminer si un objet hérite de la classe ou de l’interface d’un autre objet

1. Sur l’objet que vous pensez peut être du type de base, appelez la méthode <xref:System.Object.GetType%2A>.

2. Sur l' <xref:System.Type?displayProperty=nameWithType> objet retourné par <xref:System.Object.GetType%2A>, appelez la méthode <xref:System.Type.IsInstanceOfType%2A>.

3. Dans la liste d’arguments pour <xref:System.Type.IsInstanceOfType%2A>, spécifiez l’objet dont vous pensez qu’il peut s’agir du type dérivé.

    <xref:System.Type.IsInstanceOfType%2A> retourne `True` si son type d’argument hérite du type d’objet <xref:System.Type?displayProperty=nameWithType>.

## <a name="example"></a>Exemple
 L’exemple suivant détermine si un objet représente une classe dérivée de la classe d’un autre objet.

```vb
Public Class baseClass
End Class
Public Class derivedClass : Inherits baseClass
End Class
Public Class testTheseClasses
    Public Sub seeIfRelated()
        Dim baseObj As Object = New baseClass()
        Dim derivedObj As Object = New derivedClass()
        Dim related As Boolean
        related = baseObj.GetType().IsInstanceOfType(derivedObj)
        MsgBox(CStr(related))
    End Sub
End Class
```

Notez le placement inattendu des deux variables objets dans l’appel à <xref:System.Type.IsInstanceOfType%2A>. Le type de base supposé est utilisé pour générer la classe <xref:System.Type?displayProperty=nameWithType>, et le type dérivé supposé est passé comme argument à la méthode <xref:System.Type.IsInstanceOfType%2A>.

## <a name="see-also"></a>Voir aussi

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Valeurs des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Guide pratique : déterminer si deux objets sont identiques](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
