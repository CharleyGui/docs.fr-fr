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
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a><span data-ttu-id="763b6-102">Comment : déterminer si deux objets sont liés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="763b6-102">How to: Determine Whether Two Objects Are Related (Visual Basic)</span></span>

<span data-ttu-id="763b6-103">Vous pouvez comparer deux objets pour déterminer la relation, le cas échéant, entre les classes à partir desquelles elles sont créées.</span><span class="sxs-lookup"><span data-stu-id="763b6-103">You can compare two objects to determine the relationship, if any, between the classes from which they are created.</span></span> <span data-ttu-id="763b6-104">La méthode <xref:System.Type.IsInstanceOfType%2A> de la classe <xref:System.Type?displayProperty=nameWithType> retourne `True` si la classe spécifiée hérite de la classe actuelle, ou si le type actuel est une interface prise en charge par la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="763b6-104">The <xref:System.Type.IsInstanceOfType%2A> method of the <xref:System.Type?displayProperty=nameWithType> class returns `True` if the specified class inherits from the current class, or if the current type is an interface supported by the specified class.</span></span>

### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a><span data-ttu-id="763b6-105">Pour déterminer si un objet hérite de la classe ou de l’interface d’un autre objet</span><span class="sxs-lookup"><span data-stu-id="763b6-105">To determine if one object inherits from another object's class or interface</span></span>

1. <span data-ttu-id="763b6-106">Sur l’objet que vous pensez peut être du type de base, appelez la méthode <xref:System.Object.GetType%2A>.</span><span class="sxs-lookup"><span data-stu-id="763b6-106">On the object you think might be of the base type, invoke the <xref:System.Object.GetType%2A> method.</span></span>

2. <span data-ttu-id="763b6-107">Sur l' <xref:System.Type?displayProperty=nameWithType> objet retourné par <xref:System.Object.GetType%2A>, appelez la méthode <xref:System.Type.IsInstanceOfType%2A>.</span><span class="sxs-lookup"><span data-stu-id="763b6-107">On the <xref:System.Type?displayProperty=nameWithType> object returned by <xref:System.Object.GetType%2A>, invoke the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>

3. <span data-ttu-id="763b6-108">Dans la liste d’arguments pour <xref:System.Type.IsInstanceOfType%2A>, spécifiez l’objet dont vous pensez qu’il peut s’agir du type dérivé.</span><span class="sxs-lookup"><span data-stu-id="763b6-108">In the argument list for <xref:System.Type.IsInstanceOfType%2A>, specify the object you think might be of the derived type.</span></span>

    <span data-ttu-id="763b6-109"><xref:System.Type.IsInstanceOfType%2A> retourne `True` si son type d’argument hérite du type d’objet <xref:System.Type?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="763b6-109"><xref:System.Type.IsInstanceOfType%2A> returns `True` if its argument type inherits from the <xref:System.Type?displayProperty=nameWithType> object type.</span></span>

## <a name="example"></a><span data-ttu-id="763b6-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="763b6-110">Example</span></span>
 <span data-ttu-id="763b6-111">L’exemple suivant détermine si un objet représente une classe dérivée de la classe d’un autre objet.</span><span class="sxs-lookup"><span data-stu-id="763b6-111">The following example determines whether one object represents a class derived from another object's class.</span></span>

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

<span data-ttu-id="763b6-112">Notez le placement inattendu des deux variables objets dans l’appel à <xref:System.Type.IsInstanceOfType%2A>.</span><span class="sxs-lookup"><span data-stu-id="763b6-112">Note the unexpected placement of the two object variables in the call to <xref:System.Type.IsInstanceOfType%2A>.</span></span> <span data-ttu-id="763b6-113">Le type de base supposé est utilisé pour générer la classe <xref:System.Type?displayProperty=nameWithType>, et le type dérivé supposé est passé comme argument à la méthode <xref:System.Type.IsInstanceOfType%2A>.</span><span class="sxs-lookup"><span data-stu-id="763b6-113">The supposed base type is used to generate the <xref:System.Type?displayProperty=nameWithType> class, and the supposed derived type is passed as an argument to the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>

## <a name="see-also"></a><span data-ttu-id="763b6-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="763b6-114">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [<span data-ttu-id="763b6-115">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="763b6-115">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="763b6-116">Variables objets</span><span class="sxs-lookup"><span data-stu-id="763b6-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="763b6-117">Valeurs des variables objets</span><span class="sxs-lookup"><span data-stu-id="763b6-117">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="763b6-118">Guide pratique : déterminer si deux objets sont identiques</span><span class="sxs-lookup"><span data-stu-id="763b6-118">How to: Determine Whether Two Objects Are Identical</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
