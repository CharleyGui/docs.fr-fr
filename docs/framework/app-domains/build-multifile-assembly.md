---
title: 'Comment : générer un assembly multifichier'
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- Al.exe
- command-line compilers
- assembly manifest, multifile assemblies
- assemblies [.NET Framework], compiling
- Assembly Linker
- code modules
- multifile assemblies
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
ms.openlocfilehash: 0f8c6d57425657e321d80f9edffa20f27bc28770
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429558"
---
# <a name="how-to-build-a-multifile-assembly"></a><span data-ttu-id="36535-102">Comment : générer un assembly multifichier</span><span class="sxs-lookup"><span data-stu-id="36535-102">How to: Build a multifile assembly</span></span>

<span data-ttu-id="36535-103">Cet article explique comment créer un assembly multifichier et fournit le code illustrant chaque étape de la procédure.</span><span class="sxs-lookup"><span data-stu-id="36535-103">This article explains how to create a multifile assembly and provides code that illustrates each step in the procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="36535-104">L'IDE de Visual Studio pour C# et Visual Basic ne peut être utilisé que pour créer des assemblys à fichier unique.</span><span class="sxs-lookup"><span data-stu-id="36535-104">The Visual Studio IDE for C# and Visual Basic can only be used to create single-file assemblies.</span></span> <span data-ttu-id="36535-105">Si vous souhaitez créer des assemblys multifichiers, vous devez utiliser les compilateurs de ligne de commande ou Visual Studio avec Visual C++.</span><span class="sxs-lookup"><span data-stu-id="36535-105">If you want to create multifile assemblies, you must use the command-line compilers or Visual Studio with Visual C++.</span></span> <span data-ttu-id="36535-106">Les assemblys multifichiers sont pris en charge par .NET Framework uniquement.</span><span class="sxs-lookup"><span data-stu-id="36535-106">Multifile assemblies are supported by .NET Framework only.</span></span>

## <a name="create-a-multifile-assembly"></a><span data-ttu-id="36535-107">Créer un assembly multifichier</span><span class="sxs-lookup"><span data-stu-id="36535-107">Create a multifile assembly</span></span>

1. <span data-ttu-id="36535-108">Compilez tous les fichiers contenant des espaces de noms référencés par d'autres modules de l'assembly dans des modules de code.</span><span class="sxs-lookup"><span data-stu-id="36535-108">Compile all files that contain namespaces referenced by other modules in the assembly into code modules.</span></span> <span data-ttu-id="36535-109">L’extension par défaut pour les modules de code est *. netmodule*.</span><span class="sxs-lookup"><span data-stu-id="36535-109">The default extension for code modules is *.netmodule*.</span></span>

   <span data-ttu-id="36535-110">Par exemple, supposons que le fichier `Stringer` a un espace de noms appelé `myStringer`, qui inclut une classe appelée `Stringer`.</span><span class="sxs-lookup"><span data-stu-id="36535-110">For example, let's say the `Stringer` file has a namespace called `myStringer`, which includes a class called `Stringer`.</span></span> <span data-ttu-id="36535-111">La classe `Stringer` contient une méthode appelée `StringerMethod` qui écrit une seule ligne dans la console.</span><span class="sxs-lookup"><span data-stu-id="36535-111">The `Stringer` class contains a method called `StringerMethod` that writes a single line to the console.</span></span>

   ```cpp
   // Assembly building example in the .NET Framework.
   using namespace System;

   namespace myStringer
   {
       public ref class Stringer
       {
       public:
           void StringerMethod()
           {
               System::Console::WriteLine("This is a line from StringerMethod.");
           }
       };
   }
   ```

   ```csharp
   // Assembly building example in the .NET Framework.
   using System;

   namespace myStringer
   {
       public class Stringer
       {
           public void StringerMethod()
           {
               System.Console.WriteLine("This is a line from StringerMethod.");
           }
       }
   }
   ```

   ```vb
   ' Assembly building example in the .NET Framework.
   Namespace myStringer
       Public Class Stringer
           Public Sub StringerMethod()
               System.Console.WriteLine("This is a line from StringerMethod.")
           End Sub
       End Class
   End Namespace
   ```

2. <span data-ttu-id="36535-112">Utilisez la commande suivante pour compiler ce code :</span><span class="sxs-lookup"><span data-stu-id="36535-112">Use the following command to compile this code:</span></span>

   ```cpp
   cl /clr:pure /LN Stringer.cpp
   ```

   ```csharp
   csc /t:module Stringer.cs
   ```

   ```vb
   vbc /t:module Stringer.vb
   ```

   <span data-ttu-id="36535-113">La spécification du paramètre *module* à l’aide de l’option du compilateur **/t:** indique que le fichier doit être compilé comme module et non comme assembly.</span><span class="sxs-lookup"><span data-stu-id="36535-113">Specifying the *module* parameter with the **/t:** compiler option indicates that the file should be compiled as a module rather than as an assembly.</span></span> <span data-ttu-id="36535-114">Le compilateur produit un module appelé *Stringer. netmodule*, qui peut être ajouté à un assembly.</span><span class="sxs-lookup"><span data-stu-id="36535-114">The compiler produces a module called *Stringer.netmodule*, which can be added to an assembly.</span></span>

3. <span data-ttu-id="36535-115">Compilez tous les autres modules à l'aide des options du compilateur nécessaires pour indiquer les autres modules référencés dans le code.</span><span class="sxs-lookup"><span data-stu-id="36535-115">Compile all other modules, using the necessary compiler options to indicate the other modules that are referenced in the code.</span></span> <span data-ttu-id="36535-116">Cette étape utilise l’option du compilateur **/addmodule**.</span><span class="sxs-lookup"><span data-stu-id="36535-116">This step uses the **/addmodule** compiler option.</span></span>

   <span data-ttu-id="36535-117">Dans l’exemple suivant, un module de code appelé *client* a une méthode `Main` de point d’entrée qui fait référence à une méthode dans le module *Stringer. dll* créé à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="36535-117">In the following example, a code module called *Client* has an entry point `Main` method that references a method in the *Stringer.dll* module created in step 1.</span></span>

   ```cpp
   #using "Stringer.netmodule"

   using namespace System;
   using namespace myStringer; //The namespace created in Stringer.netmodule.

   ref class MainClientApp
   {
       // Static method Main is the entry point method.
   public:
       static void Main()
       {
           Stringer^ myStringInstance = gcnew Stringer();
           Console::WriteLine("Client code executes");
           myStringInstance->StringerMethod();
       }
   };

   int main()
   {
       MainClientApp::Main();
   }
   ```

   ```csharp
   using System;
   using myStringer;

   class MainClientApp
   {
       // Static method Main is the entry point method.
       public static void Main()
       {
           Stringer myStringInstance = new Stringer();
           Console.WriteLine("Client code executes");
           myStringInstance.StringerMethod();
       }
   }
   ```

   ```vb
   Imports myStringer

   Class MainClientApp
       ' Static method Main is the entry point method.
       Public Shared Sub Main()
           Dim myStringInstance As New Stringer()
           Console.WriteLine("Client code executes")
           myStringInstance.StringerMethod()
       End Sub
   End Class
   ```

4. <span data-ttu-id="36535-118">Utilisez la commande suivante pour compiler ce code :</span><span class="sxs-lookup"><span data-stu-id="36535-118">Use the following command to compile this code:</span></span>

   ```cpp
   cl /clr:pure /FUStringer.netmodule /LN Client.cpp
   ```

   ```csharp
   csc /addmodule:Stringer.netmodule /t:module Client.cs
   ```

   ```vb
   vbc /addmodule:Stringer.netmodule /t:module Client.vb
   ```

   <span data-ttu-id="36535-119">Spécifiez l’option **/t:module**, car ce module sera ajouté à un assembly lors d’une étape ultérieure.</span><span class="sxs-lookup"><span data-stu-id="36535-119">Specify the **/t:module** option because this module will be added to an assembly in a future step.</span></span> <span data-ttu-id="36535-120">Spécifiez l’option **/addmodule** , car le code du *client* référence un espace de noms créé par le code dans *Stringer. netmodule*.</span><span class="sxs-lookup"><span data-stu-id="36535-120">Specify the **/addmodule** option because the code in *Client* references a namespace created by the code in *Stringer.netmodule*.</span></span> <span data-ttu-id="36535-121">Le compilateur produit un module appelé *client. netmodule* qui contient une référence à un autre module, *Stringer. netmodule*.</span><span class="sxs-lookup"><span data-stu-id="36535-121">The compiler produces a module called *Client.netmodule* that contains a reference to another module, *Stringer.netmodule*.</span></span>

   > [!NOTE]
   > <span data-ttu-id="36535-122">Les compilateurs C# et Visual Basic prennent en charge la création directe d'assemblys multifichiers à l'aide de deux syntaxes différentes.</span><span class="sxs-lookup"><span data-stu-id="36535-122">The C# and Visual Basic compilers support directly creating multifile assemblies using the following two different syntaxes.</span></span>
   >
   > <span data-ttu-id="36535-123">Deux compilations créent un assembly à deux fichiers :</span><span class="sxs-lookup"><span data-stu-id="36535-123">Two compilations create a two-file assembly:</span></span>
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /t:module Stringer.cs
   >   csc Client.cs /addmodule:Stringer.netmodule
   >   ```
   >
   >   ```vb
   >   vbc /t:module Stringer.vb
   >   vbc Client.vb /addmodule:Stringer.netmodule
   >   ```
   >
   > <span data-ttu-id="36535-124">Une compilation crée un assembly à deux fichiers :</span><span class="sxs-lookup"><span data-stu-id="36535-124">One compilation creates a two-file assembly:</span></span>
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /out:Client.exe Client.cs /out:Stringer.netmodule Stringer.cs
   >   ```
   >
   >   ```vb
   >   vbc /out:Client.exe Client.vb /out:Stringer.netmodule Stringer.vb
   >   ```

5. <span data-ttu-id="36535-125">Utilisez l’utilitaire [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) pour créer le fichier de sortie qui contient le manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="36535-125">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the output file that contains the assembly manifest.</span></span> <span data-ttu-id="36535-126">Ce fichier contient des informations sur les références de tous les modules ou ressources faisant partie de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="36535-126">This file contains reference information for all modules or resources that are part of the assembly.</span></span>

    <span data-ttu-id="36535-127">Saisissez ensuite la commande suivante dans l’invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="36535-127">At the command prompt, type the following command:</span></span>

    <span data-ttu-id="36535-128">\<*module name* **al** \<nom du module al nom du module>... *module name*> </span><span class="sxs-lookup"><span data-stu-id="36535-128">**al** \<*module name*> \<*module name*> …</span></span> <span data-ttu-id="36535-129">**/main :**\<*nom*> de méthode **/out :**\<*nom*> de fichier **/target :**\<*type de fichier d’assembly*></span><span class="sxs-lookup"><span data-stu-id="36535-129">**/main:**\<*method name*> **/out:**\<*file name*> **/target:**\<*assembly file type*></span></span>

    <span data-ttu-id="36535-130">Dans cette commande, les arguments *nom_module* spécifient le nom de chaque module à inclure dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="36535-130">In this command, the *module name* arguments specify the name of each module to include in the assembly.</span></span> <span data-ttu-id="36535-131">L’option **/main:** spécifie le nom de la méthode représentant le point d’entrée de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="36535-131">The **/main:** option specifies the method name that is the assembly's entry point.</span></span> <span data-ttu-id="36535-132">L’option **/out:** spécifie le nom du fichier de sortie, qui contient les métadonnées de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="36535-132">The **/out:** option specifies the name of the output file, which contains assembly metadata.</span></span> <span data-ttu-id="36535-133">L’option **/target :** spécifie que l’assembly est un fichier exécutable (*. exe*) d’application console, un fichier exécutable Windows (*. Win*) ou un fichier de bibliothèque (*. lib*).</span><span class="sxs-lookup"><span data-stu-id="36535-133">The **/target:** option specifies that the assembly is a console application executable (*.exe*) file, a Windows executable (*.win*) file, or a library (*.lib*) file.</span></span>

    <span data-ttu-id="36535-134">Dans l’exemple suivant, *al. exe* crée un assembly qui est un exécutable d’application console appelé *myAssembly. exe*.</span><span class="sxs-lookup"><span data-stu-id="36535-134">In the following example, *Al.exe* creates an assembly that is a console application executable called *myAssembly.exe*.</span></span> <span data-ttu-id="36535-135">L’application se compose de deux modules appelés *client. netmodule* et *Stringer. netmodule*, et du fichier exécutable appelé *myAssembly. exe*, qui contient uniquement les métadonnées de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="36535-135">The application consists of two modules called *Client.netmodule* and *Stringer.netmodule*, and the executable file called *myAssembly.exe*, which contains only assembly metadata.</span></span> <span data-ttu-id="36535-136">Le point d’entrée de l’assembly `Main` est la méthode de `MainClientApp`la classe, qui se trouve dans *client. dll*.</span><span class="sxs-lookup"><span data-stu-id="36535-136">The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in *Client.dll*.</span></span>

    ```cmd
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    <span data-ttu-id="36535-137">Vous pouvez utiliser le [Désassembleur MSIL (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) pour examiner le contenu d’un assembly ou déterminer si un fichier est un assembly ou un module.</span><span class="sxs-lookup"><span data-stu-id="36535-137">You can use the [MSIL Disassembler (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) to examine the contents of an assembly, or determine whether a file is an assembly or a module.</span></span>

## <a name="see-also"></a><span data-ttu-id="36535-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36535-138">See also</span></span>

- [<span data-ttu-id="36535-139">Créer des assemblys</span><span class="sxs-lookup"><span data-stu-id="36535-139">Create assemblies</span></span>](../../standard/assembly/create.md)
- [<span data-ttu-id="36535-140">Comment : afficher le contenu d’un assembly</span><span class="sxs-lookup"><span data-stu-id="36535-140">How to: View assembly contents</span></span>](../../standard/assembly/view-contents.md)
- [<span data-ttu-id="36535-141">Comment le runtime localise les assemblys</span><span class="sxs-lookup"><span data-stu-id="36535-141">How the runtime locates assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="36535-142">Assemblys multifichiers</span><span class="sxs-lookup"><span data-stu-id="36535-142">Multifile assemblies</span></span>](multifile-assemblies.md)
