---
title: Assemblys friend
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: a74d4b74ead8492028a092e090f9281231802a87
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348175"
---
# <a name="friend-assemblies"></a><span data-ttu-id="bf717-102">Assemblys friend</span><span class="sxs-lookup"><span data-stu-id="bf717-102">Friend assemblies</span></span>

<span data-ttu-id="bf717-103">A *friend assembly* is an assembly that can access another assembly's [internal](../../csharp/language-reference/keywords/internal.md) (C#) or [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) types and members.</span><span class="sxs-lookup"><span data-stu-id="bf717-103">A *friend assembly* is an assembly that can access another assembly's [internal](../../csharp/language-reference/keywords/internal.md) (C#) or [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) types and members.</span></span> <span data-ttu-id="bf717-104">Si vous identifiez un assembly comme étant un assembly friend, vous n’avez plus à marquer ses types et ses membres comme publics pour qu’ils soient accessibles aux autres assemblys.</span><span class="sxs-lookup"><span data-stu-id="bf717-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="bf717-105">Ceci est particulièrement utile dans les scénarios suivants :</span><span class="sxs-lookup"><span data-stu-id="bf717-105">This is especially convenient in the following scenarios:</span></span>

- <span data-ttu-id="bf717-106">Pendant un test unitaire, lorsque le code de test s’exécute dans un assembly séparé, mais nécessite l’accès aux membres de l’assembly actuellement testés qui sont marqués comme `internal` en C# ou `Friend` en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bf717-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

- <span data-ttu-id="bf717-107">Lorsque vous développez une bibliothèque de classes et que des ajouts à la bibliothèque sont contenus dans des assemblys séparés, mais nécessitent l’accès aux membres des assemblys existants qui sont marqués comme `internal` en C# ou `Friend` en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bf717-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

## <a name="remarks"></a><span data-ttu-id="bf717-108">Notes</span><span class="sxs-lookup"><span data-stu-id="bf717-108">Remarks</span></span>

<span data-ttu-id="bf717-109">Vous pouvez utiliser l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> pour identifier un ou plusieurs assemblys friend pour un assembly donné.</span><span class="sxs-lookup"><span data-stu-id="bf717-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="bf717-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in *Assembly A* and specifies assembly *AssemblyB* as a friend assembly.</span><span class="sxs-lookup"><span data-stu-id="bf717-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in *Assembly A* and specifies assembly *AssemblyB* as a friend assembly.</span></span> <span data-ttu-id="bf717-111">This gives assembly *AssemblyB* access to all types and members in *Assembly A* that are marked as `internal` in C# or `Friend` in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bf717-111">This gives assembly *AssemblyB* access to all types and members in *Assembly A* that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

> [!NOTE]
> <span data-ttu-id="bf717-112">When you compile an assembly like *AssemblyB* that will access internal types or internal members of another assembly like *Assembly A*, you must explicitly specify the name of the output file ( *.exe* or *.dll*) by using the **-out** compiler option.</span><span class="sxs-lookup"><span data-stu-id="bf717-112">When you compile an assembly like *AssemblyB* that will access internal types or internal members of another assembly like *Assembly A*, you must explicitly specify the name of the output file (*.exe* or *.dll*) by using the **-out** compiler option.</span></span> <span data-ttu-id="bf717-113">Ceci est nécessaire, car le compilateur n’a pas encore généré le nom de l’assembly qu’il est en train de créer au moment où il effectue une liaison avec les références externes.</span><span class="sxs-lookup"><span data-stu-id="bf717-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="bf717-114">For more information, see [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="bf717-114">For more information, see [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>

```csharp
using System.Runtime.CompilerServices;
using System;

[assembly: InternalsVisibleTo("AssemblyB")]

// The class is internal by default.
class FriendClass
{
    public void Test()
    {
        Console.WriteLine("Sample Class");
    }
}

// Public class that has an internal method.
public class ClassWithFriendMethod
{
    internal void Test()
    {
        Console.WriteLine("Sample Method");
    }

}
```

```vb
Imports System.Runtime.CompilerServices
<Assembly: InternalsVisibleTo("AssemblyB")>

' Friend class.
Friend Class FriendClass
    Public Sub Test()
        Console.WriteLine("Sample Class")
    End Sub
End Class

' Public class with a Friend method.
Public Class ClassWithFriendMethod
    Friend Sub Test()
        Console.WriteLine("Sample Method")
    End Sub
End Class
```

<span data-ttu-id="bf717-115">Only assemblies that you explicitly specify as friends can access `internal` (C#) or `Friend` (Visual Basic) types and members.</span><span class="sxs-lookup"><span data-stu-id="bf717-115">Only assemblies that you explicitly specify as friends can access `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span> <span data-ttu-id="bf717-116">For example, if *AssemblyB* is a friend of *Assembly A* and *Assembly C* references *AssemblyB*, *Assembly C* does not have access to `internal` (C#) or `Friend` (Visual Basic) types in *Assembly A*.</span><span class="sxs-lookup"><span data-stu-id="bf717-116">For example, if *AssemblyB* is a friend of *Assembly A* and *Assembly C* references *AssemblyB*, *Assembly C* does not have access to `internal` (C#) or `Friend` (Visual Basic) types in *Assembly A*.</span></span>

<span data-ttu-id="bf717-117">Le compilateur effectue une validation de base du nom de l’assembly friend soumis à l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="bf717-117">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="bf717-118">If *Assembly A* declares *AssemblyB* as a friend assembly, the validation rules are as follows:</span><span class="sxs-lookup"><span data-stu-id="bf717-118">If *Assembly A* declares *AssemblyB* as a friend assembly, the validation rules are as follows:</span></span>

- <span data-ttu-id="bf717-119">If *Assembly A* is strong named, *AssemblyB* must also be strong named.</span><span class="sxs-lookup"><span data-stu-id="bf717-119">If *Assembly A* is strong named, *AssemblyB* must also be strong named.</span></span> <span data-ttu-id="bf717-120">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign *AssemblyB*.</span><span class="sxs-lookup"><span data-stu-id="bf717-120">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign *AssemblyB*.</span></span>

     <span data-ttu-id="bf717-121">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of *AssemblyB*.</span><span class="sxs-lookup"><span data-stu-id="bf717-121">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of *AssemblyB*.</span></span> <span data-ttu-id="bf717-122">Don't include the assembly version, culture, architecture, or public key token.</span><span class="sxs-lookup"><span data-stu-id="bf717-122">Don't include the assembly version, culture, architecture, or public key token.</span></span>

- <span data-ttu-id="bf717-123">If *Assembly A* is not strong named, the friend assembly name should consist of only the assembly name.</span><span class="sxs-lookup"><span data-stu-id="bf717-123">If *Assembly A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="bf717-124">For more information, see [How to: Create unsigned friend assemblies](create-unsigned-friend.md).</span><span class="sxs-lookup"><span data-stu-id="bf717-124">For more information, see [How to: Create unsigned friend assemblies](create-unsigned-friend.md).</span></span>

- <span data-ttu-id="bf717-125">If *AssemblyB* is strong named, you must specify the strong-name key for *AssemblyB* by using the project setting or the command-line `/keyfile` compiler option.</span><span class="sxs-lookup"><span data-stu-id="bf717-125">If *AssemblyB* is strong named, you must specify the strong-name key for *AssemblyB* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="bf717-126">For more information, see [How to: Create signed friend assemblies](create-signed-friend.md).</span><span class="sxs-lookup"><span data-stu-id="bf717-126">For more information, see [How to: Create signed friend assemblies](create-signed-friend.md).</span></span>

 <span data-ttu-id="bf717-127">La classe <xref:System.Security.Permissions.StrongNameIdentityPermission> offre également la possibilité de partager des types, avec les différences suivantes :</span><span class="sxs-lookup"><span data-stu-id="bf717-127">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>

- <span data-ttu-id="bf717-128"><xref:System.Security.Permissions.StrongNameIdentityPermission> s’applique à un type individuel, alors qu’un assembly friend s’applique à l’assembly entier.</span><span class="sxs-lookup"><span data-stu-id="bf717-128"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>

- <span data-ttu-id="bf717-129">If there are hundreds of types in *Assembly A* that you want to share with *AssemblyB*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span><span class="sxs-lookup"><span data-stu-id="bf717-129">If there are hundreds of types in *Assembly A* that you want to share with *AssemblyB*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="bf717-130">Si vous utilisez un assembly friend, vous n’aurez à déclarer la relation d’assembly friend qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="bf717-130">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>

- <span data-ttu-id="bf717-131">Si vous utilisez <xref:System.Security.Permissions.StrongNameIdentityPermission>, les types que vous voulez partager doivent être déclarés comme publics.</span><span class="sxs-lookup"><span data-stu-id="bf717-131">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="bf717-132">If you use a friend assembly, the shared types are declared as `internal` (C#) or `Friend` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="bf717-132">If you use a friend assembly, the shared types are declared as `internal` (C#) or `Friend` (Visual Basic).</span></span>

<span data-ttu-id="bf717-133">For information about how to access an assembly's `internal` (C#) or `Friend` (Visual Basic) types and methods from a module file (a file with the *.netmodule* extension), see [-moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) or [-moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span><span class="sxs-lookup"><span data-stu-id="bf717-133">For information about how to access an assembly's `internal` (C#) or `Friend` (Visual Basic) types and methods from a module file (a file with the *.netmodule* extension), see [-moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) or [-moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bf717-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf717-134">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [<span data-ttu-id="bf717-135">How to: Create unsigned friend assemblies</span><span class="sxs-lookup"><span data-stu-id="bf717-135">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="bf717-136">How to: Create signed friend assemblies</span><span class="sxs-lookup"><span data-stu-id="bf717-136">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="bf717-137">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="bf717-137">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="bf717-138">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="bf717-138">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="bf717-139">Programming concepts (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf717-139">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
