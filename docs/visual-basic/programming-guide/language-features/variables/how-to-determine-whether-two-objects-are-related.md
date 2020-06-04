---
title: 'Comment : déterminer si deux objets sont liés'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: 30e88a21e737aa57513745899577381ed34151a2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410462"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>Comment : déterminer si deux objets sont liés (Visual Basic)

Vous pouvez comparer deux objets pour déterminer la relation, le cas échéant, entre les classes à partir desquelles elles sont créées. La <xref:System.Type.IsInstanceOfType%2A> méthode de la <xref:System.Type?displayProperty=nameWithType> classe retourne `True` si la classe spécifiée hérite de la classe actuelle, ou si le type actuel est une interface prise en charge par la classe spécifiée.

### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>Pour déterminer si un objet hérite de la classe ou de l’interface d’un autre objet

1. Sur l’objet que vous pensez peut être du type de base, appelez la <xref:System.Object.GetType%2A> méthode.

2. Sur l' <xref:System.Type?displayProperty=nameWithType> objet retourné par <xref:System.Object.GetType%2A> , appelez la <xref:System.Type.IsInstanceOfType%2A> méthode.

3. Dans la liste d’arguments pour <xref:System.Type.IsInstanceOfType%2A> , spécifiez l’objet que vous pensez peut être du type dérivé.

    <xref:System.Type.IsInstanceOfType%2A>retourne `True` si son type d’argument hérite du <xref:System.Type?displayProperty=nameWithType> type d’objet.

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

Notez le placement inattendu des deux variables objets dans l’appel à <xref:System.Type.IsInstanceOfType%2A> . Le type de base supposé est utilisé pour générer la <xref:System.Type?displayProperty=nameWithType> classe, et le type dérivé supposé est passé comme argument à la <xref:System.Type.IsInstanceOfType%2A> méthode.

## <a name="see-also"></a>Voir aussi

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [Object Data Type](../../../language-reference/data-types/object-data-type.md)
- [Variables objets](object-variables.md)
- [Valeurs des variables objets](object-variable-values.md)
- [Guide pratique : déterminer si deux objets sont identiques](how-to-determine-whether-two-objects-are-identical.md)
