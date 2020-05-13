---
title: 'Comment : signer un assembly avec un nom fort'
description: Cet article explique comment signer un assembly .NET avec un nom fort à l’aide de l’onglet signature, de l’éditeur de liens assembly, des attributs d’assembly ou des options du compilateur.
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: d4888a12ac0494ca34eac3553a5374c3517fee38
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378622"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a><span data-ttu-id="fd045-103">Comment : signer un assembly avec un nom fort</span><span class="sxs-lookup"><span data-stu-id="fd045-103">How to: Sign an assembly with a strong name</span></span>

> [!NOTE]
> <span data-ttu-id="fd045-104">Bien que .NET Core prenne en charge les assemblys avec nom fort et que tous les assemblys de la bibliothèque .NET Core soient signés, la majorité des assemblys tiers n’ont pas besoin de noms forts.</span><span class="sxs-lookup"><span data-stu-id="fd045-104">Although .NET Core supports strong-named assemblies, and all assemblies in the .NET Core library are signed, the majority of third-party assemblies do not need strong names.</span></span> <span data-ttu-id="fd045-105">Pour plus d’informations, consultez [signature avec nom fort](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="fd045-105">For more information, see [Strong Name Signing](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) on GitHub.</span></span>

<span data-ttu-id="fd045-106">Il existe plusieurs façons de signer un assembly avec un nom fort :</span><span class="sxs-lookup"><span data-stu-id="fd045-106">There are a number of ways to sign an assembly with a strong name:</span></span>  
  
- <span data-ttu-id="fd045-107">À l'aide de l'onglet **Signature** dans la boîte de dialogue **Propriétés** d'un projet dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fd045-107">By using the **Signing** tab in a project's **Properties** dialog box in Visual Studio.</span></span> <span data-ttu-id="fd045-108">Il s'agit de la façon la plus facile et la plus pratique de signer un assembly avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="fd045-108">This is the easiest and most convenient way to sign an assembly with a strong name.</span></span>  
  
- <span data-ttu-id="fd045-109">À l’aide de l’outil [Assembly Linker (al. exe)](../../framework/tools/al-exe-assembly-linker.md) pour lier un module de code .NET Framework (un fichier *. netmodule* ) à un fichier de clé.</span><span class="sxs-lookup"><span data-stu-id="fd045-109">By using the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) to link a .NET Framework code module (a *.netmodule* file) with a key file.</span></span>  
  
- <span data-ttu-id="fd045-110">À l'aide d'attributs d'assembly pour insérer les informations de nom fort dans votre code.</span><span class="sxs-lookup"><span data-stu-id="fd045-110">By using assembly attributes to insert the strong name information into your code.</span></span> <span data-ttu-id="fd045-111">Vous pouvez utiliser l'attribut <xref:System.Reflection.AssemblyKeyFileAttribute> ou <xref:System.Reflection.AssemblyKeyNameAttribute> , selon l'emplacement du fichier de clé à utiliser.</span><span class="sxs-lookup"><span data-stu-id="fd045-111">You can use either the <xref:System.Reflection.AssemblyKeyFileAttribute> or the <xref:System.Reflection.AssemblyKeyNameAttribute> attribute, depending on where the key file to be used is located.</span></span>  
  
- <span data-ttu-id="fd045-112">À l'aide des options du compilateur.</span><span class="sxs-lookup"><span data-stu-id="fd045-112">By using compiler options.</span></span>  
  
 <span data-ttu-id="fd045-113">Pour signer un assembly avec un nom fort, vous devez avoir une paire de clés de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="fd045-113">You must have a cryptographic key pair to sign an assembly with a strong name.</span></span> <span data-ttu-id="fd045-114">Pour plus d’informations sur la création d’une paire de clés, consultez [Comment : créer une paire de clés publique/privée](create-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="fd045-114">For more information about creating a key pair, see [How to: Create a public-private key pair](create-public-private-key-pair.md).</span></span>  
  
## <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a><span data-ttu-id="fd045-115">Créer et signer un assembly avec un nom fort à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fd045-115">Create and sign an assembly with a strong name by using Visual Studio</span></span>  
  
1. <span data-ttu-id="fd045-116">Dans l’ **Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="fd045-116">In **Solution Explorer**, open the shortcut menu for the project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="fd045-117">Choisissez l'onglet **Signature** .</span><span class="sxs-lookup"><span data-stu-id="fd045-117">Choose the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="fd045-118">Sélectionnez la zone **Signer l'assembly** .</span><span class="sxs-lookup"><span data-stu-id="fd045-118">Select the **Sign the assembly** box.</span></span>  
  
4. <span data-ttu-id="fd045-119">Dans la zone **choisir un fichier de clé de nom fort** , choisissez **Parcourir**, puis naviguez jusqu’au fichier de clé.</span><span class="sxs-lookup"><span data-stu-id="fd045-119">In the **Choose a strong name key file** box, choose **Browse**, and then navigate to the key file.</span></span> <span data-ttu-id="fd045-120">Pour créer un nouveau fichier de clé, choisissez **nouveau** et entrez son nom dans la boîte de dialogue **créer une clé de nom fort** .</span><span class="sxs-lookup"><span data-stu-id="fd045-120">To create a new key file, choose **New** and enter its name in the **Create Strong Name Key** dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fd045-121">Pour [différer la signature d’un assembly](delay-sign.md), choisissez un fichier de clé publique.</span><span class="sxs-lookup"><span data-stu-id="fd045-121">In order to [delay sign an assembly](delay-sign.md), choose a public key file.</span></span>  
  
### <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a><span data-ttu-id="fd045-122">Créer et signer un assembly avec un nom fort à l’aide de l’Assembly Linker</span><span class="sxs-lookup"><span data-stu-id="fd045-122">Create and sign an assembly with a strong name by using the Assembly Linker</span></span>  
  
<span data-ttu-id="fd045-123">À l' [invite de commandes développeur pour Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), entrez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="fd045-123">At the [Developer Command Prompt for Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), enter the following command:</span></span>  

<span data-ttu-id="fd045-124">**al** **/out :** \< *AssemblyName* >  \* \< modulename>\* **/keyfile :** \< *keyfilename*></span><span class="sxs-lookup"><span data-stu-id="fd045-124">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span></span>  

<span data-ttu-id="fd045-125">Où :</span><span class="sxs-lookup"><span data-stu-id="fd045-125">Where:</span></span>  

- <span data-ttu-id="fd045-126">*AssemblyName* est le nom de l’assembly fortement signé (un fichier *. dll* ou *. exe* ) que l’éditeur de liens d’assembly enverra.</span><span class="sxs-lookup"><span data-stu-id="fd045-126">*assemblyName* is the name of the strongly signed assembly (a *.dll* or *.exe* file) that Assembly Linker will emit.</span></span>  
  
- <span data-ttu-id="fd045-127">*modulename* est le nom d’un module de code .NET Framework (un fichier *. netmodule* ) qui comprend un ou plusieurs types.</span><span class="sxs-lookup"><span data-stu-id="fd045-127">*moduleName* is the name of a .NET Framework code module (a *.netmodule* file) that includes one or more types.</span></span> <span data-ttu-id="fd045-128">Vous pouvez créer un fichier *. netmodule* en compilant votre code avec le `/target:module` commutateur en C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fd045-128">You can create a *.netmodule* file by compiling your code with the `/target:module` switch in C# or Visual Basic.</span></span>
  
- <span data-ttu-id="fd045-129">*keyfilename* est le nom du conteneur ou du fichier qui contient la paire de clés.</span><span class="sxs-lookup"><span data-stu-id="fd045-129">*keyfileName* is the name of the container or file that contains the key pair.</span></span> <span data-ttu-id="fd045-130">Assembly Linker interprète un chemin d’accès relatif par rapport au répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="fd045-130">Assembly Linker interprets a relative path in relation to the current directory.</span></span>  

<span data-ttu-id="fd045-131">L’exemple suivant signe l’assembly *myAssembly. dll* avec un nom fort à l’aide du fichier de clé *sgKey. snk*.</span><span class="sxs-lookup"><span data-stu-id="fd045-131">The following example signs the assembly *MyAssembly.dll* with a strong name by using the key file *sgKey.snk*.</span></span>  

```console
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
<span data-ttu-id="fd045-132">Pour plus d'informations sur l'utilisation de cet outil, consultez [Assembly Linker](../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="fd045-132">For more information about this tool, see [Assembly Linker](../../framework/tools/al-exe-assembly-linker.md).</span></span>  
  
## <a name="sign-an-assembly-with-a-strong-name-by-using-attributes"></a><span data-ttu-id="fd045-133">Signer un assembly avec un nom fort à l’aide d’attributs</span><span class="sxs-lookup"><span data-stu-id="fd045-133">Sign an assembly with a strong name by using attributes</span></span>  
  
1. <span data-ttu-id="fd045-134">Ajoutez l'attribut <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> ou <xref:System.Reflection.AssemblyKeyNameAttribute> à votre fichier de code source et spécifiez le nom du fichier ou du conteneur qui contient la paire de clés à utiliser lors de la signature de l'assembly avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="fd045-134">Add the <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute to your source code file, and specify the name of the file or container that contains the key pair to use when signing the assembly with a strong name.</span></span>  

2. <span data-ttu-id="fd045-135">Compilez le fichier de code source normalement.</span><span class="sxs-lookup"><span data-stu-id="fd045-135">Compile the source code file normally.</span></span>  

   > [!NOTE]
   > <span data-ttu-id="fd045-136">Les compilateurs C# et Visual Basic génèrent des avertissements (CS1699 et BC41008, respectivement) lorsqu'ils rencontrent l'attribut <xref:System.Reflection.AssemblyKeyFileAttribute> ou <xref:System.Reflection.AssemblyKeyNameAttribute> dans le code source.</span><span class="sxs-lookup"><span data-stu-id="fd045-136">The C# and Visual Basic compilers issue compiler warnings (CS1699 and BC41008, respectively) when they encounter the <xref:System.Reflection.AssemblyKeyFileAttribute> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute in source code.</span></span> <span data-ttu-id="fd045-137">Vous pouvez ignorer les avertissements.</span><span class="sxs-lookup"><span data-stu-id="fd045-137">You can ignore the warnings.</span></span>  

<span data-ttu-id="fd045-138">L’exemple suivant utilise l' <xref:System.Reflection.AssemblyKeyFileAttribute> attribut avec un fichier de clé appelé *keyfile. snk*, qui se trouve dans le répertoire où l’assembly est compilé.</span><span class="sxs-lookup"><span data-stu-id="fd045-138">The following example uses the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute with a key file called *keyfile.snk*, which is located in the directory where the assembly is compiled.</span></span>  

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

<span data-ttu-id="fd045-139">Vous pouvez également différer la signature d'un assembly lors de la compilation de votre fichier source.</span><span class="sxs-lookup"><span data-stu-id="fd045-139">You can also delay sign an assembly when compiling your source file.</span></span> <span data-ttu-id="fd045-140">Pour plus d’informations, consultez [Temporiser la signature d’un assembly](delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="fd045-140">For more information, see [Delay-sign an assembly](delay-sign.md).</span></span>  

## <a name="sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a><span data-ttu-id="fd045-141">Signer un assembly avec un nom fort à l’aide du compilateur</span><span class="sxs-lookup"><span data-stu-id="fd045-141">Sign an assembly with a strong name by using the compiler</span></span>  

<span data-ttu-id="fd045-142">Compilez vos fichiers de code source avec l'option du compilateur `/keyfile` ou `/delaysign` en C# et Visual Basic, ou l'option de l'éditeur de liens `/KEYFILE` ou `/DELAYSIGN` en C++.</span><span class="sxs-lookup"><span data-stu-id="fd045-142">Compile your source code file or files with the `/keyfile` or `/delaysign` compiler option in C# and Visual Basic, or the `/KEYFILE` or `/DELAYSIGN` linker option in C++.</span></span> <span data-ttu-id="fd045-143">Après le nom de l'option, ajoutez une virgule et le nom du fichier de clé.</span><span class="sxs-lookup"><span data-stu-id="fd045-143">After the option name, add a colon and the name of the key file.</span></span> <span data-ttu-id="fd045-144">Lorsque vous utilisez des compilateurs de ligne de commande, vous pouvez copier le fichier de clé dans le répertoire qui contient vos fichiers de code source.</span><span class="sxs-lookup"><span data-stu-id="fd045-144">When using command-line compilers, you can copy the key file to the directory that contains your source code files.</span></span>  

<span data-ttu-id="fd045-145">Pour plus d’informations sur la signature différée, consultez [temporisation d’un assembly](delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="fd045-145">For information on delay signing, see [Delay-sign an assembly](delay-sign.md).</span></span>  

<span data-ttu-id="fd045-146">L’exemple suivant utilise le compilateur C# et signe l’assembly *utilitylibrary. dll* avec un nom fort à l’aide du fichier de clé *sgKey. snk*.</span><span class="sxs-lookup"><span data-stu-id="fd045-146">The following example uses the C# compiler and signs the assembly *UtilityLibrary.dll* with a strong name by using the key file *sgKey.snk*.</span></span>  

```cmd
csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
```  

## <a name="see-also"></a><span data-ttu-id="fd045-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd045-147">See also</span></span>

- [<span data-ttu-id="fd045-148">Créer et utiliser des assemblys avec nom fort</span><span class="sxs-lookup"><span data-stu-id="fd045-148">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="fd045-149">Guide pratique pour créer une paire de clés publique/privée</span><span class="sxs-lookup"><span data-stu-id="fd045-149">How to: Create a public-private key pair</span></span>](create-public-private-key-pair.md)
- [<span data-ttu-id="fd045-150">Al. exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="fd045-150">Al.exe (Assembly Linker)</span></span>](../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="fd045-151">Temporiser la signature d’un assembly</span><span class="sxs-lookup"><span data-stu-id="fd045-151">Delay-sign an assembly</span></span>](delay-sign.md)
- [<span data-ttu-id="fd045-152">Gérer la signature d’assemblys et de manifestes</span><span class="sxs-lookup"><span data-stu-id="fd045-152">Manage assembly and manifest signing</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [<span data-ttu-id="fd045-153">Signature, page du concepteur de projets</span><span class="sxs-lookup"><span data-stu-id="fd045-153">Signing page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
