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
ms.openlocfilehash: 26c98adda7305783b0220141db35b08285b21554
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91084084"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a>Structures et autres éléments de programmation (Visual Basic)

Vous pouvez utiliser des structures conjointement avec des tableaux, des objets et des procédures, ainsi qu’entre eux. Les interactions utilisent la même syntaxe que celles que ces éléments utilisent individuellement.  
  
> [!NOTE]
> Vous ne pouvez pas initialiser l’un des éléments de structure dans la déclaration de structure. Vous pouvez assigner des valeurs uniquement aux éléments d’une variable déclarée comme étant d’un type structure.  
  
## <a name="structures-and-arrays"></a>Structures et tableaux  

 Une structure peut contenir un tableau comme un ou plusieurs de ses éléments. L'exemple suivant illustre ce comportement.  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure
```  
  
 Vous accédez aux valeurs d’un tableau dans une structure de la même façon que vous accédez à une propriété sur un objet. L'exemple suivant illustre ce comportement.  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 Vous pouvez également déclarer un tableau de structures. L'exemple suivant illustre ce comportement.  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 Vous suivez les mêmes règles pour accéder aux composants de cette architecture de données. L'exemple suivant illustre ce comportement.  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a>Structures et objets  

 Une structure peut contenir un objet comme un ou plusieurs de ses éléments. L'exemple suivant illustre ce comportement.  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 Vous devez utiliser une classe d’objet spécifique dans une telle déclaration, plutôt que `Object` .  
  
## <a name="structures-and-procedures"></a>Structures et procédures  

 Vous pouvez passer une structure en tant qu’argument de procédure. L'exemple suivant illustre ce comportement.  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 L’exemple précédent passe la structure *par référence*, ce qui permet à la procédure de modifier ses éléments afin que les modifications prennent effet dans le code appelant. Si vous souhaitez protéger une structure contre une telle modification, transmettez-la par valeur.  
  
 Vous pouvez également retourner une structure à partir d’une `Function` procédure. L'exemple suivant illustre ce comportement.  
  
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
  
## <a name="structures-within-structures"></a>Structures dans les structures  

 Les structures peuvent contenir d’autres structures. L'exemple suivant illustre ce comportement.  
  
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
  
 Vous pouvez également utiliser cette technique pour encapsuler une structure définie dans un module au sein d’une structure définie dans un autre module.  
  
 Les structures peuvent contenir d’autres structures à une profondeur arbitraire.  
  
## <a name="see-also"></a>Voir aussi

- [Data types](index.md)
- [Types de données élémentaires](elementary-data-types.md)
- [Types de données composites](composite-data-types.md)
- [Types valeur et types référence](value-types-and-reference-types.md)
- [Structures](structures.md)
- [Dépannage des types de données](troubleshooting-data-types.md)
- [Procédure : Déclarer une structure](how-to-declare-a-structure.md)
- [Variables de structure](structure-variables.md)
- [Structures et classes](structures-and-classes.md)
- [Structure, instruction](../../../language-reference/statements/structure-statement.md)
