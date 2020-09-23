---
title: -platform
ms.date: 03/13/2018
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
ms.openlocfilehash: 488a1da6b25bcb4b42f0d355c6faee542046d0f5
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91098889"
---
# <a name="-platform-visual-basic"></a><span data-ttu-id="dfd0c-102">-plateforme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dfd0c-102">-platform (Visual Basic)</span></span>

<span data-ttu-id="dfd0c-103">Spécifie la version de plateforme du CLR (Common Language Runtime) qui peut exécuter le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-103">Specifies which platform version of common language runtime (CLR) can run the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfd0c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dfd0c-104">Syntax</span></span>  
  
```console  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a><span data-ttu-id="dfd0c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="dfd0c-105">Arguments</span></span>  
  
|<span data-ttu-id="dfd0c-106">Terme</span><span class="sxs-lookup"><span data-stu-id="dfd0c-106">Term</span></span>|<span data-ttu-id="dfd0c-107">Définition</span><span class="sxs-lookup"><span data-stu-id="dfd0c-107">Definition</span></span>|  
|---|---|  
|`x86`|<span data-ttu-id="dfd0c-108">Compile votre assembly pour qu'il soit exécuté par le CLR 32 bits x86.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-108">Compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>|  
|`x64`|<span data-ttu-id="dfd0c-109">Compile votre assembly pour qu'il soit exécuté par le CLR 64 bits sur un ordinateur qui prend en charge le jeu d'instructions AMD64 ou EM64T.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-109">Compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>|  
|`Itanium`|<span data-ttu-id="dfd0c-110">Compile votre assembly pour qu'il soit exécuté par le CLR 64 bits sur un ordinateur doté d'un processeur Itanium.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-110">Compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>|  
|`arm`|<span data-ttu-id="dfd0c-111">Compile votre assembly pour qu'il s'exécute sur un ordinateur doté d'un processeur ARM (Advanced RISC Machine).</span><span class="sxs-lookup"><span data-stu-id="dfd0c-111">Compiles your assembly to be run on a computer with an ARM (Advanced RISC Machine) processor.</span></span>|  
|`anycpu`|<span data-ttu-id="dfd0c-112">Compile votre assembly pour qu'il s'exécute sur n'importe quelle plateforme.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-112">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="dfd0c-113">L'application s'exécutera en tant qu'application 32 bits sur les versions 32 bits de Windows et en tant qu'application 64 bits sur les versions 64 bits de Windows.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-113">The application will run as a 32-bit application on 32-bit versions of Windows and as a 64-bit application on 64-bit versions of Windows.</span></span> <span data-ttu-id="dfd0c-114">Cet indicateur est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-114">This flag is the default value.</span></span>|  
|`anycpu32bitpreferred`|<span data-ttu-id="dfd0c-115">Compile votre assembly pour qu'il s'exécute sur n'importe quelle plateforme.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-115">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="dfd0c-116">L'application s'exécutera en tant qu'application 32 bits sur les versions 32 et 64 bits de Windows.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-116">The application will run as a 32-bit application on both 32-bit and 64-bit versions of Windows.</span></span> <span data-ttu-id="dfd0c-117">Cet indicateur n’est valide que pour les fichiers exécutables (. EXE) et requiert .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-117">This flag is valid only for executables (.EXE) and requires .NET Framework 4.5.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfd0c-118">Notes</span><span class="sxs-lookup"><span data-stu-id="dfd0c-118">Remarks</span></span>  

 <span data-ttu-id="dfd0c-119">Utilisez l'option `-platform` pour spécifier le type de processeur ciblé par le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-119">Use the `-platform` option to specify the type of processor targeted by the output file.</span></span>  
  
 <span data-ttu-id="dfd0c-120">En général, les assemblys .NET Framework écrits en Visual Basic s'exécutent de la même façon, quelle que soit la plateforme.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-120">In general, .NET Framework assemblies written in Visual Basic will run the same regardless of the platform.</span></span> <span data-ttu-id="dfd0c-121">Cependant, dans certains cas, leur comportement peut varier d'une plateforme à une autre.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-121">However, there are some cases that behave differently on different platforms.</span></span> <span data-ttu-id="dfd0c-122">Voici les cas les plus courants :</span><span class="sxs-lookup"><span data-stu-id="dfd0c-122">These common cases are:</span></span>  
  
- <span data-ttu-id="dfd0c-123">Structures contenant des membres qui changent de taille selon la plateforme, comme un type pointeur.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-123">Structures that contain members that change size depending on the platform, such as any pointer type.</span></span>  
  
- <span data-ttu-id="dfd0c-124">Opération arithmétique de pointeur qui inclut des tailles constantes.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-124">Pointer arithmetic that includes constant sizes.</span></span>  
  
- <span data-ttu-id="dfd0c-125">Appel de plateforme incorrect ou déclarations COM qui utilisent `Integer` pour des handles au lieu de <xref:System.IntPtr>.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-125">Incorrect platform invoke or COM declarations that use `Integer` for handles instead of <xref:System.IntPtr>.</span></span>  
  
- <span data-ttu-id="dfd0c-126">Cast de <xref:System.IntPtr> en `Integer`.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-126">Casting <xref:System.IntPtr> to `Integer`.</span></span>  
  
- <span data-ttu-id="dfd0c-127">Utilisation d'un appel de plateforme ou de COM interop avec des composants qui n'existent pas sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-127">Using platform invoke or COM interop with components that do not exist on all platforms.</span></span>  
  
 <span data-ttu-id="dfd0c-128">L’option **-Platform** permet d’atténuer certains problèmes si vous savez que vous avez fait des hypothèses sur l’architecture sur laquelle votre code s’exécutera.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-128">The **-platform** option will mitigate some issues if you know you have made assumptions about the architecture your code will run on.</span></span> <span data-ttu-id="dfd0c-129">Plus précisément :</span><span class="sxs-lookup"><span data-stu-id="dfd0c-129">Specifically:</span></span>  
  
- <span data-ttu-id="dfd0c-130">Si vous décidez de cibler une plateforme 64 bits et que l'application est exécutée sur un ordinateur 32 bits, le message d'erreur intervient bien plus tôt et est davantage axé sur le problème que sur l'erreur qui se produit quand ce commutateur n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-130">If you decide to target a 64-bit platform, and the application is run on a 32-bit machine, the error message comes much earlier and is more targeted at the problem than the error that occurs without using this switch.</span></span>  
  
- <span data-ttu-id="dfd0c-131">Si vous définissez l'indicateur `x86` au niveau de l'option et que l'application est par la suite exécutée sur un ordinateur 64 bits, l'application s'exécutera dans le sous-système WOW au lieu de s'exécuter en mode natif.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-131">If you set the `x86` flag on the option and the application is subsequently run on a 64-bit machine, the application will run in the WOW subsystem instead of running natively.</span></span>  
  
 <span data-ttu-id="dfd0c-132">Sur un système d'exploitation Windows 64 bits :</span><span class="sxs-lookup"><span data-stu-id="dfd0c-132">On a 64-bit Windows operating system:</span></span>  
  
- <span data-ttu-id="dfd0c-133">Les assemblys compilés avec `-platform:x86` s'exécutent sur le CLR 32 bits fonctionnant sous WOW64.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-133">Assemblies compiled with `-platform:x86` will execute on the 32-bit CLR running under WOW64.</span></span>  
  
- <span data-ttu-id="dfd0c-134">Les fichiers exécutables compilés avec `-platform:anycpu` s'exécutent sur le CLR 64 bits.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-134">Executables compiled with the `-platform:anycpu` will execute on the 64-bit CLR.</span></span>  
  
- <span data-ttu-id="dfd0c-135">Une DLL compilée avec `-platform:anycpu` s'exécute sur le même CLR que le processus dans lequel elle est chargée.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-135">A DLL compiled with the `-platform:anycpu` will execute on the same CLR as the process into which it loaded.</span></span>  
  
- <span data-ttu-id="dfd0c-136">Les fichiers exécutables compilés avec `-platform:anycpu32bitpreferred` s'exécutent sur le CLR 32 bits.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-136">Executables that are compiled with `-platform:anycpu32bitpreferred` will execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="dfd0c-137">Pour plus d’informations sur le développement d’une application pour qu’elle s’exécute sur une version 64 bits de Windows, consultez la page sur les [applications 64 bits](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="dfd0c-137">For more information about how to develop an application to run on a 64-bit version of Windows, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a><span data-ttu-id="dfd0c-138">Pour définir-Platform dans l’IDE de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dfd0c-138">To set -platform in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="dfd0c-139">Dans **Explorateur de solutions**, choisissez le projet, ouvrez le menu **projet** , puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-139">In **Solution Explorer**, choose the project, open the **Project** menu, and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="dfd0c-140">Sous l’onglet **compiler** , activez ou désactivez la case à cocher **préférer 32 bits** ou, dans la liste **unité centrale cible** , choisissez une valeur.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-140">On the **Compile** tab, select or clear the **Prefer 32-bit** check box, or, in the **Target CPU** list, choose a value.</span></span>  
  
     <span data-ttu-id="dfd0c-141">Pour plus d’informations, consultez [compiler, page du concepteur de projets (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="dfd0c-141">For more information, see [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfd0c-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="dfd0c-142">Example</span></span>  

 <span data-ttu-id="dfd0c-143">L'exemple suivant montre comment utiliser l'option de compilateur `-platform`.</span><span class="sxs-lookup"><span data-stu-id="dfd0c-143">The following example illustrates how to use the `-platform` compiler option.</span></span>  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="dfd0c-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dfd0c-144">See also</span></span>

- [<span data-ttu-id="dfd0c-145">-cible (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dfd0c-145">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="dfd0c-146">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dfd0c-146">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="dfd0c-147">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="dfd0c-147">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
