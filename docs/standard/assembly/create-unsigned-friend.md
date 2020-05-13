---
title: 'Comment : créer des assemblys friend non signés'
description: Cet article montre comment utiliser des assemblys friend avec des assemblys qui ne sont pas signés. Elle contient des informations sur la sécurité .NET.
ms.date: 08/19/2019
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
dev_langs:
- csharp
- vb
ms.openlocfilehash: 8d3e13669c36048759fedeb3df1bfb59fd476317
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378968"
---
# <a name="how-to-create-unsigned-friend-assemblies"></a><span data-ttu-id="0d217-104">Comment : créer des assemblys friend non signés</span><span class="sxs-lookup"><span data-stu-id="0d217-104">How to: Create unsigned friend assemblies</span></span>

<span data-ttu-id="0d217-105">Cet exemple montre comment utiliser des assemblys friend avec des assemblys qui ne sont pas signés.</span><span class="sxs-lookup"><span data-stu-id="0d217-105">This example shows how to use friend assemblies with assemblies that are unsigned.</span></span>

## <a name="create-an-assembly-and-a-friend-assembly"></a><span data-ttu-id="0d217-106">Créer un assembly et un assembly friend</span><span class="sxs-lookup"><span data-stu-id="0d217-106">Create an assembly and a friend assembly</span></span>

1. <span data-ttu-id="0d217-107">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="0d217-107">Open a command prompt.</span></span>

2. <span data-ttu-id="0d217-108">Créez un fichier C# ou Visual Basic nommé *friend_unsigned_A* qui contient le code suivant.</span><span class="sxs-lookup"><span data-stu-id="0d217-108">Create a C# or Visual Basic file named *friend_unsigned_A* that contains the following code.</span></span> <span data-ttu-id="0d217-109">Le code utilise l' <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribut pour déclarer *friend_unsigned_B* comme un assembly friend.</span><span class="sxs-lookup"><span data-stu-id="0d217-109">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_unsigned_B* as a friend assembly.</span></span>

   ```csharp
   // friend_unsigned_A.cs
   // Compile with:
   // csc /target:library friend_unsigned_A.cs
   using System.Runtime.CompilerServices;
   using System;

   [assembly: InternalsVisibleTo("friend_unsigned_B")]

   // Type is internal by default.
   class Class1
   {
       public void Test()
       {
           Console.WriteLine("Class1.Test");
       }
   }

   // Public type with internal member.
   public class Class2
   {
       internal void Test()
       {
           Console.WriteLine("Class2.Test");
       }
   }
   ```

   ```vb
   ' friend_unsigned_A.vb
   ' Compile with:
   ' vbc -target:library friend_unsigned_A.vb
   Imports System.Runtime.CompilerServices

   <Assembly: InternalsVisibleTo("friend_unsigned_B")>

   ' Friend type.
   Friend Class Class1
       Public Sub Test()
           Console.WriteLine("Class1.Test")
       End Sub
   End Class

   ' Public type with Friend member.
   Public Class Class2
       Friend Sub Test()
           Console.WriteLine("Class2.Test")
       End Sub
   End Class
   ```

3. <span data-ttu-id="0d217-110">Compilez et signez *friend_unsigned_A* à l’aide de la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="0d217-110">Compile and sign *friend_unsigned_A* by using the following command:</span></span>

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. <span data-ttu-id="0d217-111">Créez un fichier C# ou Visual Basic nommé *friend_unsigned_B* qui contient le code suivant.</span><span class="sxs-lookup"><span data-stu-id="0d217-111">Create a C# or Visual Basic file named *friend_unsigned_B* that contains the following code.</span></span> <span data-ttu-id="0d217-112">Étant donné que *friend_unsigned_A* spécifie *friend_unsigned_B* comme assembly friend, le code dans *friend_unsigned_B* peut accéder aux `internal` types et aux membres (C#) ou `Friend` (Visual Basic) à partir de *friend_unsigned_A*.</span><span class="sxs-lookup"><span data-stu-id="0d217-112">Because *friend_unsigned_A* specifies *friend_unsigned_B* as a friend assembly, the code in *friend_unsigned_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_unsigned_A*.</span></span>

   ```csharp
   // friend_unsigned_B.cs
   // Compile with:
   // csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   public class Program
   {
       static void Main()
       {
           // Access an internal type.
           Class1 inst1 = new Class1();
           inst1.Test();

           Class2 inst2 = new Class2();
           // Access an internal member of a public type.
           inst2.Test();

           System.Console.ReadLine();
       }
   }
   ```

   ```vb
   ' friend_unsigned_B.vb
   ' Compile with:
   ' vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   Module Module1
       Sub Main()
           ' Access a Friend type.
           Dim inst1 As New Class1()
           inst1.Test()

           Dim inst2 As New Class2()
           ' Access a Friend member of a public type.
           inst2.Test()

           System.Console.ReadLine()
       End Sub
   End Module
   ```

5. <span data-ttu-id="0d217-113">Compilez *friend_unsigned_B* à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="0d217-113">Compile *friend_unsigned_B* by using the following command.</span></span>

   ```csharp
   csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   ```

   ```vb
   vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   ```

   <span data-ttu-id="0d217-114">Le nom de l’assembly qui est généré par le compilateur doit correspondre au nom de l’assembly friend qui est passé à l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0d217-114">The name of the assembly that is generated by the compiler must match the friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="0d217-115">Vous devez spécifier explicitement le nom de l’assembly de sortie (*. exe* ou *. dll*) à l’aide de l' `-out` option du compilateur.</span><span class="sxs-lookup"><span data-stu-id="0d217-115">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `-out` compiler option.</span></span> <span data-ttu-id="0d217-116">Pour plus d’informations, consultez [-out (options du compilateur C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) ou [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="0d217-116">For more information, see [-out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..</span></span>

6. <span data-ttu-id="0d217-117">Exécutez le fichier *friend_unsigned_B. exe* .</span><span class="sxs-lookup"><span data-stu-id="0d217-117">Run the *friend_unsigned_B.exe* file.</span></span>

   <span data-ttu-id="0d217-118">Le programme génère deux chaînes : **Class1. test** et **Classe2. test**.</span><span class="sxs-lookup"><span data-stu-id="0d217-118">The program outputs two strings: **Class1.Test** and **Class2.Test**.</span></span>

## <a name="net-security"></a><span data-ttu-id="0d217-119">Sécurité .NET</span><span class="sxs-lookup"><span data-stu-id="0d217-119">.NET security</span></span>

<span data-ttu-id="0d217-120">Il existe des similitudes entre l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> et la classe <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="0d217-120">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="0d217-121">La principale différence est que <xref:System.Security.Permissions.StrongNameIdentityPermission> peut demander des autorisations de sécurité pour exécuter une section de code particulière, alors que l' <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribut contrôle la visibilité des `internal` `Friend` types et des membres (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="0d217-121">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal`  or `Friend` (Visual Basic) types and members.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d217-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d217-122">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="0d217-123">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="0d217-123">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="0d217-124">Assemblys friend</span><span class="sxs-lookup"><span data-stu-id="0d217-124">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="0d217-125">Comment : créer des assemblys friend signés</span><span class="sxs-lookup"><span data-stu-id="0d217-125">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="0d217-126">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="0d217-126">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="0d217-127">Concepts de programmation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d217-127">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
