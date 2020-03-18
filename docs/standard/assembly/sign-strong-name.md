---
title: 'Comment: Signer une assemblée avec un nom fort'
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
ms.openlocfilehash: 9998e69e8bf1505bcfc7a9103e9d89616dad9633
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160311"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a><span data-ttu-id="b385e-102">Comment: Signer une assemblée avec un nom fort</span><span class="sxs-lookup"><span data-stu-id="b385e-102">How to: Sign an assembly with a strong name</span></span>

> [!NOTE]
> <span data-ttu-id="b385e-103">Bien que .NET Core soutienne des assemblées de nom fort, et que toutes les assemblées de la bibliothèque .NET Core soient signées, la majorité des assemblées tierces n’ont pas besoin de noms forts.</span><span class="sxs-lookup"><span data-stu-id="b385e-103">Although .NET Core supports strong-named assemblies, and all assemblies in the .NET Core library are signed, the majority of third-party assemblies do not need strong names.</span></span> <span data-ttu-id="b385e-104">Pour plus d’informations, voir [Strong Name Signing](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="b385e-104">For more information, see [Strong Name Signing](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) on GitHub.</span></span>

<span data-ttu-id="b385e-105">Il existe plusieurs façons de signer un assembly avec un nom fort :</span><span class="sxs-lookup"><span data-stu-id="b385e-105">There are a number of ways to sign an assembly with a strong name:</span></span>  
  
- <span data-ttu-id="b385e-106">À l'aide de l'onglet **Signature** dans la boîte de dialogue **Propriétés** d'un projet dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b385e-106">By using the **Signing** tab in a project's **Properties** dialog box in Visual Studio.</span></span> <span data-ttu-id="b385e-107">Il s'agit de la façon la plus facile et la plus pratique de signer un assembly avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="b385e-107">This is the easiest and most convenient way to sign an assembly with a strong name.</span></span>  
  
- <span data-ttu-id="b385e-108">En utilisant le [Linker d’assemblage (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) pour lier un module de code cadre .NET (un fichier *.netmodule)* avec un fichier clé.</span><span class="sxs-lookup"><span data-stu-id="b385e-108">By using the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) to link a .NET Framework code module (a *.netmodule* file) with a key file.</span></span>  
  
- <span data-ttu-id="b385e-109">À l'aide d'attributs d'assembly pour insérer les informations de nom fort dans votre code.</span><span class="sxs-lookup"><span data-stu-id="b385e-109">By using assembly attributes to insert the strong name information into your code.</span></span> <span data-ttu-id="b385e-110">Vous pouvez utiliser l'attribut <xref:System.Reflection.AssemblyKeyFileAttribute> ou <xref:System.Reflection.AssemblyKeyNameAttribute> , selon l'emplacement du fichier de clé à utiliser.</span><span class="sxs-lookup"><span data-stu-id="b385e-110">You can use either the <xref:System.Reflection.AssemblyKeyFileAttribute> or the <xref:System.Reflection.AssemblyKeyNameAttribute> attribute, depending on where the key file to be used is located.</span></span>  
  
- <span data-ttu-id="b385e-111">À l'aide des options du compilateur.</span><span class="sxs-lookup"><span data-stu-id="b385e-111">By using compiler options.</span></span>  
  
 <span data-ttu-id="b385e-112">Pour signer un assembly avec un nom fort, vous devez avoir une paire de clés de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="b385e-112">You must have a cryptographic key pair to sign an assembly with a strong name.</span></span> <span data-ttu-id="b385e-113">Pour plus d’informations sur la création d’une paire de clés, voir [Comment : Créer une paire de clés public-privé.](create-public-private-key-pair.md)</span><span class="sxs-lookup"><span data-stu-id="b385e-113">For more information about creating a key pair, see [How to: Create a public-private key pair](create-public-private-key-pair.md).</span></span>  
  
## <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a><span data-ttu-id="b385e-114">Créez et signez un assemblage avec un nom fort en utilisant Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b385e-114">Create and sign an assembly with a strong name by using Visual Studio</span></span>  
  
1. <span data-ttu-id="b385e-115">Dans l’ **Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="b385e-115">In **Solution Explorer**, open the shortcut menu for the project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="b385e-116">Choisissez l'onglet **Signature** .</span><span class="sxs-lookup"><span data-stu-id="b385e-116">Choose the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="b385e-117">Sélectionnez la zone **Signer l'assembly** .</span><span class="sxs-lookup"><span data-stu-id="b385e-117">Select the **Sign the assembly** box.</span></span>  
  
4. <span data-ttu-id="b385e-118">Dans la **boîte de fichier de fichier De nom fort,** choisissez **Browse,** puis naviguez vers le fichier clé.</span><span class="sxs-lookup"><span data-stu-id="b385e-118">In the **Choose a strong name key file** box, choose **Browse**, and then navigate to the key file.</span></span> <span data-ttu-id="b385e-119">Pour créer un nouveau fichier clé, choisissez **New** et entrez son nom dans la boîte de dialogue **Create Strong Name Key.**</span><span class="sxs-lookup"><span data-stu-id="b385e-119">To create a new key file, choose **New** and enter its name in the **Create Strong Name Key** dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b385e-120">Pour [différer la signature d’un assembly](delay-sign.md), choisissez un fichier de clé publique.</span><span class="sxs-lookup"><span data-stu-id="b385e-120">In order to [delay sign an assembly](delay-sign.md), choose a public key file.</span></span>  
  
### <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a><span data-ttu-id="b385e-121">Créer et signer une assemblée avec un nom fort en utilisant le Lien d’assemblage</span><span class="sxs-lookup"><span data-stu-id="b385e-121">Create and sign an assembly with a strong name by using the Assembly Linker</span></span>  
  
<span data-ttu-id="b385e-122">Au [Developer Command Prompt for Visual Studio,](../../framework/tools/developer-command-prompt-for-vs.md)entrez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="b385e-122">At the [Developer Command Prompt for Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), enter the following command:</span></span>  

<span data-ttu-id="b385e-123">**al** **/out:**\<*module assemblyNameName*> *\<>* **/keyfile:**\<*keyfileName*></span><span class="sxs-lookup"><span data-stu-id="b385e-123">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span></span>  

<span data-ttu-id="b385e-124">Où :</span><span class="sxs-lookup"><span data-stu-id="b385e-124">Where:</span></span>  

- <span data-ttu-id="b385e-125">*assemblyName* est le nom de l’assemblage fortement signé (un *fichier .dll* ou *.exe)* que l’Assemblée Linker émettra.</span><span class="sxs-lookup"><span data-stu-id="b385e-125">*assemblyName* is the name of the strongly signed assembly (a *.dll* or *.exe* file) that Assembly Linker will emit.</span></span>  
  
- <span data-ttu-id="b385e-126">*moduleName* est le nom d’un module de code cadre .NET (un fichier *.netmodule)* qui comprend un ou plusieurs types.</span><span class="sxs-lookup"><span data-stu-id="b385e-126">*moduleName* is the name of a .NET Framework code module (a *.netmodule* file) that includes one or more types.</span></span> <span data-ttu-id="b385e-127">Vous pouvez créer un fichier *.netmodule* en `/target:module` compilant votre code avec le commutateur en C ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b385e-127">You can create a *.netmodule* file by compiling your code with the `/target:module` switch in C# or Visual Basic.</span></span>
  
- <span data-ttu-id="b385e-128">*keyfileName* est le nom du conteneur ou du fichier qui contient la paire de clés.</span><span class="sxs-lookup"><span data-stu-id="b385e-128">*keyfileName* is the name of the container or file that contains the key pair.</span></span> <span data-ttu-id="b385e-129">Assembly Linker interprète une voie relative par rapport à l’annuaire actuel.</span><span class="sxs-lookup"><span data-stu-id="b385e-129">Assembly Linker interprets a relative path in relation to the current directory.</span></span>  

<span data-ttu-id="b385e-130">L’exemple suivant signe l’assemblage *MyAssembly.dll* avec un nom fort en utilisant le fichier clé *sgKey.snk*.</span><span class="sxs-lookup"><span data-stu-id="b385e-130">The following example signs the assembly *MyAssembly.dll* with a strong name by using the key file *sgKey.snk*.</span></span>  

```console
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
<span data-ttu-id="b385e-131">Pour plus d'informations sur l'utilisation de cet outil, consultez [Assembly Linker](../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="b385e-131">For more information about this tool, see [Assembly Linker](../../framework/tools/al-exe-assembly-linker.md).</span></span>  
  
## <a name="sign-an-assembly-with-a-strong-name-by-using-attributes"></a><span data-ttu-id="b385e-132">Signez un assemblage avec un nom fort en utilisant des attributs</span><span class="sxs-lookup"><span data-stu-id="b385e-132">Sign an assembly with a strong name by using attributes</span></span>  
  
1. <span data-ttu-id="b385e-133">Ajoutez l'attribut <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> ou <xref:System.Reflection.AssemblyKeyNameAttribute> à votre fichier de code source et spécifiez le nom du fichier ou du conteneur qui contient la paire de clés à utiliser lors de la signature de l'assembly avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="b385e-133">Add the <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute to your source code file, and specify the name of the file or container that contains the key pair to use when signing the assembly with a strong name.</span></span>  

2. <span data-ttu-id="b385e-134">Compilez le fichier de code source normalement.</span><span class="sxs-lookup"><span data-stu-id="b385e-134">Compile the source code file normally.</span></span>  

   > [!NOTE]
   > <span data-ttu-id="b385e-135">Les compilateurs C# et Visual Basic génèrent des avertissements (CS1699 et BC41008, respectivement) lorsqu'ils rencontrent l'attribut <xref:System.Reflection.AssemblyKeyFileAttribute> ou <xref:System.Reflection.AssemblyKeyNameAttribute> dans le code source.</span><span class="sxs-lookup"><span data-stu-id="b385e-135">The C# and Visual Basic compilers issue compiler warnings (CS1699 and BC41008, respectively) when they encounter the <xref:System.Reflection.AssemblyKeyFileAttribute> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute in source code.</span></span> <span data-ttu-id="b385e-136">Vous pouvez ignorer les avertissements.</span><span class="sxs-lookup"><span data-stu-id="b385e-136">You can ignore the warnings.</span></span>  

<span data-ttu-id="b385e-137">L’exemple suivant <xref:System.Reflection.AssemblyKeyFileAttribute> utilise l’attribut avec un fichier clé appelé *keyfile.snk*, qui est situé dans l’annuaire où l’assemblage est compilé.</span><span class="sxs-lookup"><span data-stu-id="b385e-137">The following example uses the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute with a key file called *keyfile.snk*, which is located in the directory where the assembly is compiled.</span></span>  

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

<span data-ttu-id="b385e-138">Vous pouvez également différer la signature d'un assembly lors de la compilation de votre fichier source.</span><span class="sxs-lookup"><span data-stu-id="b385e-138">You can also delay sign an assembly when compiling your source file.</span></span> <span data-ttu-id="b385e-139">Pour plus d’informations, voir [Retard-signer une assemblée](delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="b385e-139">For more information, see [Delay-sign an assembly](delay-sign.md).</span></span>  

## <a name="sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a><span data-ttu-id="b385e-140">Signez un assemblage avec un nom fort en utilisant le compilateur</span><span class="sxs-lookup"><span data-stu-id="b385e-140">Sign an assembly with a strong name by using the compiler</span></span>  

<span data-ttu-id="b385e-141">Compilez vos fichiers de code source avec l'option du compilateur `/keyfile` ou `/delaysign` en C# et Visual Basic, ou l'option de l'éditeur de liens `/KEYFILE` ou `/DELAYSIGN` en C++.</span><span class="sxs-lookup"><span data-stu-id="b385e-141">Compile your source code file or files with the `/keyfile` or `/delaysign` compiler option in C# and Visual Basic, or the `/KEYFILE` or `/DELAYSIGN` linker option in C++.</span></span> <span data-ttu-id="b385e-142">Après le nom de l'option, ajoutez une virgule et le nom du fichier de clé.</span><span class="sxs-lookup"><span data-stu-id="b385e-142">After the option name, add a colon and the name of the key file.</span></span> <span data-ttu-id="b385e-143">Lorsque vous utilisez des compilateurs de ligne de commande, vous pouvez copier le fichier de clé dans le répertoire qui contient vos fichiers de code source.</span><span class="sxs-lookup"><span data-stu-id="b385e-143">When using command-line compilers, you can copy the key file to the directory that contains your source code files.</span></span>  

<span data-ttu-id="b385e-144">Pour plus d’informations sur la signature des retards, voir [Retard-signer une assemblée](delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="b385e-144">For information on delay signing, see [Delay-sign an assembly](delay-sign.md).</span></span>  

<span data-ttu-id="b385e-145">L’exemple suivant utilise le compilateur C et signe l’assemblage *UtilityLibrary.dll* avec un nom fort en utilisant le fichier clé *sgKey.snk*.</span><span class="sxs-lookup"><span data-stu-id="b385e-145">The following example uses the C# compiler and signs the assembly *UtilityLibrary.dll* with a strong name by using the key file *sgKey.snk*.</span></span>  

```cmd
csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
```  

## <a name="see-also"></a><span data-ttu-id="b385e-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b385e-146">See also</span></span>

- [<span data-ttu-id="b385e-147">Créer et utiliser des assemblys avec nom fort</span><span class="sxs-lookup"><span data-stu-id="b385e-147">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="b385e-148">Guide pratique pour créer une paire de clés publique/privée</span><span class="sxs-lookup"><span data-stu-id="b385e-148">How to: Create a public-private key pair</span></span>](create-public-private-key-pair.md)
- [<span data-ttu-id="b385e-149">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="b385e-149">Al.exe (Assembly Linker)</span></span>](../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="b385e-150">Temporiser la signature d’un assembly</span><span class="sxs-lookup"><span data-stu-id="b385e-150">Delay-sign an assembly</span></span>](delay-sign.md)
- [<span data-ttu-id="b385e-151">Gérer l’assemblage et la signature manifeste</span><span class="sxs-lookup"><span data-stu-id="b385e-151">Manage assembly and manifest signing</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [<span data-ttu-id="b385e-152">Page Signature, Concepteur de projet</span><span class="sxs-lookup"><span data-stu-id="b385e-152">Signing page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
