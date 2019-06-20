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
ms.openlocfilehash: 91f64756b2fbf14dc96550420cd936973e6bec87
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67268296"
---
# <a name="-sdkpath"></a><span data-ttu-id="e1f23-102">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="e1f23-102">-sdkpath</span></span>
<span data-ttu-id="e1f23-103">Spécifie l’emplacement de mscorlib.dll et de Microsoft.VisualBasic.dll.</span><span class="sxs-lookup"><span data-stu-id="e1f23-103">Specifies the location of mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1f23-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1f23-104">Syntax</span></span>  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="e1f23-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e1f23-105">Arguments</span></span>  
 `path`  
 <span data-ttu-id="e1f23-106">Le répertoire contenant les versions de mscorlib.dll et de Microsoft.VisualBasic.dll à utiliser pour la compilation.</span><span class="sxs-lookup"><span data-stu-id="e1f23-106">The directory containing the versions of mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="e1f23-107">Ce chemin d’accès n’est pas vérifié jusqu'à ce qu’il est chargé.</span><span class="sxs-lookup"><span data-stu-id="e1f23-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="e1f23-108">Placez le nom de répertoire entre guillemets ( » «) s’il contient un espace.</span><span class="sxs-lookup"><span data-stu-id="e1f23-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1f23-109">Notes</span><span class="sxs-lookup"><span data-stu-id="e1f23-109">Remarks</span></span>  
 <span data-ttu-id="e1f23-110">Cette option indique au compilateur de Visual Basic pour charger le mscorlib.dll et Microsoft.VisualBasic.dll fichiers à partir d’un emplacement non défini par défaut.</span><span class="sxs-lookup"><span data-stu-id="e1f23-110">This option tells the Visual Basic compiler to load the mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="e1f23-111">Le `-sdkpath` option a été conçue pour être utilisée avec [- /netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span><span class="sxs-lookup"><span data-stu-id="e1f23-111">The `-sdkpath` option was designed to be used with [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span></span> <span data-ttu-id="e1f23-112">Le .NET Compact Framework utilise différentes versions de ces bibliothèques d’assistance pour éviter l’utilisation de types et les fonctionnalités de langage introuvables sur les appareils.</span><span class="sxs-lookup"><span data-stu-id="e1f23-112">The .NET Compact Framework uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1f23-113">Le `-sdkpath` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="e1f23-113">The `-sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="e1f23-114">Le `-sdkpath` option est définie lorsqu’un projet smart device de Visual Basic est chargé.</span><span class="sxs-lookup"><span data-stu-id="e1f23-114">The `-sdkpath` option is set when a Visual Basic device project is loaded.</span></span>  
  
 <span data-ttu-id="e1f23-115">Vous pouvez spécifier que le compilateur doit compiler sans référence à la bibliothèque Runtime Visual Basic à l’aide de la `-vbruntime` option du compilateur.</span><span class="sxs-lookup"><span data-stu-id="e1f23-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `-vbruntime` compiler option.</span></span> <span data-ttu-id="e1f23-116">Pour plus d’informations, consultez [- vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span><span class="sxs-lookup"><span data-stu-id="e1f23-116">For more information, see [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1f23-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="e1f23-117">Example</span></span>  
 <span data-ttu-id="e1f23-118">Le code suivant compile `Myfile.vb` avec .NET Compact Framework, l’utilisation des versions de Mscorlib.dll et de Microsoft.VisualBasic.dll trouvées dans le répertoire d’installation par défaut du .NET Compact Framework sur le lecteur C.</span><span class="sxs-lookup"><span data-stu-id="e1f23-118">The following code compiles `Myfile.vb` with the .NET Compact Framework, using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the .NET Compact Framework on the C drive.</span></span> <span data-ttu-id="e1f23-119">En règle générale, vous utiliseriez la version la plus récente du .NET Compact Framework.</span><span class="sxs-lookup"><span data-stu-id="e1f23-119">Typically, you would use the most recent version of the .NET Compact Framework.</span></span>  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1f23-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1f23-120">See also</span></span>

- [<span data-ttu-id="e1f23-121">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e1f23-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="e1f23-122">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="e1f23-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="e1f23-123">-netcf</span><span class="sxs-lookup"><span data-stu-id="e1f23-123">-netcf</span></span>](../../../visual-basic/reference/command-line-compiler/netcf.md)
- [<span data-ttu-id="e1f23-124">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="e1f23-124">-vbruntime</span></span>](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
