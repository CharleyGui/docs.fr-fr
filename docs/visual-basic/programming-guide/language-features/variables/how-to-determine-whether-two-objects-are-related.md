---
title: 'Procédure : Déterminer si deux objets sont liés (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: 2b17be4ef5a7dabfc4779ab6f5675cc2baec9c3c
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626554"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>Procédure : Déterminer si deux objets sont liés (Visual Basic)

Vous pouvez comparer deux objets pour déterminer la relation, le cas échéant, entre les classes à partir desquelles elles sont créées. La <xref:System.Type.IsInstanceOfType%2A> méthode de la <xref:System.Type?displayProperty=nameWithType> classe retourne `True` si la classe spécifiée hérite de la classe actuelle, ou si le type actuel est une interface prise en charge par la classe spécifiée.

### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>Pour déterminer si un objet hérite de la classe ou de l’interface d’un autre objet

1. Sur l’objet que vous pensez peut être du type de base, appelez <xref:System.Object.GetType%2A> la méthode.

2. Sur l' <xref:System.Type?displayProperty=nameWithType> objet retourné par <xref:System.Object.GetType%2A>, appelez la <xref:System.Type.IsInstanceOfType%2A> méthode.

3. Dans la liste d’arguments <xref:System.Type.IsInstanceOfType%2A>pour, spécifiez l’objet que vous pensez peut être du type dérivé.

    <xref:System.Type.IsInstanceOfType%2A>retourne `True` si son type <xref:System.Type?displayProperty=nameWithType> d’argument hérite du type d’objet.

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

Notez le placement inattendu des deux variables objets dans l’appel à <xref:System.Type.IsInstanceOfType%2A>. Le type de base supposé est utilisé pour générer <xref:System.Type?displayProperty=nameWithType> la classe, et le type dérivé supposé est passé comme argument à la <xref:System.Type.IsInstanceOfType%2A> méthode.

## <a name="see-also"></a>Voir aussi

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [Object (type de données)](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Valeurs des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Guide pratique : Déterminer si deux objets sont identiques](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
