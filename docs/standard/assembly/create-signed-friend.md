---
title: 'Procédure : Créer des assemblys friend signés'
ms.date: 08/19/2019
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
dev_langs:
- csharp
- vb
ms.openlocfilehash: 19c301c6b96e1070447401af9105fba2e0f0837f
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973361"
---
# <a name="how-to-create-signed-friend-assemblies"></a><span data-ttu-id="856b3-102">Procédure : Créer des assemblys friend signés</span><span class="sxs-lookup"><span data-stu-id="856b3-102">How to: Create signed friend assemblies</span></span>
<span data-ttu-id="856b3-103">Cet exemple montre comment utiliser des assemblys friend avec des assemblys ayant des noms forts.</span><span class="sxs-lookup"><span data-stu-id="856b3-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="856b3-104">Les deux assemblys doivent avoir des noms forts.</span><span class="sxs-lookup"><span data-stu-id="856b3-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="856b3-105">Bien que les deux assemblys dans cet exemple utilisent les mêmes clés, vous pouvez utiliser des clés différentes pour deux assemblys.</span><span class="sxs-lookup"><span data-stu-id="856b3-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
## <a name="create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="856b3-106">Créer un assembly signé et un assembly friend</span><span class="sxs-lookup"><span data-stu-id="856b3-106">Create a signed assembly and a friend assembly</span></span>  
  
1. <span data-ttu-id="856b3-107">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="856b3-107">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="856b3-108">Utilisez la séquence de commandes suivante avec l’outil Strong Name Tool pour générer un fichier de clé et afficher sa clé publique.</span><span class="sxs-lookup"><span data-stu-id="856b3-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="856b3-109">Pour plus d’informations, consultez [sn. exe (Strong Name Tool)](../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="856b3-109">For more information, see [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
    1. <span data-ttu-id="856b3-110">Générez une clé de nom fort pour cet exemple et stockez-la dans le fichier *FriendAssemblies. snk*:</span><span class="sxs-lookup"><span data-stu-id="856b3-110">Generate a strong-name key for this example and store it in the file *FriendAssemblies.snk*:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2. <span data-ttu-id="856b3-111">Extrayez la clé publique de *FriendAssemblies. snk* et placez-la dans *FriendAssemblies. PublicKey*:</span><span class="sxs-lookup"><span data-stu-id="856b3-111">Extract the public key from *FriendAssemblies.snk* and put it into *FriendAssemblies.publickey*:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. <span data-ttu-id="856b3-112">Affichez la clé publique stockée dans le fichier *FriendAssemblies. PublicKey*:</span><span class="sxs-lookup"><span data-stu-id="856b3-112">Display the public key stored in the file *FriendAssemblies.publickey*:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. <span data-ttu-id="856b3-113">Créez un C# fichier ou Visual Basic nommé *friend_signed_A* qui contient le code suivant.</span><span class="sxs-lookup"><span data-stu-id="856b3-113">Create a C# or Visual Basic file named *friend_signed_A* that contains the following code.</span></span> <span data-ttu-id="856b3-114">Le code utilise l' <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribut pour déclarer *friend_signed_B* comme assembly friend.</span><span class="sxs-lookup"><span data-stu-id="856b3-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_signed_B* as a friend assembly.</span></span>  
   
   <span data-ttu-id="856b3-115">L’outil Strong Name Tool génère une nouvelle clé publique chaque fois qu’il s’exécute.</span><span class="sxs-lookup"><span data-stu-id="856b3-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="856b3-116">Vous devez donc remplacer la clé publique dans le code suivant par la clé publique que vous venez de générer, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="856b3-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  
   
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
   
4. <span data-ttu-id="856b3-117">Compilez et signez *friend_signed_A* à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="856b3-117">Compile and sign *friend_signed_A* by using the following command.</span></span>  
   
   ```csharp
   csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   ```  
   
   ```vb
   Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   ```  
   
5. <span data-ttu-id="856b3-118">Créez un C# fichier ou Visual Basic nommé *friend_signed_B* qui contient le code suivant.</span><span class="sxs-lookup"><span data-stu-id="856b3-118">Create a C# or Visual Basic file named *friend_signed_B* that contains the following code.</span></span> <span data-ttu-id="856b3-119">Étant donné que *friend_signed_A* spécifie *friend_signed_B* comme assembly friend, le code de `internal` *friend_signed_B* peut accéder aux types et aux membres (C#) ou `Friend` (Visual Basic) à partir de *friend_signed_A*.</span><span class="sxs-lookup"><span data-stu-id="856b3-119">Because *friend_signed_A* specifies *friend_signed_B* as a friend assembly, the code in *friend_signed_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_signed_A*.</span></span> <span data-ttu-id="856b3-120">Le fichier contient le code suivant.</span><span class="sxs-lookup"><span data-stu-id="856b3-120">The file contains the following code.</span></span>  
   
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
   
6. <span data-ttu-id="856b3-121">Compilez et signez *friend_signed_B* à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="856b3-121">Compile and sign *friend_signed_B* by using the following command.</span></span>  
   
   ```csharp
   csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   ```  
   
   ```vb
   vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   ```  
   
   <span data-ttu-id="856b3-122">Le nom de l’assembly généré par le compilateur doit correspondre au nom de l’assembly friend passé à l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="856b3-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="856b3-123">Vous devez spécifier explicitement le nom de l’assembly de sortie ( *. exe* ou *. dll*) à `/out` l’aide de l’option du compilateur.</span><span class="sxs-lookup"><span data-stu-id="856b3-123">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `/out` compiler option.</span></span> <span data-ttu-id="856b3-124">Pour plus d’informations, consultez [/outC# (options du compilateur)](../../csharp/language-reference/compiler-options/out-compiler-option.md) ou [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="856b3-124">For more information, see [/out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>  
   
7. <span data-ttu-id="856b3-125">Exécutez le fichier *friend_signed_B. exe* .</span><span class="sxs-lookup"><span data-stu-id="856b3-125">Run the *friend_signed_B.exe* file.</span></span>  
   
   <span data-ttu-id="856b3-126">Le programme génère la chaîne **Class1. test**.</span><span class="sxs-lookup"><span data-stu-id="856b3-126">The program outputs the string **Class1.Test**.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="856b3-127">Sécurité .NET</span><span class="sxs-lookup"><span data-stu-id="856b3-127">.NET security</span></span>  
 <span data-ttu-id="856b3-128">Il existe des similitudes entre l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> et la classe <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="856b3-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="856b3-129">La principale différence est que <xref:System.Security.Permissions.StrongNameIdentityPermission> peut demander des autorisations de sécurité pour exécuter une section de code particulière, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> alors que l’attribut contrôle laC#visibilité des `Friend` types et des `internal` membres () ou (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="856b3-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="856b3-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="856b3-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="856b3-131">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="856b3-131">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="856b3-132">Assemblys friend</span><span class="sxs-lookup"><span data-stu-id="856b3-132">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="856b3-133">Guide pratique : Créer des assemblys friend non signés</span><span class="sxs-lookup"><span data-stu-id="856b3-133">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="856b3-134">/keyfile (C#)</span><span class="sxs-lookup"><span data-stu-id="856b3-134">/keyfile (C#)</span></span>](../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [<span data-ttu-id="856b3-135">-keyfile (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="856b3-135">-keyfile (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="856b3-136">SN. exe (outil Strong Name Tool)</span><span class="sxs-lookup"><span data-stu-id="856b3-136">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="856b3-137">Créer et utiliser des assemblys avec nom fort</span><span class="sxs-lookup"><span data-stu-id="856b3-137">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="856b3-138">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="856b3-138">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="856b3-139">Concepts de programmation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="856b3-139">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
