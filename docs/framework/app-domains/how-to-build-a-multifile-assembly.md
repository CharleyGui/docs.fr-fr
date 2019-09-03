---
title: 'Procédure : générer un assembly multifichier'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
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
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a964e73cc41cebad33a3edc34b89ef240fbc62c8
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040854"
---
# <a name="how-to-build-a-multifile-assembly"></a><span data-ttu-id="94f73-102">Procédure : générer un assembly multifichier</span><span class="sxs-lookup"><span data-stu-id="94f73-102">How to: Build a Multifile Assembly</span></span>

<span data-ttu-id="94f73-103">Cet article explique comment créer un assembly multifichier et fournit le code illustrant chaque étape de la procédure.</span><span class="sxs-lookup"><span data-stu-id="94f73-103">This article explains how to create a multifile assembly and provides code that illustrates each step in the procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="94f73-104">L'IDE de Visual Studio pour C# et Visual Basic ne peut être utilisé que pour créer des assemblys à fichier unique.</span><span class="sxs-lookup"><span data-stu-id="94f73-104">The Visual Studio IDE for C# and Visual Basic can only be used to create single-file assemblies.</span></span> <span data-ttu-id="94f73-105">Si vous souhaitez créer des assemblys multifichiers, vous devez utiliser les compilateurs de ligne de commande ou Visual Studio avec Visual C++.</span><span class="sxs-lookup"><span data-stu-id="94f73-105">If you want to create multifile assemblies, you must use the command-line compilers or Visual Studio with Visual C++.</span></span>

### <a name="to-create-a-multifile-assembly"></a><span data-ttu-id="94f73-106">Pour créer un assembly multifichier</span><span class="sxs-lookup"><span data-stu-id="94f73-106">To create a multifile assembly</span></span>

01. <span data-ttu-id="94f73-107">Compilez tous les fichiers contenant des espaces de noms référencés par d'autres modules de l'assembly dans des modules de code.</span><span class="sxs-lookup"><span data-stu-id="94f73-107">Compile all files that contain namespaces referenced by other modules in the assembly into code modules.</span></span> <span data-ttu-id="94f73-108">L'extension par défaut pour les modules de code est .netmodule.</span><span class="sxs-lookup"><span data-stu-id="94f73-108">The default extension for code modules is .netmodule.</span></span>

    <span data-ttu-id="94f73-109">Par exemple, supposons que le fichier `Stringer` a un espace de noms appelé `myStringer`, qui inclut une classe appelée `Stringer`.</span><span class="sxs-lookup"><span data-stu-id="94f73-109">For example, let's say the `Stringer` file has a namespace called `myStringer`, which includes a class called `Stringer`.</span></span> <span data-ttu-id="94f73-110">La classe `Stringer` contient une méthode appelée `StringerMethod` qui écrit une seule ligne dans la console.</span><span class="sxs-lookup"><span data-stu-id="94f73-110">The `Stringer` class contains a method called `StringerMethod` that writes a single line to the console.</span></span>

    [!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]
    [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]
    [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]

    <span data-ttu-id="94f73-111">Utilisez la commande suivante pour compiler ce code :</span><span class="sxs-lookup"><span data-stu-id="94f73-111">Use the following command to compile this code:</span></span>

    [!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]
    [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]
    [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]

    <span data-ttu-id="94f73-112">La spécification du paramètre *module* à l’aide de l’option du compilateur **/t:** indique que le fichier doit être compilé comme module et non comme assembly.</span><span class="sxs-lookup"><span data-stu-id="94f73-112">Specifying the *module* parameter with the **/t:** compiler option indicates that the file should be compiled as a module rather than as an assembly.</span></span> <span data-ttu-id="94f73-113">Le compilateur produit un module appelé `Stringer.netmodule`, qui peut être ajouté à un assembly.</span><span class="sxs-lookup"><span data-stu-id="94f73-113">The compiler produces a module called `Stringer.netmodule`, which can be added to an assembly.</span></span>

02. <span data-ttu-id="94f73-114">Compilez tous les autres modules à l'aide des options du compilateur nécessaires pour indiquer les autres modules référencés dans le code.</span><span class="sxs-lookup"><span data-stu-id="94f73-114">Compile all other modules, using the necessary compiler options to indicate the other modules that are referenced in the code.</span></span> <span data-ttu-id="94f73-115">Cette étape utilise l’option du compilateur **/addmodule**.</span><span class="sxs-lookup"><span data-stu-id="94f73-115">This step uses the **/addmodule** compiler option.</span></span>

    <span data-ttu-id="94f73-116">Dans l'exemple suivant, un module de code appelé `Client` a une méthode `Main` de point d'entrée, qui référence une méthode du module `Stringer.dll` créé à l'étape 1.</span><span class="sxs-lookup"><span data-stu-id="94f73-116">In the following example, a code module called `Client` has an entry point `Main` method that references a method in the `Stringer.dll` module created in step 1.</span></span>

    [!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]
    [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]
    [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]

    <span data-ttu-id="94f73-117">Utilisez la commande suivante pour compiler ce code :</span><span class="sxs-lookup"><span data-stu-id="94f73-117">Use the following command to compile this code:</span></span>

    [!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]
    [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]
    [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]

    <span data-ttu-id="94f73-118">Spécifiez l’option **/t:module**, car ce module sera ajouté à un assembly lors d’une étape ultérieure.</span><span class="sxs-lookup"><span data-stu-id="94f73-118">Specify the **/t:module** option because this module will be added to an assembly in a future step.</span></span> <span data-ttu-id="94f73-119">Spécifiez l’option **/addmodule**, car le code dans `Client`  référence un espace de noms créé par le code dans `Stringer.netmodule`.</span><span class="sxs-lookup"><span data-stu-id="94f73-119">Specify the **/addmodule** option because the code in `Client` references a namespace created by the code in `Stringer.netmodule`.</span></span> <span data-ttu-id="94f73-120">Le compilateur produit un module appelé `Client.netmodule` qui contient une référence à un autre module, `Stringer.netmodule`.</span><span class="sxs-lookup"><span data-stu-id="94f73-120">The compiler produces a module called `Client.netmodule` that contains a reference to another module, `Stringer.netmodule`.</span></span>

    >[!NOTE]
    ><span data-ttu-id="94f73-121">Les compilateurs C# et Visual Basic prennent en charge la création directe d'assemblys multifichiers à l'aide de deux syntaxes différentes.</span><span class="sxs-lookup"><span data-stu-id="94f73-121">The C# and Visual Basic compilers support directly creating multifile assemblies using the following two different syntaxes.</span></span>
    >
    >- <span data-ttu-id="94f73-122">Deux compilations créent un assembly à deux fichiers : [!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]</span><span class="sxs-lookup"><span data-stu-id="94f73-122">Two compilations create a two-file assembly: [!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]</span></span>
    >  [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]
    >  [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]
    >
    >- <span data-ttu-id="94f73-123">Une compilation crée un assembly à deux fichiers : [!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]</span><span class="sxs-lookup"><span data-stu-id="94f73-123">One compilation creates a two-file assembly: [!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]</span></span>
    >  [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]
    >  [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]

03. <span data-ttu-id="94f73-124">Utilisez l’utilitaire [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) pour créer le fichier de sortie qui contient le manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="94f73-124">Use the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to create the output file that contains the assembly manifest.</span></span> <span data-ttu-id="94f73-125">Ce fichier contient des informations sur les références de tous les modules ou ressources faisant partie de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="94f73-125">This file contains reference information for all modules or resources that are part of the assembly.</span></span>

    <span data-ttu-id="94f73-126">À l'invite de commandes, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="94f73-126">At the command prompt, type the following command:</span></span>

    <span data-ttu-id="94f73-127">**al** \<*nom_module*> \<*nom_module*> …</span><span class="sxs-lookup"><span data-stu-id="94f73-127">**al** \<*module name*> \<*module name*> …</span></span> <span data-ttu-id="94f73-128">**/main:** \<*nom_méthode*>  **/out:** \<*nom_fichier*>  **/target:** \<*type_fichier_assembly*></span><span class="sxs-lookup"><span data-stu-id="94f73-128">**/main:**\<*method name*> **/out:**\<*file name*> **/target:**\<*assembly file type*></span></span>

    <span data-ttu-id="94f73-129">Dans cette commande, les arguments *nom_module* spécifient le nom de chaque module à inclure dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="94f73-129">In this command, the *module name* arguments specify the name of each module to include in the assembly.</span></span> <span data-ttu-id="94f73-130">L’option **/main:** spécifie le nom de la méthode représentant le point d’entrée de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="94f73-130">The **/main:** option specifies the method name that is the assembly's entry point.</span></span> <span data-ttu-id="94f73-131">L’option **/out:** spécifie le nom du fichier de sortie, qui contient les métadonnées de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="94f73-131">The **/out:** option specifies the name of the output file, which contains assembly metadata.</span></span> <span data-ttu-id="94f73-132">L’option **/target:** indique que l’assembly est un fichier exécutable (.exe) d’application console, un fichier exécutable Windows (.win) ou un fichier bibliothèque (.lib).</span><span class="sxs-lookup"><span data-stu-id="94f73-132">The **/target:** option specifies that the assembly is a console application executable (.exe) file, a Windows executable (.win) file, or a library (.lib) file.</span></span>

    <span data-ttu-id="94f73-133">Dans l'exemple suivant, Al.exe crée un assembly qui est un exécutable d'application console appelé `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="94f73-133">In the following example, Al.exe creates an assembly that is a console application executable called `myAssembly.exe`.</span></span> <span data-ttu-id="94f73-134">L’application se compose de deux modules appelés `Client.netmodule` et `Stringer.netmodule`, et du fichier exécutable appelé `myAssembly.exe,` qui contient uniquement les métadonnées de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="94f73-134">The application consists of two modules called `Client.netmodule` and `Stringer.netmodule`, and the executable file called `myAssembly.exe,` which contains only assembly metadata.</span></span> <span data-ttu-id="94f73-135">Le point d'entrée de l'assembly est la méthode `Main` de la classe `MainClientApp`, qui est située dans `Client.dll`.</span><span class="sxs-lookup"><span data-stu-id="94f73-135">The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in `Client.dll`.</span></span>

    ```
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    <span data-ttu-id="94f73-136">Vous pouvez utiliser le [Désassembleur MSIL (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) pour examiner le contenu d’un assembly ou déterminer si un fichier est un assembly ou un module.</span><span class="sxs-lookup"><span data-stu-id="94f73-136">You can use the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the contents of an assembly, or determine whether a file is an assembly or a module.</span></span>

## <a name="see-also"></a><span data-ttu-id="94f73-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94f73-137">See also</span></span>

- [<span data-ttu-id="94f73-138">Création d’assemblys</span><span class="sxs-lookup"><span data-stu-id="94f73-138">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)
- [<span data-ttu-id="94f73-139">Guide pratique pour afficher le contenu d’un assembly</span><span class="sxs-lookup"><span data-stu-id="94f73-139">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)
- [<span data-ttu-id="94f73-140">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="94f73-140">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="94f73-141">Assemblys multifichiers</span><span class="sxs-lookup"><span data-stu-id="94f73-141">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)
