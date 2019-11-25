---
title: Déclaration des variables objets
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- declarations [Visual Basic], class
- classes [Visual Basic], declaring
- binding [Visual Basic], late and early
- object variables [Visual Basic], declaring
- variables [Visual Basic], object
- declaring variables [Visual Basic], object variables
- declaring classes [Visual Basic]
- late binding [Visual Basic]
ms.assetid: 2a5a41a3-1aa8-4236-b1f0-2382af7bf715
ms.openlocfilehash: d1964e3768124dde1deeabfada9006ff5a59def0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351816"
---
# <a name="object-variable-declaration-visual-basic"></a>Déclaration des variables objets (Visual Basic)
You use a normal declaration statement to declare an object variable. For the data type, you specify either `Object` (that is, the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)) or a more specific class from which the object is to be created.  
  
 Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.  
  
 When you declare a variable with a specific object class, it can access all the methods and properties exposed by that class and the classes from which it inherits. If you declare the variable with <xref:System.Object>, it can access only the members of the <xref:System.Object> class, unless you turn `Option Strict Off` to allow late binding.  
  
## <a name="declaration-syntax"></a>Syntaxe de déclaration  
 Use the following syntax to declare an object variable:  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 You can also specify [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), or [Static](../../../../visual-basic/language-reference/modifiers/static.md) in the declaration. The following example declarations are valid:  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a>Late Binding and Early Binding  
 Sometimes the specific class is unknown until your code runs. In this case, you must declare the object variable with the `Object` data type. This creates a general reference to any type of object, and the specific class is assigned at run time. This is called *late binding*. Late binding requires additional execution time. It also limits your code to the methods and properties of the class you have most recently assigned to it. This can cause run-time errors if your code attempts to access members of a different class.  
  
 When you know the specific class at compile time, you should declare the object variable to be of that class. Il s’agit de la *liaison anticipée*. Early binding improves performance and guarantees your code access to all the methods and properties of the specific class. In the preceding example declarations, if variable `objA` uses only objects of class <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, you should specify `As System.Windows.Forms.Label` in its declaration.  
  
### <a name="advantages-of-early-binding"></a>Avantages de la liaison anticipée  
 Declaring an object variable as a specific class gives you several advantages:  
  
- Automatic type checking  
  
- Guaranteed access to all members of the specific class  
  
- Microsoft IntelliSense support in the Code Editor  
  
- Improved readability of your code  
  
- Fewer errors in your code  
  
- Errors caught at compile time rather than run time  
  
- Faster code execution  
  
## <a name="access-to-object-variable-members"></a>Access to Object Variable Members  
 When `Option Strict` is turned `On`, an object variable can access only the methods and properties of the class with which you declare it. L'exemple suivant illustre ce comportement.  
  
```vb  
' Option statements must precede all other source file lines.  
Option Strict On  
' Imports statement must precede all declarations in the source file.  
Imports System.Windows.Forms  
Public Sub accessMembers()  
    Dim p As Object  
    Dim q As System.Windows.Forms.Label  
    p = New System.Windows.Forms.Label  
    q = New System.Windows.Forms.Label  
    Dim j, k As Integer  
    ' The following statement generates a compiler ERROR.  
    j = p.Left  
    ' The following statement retrieves the left edge of the label in pixels.  
    k = q.Left  
End Sub  
```  
  
 Dans cet exemple, `p` peut utiliser uniquement les membres de la <xref:System.Object> classe proprement dite, qui n’incluent pas la propriété `Left` . En revanche, `q` a été déclaré comme étant de type <xref:System.Windows.Forms.Label>. Il peut donc utiliser toutes les méthodes et propriétés de la classe <xref:System.Windows.Forms.Label> dans l’espace de noms <xref:System.Windows.Forms> .  
  
## <a name="flexibility-of-object-variables"></a>Flexibility of Object Variables  
 When working with objects in an inheritance hierarchy, you have a choice of which class to use for declaring your object variables. In making this choice, you must balance flexibility of object assignment against access to members of a class. For example, consider the inheritance hierarchy that leads to the <xref:System.Windows.Forms.Form?displayProperty=nameWithType> class:  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 Suppose your application defines a form class called `specialForm`, which inherits from class <xref:System.Windows.Forms.Form>. You can declare an object variable that refers specifically to `specialForm`, as the following example shows.  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 The declaration in the preceding example limits the variable `nextForm` to objects of class `specialForm`, but it also makes all the methods and properties of `specialForm` available to `nextForm`, as well as all the members of all the classes from which `specialForm` inherits.  
  
 You can make an object variable more general by declaring it to be of type <xref:System.Windows.Forms.Form>, as the following example shows.  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 The declaration in the preceding example lets you assign any form in your application to `anyForm`. However, although `anyForm` can access all the members of class <xref:System.Windows.Forms.Form>, it cannot use any of the additional methods or properties defined for specific forms such as `specialForm`.  
  
 All the members of a base class are available to derived classes, but the additional members of a derived class are unavailable to the base class.  
  
## <a name="see-also"></a>Voir aussi

- [Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Assignation des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Valeurs des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [How to: Declare an Object Variable and Assign an Object to It in Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [Guide pratique : accéder aux membres d’un objet](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [New (opérateur)](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Option Strict (instruction)](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Inférence de type local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
