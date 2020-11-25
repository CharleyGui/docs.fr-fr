---
title: 'Comment : créer des assemblys friend signés'
description: Cet article montre comment utiliser des assemblys friend avec des assemblys avec des noms forts. Elle contient des informations sur la sécurité .NET.
ms.date: 08/19/2019
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
dev_langs:
- csharp
- vb
ms.openlocfilehash: 4c441501ae0f939f69ac863a990d6e392bd35fc4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734268"
---
# <a name="how-to-create-signed-friend-assemblies"></a><span data-ttu-id="b3ecb-104">Comment : créer des assemblys friend signés</span><span class="sxs-lookup"><span data-stu-id="b3ecb-104">How to: Create signed friend assemblies</span></span>

<span data-ttu-id="b3ecb-105">Cet exemple montre comment utiliser des assemblys friend avec des assemblys ayant des noms forts.</span><span class="sxs-lookup"><span data-stu-id="b3ecb-105">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="b3ecb-106">Les deux assemblys doivent avoir des noms forts.</span><span class="sxs-lookup"><span data-stu-id="b3ecb-106">Both assemblies must be strong named.</span></span> <span data-ttu-id="b3ecb-107">Bien que les deux assemblys dans cet exemple utilisent les mêmes clés, vous pouvez utiliser des clés différentes pour deux assemblys.</span><span class="sxs-lookup"><span data-stu-id="b3ecb-107">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
## <a name="create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="b3ecb-108">Créer un assembly signé et un assembly friend</span><span class="sxs-lookup"><span data-stu-id="b3ecb-108">Create a signed assembly and a friend assembly</span></span>  
  
1. <span data-ttu-id="b3ecb-109">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="b3ecb-109">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="b3ecb-110">Utilisez la séquence de commandes suivante avec l’outil Strong Name Tool pour générer un fichier de clé et afficher sa clé publique.</span><span class="sxs-lookup"><span data-stu-id="b3ecb-110">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="b3ecb-111">Pour plus d’informations, consultez [Sn.exe (outil Strong Name Tool)](../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="b3ecb-111">For more information, see [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
    1. <span data-ttu-id="b3ecb-112">Générez une clé de nom fort pour cet exemple et stockez-la dans le fichier *FriendAssemblies. snk*:</span><span class="sxs-lookup"><span data-stu-id="b3ecb-112">Generate a strong-name key for this example and store it in the file *FriendAssemblies.snk*:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2. <span data-ttu-id="b3ecb-113">Extrayez la clé publique de *FriendAssemblies. snk* et placez-la dans *FriendAssemblies. PublicKey*:</span><span class="sxs-lookup"><span data-stu-id="b3ecb-113">Extract the public key from *FriendAssemblies.snk* and put it into *FriendAssemblies.publickey*:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. <span data-ttu-id="b3ecb-114">Affichez la clé publique stockée dans le fichier *FriendAssemblies. PublicKey*:</span><span class="sxs-lookup"><span data-stu-id="b3ecb-114">Display the public key stored in the file *FriendAssemblies.publickey*:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. <span data-ttu-id="b3ecb-115">Créez un fichier C# ou Visual Basic nommé *friend_signed_A* qui contient le code suivant.</span><span class="sxs-lookup"><span data-stu-id="b3ecb-115">Create a C# or Visual Basic file named *friend_signed_A* that contains the following code.</span></span> <span data-ttu-id="b3ecb-116">Le code utilise l' <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribut pour déclarer *friend_signed_B* comme un assembly friend.</span><span class="sxs-lookup"><span data-stu-id="b3ecb-116">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_signed_B* as a friend assembly.</span></span>  

   <span data-ttu-id="b3ecb-117">L’outil Strong Name Tool génère une nouvelle clé publique chaque fois qu’il s’exécute.</span><span class="sxs-lookup"><span data-stu-id="b3ecb-117">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="b3ecb-118">Vous devez donc remplacer la clé publique dans le code suivant par la clé publique que vous venez de générer, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b3ecb-118">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  

   ```csharp  
   // friend_signed_A.cs  
   // Compile with:
   // csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   using System.Runtime.CompilerServices;  

   [assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")]  
   class Class1  
   {  
       public void Test()  
       {  
           System.Console.WriteLine("Class1.Test");  
           System.Console.ReadLine();  
       }  
   }  
   ```  

   ```vb  
   ' friend_signed_A.vb  
   ' Compile with:
   ' Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   Imports System.Runtime.CompilerServices  

   <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>
   Public Class Class1  
       Public Sub Test()  
           System.Console.WriteLine("Class1.Test")  
           System.Console.ReadLine()  
       End Sub  
   End Class  
   ```  

4. <span data-ttu-id="b3ecb-119">Compilez et signez *friend_signed_A* à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="b3ecb-119">Compile and sign *friend_signed_A* by using the following command.</span></span>  

   ```csharp
   csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   ```  

   ```vb
   Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   ```  

5. <span data-ttu-id="b3ecb-120">Créez un fichier C# ou Visual Basic nommé *friend_signed_B* qui contient le code suivant.</span><span class="sxs-lookup"><span data-stu-id="b3ecb-120">Create a C# or Visual Basic file named *friend_signed_B* that contains the following code.</span></span> <span data-ttu-id="b3ecb-121">Étant donné que *friend_signed_A* spécifie *friend_signed_B* comme assembly friend, le code dans *friend_signed_B* peut accéder aux `internal` types et aux membres (C#) ou `Friend` (Visual Basic) à partir de *friend_signed_A*.</span><span class="sxs-lookup"><span data-stu-id="b3ecb-121">Because *friend_signed_A* specifies *friend_signed_B* as a friend assembly, the code in *friend_signed_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_signed_A*.</span></span> <span data-ttu-id="b3ecb-122">Le fichier contient le code suivant.</span><span class="sxs-lookup"><span data-stu-id="b3ecb-122">The file contains the following code.</span></span>  

   ```csharp  
   // friend_signed_B.cs  
   // Compile with:
   // csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   public class Program  
   {  
       static void Main()  
       {  
           Class1 inst = new Class1();  
           inst.Test();  
       }  
   }  
   ```  

   ```vb  
   ' friend_signed_B.vb  
   ' Compile with:
   ' Vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   Module Sample  
       Public Sub Main()  
           Dim inst As New Class1  
           inst.Test()  
       End Sub  
   End Module  
   ```  

6. <span data-ttu-id="b3ecb-123">Compilez et signez *friend_signed_B* à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="b3ecb-123">Compile and sign *friend_signed_B* by using the following command.</span></span>  

   ```csharp
   csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   ```  

   ```vb
   vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   ```  

   <span data-ttu-id="b3ecb-124">Le nom de l’assembly généré par le compilateur doit correspondre au nom de l’assembly friend passé à l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b3ecb-124">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="b3ecb-125">Vous devez spécifier explicitement le nom de l’assembly de sortie (*. exe* ou *. dll*) à l’aide de l' `-out` option du compilateur.</span><span class="sxs-lookup"><span data-stu-id="b3ecb-125">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `-out` compiler option.</span></span> <span data-ttu-id="b3ecb-126">Pour plus d’informations, consultez [-out (options du compilateur C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) ou [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="b3ecb-126">For more information, see [-out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>  

7. <span data-ttu-id="b3ecb-127">Exécutez le fichier *friend_signed_B.exe* .</span><span class="sxs-lookup"><span data-stu-id="b3ecb-127">Run the *friend_signed_B.exe* file.</span></span>  

   <span data-ttu-id="b3ecb-128">Le programme génère la chaîne **Class1. test**.</span><span class="sxs-lookup"><span data-stu-id="b3ecb-128">The program outputs the string **Class1.Test**.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="b3ecb-129">Sécurité .NET</span><span class="sxs-lookup"><span data-stu-id="b3ecb-129">.NET security</span></span>  

 <span data-ttu-id="b3ecb-130">Il existe des similitudes entre l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> et la classe <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="b3ecb-130">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="b3ecb-131">La principale différence est que <xref:System.Security.Permissions.StrongNameIdentityPermission> peut demander des autorisations de sécurité pour exécuter une section de code particulière, alors que l' <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribut contrôle la visibilité des `internal` types et des membres (C#) ou `Friend` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="b3ecb-131">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3ecb-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3ecb-132">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="b3ecb-133">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="b3ecb-133">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="b3ecb-134">Assemblys friend</span><span class="sxs-lookup"><span data-stu-id="b3ecb-134">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="b3ecb-135">Comment : créer des assemblys friend non signés</span><span class="sxs-lookup"><span data-stu-id="b3ecb-135">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="b3ecb-136">-keyfile (C#)</span><span class="sxs-lookup"><span data-stu-id="b3ecb-136">-keyfile (C#)</span></span>](../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [<span data-ttu-id="b3ecb-137">-keyfile (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3ecb-137">-keyfile (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="b3ecb-138">Sn.exe (outil Strong Name Tool)</span><span class="sxs-lookup"><span data-stu-id="b3ecb-138">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="b3ecb-139">Créer et utiliser des assemblys avec nom fort</span><span class="sxs-lookup"><span data-stu-id="b3ecb-139">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="b3ecb-140">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="b3ecb-140">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="b3ecb-141">Concepts de programmation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3ecb-141">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
