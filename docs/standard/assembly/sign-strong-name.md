---
title: 'Procédure : Signer un assembly avec un nom fort'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 527fd68ef40e152b57a1fc98113094d3b41fbaae
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973060"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a><span data-ttu-id="20b30-102">Procédure : Signer un assembly avec un nom fort</span><span class="sxs-lookup"><span data-stu-id="20b30-102">How to: Sign an assembly with a strong name</span></span>

> [!NOTE]
> <span data-ttu-id="20b30-103">Bien que .NET Core prenne en charge les assemblys avec nom fort et que tous les assemblys de la bibliothèque .NET Core soient signés, la majorité des assemblys tiers n’ont pas besoin de noms forts.</span><span class="sxs-lookup"><span data-stu-id="20b30-103">Although .NET Core supports strong-named assemblies, and all assemblies in the .NET Core library are signed, the majority of third-party assemblies do not need strong names.</span></span> <span data-ttu-id="20b30-104">Pour plus d’informations, consultez [signature avec nom fort](https://github.com/dotnet/corefx/blob/master/Documentation/project-docs/strong-name-signing.md) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="20b30-104">For more information, see [Strong Name Signing](https://github.com/dotnet/corefx/blob/master/Documentation/project-docs/strong-name-signing.md) on GitHub.</span></span>

<span data-ttu-id="20b30-105">Il existe plusieurs façons de signer un assembly avec un nom fort :</span><span class="sxs-lookup"><span data-stu-id="20b30-105">There are a number of ways to sign an assembly with a strong name:</span></span>  
  
- <span data-ttu-id="20b30-106">À l'aide de l'onglet **Signature** dans la boîte de dialogue **Propriétés** d'un projet dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="20b30-106">By using the **Signing** tab in a project's **Properties** dialog box in Visual Studio.</span></span> <span data-ttu-id="20b30-107">Il s'agit de la façon la plus facile et la plus pratique de signer un assembly avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="20b30-107">This is the easiest and most convenient way to sign an assembly with a strong name.</span></span>  
  
- <span data-ttu-id="20b30-108">À l’aide de l’outil [Assembly Linker (al. exe)](../../framework/tools/al-exe-assembly-linker.md) pour lier un module de code .NET Framework (un fichier *. netmodule* ) à un fichier de clé.</span><span class="sxs-lookup"><span data-stu-id="20b30-108">By using the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) to link a .NET Framework code module (a *.netmodule* file) with a key file.</span></span>  
  
- <span data-ttu-id="20b30-109">À l'aide d'attributs d'assembly pour insérer les informations de nom fort dans votre code.</span><span class="sxs-lookup"><span data-stu-id="20b30-109">By using assembly attributes to insert the strong name information into your code.</span></span> <span data-ttu-id="20b30-110">Vous pouvez utiliser l'attribut <xref:System.Reflection.AssemblyKeyFileAttribute> ou <xref:System.Reflection.AssemblyKeyNameAttribute> , selon l'emplacement du fichier de clé à utiliser.</span><span class="sxs-lookup"><span data-stu-id="20b30-110">You can use either the <xref:System.Reflection.AssemblyKeyFileAttribute> or the <xref:System.Reflection.AssemblyKeyNameAttribute> attribute, depending on where the key file to be used is located.</span></span>  
  
- <span data-ttu-id="20b30-111">À l'aide des options du compilateur.</span><span class="sxs-lookup"><span data-stu-id="20b30-111">By using compiler options.</span></span>  
  
 <span data-ttu-id="20b30-112">Pour signer un assembly avec un nom fort, vous devez avoir une paire de clés de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="20b30-112">You must have a cryptographic key pair to sign an assembly with a strong name.</span></span> <span data-ttu-id="20b30-113">Pour plus d’informations sur la création d’une paire de clés, consultez [Guide pratique pour créer une paire de clés publique/privée](create-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="20b30-113">For more information about creating a key pair, see [How to: Create a public-private key pair](create-public-private-key-pair.md).</span></span>  
  
## <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a><span data-ttu-id="20b30-114">Créer et signer un assembly avec un nom fort à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="20b30-114">Create and sign an assembly with a strong name by using Visual Studio</span></span>  
  
1. <span data-ttu-id="20b30-115">Dans l’ **Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="20b30-115">In **Solution Explorer**, open the shortcut menu for the project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="20b30-116">Choisissez l'onglet **Signature** .</span><span class="sxs-lookup"><span data-stu-id="20b30-116">Choose the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="20b30-117">Sélectionnez la zone **Signer l'assembly** .</span><span class="sxs-lookup"><span data-stu-id="20b30-117">Select the **Sign the assembly** box.</span></span>  
  
4. <span data-ttu-id="20b30-118">Dans la zone **choisir un fichier de clé de nom fort** , choisissez **Parcourir**, puis naviguez jusqu’au fichier de clé.</span><span class="sxs-lookup"><span data-stu-id="20b30-118">In the **Choose a strong name key file** box, choose **Browse**, and then navigate to the key file.</span></span> <span data-ttu-id="20b30-119">Pour créer un nouveau fichier de clé, choisissez **nouveau** et entrez son nom dans la boîte de dialogue **créer une clé de nom fort** .</span><span class="sxs-lookup"><span data-stu-id="20b30-119">To create a new key file, choose **New** and enter its name in the **Create Strong Name Key** dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="20b30-120">Pour [différer la signature d’un assembly](delay-sign.md), choisissez un fichier de clé publique.</span><span class="sxs-lookup"><span data-stu-id="20b30-120">In order to [delay sign an assembly](delay-sign.md), choose a public key file.</span></span>  
  
### <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a><span data-ttu-id="20b30-121">Créer et signer un assembly avec un nom fort à l’aide de l’Assembly Linker</span><span class="sxs-lookup"><span data-stu-id="20b30-121">Create and sign an assembly with a strong name by using the Assembly Linker</span></span>  
  
<span data-ttu-id="20b30-122">À l' [invite de commandes développeur pour Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), entrez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="20b30-122">At the [Developer Command Prompt for Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), enter the following command:</span></span>  

<span data-ttu-id="20b30-123">**al** **/out:** \<*assemblyName*>  *\<moduleName>* **/keyfile:** \<*keyfileName*></span><span class="sxs-lookup"><span data-stu-id="20b30-123">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span></span>  

<span data-ttu-id="20b30-124">Où :</span><span class="sxs-lookup"><span data-stu-id="20b30-124">Where:</span></span>  

- <span data-ttu-id="20b30-125">*AssemblyName* est le nom de l’assembly fortement signé (un fichier *. dll* ou *. exe* ) que l’éditeur de liens d’assembly enverra.</span><span class="sxs-lookup"><span data-stu-id="20b30-125">*assemblyName* is the name of the strongly signed assembly (a *.dll* or *.exe* file) that Assembly Linker will emit.</span></span>  
  
- <span data-ttu-id="20b30-126">*modulename* est le nom d’un module de code .NET Framework (un fichier *. netmodule* ) qui comprend un ou plusieurs types.</span><span class="sxs-lookup"><span data-stu-id="20b30-126">*moduleName* is the name of a .NET Framework code module (a *.netmodule* file) that includes one or more types.</span></span> <span data-ttu-id="20b30-127">Vous pouvez créer un fichier *. netmodule* en compilant votre code `/target:module` avec le C# commutateur ou en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="20b30-127">You can create a *.netmodule* file by compiling your code with the `/target:module` switch in C# or Visual Basic.</span></span>
  
- <span data-ttu-id="20b30-128">*keyfilename* est le nom du conteneur ou du fichier qui contient la paire de clés.</span><span class="sxs-lookup"><span data-stu-id="20b30-128">*keyfileName* is the name of the container or file that contains the key pair.</span></span> <span data-ttu-id="20b30-129">Assembly Linker interprète un chemin d’accès relatif par rapport au répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="20b30-129">Assembly Linker interprets a relative path in relation to the current directory.</span></span>  

<span data-ttu-id="20b30-130">L’exemple suivant signe l’assembly *myAssembly. dll* avec un nom fort à l’aide du fichier de clé *sgKey. snk*.</span><span class="sxs-lookup"><span data-stu-id="20b30-130">The following example signs the assembly *MyAssembly.dll* with a strong name by using the key file *sgKey.snk*.</span></span>  

```console
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
<span data-ttu-id="20b30-131">Pour plus d'informations sur l'utilisation de cet outil, consultez [Assembly Linker](../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="20b30-131">For more information about this tool, see [Assembly Linker](../../framework/tools/al-exe-assembly-linker.md).</span></span>  
  
## <a name="sign-an-assembly-with-a-strong-name-by-using-attributes"></a><span data-ttu-id="20b30-132">Signer un assembly avec un nom fort à l’aide d’attributs</span><span class="sxs-lookup"><span data-stu-id="20b30-132">Sign an assembly with a strong name by using attributes</span></span>  
  
1. <span data-ttu-id="20b30-133">Ajoutez l'attribut <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> ou <xref:System.Reflection.AssemblyKeyNameAttribute> à votre fichier de code source et spécifiez le nom du fichier ou du conteneur qui contient la paire de clés à utiliser lors de la signature de l'assembly avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="20b30-133">Add the <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute to your source code file, and specify the name of the file or container that contains the key pair to use when signing the assembly with a strong name.</span></span>  
   
2. <span data-ttu-id="20b30-134">Compilez le fichier de code source normalement.</span><span class="sxs-lookup"><span data-stu-id="20b30-134">Compile the source code file normally.</span></span>  
   
   > [!NOTE]
   > <span data-ttu-id="20b30-135">Les compilateurs C# et Visual Basic génèrent des avertissements (CS1699 et BC41008, respectivement) lorsqu'ils rencontrent l'attribut <xref:System.Reflection.AssemblyKeyFileAttribute> ou <xref:System.Reflection.AssemblyKeyNameAttribute> dans le code source.</span><span class="sxs-lookup"><span data-stu-id="20b30-135">The C# and Visual Basic compilers issue compiler warnings (CS1699 and BC41008, respectively) when they encounter the <xref:System.Reflection.AssemblyKeyFileAttribute> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute in source code.</span></span> <span data-ttu-id="20b30-136">Vous pouvez ignorer les avertissements.</span><span class="sxs-lookup"><span data-stu-id="20b30-136">You can ignore the warnings.</span></span>  

<span data-ttu-id="20b30-137">L’exemple suivant utilise l' <xref:System.Reflection.AssemblyKeyFileAttribute> attribut avec un fichier de clé appelé *keyfile. snk*, qui se trouve dans le répertoire où l’assembly est compilé.</span><span class="sxs-lookup"><span data-stu-id="20b30-137">The following example uses the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute with a key file called *keyfile.snk*, which is located in the directory where the assembly is compiled.</span></span>  

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

<span data-ttu-id="20b30-138">Vous pouvez également différer la signature d'un assembly lors de la compilation de votre fichier source.</span><span class="sxs-lookup"><span data-stu-id="20b30-138">You can also delay sign an assembly when compiling your source file.</span></span> <span data-ttu-id="20b30-139">Pour plus d’informations, consultez [Temporiser la signature d’un assembly](delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="20b30-139">For more information, see [Delay-sign an assembly](delay-sign.md).</span></span>  

## <a name="sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a><span data-ttu-id="20b30-140">Signer un assembly avec un nom fort à l’aide du compilateur</span><span class="sxs-lookup"><span data-stu-id="20b30-140">Sign an assembly with a strong name by using the compiler</span></span>  

<span data-ttu-id="20b30-141">Compilez vos fichiers de code source avec l'option du compilateur `/keyfile` ou `/delaysign` en C# et Visual Basic, ou l'option de l'éditeur de liens `/KEYFILE` ou `/DELAYSIGN` en C++.</span><span class="sxs-lookup"><span data-stu-id="20b30-141">Compile your source code file or files with the `/keyfile` or `/delaysign` compiler option in C# and Visual Basic, or the `/KEYFILE` or `/DELAYSIGN` linker option in C++.</span></span> <span data-ttu-id="20b30-142">Après le nom de l'option, ajoutez une virgule et le nom du fichier de clé.</span><span class="sxs-lookup"><span data-stu-id="20b30-142">After the option name, add a colon and the name of the key file.</span></span> <span data-ttu-id="20b30-143">Lorsque vous utilisez des compilateurs de ligne de commande, vous pouvez copier le fichier de clé dans le répertoire qui contient vos fichiers de code source.</span><span class="sxs-lookup"><span data-stu-id="20b30-143">When using command-line compilers, you can copy the key file to the directory that contains your source code files.</span></span>  

<span data-ttu-id="20b30-144">Pour plus d’informations sur la signature différée, consultez [temporisation d’un assembly](delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="20b30-144">For information on delay signing, see [Delay-sign an assembly](delay-sign.md).</span></span>  

<span data-ttu-id="20b30-145">L’exemple suivant utilise le C# compilateur et signe l’assembly *utilitylibrary. dll* avec un nom fort à l’aide du fichier de clé *sgKey. snk*.</span><span class="sxs-lookup"><span data-stu-id="20b30-145">The following example uses the C# compiler and signs the assembly *UtilityLibrary.dll* with a strong name by using the key file *sgKey.snk*.</span></span>  

```cmd
csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
```  

## <a name="see-also"></a><span data-ttu-id="20b30-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20b30-146">See also</span></span>

- [<span data-ttu-id="20b30-147">Créer et utiliser des assemblys avec nom fort</span><span class="sxs-lookup"><span data-stu-id="20b30-147">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="20b30-148">Guide pratique pour créer une paire de clés publique/privée</span><span class="sxs-lookup"><span data-stu-id="20b30-148">How to: Create a public-private key pair</span></span>](create-public-private-key-pair.md)
- [<span data-ttu-id="20b30-149">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="20b30-149">Al.exe (Assembly Linker)</span></span>](../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="20b30-150">Temporiser la signature d’un assembly</span><span class="sxs-lookup"><span data-stu-id="20b30-150">Delay-sign an assembly</span></span>](delay-sign.md)
- [<span data-ttu-id="20b30-151">Gérer la signature d’assemblys et de manifestes</span><span class="sxs-lookup"><span data-stu-id="20b30-151">Manage assembly and manifest signing</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [<span data-ttu-id="20b30-152">Signature, page du Concepteur de projets</span><span class="sxs-lookup"><span data-stu-id="20b30-152">Signing page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
