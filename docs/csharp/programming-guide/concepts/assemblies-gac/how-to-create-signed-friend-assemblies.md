---
title: 'Procédure : Créer des assemblys friend signés (C#)'
ms.date: 07/20/2015
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
ms.openlocfilehash: 7715726a200150b044fb8e97216fa02d0e784838
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595929"
---
# <a name="how-to-create-signed-friend-assemblies-c"></a><span data-ttu-id="f5159-102">Procédure : Créer des assemblys friend signés (C#)</span><span class="sxs-lookup"><span data-stu-id="f5159-102">How to: Create Signed Friend Assemblies (C#)</span></span>
<span data-ttu-id="f5159-103">Cet exemple montre comment utiliser des assemblys friend avec des assemblys ayant des noms forts.</span><span class="sxs-lookup"><span data-stu-id="f5159-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="f5159-104">Les deux assemblys doivent avoir des noms forts.</span><span class="sxs-lookup"><span data-stu-id="f5159-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="f5159-105">Bien que les deux assemblys dans cet exemple utilisent les mêmes clés, vous pouvez utiliser des clés différentes pour deux assemblys.</span><span class="sxs-lookup"><span data-stu-id="f5159-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="f5159-106">Pour créer un assembly signé et un assembly friend</span><span class="sxs-lookup"><span data-stu-id="f5159-106">To create a signed assembly and a friend assembly</span></span>  
  
1. <span data-ttu-id="f5159-107">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="f5159-107">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="f5159-108">Utilisez la séquence de commandes suivante avec l’outil Strong Name Tool pour générer un fichier de clé et afficher sa clé publique.</span><span class="sxs-lookup"><span data-stu-id="f5159-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="f5159-109">Pour plus d’informations, consultez [Sn.exe (Strong Name Tool)](../../../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="f5159-109">For more information, see [Sn.exe (Strong Name Tool)](../../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
    1. <span data-ttu-id="f5159-110">Générez une clé de nom fort pour cet exemple et stockez-la dans le fichier FriendAssemblies.snk :</span><span class="sxs-lookup"><span data-stu-id="f5159-110">Generate a strong-name key for this example and store it in the file FriendAssemblies.snk:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2. <span data-ttu-id="f5159-111">Extrayez la clé publique de FriendAssemblies.snk et mettez-la dans FriendAssemblies.publickey :</span><span class="sxs-lookup"><span data-stu-id="f5159-111">Extract the public key from FriendAssemblies.snk and put it into FriendAssemblies.publickey:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. <span data-ttu-id="f5159-112">Affichez la clé publique stockée dans le fichier FriendAssemblies.publickey :</span><span class="sxs-lookup"><span data-stu-id="f5159-112">Display the public key stored in the file FriendAssemblies.publickey:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. <span data-ttu-id="f5159-113">Créez un fichier C# nommé `friend_signed_A` qui contient le code suivant.</span><span class="sxs-lookup"><span data-stu-id="f5159-113">Create a C# file named `friend_signed_A` that contains the following code.</span></span> <span data-ttu-id="f5159-114">Le code utilise l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> pour déclarer friend_signed_B comme assembly friend.</span><span class="sxs-lookup"><span data-stu-id="f5159-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare friend_signed_B as a friend assembly.</span></span>  
  
     <span data-ttu-id="f5159-115">L’outil Strong Name Tool génère une nouvelle clé publique chaque fois qu’il s’exécute.</span><span class="sxs-lookup"><span data-stu-id="f5159-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="f5159-116">Vous devez donc remplacer la clé publique dans le code suivant par la clé publique que vous venez de générer, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="f5159-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  
  
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
  
4. <span data-ttu-id="f5159-117">Compilez et signez friend_signed_A à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="f5159-117">Compile and sign friend_signed_A by using the following command.</span></span>  
  
    ```csharp  
    csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    ```  
  
5. <span data-ttu-id="f5159-118">Créez un fichier C# nommé `friend_signed_B` contenant le code suivant.</span><span class="sxs-lookup"><span data-stu-id="f5159-118">Create a C# file that is named `friend_signed_B` and contains the following code.</span></span> <span data-ttu-id="f5159-119">Étant donné que friend_signed_A spécifie friend_signed_B comme assembly friend, le code de friend_signed_B peut accéder aux membres et aux types `internal` de friend_signed_A.</span><span class="sxs-lookup"><span data-stu-id="f5159-119">Because friend_signed_A specifies friend_signed_B as a friend assembly, the code in friend_signed_B can access `internal` types and members from friend_signed_A.</span></span> <span data-ttu-id="f5159-120">Le fichier contient le code suivant.</span><span class="sxs-lookup"><span data-stu-id="f5159-120">The file contains the following code.</span></span>  
  
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
  
6. <span data-ttu-id="f5159-121">Compilez et signez friend_signed_B à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="f5159-121">Compile and sign friend_signed_B by using the following command.</span></span>  
  
    ```csharp  
    csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    ```  
  
     <span data-ttu-id="f5159-122">Le nom de l’assembly généré par le compilateur doit correspondre au nom de l’assembly friend passé à l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f5159-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="f5159-123">Vous devez spécifier explicitement le nom de l’assembly de sortie (.exe ou .dll) à l’aide de l’option du compilateur `/out`.</span><span class="sxs-lookup"><span data-stu-id="f5159-123">You must explicitly specify the name of the output assembly (.exe or .dll) by using the `/out` compiler option.</span></span>  <span data-ttu-id="f5159-124">Pour plus d’informations, consultez l’article [/out (C# Compiler Options) (/out [Options du compilateur C#])](../../../language-reference/compiler-options/out-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="f5159-124">For more information, see [/out (C# Compiler Options)](../../../language-reference/compiler-options/out-compiler-option.md).</span></span>  
  
7. <span data-ttu-id="f5159-125">Exécutez le fichier friend_signed_B.exe.</span><span class="sxs-lookup"><span data-stu-id="f5159-125">Run the friend_signed_B.exe file.</span></span>  
  
     <span data-ttu-id="f5159-126">Le programme imprime la chaîne « Class1.Test ».</span><span class="sxs-lookup"><span data-stu-id="f5159-126">The program prints the string "Class1.Test".</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f5159-127">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f5159-127">.NET Framework Security</span></span>  
 <span data-ttu-id="f5159-128">Il existe des similitudes entre l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> et la classe <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="f5159-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="f5159-129">La principale différence est que <xref:System.Security.Permissions.StrongNameIdentityPermission> peut demander des autorisations de sécurité pour exécuter une section de code particulière, tandis que l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> contrôle la visibilité des membres et types `internal`.</span><span class="sxs-lookup"><span data-stu-id="f5159-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5159-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5159-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="f5159-131">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="f5159-131">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
- [<span data-ttu-id="f5159-132">Assemblys friend</span><span class="sxs-lookup"><span data-stu-id="f5159-132">Friend Assemblies</span></span>](../../../../standard/assembly/friend-assemblies.md)
- [<span data-ttu-id="f5159-133">Guide pratique pour créer des assemblys friend non signés (C#)</span><span class="sxs-lookup"><span data-stu-id="f5159-133">How to: Create Unsigned Friend Assemblies (C#)</span></span>](./how-to-create-unsigned-friend-assemblies.md)
- [<span data-ttu-id="f5159-134">/keyfile</span><span class="sxs-lookup"><span data-stu-id="f5159-134">/keyfile</span></span>](../../../language-reference/compiler-options/keyfile-compiler-option.md)
- [<span data-ttu-id="f5159-135">Sn.exe (outil Strong Name)</span><span class="sxs-lookup"><span data-stu-id="f5159-135">Sn.exe (Strong Name Tool)</span></span>](../../../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="f5159-136">Création et utilisation d’assemblys avec nom fort</span><span class="sxs-lookup"><span data-stu-id="f5159-136">Creating and Using Strong-Named Assemblies</span></span>](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md)
- [<span data-ttu-id="f5159-137">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="f5159-137">C# Programming Guide</span></span>](../../index.md)
