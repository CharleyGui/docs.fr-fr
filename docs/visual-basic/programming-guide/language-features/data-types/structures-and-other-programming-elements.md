---
title: Structures et autres éléments de programmation
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
ms.openlocfilehash: 309d0e5214897675e1758bd98b964392b379ca1b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346121"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a>Structures et autres éléments de programmation (Visual Basic)
You can use structures in conjunction with arrays, objects, and procedures, as well as with each other. The interactions use the same syntax as these elements use individually.  
  
> [!NOTE]
> You cannot initialize any of the structure elements in the structure declaration. You can assign values only to elements of a variable that has been declared to be of a structure type.  
  
## <a name="structures-and-arrays"></a>Structures and Arrays  
 A structure can contain an array as one or more of its elements. L'exemple suivant illustre ce comportement.  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 You access the values of an array within a structure the same way you access a property on an object. L'exemple suivant illustre ce comportement.  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 You can also declare an array of structures. L'exemple suivant illustre ce comportement.  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 You follow the same rules to access the components of this data architecture. L'exemple suivant illustre ce comportement.  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a>Structures and Objects  
 A structure can contain an object as one or more of its elements. L'exemple suivant illustre ce comportement.  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 You should use a specific object class in such a declaration, rather than `Object`.  
  
## <a name="structures-and-procedures"></a>Structures and Procedures  
 You can pass a structure as a procedure argument. L'exemple suivant illustre ce comportement.  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 The preceding example passes the structure *by reference*, which allows the procedure to modify its elements so that the changes take effect in the calling code. If you want to protect a structure against such modification, pass it by value.  
  
 You can also return a structure from a `Function` procedure. L'exemple suivant illustre ce comportement.  
  
```vb  
Dim allSystems(100) As systemInfo  
Function findByDate(ByVal searchDate As Date) As systemInfo  
    Dim i As Integer  
    For i = 1 To 100  
        If allSystems(i).purchaseDate = searchDate Then Return allSystems(i)  
    Next i  
   ' Process error: system with desired purchase date not found.  
End Function  
```  
  
## <a name="structures-within-structures"></a>Structures Within Structures  
 Structures can contain other structures. L'exemple suivant illustre ce comportement.  
  
```vb  
Public Structure driveInfo  
    Public type As String  
    Public size As Long  
End Structure  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As driveInfo  
    Public purchaseDate As Date  
End Structure  
```  
  
```vb  
Dim allSystems(100) As systemInfo  
ReDim allSystems(1).diskDrives(3)  
allSystems(1).diskDrives(0).type = "Floppy"  
```  
  
 You can also use this technique to encapsulate a structure defined in one module within a structure defined in a different module.  
  
 Structures can contain other structures to an arbitrary depth.  
  
## <a name="see-also"></a>Voir aussi

- [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Types de données élémentaires](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Types de données composites](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Types valeur et types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Dépannage des types de données](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Guide pratique : déclarer une structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Variables de structure](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [Structures et classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Structure (instruction)](../../../../visual-basic/language-reference/statements/structure-statement.md)
