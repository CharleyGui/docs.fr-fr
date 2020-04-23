---
title: 'Comment : générer un assembly à fichier unique .NET Framework'
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
ms.openlocfilehash: b7cb06da74a21dab6f60f0d4c3ac1748fcbe4526
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644299"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a><span data-ttu-id="45166-102">Comment : générer un assembly à fichier unique .NET Framework</span><span class="sxs-lookup"><span data-stu-id="45166-102">How to: Build a .NET Framework single-file assembly</span></span>

<span data-ttu-id="45166-103">Un assembly à fichier unique, qui est le type d’assembly le plus simple, contient l’implémentation et les informations de type, ainsi que le [manifeste d’assembly](../../standard/assembly/manifest.md).</span><span class="sxs-lookup"><span data-stu-id="45166-103">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../standard/assembly/manifest.md).</span></span> <span data-ttu-id="45166-104">Vous pouvez utiliser des compilateurs de ligne de commande ou Visual Studio pour créer un assembly à fichier unique qui cible le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="45166-104">You can use command-line compilers or Visual Studio to create a single-file assembly that targets the .NET Framework.</span></span> <span data-ttu-id="45166-105">Par défaut, le compilateur crée un fichier d’assembly avec une extension *. exe* .</span><span class="sxs-lookup"><span data-stu-id="45166-105">By default, the compiler creates an assembly file with an *.exe* extension.</span></span>

> [!NOTE]
> <span data-ttu-id="45166-106">Visual Studio pour C# et Visual Basic peut être utilisé uniquement pour créer des assemblys à fichier unique.</span><span class="sxs-lookup"><span data-stu-id="45166-106">Visual Studio for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="45166-107">Si vous souhaitez créer des assemblys multifichiers, vous devez utiliser les compilateurs de ligne de commande ou Visual C++.</span><span class="sxs-lookup"><span data-stu-id="45166-107">If you want to create multifile assemblies, you must use command-line compilers or Visual C++.</span></span>

<span data-ttu-id="45166-108">Les procédures suivantes montrent comment créer des assemblys à fichier unique à l’aide des compilateurs de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="45166-108">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>

## <a name="create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="45166-109">Créer un assembly avec une extension. exe</span><span class="sxs-lookup"><span data-stu-id="45166-109">Create an assembly with an .exe extension</span></span>

<span data-ttu-id="45166-110">Saisissez ensuite la commande suivante dans l’invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="45166-110">At the command prompt, type the following command:</span></span>

<span data-ttu-id="45166-111">\<*nom du*> \<*module* de commande du compilateur></span><span class="sxs-lookup"><span data-stu-id="45166-111">\<*compiler command*> \<*module name*></span></span>

<span data-ttu-id="45166-112">Dans cette commande, *commande_du_compilateur* est la commande du compilateur pour le langage utilisé dans votre module de code, et *nom_du_module* est le nom du module de code à compiler dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="45166-112">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="45166-113">L’exemple suivant crée un assembly nommé *myCode. exe* à partir d’un `myCode`module de code appelé.</span><span class="sxs-lookup"><span data-stu-id="45166-113">The following example creates an assembly named *myCode.exe* from a code module called `myCode`.</span></span>

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="45166-114">Créer un assembly avec une extension. exe et spécifier le nom du fichier de sortie</span><span class="sxs-lookup"><span data-stu-id="45166-114">Create an assembly with an .exe extension and specify the output file name</span></span>

<span data-ttu-id="45166-115">Saisissez ensuite la commande suivante dans l’invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="45166-115">At the command prompt, type the following command:</span></span>

<span data-ttu-id="45166-116">\<*commande*> du compilateur **/out :**\<nom de*fichier*> \<nom du*module*></span><span class="sxs-lookup"><span data-stu-id="45166-116">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>

<span data-ttu-id="45166-117">Dans cette commande, *commande_du_compilateur* est la commande du compilateur pour le langage utilisé dans votre module de code, *nom_du_fichier* est le nom du fichier de sortie, et *nom_du_module* est le nom du module de code à compiler dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="45166-117">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="45166-118">L’exemple suivant crée un assembly nommé *myAssembly. exe* à partir d’un `myCode`module de code appelé.</span><span class="sxs-lookup"><span data-stu-id="45166-118">The following example creates an assembly named *myAssembly.exe* from a code module called `myCode`.</span></span>

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a><span data-ttu-id="45166-119">Créer des assemblys de bibliothèque</span><span class="sxs-lookup"><span data-stu-id="45166-119">Create library assemblies</span></span>
 <span data-ttu-id="45166-120">Un assembly de bibliothèque est similaire à une bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="45166-120">A library assembly is similar to a class library.</span></span> <span data-ttu-id="45166-121">Il contient des types qui seront référencés par d’autres assemblys, mais n’a aucun point d’entrée pour commencer l’exécution.</span><span class="sxs-lookup"><span data-stu-id="45166-121">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>

<span data-ttu-id="45166-122">Pour créer un assembly de bibliothèque, à l’invite de commandes, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="45166-122">To create a library assembly, at the command prompt, type the following command:</span></span>

<span data-ttu-id="45166-123">\<*commande*> du compilateur **-** \< *nom du module* t :Library></span><span class="sxs-lookup"><span data-stu-id="45166-123">\<*compiler command*> **-t:library** \<*module name*></span></span>

<span data-ttu-id="45166-124">Dans cette commande, *commande_du_compilateur* est la commande du compilateur pour le langage utilisé dans votre module de code, et *nom_du_module* est le nom du module de code à compiler dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="45166-124">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="45166-125">Vous pouvez également utiliser d’autres options du compilateur, telles que l’option **-out:**.</span><span class="sxs-lookup"><span data-stu-id="45166-125">You can also use other compiler options, such as the **-out:** option.</span></span>

<span data-ttu-id="45166-126">L’exemple suivant crée un assembly de bibliothèque nommé *myCodeAssembly. dll* à partir d' `myCode`un module de code appelé.</span><span class="sxs-lookup"><span data-stu-id="45166-126">The following example creates a library assembly named *myCodeAssembly.dll* from a code module called `myCode`.</span></span>

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a><span data-ttu-id="45166-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45166-127">See also</span></span>

- [<span data-ttu-id="45166-128">Créer des assemblys</span><span class="sxs-lookup"><span data-stu-id="45166-128">Create assemblies</span></span>](../../standard/assembly/create.md)
- [<span data-ttu-id="45166-129">Assemblys multifichiers</span><span class="sxs-lookup"><span data-stu-id="45166-129">Multifile assemblies</span></span>](multifile-assemblies.md)
- [<span data-ttu-id="45166-130">Comment : générer un assembly multifichier</span><span class="sxs-lookup"><span data-stu-id="45166-130">How to: Build a multifile assembly</span></span>](build-multifile-assembly.md)
- [<span data-ttu-id="45166-131">Programmer avec des assemblys</span><span class="sxs-lookup"><span data-stu-id="45166-131">Program with assemblies</span></span>](../../standard/assembly/index.md)
