---
title: Assemblys friend (C#)
ms.date: 03/03/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
ms.openlocfilehash: 770eb70a5350d7d26e03cb4e605b442100da2a53
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68671194"
---
# <a name="friend-assemblies"></a><span data-ttu-id="ea31d-102">Assemblys friend</span><span class="sxs-lookup"><span data-stu-id="ea31d-102">Friend assemblies</span></span>

<span data-ttu-id="ea31d-103">Un *assembly friend* est un assembly qui peut accéder aux types et membres [internes](../../csharp/language-reference/keywords/internal.md) (en C# ou [Friend](../../visual-basic/language-reference/modifiers/friend.md) en Visual Basic) d’un autre assembly.</span><span class="sxs-lookup"><span data-stu-id="ea31d-103">A *friend assembly* is an assembly that can access another assembly's [internal](../../csharp/language-reference/keywords/internal.md) (in C# or [Friend](../../visual-basic/language-reference/modifiers/friend.md) in Visual Basic) types and members.</span></span> <span data-ttu-id="ea31d-104">Si vous identifiez un assembly comme étant un assembly friend, vous n’avez plus à marquer ses types et ses membres comme publics pour qu’ils soient accessibles aux autres assemblys.</span><span class="sxs-lookup"><span data-stu-id="ea31d-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="ea31d-105">Ceci est particulièrement utile dans les scénarios suivants :</span><span class="sxs-lookup"><span data-stu-id="ea31d-105">This is especially convenient in the following scenarios:</span></span>

- <span data-ttu-id="ea31d-106">Pendant un test unitaire, lorsque le code de test s’exécute dans un assembly séparé, mais nécessite l’accès aux membres de l’assembly actuellement testés qui sont marqués comme `internal` en C# ou `Friend` en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ea31d-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

- <span data-ttu-id="ea31d-107">Lorsque vous développez une bibliothèque de classes et que des ajouts à la bibliothèque sont contenus dans des assemblys séparés, mais nécessitent l’accès aux membres des assemblys existants qui sont marqués comme `internal` en C# ou `Friend` en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ea31d-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

## <a name="remarks"></a><span data-ttu-id="ea31d-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="ea31d-108">Remarks</span></span>

<span data-ttu-id="ea31d-109">Vous pouvez utiliser l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> pour identifier un ou plusieurs assemblys friend pour un assembly donné.</span><span class="sxs-lookup"><span data-stu-id="ea31d-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="ea31d-110">L’exemple suivant utilise l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> dans l’assembly A et spécifie l’assembly `AssemblyB` comme assembly friend.</span><span class="sxs-lookup"><span data-stu-id="ea31d-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in assembly A and specifies assembly `AssemblyB` as a friend assembly.</span></span> <span data-ttu-id="ea31d-111">De cette façon, l’assembly `AssemblyB` a accès à tous les types et membres de l’assembly A qui sont marqués comme `internal` en C# ou `Friend` en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ea31d-111">This gives assembly `AssemblyB` access to all types and members in assembly A that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

> [!NOTE]
> <span data-ttu-id="ea31d-112">Lorsque vous compilez un assembly (assembly `AssemblyB`) qui doit accéder aux types ou aux membres internes d’un autre assembly (assembly *A*), vous devez spécifier explicitement le nom du fichier de sortie (.exe ou .dll) à l’aide de l’option **/out** du compilateur.</span><span class="sxs-lookup"><span data-stu-id="ea31d-112">When you compile an assembly (assembly `AssemblyB`) that will access internal types or internal members of another assembly (assembly *A*), you must explicitly specify the name of the output file (.exe or .dll) by using the **/out** compiler option.</span></span> <span data-ttu-id="ea31d-113">Ceci est nécessaire, car le compilateur n’a pas encore généré le nom de l’assembly qu’il est en train de créer au moment où il effectue une liaison avec les références externes.</span><span class="sxs-lookup"><span data-stu-id="ea31d-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="ea31d-114">Pour plus d’informations, consultez [/out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) ou [/out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="ea31d-114">For more information, see [/out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [/out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="ea31d-115">C#</span><span class="sxs-lookup"><span data-stu-id="ea31d-115">C#</span></span>](#tab/csharp)

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

# <a name="visual-basictabvb"></a>[<span data-ttu-id="ea31d-116">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ea31d-116">Visual Basic</span></span>](#tab/vb)

```vb
Imports System.Runtime.CompilerServices
Imports System
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

---

<span data-ttu-id="ea31d-117">Seuls les assemblys que vous spécifiez explicitement, comme les assemblys friend, peuvent accéder aux types et aux membres `internal` (en C# ou `Friend` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ea31d-117">Only assemblies that you explicitly specify as friends can access `internal` (in C# or `Friend` in Visual Basic) types and members.</span></span> <span data-ttu-id="ea31d-118">Par exemple, si l’assembly B est un assembly friend de l’assembly A, et si l’assembly C référence l’assembly B, l’assembly C n’aura pas accès aux types `internal` (en C# ou `Friend` en Visual Basic) de l’assembly A.</span><span class="sxs-lookup"><span data-stu-id="ea31d-118">For example, if assembly B is a friend of assembly A and assembly C references assembly B, C does not have access to `internal` (in C# or `Friend` in Visual Basic) types in A.</span></span>

<span data-ttu-id="ea31d-119">Le compilateur effectue une validation de base du nom de l’assembly friend soumis à l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ea31d-119">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="ea31d-120">Si l’assembly *A* déclare l’assembly *B* comme étant un assembly friend, les règles de validation sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="ea31d-120">If assembly *A* declares *B* as a friend assembly, the validation rules are as follows:</span></span>

- <span data-ttu-id="ea31d-121">Si l’assembly *A* porte un nom fort, l’assembly *B* doit également porter un nom fort.</span><span class="sxs-lookup"><span data-stu-id="ea31d-121">If assembly *A* is strong named, assembly *B* must also be strong named.</span></span> <span data-ttu-id="ea31d-122">Le nom de l’assembly friend qui est passé à l’attribut doit être composé du nom de l’assembly et de la clé publique de la clé de nom fort qui est utilisée pour signer l’assembly *B*.</span><span class="sxs-lookup"><span data-stu-id="ea31d-122">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign assembly *B*.</span></span>

     <span data-ttu-id="ea31d-123">Le nom de l’assembly friend soumis à l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> ne peut pas être le nom fort de l’assembly *B* : n’incluez ni la version de l’assembly, ni la culture, ni l’architecture, ni le jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="ea31d-123">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of assembly *B*: do not include the assembly version, culture, architecture, or public key token.</span></span>

- <span data-ttu-id="ea31d-124">Si l’assembly *A* n’a pas un nom fort, le nom de l’assembly friend doit être constitué uniquement du nom de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ea31d-124">If assembly *A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="ea31d-125">Pour plus d'informations, voir [Procédure : Créer des assemblys friend non signés (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) ou [Procédure : Créer des assemblys friend non signés (C#) (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="ea31d-125">For more information, see [How to: Create Unsigned Friend Assemblies (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) or [How to: Create Unsigned Friend Assemblies (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span></span>

- <span data-ttu-id="ea31d-126">Si l’assembly *B* porte un nom fort, vous devez spécifier la clé de nom fort de l’assembly *B* en utilisant le paramètre de projet ou l’option de compilateur `/keyfile`.</span><span class="sxs-lookup"><span data-stu-id="ea31d-126">If assembly *B* is strong named, you must specify the strong-name key for assembly *B* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="ea31d-127">Pour plus d'informations, voir [Procédure : Créer des assemblys friend signés (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) ou [Procédure : Créer des assemblys friend signés (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="ea31d-127">For more information, see [How to: Create Signed Friend Assemblies (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) or [How to: Create Signed Friend Assemblies (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span></span>

 <span data-ttu-id="ea31d-128">La classe <xref:System.Security.Permissions.StrongNameIdentityPermission> offre également la possibilité de partager des types, avec les différences suivantes :</span><span class="sxs-lookup"><span data-stu-id="ea31d-128">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>

- <span data-ttu-id="ea31d-129"><xref:System.Security.Permissions.StrongNameIdentityPermission> s’applique à un type individuel, alors qu’un assembly friend s’applique à l’assembly entier.</span><span class="sxs-lookup"><span data-stu-id="ea31d-129"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>

- <span data-ttu-id="ea31d-130">Si vous souhaitez partager des centaines de types de l’assembly *A* avec l’assembly *B*, vous devez ajouter <xref:System.Security.Permissions.StrongNameIdentityPermission> à chacun d’eux.</span><span class="sxs-lookup"><span data-stu-id="ea31d-130">If there are hundreds of types in assembly *A* that you want to share with assembly *B*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="ea31d-131">Si vous utilisez un assembly friend, vous n’aurez à déclarer la relation d’assembly friend qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="ea31d-131">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>

- <span data-ttu-id="ea31d-132">Si vous utilisez <xref:System.Security.Permissions.StrongNameIdentityPermission>, les types que vous voulez partager doivent être déclarés comme publics.</span><span class="sxs-lookup"><span data-stu-id="ea31d-132">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="ea31d-133">Si vous utilisez un assembly friend, les types partagés sont déclarés comme `internal` (en C# ou `Friend` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ea31d-133">If you use a friend assembly, the shared types are declared as `internal` (in C# or `Friend` in Visual Basic).</span></span>

<span data-ttu-id="ea31d-134">Pour plus d’informations sur la façon d’accéder aux types et aux méthodes `internal` (en C# ou `Friend` en Visual Basic) d’un assembly à partir d’un fichier de module (avec l’extension .netmodule), consultez [/moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) ou [/moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span><span class="sxs-lookup"><span data-stu-id="ea31d-134">For information about how to access an assembly's `internal` (in C# or `Friend` in Visual Basic) types and methods from a module file (a file with the .netmodule extension), see [/moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) or [/moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ea31d-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea31d-135">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [<span data-ttu-id="ea31d-136">Guide pratique pour créer des assemblys friend non signés (C#)</span><span class="sxs-lookup"><span data-stu-id="ea31d-136">How to: Create Unsigned Friend Assemblies (C#)</span></span>](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [<span data-ttu-id="ea31d-137">Guide pratique pour Créer des assemblys friend non signés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea31d-137">How to: Create Unsigned Friend Assemblies (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [<span data-ttu-id="ea31d-138">Guide pratique pour créer des assemblys friend signés (C#)</span><span class="sxs-lookup"><span data-stu-id="ea31d-138">How to: Create Signed Friend Assemblies (C#)</span></span>](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [<span data-ttu-id="ea31d-139">Guide pratique pour Créer des assemblys friend signés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea31d-139">How to: Create Signed Friend Assemblies (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [<span data-ttu-id="ea31d-140">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="ea31d-140">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="ea31d-141">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="ea31d-141">C# Programming Guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="ea31d-142">Concepts de programmation</span><span class="sxs-lookup"><span data-stu-id="ea31d-142">Programming Concepts</span></span>](../../visual-basic/programming-guide/concepts/index.md)
