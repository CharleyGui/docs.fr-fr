---
description: -target:winmdobj (Options du compilateur C#)
title: -target:winmdobj (Options du compilateur C#)
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: a13e2da02698209a514e716d65c1df3508cf1508
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "91171401"
---
# <a name="-targetwinmdobj-c-compiler-options"></a><span data-ttu-id="fcb5e-103">-target:winmdobj (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="fcb5e-103">-target:winmdobj (C# Compiler Options)</span></span>

<span data-ttu-id="fcb5e-104">Si vous utilisez l’option du compilateur **-target:winmdobj**, le compilateur crée un fichier .winmdobj intermédiaire que vous pouvez convertir en fichier binaire (.winmd) Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="fcb5e-104">If you use the **-target:winmdobj** compiler option, the compiler creates an intermediate .winmdobj file that you can convert to a Windows Runtime binary (.winmd) file.</span></span> <span data-ttu-id="fcb5e-105">Le fichier .winmd peut ensuite être consommé par des programmes JavaScript et C++, en plus des programmes en langage managé.</span><span class="sxs-lookup"><span data-stu-id="fcb5e-105">The .winmd file can then be consumed by JavaScript and C++ programs, in addition to managed language programs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcb5e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fcb5e-106">Syntax</span></span>  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a><span data-ttu-id="fcb5e-107">Notes</span><span class="sxs-lookup"><span data-stu-id="fcb5e-107">Remarks</span></span>  

 <span data-ttu-id="fcb5e-108">Le paramètre **winmdobj** signale au compilateur qu’un module intermédiaire est requis.</span><span class="sxs-lookup"><span data-stu-id="fcb5e-108">The **winmdobj** setting signals to the compiler that an intermediate module is required.</span></span> <span data-ttu-id="fcb5e-109">En réponse, Visual Studio compile la bibliothèque de classes C# comme fichier .winmdobj.</span><span class="sxs-lookup"><span data-stu-id="fcb5e-109">In response, Visual Studio compiles the C# class library as a .winmdobj file.</span></span> <span data-ttu-id="fcb5e-110">Le fichier .winmdobj peut ensuite être acheminé via l'outil d'exportation <xref:Microsoft.Build.Tasks.WinMDExp> pour produire un fichier de métadonnées Windows (.winmd).</span><span class="sxs-lookup"><span data-stu-id="fcb5e-110">The .winmdobj file can then be fed through the <xref:Microsoft.Build.Tasks.WinMDExp> export tool to produce a Windows metadata (.winmd) file.</span></span> <span data-ttu-id="fcb5e-111">Le fichier .winmd contient à la fois le code de la bibliothèque d'origine et les métadonnées WinMD utilisées par JavaScript ou C++ et par le Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="fcb5e-111">The .winmd file contains both the code from the original library and the WinMD metadata that is used by JavaScript or C++ and by the Windows Runtime.</span></span>  
  
 <span data-ttu-id="fcb5e-112">La sortie d’un fichier qui est compilé à l’aide de l’option du compilateur **-target:winmdobj** est conçue pour être utilisée uniquement comme entrée pour l’outil d’exportation WimMDExp ; le fichier .winmdobj proprement dit n’est pas référencé directement.</span><span class="sxs-lookup"><span data-stu-id="fcb5e-112">The output of a file that’s compiled by using the **-target:winmdobj** compiler option is designed to be used only as input for the WimMDExp export tool; the .winmdobj file itself isn’t referenced directly.</span></span>  
  
 <span data-ttu-id="fcb5e-113">À moins que vous n’utilisiez l’option [-out](./out-compiler-option.md), le fichier de sortie adopte le nom du premier fichier d’entrée.</span><span class="sxs-lookup"><span data-stu-id="fcb5e-113">Unless you use the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span> <span data-ttu-id="fcb5e-114">Une méthode [Main](../../programming-guide/main-and-command-args/index.md) n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="fcb5e-114">A [Main](../../programming-guide/main-and-command-args/index.md) method isn’t required.</span></span>  
  
 <span data-ttu-id="fcb5e-115">Si vous spécifiez l’option -target:winmdobj à une invite de commandes, tous les fichiers jusqu’à l’option **-out** ou [-target:module](./target-module-compiler-option.md) suivante sont utilisés pour créer le programme Windows.</span><span class="sxs-lookup"><span data-stu-id="fcb5e-115">If you specify the -target:winmdobj option at a command prompt, all files until the next **-out** or [-target:module](./target-module-compiler-option.md) option are used to create the Windows program.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a><span data-ttu-id="fcb5e-116">Pour définir cette option du compilateur dans l'IDE de Visual Studio pour une application Windows Store</span><span class="sxs-lookup"><span data-stu-id="fcb5e-116">To set this compiler option in the Visual Studio IDE for a Windows Store app</span></span>  
  
1. <span data-ttu-id="fcb5e-117">Dans l’**Explorateur de solutions**, ouvrez le menu contextuel de votre projet et choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="fcb5e-117">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="fcb5e-118">Choisissez l’onglet **Application**.</span><span class="sxs-lookup"><span data-stu-id="fcb5e-118">Choose the **Application** tab.</span></span>  
  
3. <span data-ttu-id="fcb5e-119">Dans la liste **Type de sortie**, choisissez **Fichier WinMD**.</span><span class="sxs-lookup"><span data-stu-id="fcb5e-119">In the **Output type** list, choose **WinMD File**.</span></span>  
  
     <span data-ttu-id="fcb5e-120">L’option de **fichier WinMD** est disponible uniquement pour les modèles d’application du Windows 8. x Store.</span><span class="sxs-lookup"><span data-stu-id="fcb5e-120">The **WinMD File** option is available only for Windows 8.x Store app templates.</span></span>  
  
 <span data-ttu-id="fcb5e-121">Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="fcb5e-121">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcb5e-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="fcb5e-122">Example</span></span>  

 <span data-ttu-id="fcb5e-123">La commande suivante compile `filename.cs` dans un fichier .winmdobj intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="fcb5e-123">The following command compiles `filename.cs` into an intermediate .winmdobj file.</span></span>  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="fcb5e-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fcb5e-124">See also</span></span>

- [<span data-ttu-id="fcb5e-125">-Target (options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="fcb5e-125">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="fcb5e-126">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="fcb5e-126">C# Compiler Options</span></span>](./index.md)
