---
title: -sdkpath
ms.date: 07/20/2015
f1_keywords:
- sdkpath
- -sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
ms.openlocfilehash: 46cec7ac3cb78c4fc97e299535f9085eff6daeff
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004692"
---
# <a name="-sdkpath"></a><span data-ttu-id="8abe3-102">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="8abe3-102">-sdkpath</span></span>
<span data-ttu-id="8abe3-103">Spécifie l’emplacement de mscorlib. dll et de Microsoft. VisualBasic. dll.</span><span class="sxs-lookup"><span data-stu-id="8abe3-103">Specifies the location of mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8abe3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8abe3-104">Syntax</span></span>  
  
```console  
-sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="8abe3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8abe3-105">Arguments</span></span>  
 `path`  
 <span data-ttu-id="8abe3-106">Répertoire contenant les versions de mscorlib. dll et de Microsoft. VisualBasic. dll à utiliser pour la compilation.</span><span class="sxs-lookup"><span data-stu-id="8abe3-106">The directory containing the versions of mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="8abe3-107">Ce chemin d’accès n’est pas vérifié tant qu’il n’est pas chargé.</span><span class="sxs-lookup"><span data-stu-id="8abe3-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="8abe3-108">Placez le nom du répertoire entre guillemets ("") s’il contient un espace.</span><span class="sxs-lookup"><span data-stu-id="8abe3-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8abe3-109">Notes</span><span class="sxs-lookup"><span data-stu-id="8abe3-109">Remarks</span></span>  
 <span data-ttu-id="8abe3-110">Cette option indique au compilateur Visual Basic de charger les fichiers Mscorlib. dll et Microsoft. VisualBasic. dll à partir d’un emplacement autre que celui par défaut.</span><span class="sxs-lookup"><span data-stu-id="8abe3-110">This option tells the Visual Basic compiler to load the mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="8abe3-111">L' `-sdkpath` option a été conçue pour être utilisée avec [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span><span class="sxs-lookup"><span data-stu-id="8abe3-111">The `-sdkpath` option was designed to be used with [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span></span> <span data-ttu-id="8abe3-112">Le .NET Compact Framework utilise différentes versions de ces bibliothèques de prise en charge pour éviter l’utilisation de types et de fonctionnalités de langage introuvables sur les appareils.</span><span class="sxs-lookup"><span data-stu-id="8abe3-112">The .NET Compact Framework uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8abe3-113">L' `-sdkpath` option n’est pas disponible dans l’environnement de développement Visual Studio. elle est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="8abe3-113">The `-sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="8abe3-114">L' `-sdkpath` option est définie lors du chargement d’un projet d’appareil Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8abe3-114">The `-sdkpath` option is set when a Visual Basic device project is loaded.</span></span>  
  
 <span data-ttu-id="8abe3-115">Vous pouvez spécifier que le compilateur doit compiler sans référence à la bibliothèque Visual Basic Runtime à l’aide de `-vbruntime` l’option du compilateur.</span><span class="sxs-lookup"><span data-stu-id="8abe3-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `-vbruntime` compiler option.</span></span> <span data-ttu-id="8abe3-116">Pour plus d’informations, consultez [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span><span class="sxs-lookup"><span data-stu-id="8abe3-116">For more information, see [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8abe3-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="8abe3-117">Example</span></span>  
 <span data-ttu-id="8abe3-118">Le code suivant est compilé `Myfile.vb` avec l' .NET Compact Framework, à l’aide des versions de mscorlib. dll et de Microsoft. VisualBasic. dll trouvées dans le répertoire d’installation par défaut du .NET Compact Framework sur le lecteur C.</span><span class="sxs-lookup"><span data-stu-id="8abe3-118">The following code compiles `Myfile.vb` with the .NET Compact Framework, using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the .NET Compact Framework on the C drive.</span></span> <span data-ttu-id="8abe3-119">En règle générale, vous utilisez la version la plus récente du .NET Compact Framework.</span><span class="sxs-lookup"><span data-stu-id="8abe3-119">Typically, you would use the most recent version of the .NET Compact Framework.</span></span>  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="8abe3-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8abe3-120">See also</span></span>

- [<span data-ttu-id="8abe3-121">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8abe3-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="8abe3-122">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="8abe3-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="8abe3-123">-netcf</span><span class="sxs-lookup"><span data-stu-id="8abe3-123">-netcf</span></span>](../../../visual-basic/reference/command-line-compiler/netcf.md)
- [<span data-ttu-id="8abe3-124">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="8abe3-124">-vbruntime</span></span>](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
