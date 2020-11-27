---
title: 'Comment : générer un assembly à fichier unique .NET Framework'
description: Découvrez comment créer un assembly à fichier unique dans .NET. Un assembly à fichier unique peut être une bibliothèque (. dll) qui cible .NET, ou il peut s’agir d’un fichier exécutable (. exe).
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
dev_langs:
- csharp
- vb
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
ms.openlocfilehash: bdffa9417a7d52e9c825ca6455997b9bfa7408e4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271523"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a><span data-ttu-id="bdeec-104">Comment : générer un assembly à fichier unique .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bdeec-104">How to: Build a .NET Framework single-file assembly</span></span>

<span data-ttu-id="bdeec-105">Un assembly à fichier unique, qui est le type d’assembly le plus simple, contient l’implémentation et les informations de type, ainsi que le [manifeste d’assembly](../../standard/assembly/manifest.md).</span><span class="sxs-lookup"><span data-stu-id="bdeec-105">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../standard/assembly/manifest.md).</span></span> <span data-ttu-id="bdeec-106">Vous pouvez utiliser des compilateurs de ligne de commande ou Visual Studio pour créer un assembly à fichier unique qui cible le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bdeec-106">You can use command-line compilers or Visual Studio to create a single-file assembly that targets the .NET Framework.</span></span> <span data-ttu-id="bdeec-107">Par défaut, le compilateur crée un fichier d’assembly avec une extension *. exe* .</span><span class="sxs-lookup"><span data-stu-id="bdeec-107">By default, the compiler creates an assembly file with an *.exe* extension.</span></span>

> [!NOTE]
> <span data-ttu-id="bdeec-108">Visual Studio pour C# et Visual Basic peut être utilisé uniquement pour créer des assemblys à fichier unique.</span><span class="sxs-lookup"><span data-stu-id="bdeec-108">Visual Studio for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="bdeec-109">Si vous souhaitez créer des assemblys multifichiers, vous devez utiliser les compilateurs de ligne de commande ou Visual C++.</span><span class="sxs-lookup"><span data-stu-id="bdeec-109">If you want to create multifile assemblies, you must use command-line compilers or Visual C++.</span></span>

<span data-ttu-id="bdeec-110">Les procédures suivantes montrent comment créer des assemblys à fichier unique à l’aide des compilateurs de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="bdeec-110">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>

## <a name="create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="bdeec-111">Créer un assembly avec une extension. exe</span><span class="sxs-lookup"><span data-stu-id="bdeec-111">Create an assembly with an .exe extension</span></span>

<span data-ttu-id="bdeec-112">Saisissez ensuite la commande suivante dans l’invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="bdeec-112">At the command prompt, type the following command:</span></span>

<span data-ttu-id="bdeec-113">\<*compiler command*> \<*module name*></span><span class="sxs-lookup"><span data-stu-id="bdeec-113">\<*compiler command*> \<*module name*></span></span>

<span data-ttu-id="bdeec-114">Dans cette commande, *commande_du_compilateur* est la commande du compilateur pour le langage utilisé dans votre module de code, et *nom_du_module* est le nom du module de code à compiler dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="bdeec-114">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="bdeec-115">L’exemple suivant crée un assembly nommé *myCode.exe* à partir d’un module de code appelé `myCode` .</span><span class="sxs-lookup"><span data-stu-id="bdeec-115">The following example creates an assembly named *myCode.exe* from a code module called `myCode`.</span></span>

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="bdeec-116">Créer un assembly avec une extension. exe et spécifier le nom du fichier de sortie</span><span class="sxs-lookup"><span data-stu-id="bdeec-116">Create an assembly with an .exe extension and specify the output file name</span></span>

<span data-ttu-id="bdeec-117">Saisissez ensuite la commande suivante dans l’invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="bdeec-117">At the command prompt, type the following command:</span></span>

<span data-ttu-id="bdeec-118">\<*compiler command*>**/out :** \<*file name*>\<*module name*></span><span class="sxs-lookup"><span data-stu-id="bdeec-118">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>

<span data-ttu-id="bdeec-119">Dans cette commande, *commande_du_compilateur* est la commande du compilateur pour le langage utilisé dans votre module de code, *nom_du_fichier* est le nom du fichier de sortie, et *nom_du_module* est le nom du module de code à compiler dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="bdeec-119">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="bdeec-120">L’exemple suivant crée un assembly nommé *myAssembly.exe* à partir d’un module de code appelé `myCode` .</span><span class="sxs-lookup"><span data-stu-id="bdeec-120">The following example creates an assembly named *myAssembly.exe* from a code module called `myCode`.</span></span>

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a><span data-ttu-id="bdeec-121">Créer des assemblys de bibliothèque</span><span class="sxs-lookup"><span data-stu-id="bdeec-121">Create library assemblies</span></span>

 <span data-ttu-id="bdeec-122">Un assembly de bibliothèque est similaire à une bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="bdeec-122">A library assembly is similar to a class library.</span></span> <span data-ttu-id="bdeec-123">Il contient des types qui seront référencés par d’autres assemblys, mais n’a aucun point d’entrée pour commencer l’exécution.</span><span class="sxs-lookup"><span data-stu-id="bdeec-123">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>

<span data-ttu-id="bdeec-124">Pour créer un assembly de bibliothèque, à l’invite de commandes, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="bdeec-124">To create a library assembly, at the command prompt, type the following command:</span></span>

<span data-ttu-id="bdeec-125">\<*compiler command*>**-t :Library**\<*module name*></span><span class="sxs-lookup"><span data-stu-id="bdeec-125">\<*compiler command*> **-t:library** \<*module name*></span></span>

<span data-ttu-id="bdeec-126">Dans cette commande, *commande_du_compilateur* est la commande du compilateur pour le langage utilisé dans votre module de code, et *nom_du_module* est le nom du module de code à compiler dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="bdeec-126">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="bdeec-127">Vous pouvez également utiliser d’autres options du compilateur, telles que l’option **-out:**.</span><span class="sxs-lookup"><span data-stu-id="bdeec-127">You can also use other compiler options, such as the **-out:** option.</span></span>

<span data-ttu-id="bdeec-128">L’exemple suivant crée un assembly de bibliothèque nommé *myCodeAssembly.dll* à partir d’un module de code appelé `myCode` .</span><span class="sxs-lookup"><span data-stu-id="bdeec-128">The following example creates a library assembly named *myCodeAssembly.dll* from a code module called `myCode`.</span></span>

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a><span data-ttu-id="bdeec-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bdeec-129">See also</span></span>

- [<span data-ttu-id="bdeec-130">Créer des assemblys</span><span class="sxs-lookup"><span data-stu-id="bdeec-130">Create assemblies</span></span>](../../standard/assembly/create.md)
- [<span data-ttu-id="bdeec-131">Assemblys multifichiers</span><span class="sxs-lookup"><span data-stu-id="bdeec-131">Multifile assemblies</span></span>](multifile-assemblies.md)
- [<span data-ttu-id="bdeec-132">Procédure : Générer un assembly multifichier</span><span class="sxs-lookup"><span data-stu-id="bdeec-132">How to: Build a multifile assembly</span></span>](build-multifile-assembly.md)
- [<span data-ttu-id="bdeec-133">Programmer avec des assemblys</span><span class="sxs-lookup"><span data-stu-id="bdeec-133">Program with assemblies</span></span>](../../standard/assembly/index.md)
