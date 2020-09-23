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
# <a name="structures-and-other-programming-elements-visual-basic"></a><span data-ttu-id="a2c0f-102">Structures et autres éléments de programmation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2c0f-102">Structures and Other Programming Elements (Visual Basic)</span></span>

<span data-ttu-id="a2c0f-103">Vous pouvez utiliser des structures conjointement avec des tableaux, des objets et des procédures, ainsi qu’entre eux.</span><span class="sxs-lookup"><span data-stu-id="a2c0f-103">You can use structures in conjunction with arrays, objects, and procedures, as well as with each other.</span></span> <span data-ttu-id="a2c0f-104">Les interactions utilisent la même syntaxe que celles que ces éléments utilisent individuellement.</span><span class="sxs-lookup"><span data-stu-id="a2c0f-104">The interactions use the same syntax as these elements use individually.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a2c0f-105">Vous ne pouvez pas initialiser l’un des éléments de structure dans la déclaration de structure.</span><span class="sxs-lookup"><span data-stu-id="a2c0f-105">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="a2c0f-106">Vous pouvez assigner des valeurs uniquement aux éléments d’une variable déclarée comme étant d’un type structure.</span><span class="sxs-lookup"><span data-stu-id="a2c0f-106">You can assign values only to elements of a variable that has been declared to be of a structure type.</span></span>  
  
## <a name="structures-and-arrays"></a><span data-ttu-id="a2c0f-107">Structures et tableaux</span><span class="sxs-lookup"><span data-stu-id="a2c0f-107">Structures and Arrays</span></span>  

 <span data-ttu-id="a2c0f-108">Une structure peut contenir un tableau comme un ou plusieurs de ses éléments.</span><span class="sxs-lookup"><span data-stu-id="a2c0f-108">A structure can contain an array as one or more of its elements.</span></span> <span data-ttu-id="a2c0f-109">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="a2c0f-109">The following example illustrates this.</span></span>  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure
```  
  
 <span data-ttu-id="a2c0f-110">Vous accédez aux valeurs d’un tableau dans une structure de la même façon que vous accédez à une propriété sur un objet.</span><span class="sxs-lookup"><span data-stu-id="a2c0f-110">You access the values of an array within a structure the same way you access a property on an object.</span></span> <span data-ttu-id="a2c0f-111">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="a2c0f-111">The following example illustrates this.</span></span>  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 <span data-ttu-id="a2c0f-112">Vous pouvez également déclarer un tableau de structures.</span><span class="sxs-lookup"><span data-stu-id="a2c0f-112">You can also declare an array of structures.</span></span> <span data-ttu-id="a2c0f-113">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="a2c0f-113">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 <span data-ttu-id="a2c0f-114">Vous suivez les mêmes règles pour accéder aux composants de cette architecture de données.</span><span class="sxs-lookup"><span data-stu-id="a2c0f-114">You follow the same rules to access the components of this data architecture.</span></span> <span data-ttu-id="a2c0f-115">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="a2c0f-115">The following example illustrates this.</span></span>  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a><span data-ttu-id="a2c0f-116">Structures et objets</span><span class="sxs-lookup"><span data-stu-id="a2c0f-116">Structures and Objects</span></span>  

 <span data-ttu-id="a2c0f-117">Une structure peut contenir un objet comme un ou plusieurs de ses éléments.</span><span class="sxs-lookup"><span data-stu-id="a2c0f-117">A structure can contain an object as one or more of its elements.</span></span> <span data-ttu-id="a2c0f-118">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="a2c0f-118">The following example illustrates this.</span></span>  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 <span data-ttu-id="a2c0f-119">Vous devez utiliser une classe d’objet spécifique dans une telle déclaration, plutôt que `Object` .</span><span class="sxs-lookup"><span data-stu-id="a2c0f-119">You should use a specific object class in such a declaration, rather than `Object`.</span></span>  
  
## <a name="structures-and-procedures"></a><span data-ttu-id="a2c0f-120">Structures et procédures</span><span class="sxs-lookup"><span data-stu-id="a2c0f-120">Structures and Procedures</span></span>  

 <span data-ttu-id="a2c0f-121">Vous pouvez passer une structure en tant qu’argument de procédure.</span><span class="sxs-lookup"><span data-stu-id="a2c0f-121">You can pass a structure as a procedure argument.</span></span> <span data-ttu-id="a2c0f-122">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="a2c0f-122">The following example illustrates this.</span></span>  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 <span data-ttu-id="a2c0f-123">L’exemple précédent passe la structure *par référence*, ce qui permet à la procédure de modifier ses éléments afin que les modifications prennent effet dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="a2c0f-123">The preceding example passes the structure *by reference*, which allows the procedure to modify its elements so that the changes take effect in the calling code.</span></span> <span data-ttu-id="a2c0f-124">Si vous souhaitez protéger une structure contre une telle modification, transmettez-la par valeur.</span><span class="sxs-lookup"><span data-stu-id="a2c0f-124">If you want to protect a structure against such modification, pass it by value.</span></span>  
  
 <span data-ttu-id="a2c0f-125">Vous pouvez également retourner une structure à partir d’une `Function` procédure.</span><span class="sxs-lookup"><span data-stu-id="a2c0f-125">You can also return a structure from a `Function` procedure.</span></span> <span data-ttu-id="a2c0f-126">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="a2c0f-126">The following example illustrates this.</span></span>  
  
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
  
## <a name="structures-within-structures"></a><span data-ttu-id="a2c0f-127">Structures dans les structures</span><span class="sxs-lookup"><span data-stu-id="a2c0f-127">Structures Within Structures</span></span>  

 <span data-ttu-id="a2c0f-128">Les structures peuvent contenir d’autres structures.</span><span class="sxs-lookup"><span data-stu-id="a2c0f-128">Structures can contain other structures.</span></span> <span data-ttu-id="a2c0f-129">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="a2c0f-129">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="a2c0f-130">Vous pouvez également utiliser cette technique pour encapsuler une structure définie dans un module au sein d’une structure définie dans un autre module.</span><span class="sxs-lookup"><span data-stu-id="a2c0f-130">You can also use this technique to encapsulate a structure defined in one module within a structure defined in a different module.</span></span>  
  
 <span data-ttu-id="a2c0f-131">Les structures peuvent contenir d’autres structures à une profondeur arbitraire.</span><span class="sxs-lookup"><span data-stu-id="a2c0f-131">Structures can contain other structures to an arbitrary depth.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2c0f-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2c0f-132">See also</span></span>

- [<span data-ttu-id="a2c0f-133">Data types</span><span class="sxs-lookup"><span data-stu-id="a2c0f-133">Data Types</span></span>](index.md)
- [<span data-ttu-id="a2c0f-134">Types de données élémentaires</span><span class="sxs-lookup"><span data-stu-id="a2c0f-134">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="a2c0f-135">Types de données composites</span><span class="sxs-lookup"><span data-stu-id="a2c0f-135">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="a2c0f-136">Types valeur et types référence</span><span class="sxs-lookup"><span data-stu-id="a2c0f-136">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="a2c0f-137">Structures</span><span class="sxs-lookup"><span data-stu-id="a2c0f-137">Structures</span></span>](structures.md)
- [<span data-ttu-id="a2c0f-138">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="a2c0f-138">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="a2c0f-139">Procédure : Déclarer une structure</span><span class="sxs-lookup"><span data-stu-id="a2c0f-139">How to: Declare a Structure</span></span>](how-to-declare-a-structure.md)
- [<span data-ttu-id="a2c0f-140">Variables de structure</span><span class="sxs-lookup"><span data-stu-id="a2c0f-140">Structure Variables</span></span>](structure-variables.md)
- [<span data-ttu-id="a2c0f-141">Structures et classes</span><span class="sxs-lookup"><span data-stu-id="a2c0f-141">Structures and Classes</span></span>](structures-and-classes.md)
- [<span data-ttu-id="a2c0f-142">Structure, instruction</span><span class="sxs-lookup"><span data-stu-id="a2c0f-142">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
