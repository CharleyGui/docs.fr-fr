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
# <a name="structures-and-other-programming-elements-visual-basic"></a><span data-ttu-id="df3d8-102">Structures et autres éléments de programmation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df3d8-102">Structures and Other Programming Elements (Visual Basic)</span></span>
<span data-ttu-id="df3d8-103">You can use structures in conjunction with arrays, objects, and procedures, as well as with each other.</span><span class="sxs-lookup"><span data-stu-id="df3d8-103">You can use structures in conjunction with arrays, objects, and procedures, as well as with each other.</span></span> <span data-ttu-id="df3d8-104">The interactions use the same syntax as these elements use individually.</span><span class="sxs-lookup"><span data-stu-id="df3d8-104">The interactions use the same syntax as these elements use individually.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df3d8-105">You cannot initialize any of the structure elements in the structure declaration.</span><span class="sxs-lookup"><span data-stu-id="df3d8-105">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="df3d8-106">You can assign values only to elements of a variable that has been declared to be of a structure type.</span><span class="sxs-lookup"><span data-stu-id="df3d8-106">You can assign values only to elements of a variable that has been declared to be of a structure type.</span></span>  
  
## <a name="structures-and-arrays"></a><span data-ttu-id="df3d8-107">Structures and Arrays</span><span class="sxs-lookup"><span data-stu-id="df3d8-107">Structures and Arrays</span></span>  
 <span data-ttu-id="df3d8-108">A structure can contain an array as one or more of its elements.</span><span class="sxs-lookup"><span data-stu-id="df3d8-108">A structure can contain an array as one or more of its elements.</span></span> <span data-ttu-id="df3d8-109">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="df3d8-109">The following example illustrates this.</span></span>  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 <span data-ttu-id="df3d8-110">You access the values of an array within a structure the same way you access a property on an object.</span><span class="sxs-lookup"><span data-stu-id="df3d8-110">You access the values of an array within a structure the same way you access a property on an object.</span></span> <span data-ttu-id="df3d8-111">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="df3d8-111">The following example illustrates this.</span></span>  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 <span data-ttu-id="df3d8-112">You can also declare an array of structures.</span><span class="sxs-lookup"><span data-stu-id="df3d8-112">You can also declare an array of structures.</span></span> <span data-ttu-id="df3d8-113">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="df3d8-113">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 <span data-ttu-id="df3d8-114">You follow the same rules to access the components of this data architecture.</span><span class="sxs-lookup"><span data-stu-id="df3d8-114">You follow the same rules to access the components of this data architecture.</span></span> <span data-ttu-id="df3d8-115">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="df3d8-115">The following example illustrates this.</span></span>  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a><span data-ttu-id="df3d8-116">Structures and Objects</span><span class="sxs-lookup"><span data-stu-id="df3d8-116">Structures and Objects</span></span>  
 <span data-ttu-id="df3d8-117">A structure can contain an object as one or more of its elements.</span><span class="sxs-lookup"><span data-stu-id="df3d8-117">A structure can contain an object as one or more of its elements.</span></span> <span data-ttu-id="df3d8-118">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="df3d8-118">The following example illustrates this.</span></span>  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 <span data-ttu-id="df3d8-119">You should use a specific object class in such a declaration, rather than `Object`.</span><span class="sxs-lookup"><span data-stu-id="df3d8-119">You should use a specific object class in such a declaration, rather than `Object`.</span></span>  
  
## <a name="structures-and-procedures"></a><span data-ttu-id="df3d8-120">Structures and Procedures</span><span class="sxs-lookup"><span data-stu-id="df3d8-120">Structures and Procedures</span></span>  
 <span data-ttu-id="df3d8-121">You can pass a structure as a procedure argument.</span><span class="sxs-lookup"><span data-stu-id="df3d8-121">You can pass a structure as a procedure argument.</span></span> <span data-ttu-id="df3d8-122">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="df3d8-122">The following example illustrates this.</span></span>  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 <span data-ttu-id="df3d8-123">The preceding example passes the structure *by reference*, which allows the procedure to modify its elements so that the changes take effect in the calling code.</span><span class="sxs-lookup"><span data-stu-id="df3d8-123">The preceding example passes the structure *by reference*, which allows the procedure to modify its elements so that the changes take effect in the calling code.</span></span> <span data-ttu-id="df3d8-124">If you want to protect a structure against such modification, pass it by value.</span><span class="sxs-lookup"><span data-stu-id="df3d8-124">If you want to protect a structure against such modification, pass it by value.</span></span>  
  
 <span data-ttu-id="df3d8-125">You can also return a structure from a `Function` procedure.</span><span class="sxs-lookup"><span data-stu-id="df3d8-125">You can also return a structure from a `Function` procedure.</span></span> <span data-ttu-id="df3d8-126">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="df3d8-126">The following example illustrates this.</span></span>  
  
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
  
## <a name="structures-within-structures"></a><span data-ttu-id="df3d8-127">Structures Within Structures</span><span class="sxs-lookup"><span data-stu-id="df3d8-127">Structures Within Structures</span></span>  
 <span data-ttu-id="df3d8-128">Structures can contain other structures.</span><span class="sxs-lookup"><span data-stu-id="df3d8-128">Structures can contain other structures.</span></span> <span data-ttu-id="df3d8-129">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="df3d8-129">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="df3d8-130">You can also use this technique to encapsulate a structure defined in one module within a structure defined in a different module.</span><span class="sxs-lookup"><span data-stu-id="df3d8-130">You can also use this technique to encapsulate a structure defined in one module within a structure defined in a different module.</span></span>  
  
 <span data-ttu-id="df3d8-131">Structures can contain other structures to an arbitrary depth.</span><span class="sxs-lookup"><span data-stu-id="df3d8-131">Structures can contain other structures to an arbitrary depth.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df3d8-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df3d8-132">See also</span></span>

- [<span data-ttu-id="df3d8-133">Types de données</span><span class="sxs-lookup"><span data-stu-id="df3d8-133">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="df3d8-134">Types de données élémentaires</span><span class="sxs-lookup"><span data-stu-id="df3d8-134">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="df3d8-135">Types de données composites</span><span class="sxs-lookup"><span data-stu-id="df3d8-135">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="df3d8-136">Types valeur et types référence</span><span class="sxs-lookup"><span data-stu-id="df3d8-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="df3d8-137">Structures</span><span class="sxs-lookup"><span data-stu-id="df3d8-137">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="df3d8-138">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="df3d8-138">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="df3d8-139">Guide pratique : déclarer une structure</span><span class="sxs-lookup"><span data-stu-id="df3d8-139">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="df3d8-140">Variables de structure</span><span class="sxs-lookup"><span data-stu-id="df3d8-140">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [<span data-ttu-id="df3d8-141">Structures et classes</span><span class="sxs-lookup"><span data-stu-id="df3d8-141">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [<span data-ttu-id="df3d8-142">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="df3d8-142">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
