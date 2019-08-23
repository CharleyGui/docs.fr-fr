---
title: -win32resource
ms.date: 03/13/2018
f1_keywords:
- -win32resource
- win32resource
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
ms.openlocfilehash: 382dcc6571aa06ecdfc32bf43080c4b7a36eb1f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961302"
---
# <a name="-win32resource"></a><span data-ttu-id="31cac-102">-win32resource</span><span class="sxs-lookup"><span data-stu-id="31cac-102">-win32resource</span></span>
<span data-ttu-id="31cac-103">Insère un fichier de ressources Win32 dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="31cac-103">Inserts a Win32 resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31cac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31cac-104">Syntax</span></span>  
  
```  
-win32resource:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="31cac-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="31cac-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="31cac-106">Nom du fichier de ressources à ajouter à votre fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="31cac-106">The name of the resource file to add to your output file.</span></span> <span data-ttu-id="31cac-107">Placez le nom de fichier entre guillemets ("") s’il contient un espace.</span><span class="sxs-lookup"><span data-stu-id="31cac-107">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31cac-108">Notes</span><span class="sxs-lookup"><span data-stu-id="31cac-108">Remarks</span></span>  
 <span data-ttu-id="31cac-109">Vous pouvez créer un fichier de ressources Win32 avec le compilateur de ressources Microsoft Windows (RC).</span><span class="sxs-lookup"><span data-stu-id="31cac-109">You can create a Win32 resource file with the Microsoft Windows Resource Compiler (RC).</span></span>  
  
 <span data-ttu-id="31cac-110">Une ressource Win32 peut contenir des informations de version ou de bitmap (icône) qui permettent d’identifier votre application dans l' **Explorateur de fichiers**.</span><span class="sxs-lookup"><span data-stu-id="31cac-110">A Win32 resource can contain version or bitmap (icon) information that helps identify your application in **File Explorer**.</span></span> <span data-ttu-id="31cac-111">Si vous ne spécifiez `-win32resource`pas, le compilateur génère des informations de version en fonction de la version de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="31cac-111">If you do not specify `-win32resource`, the compiler generates version information based on the assembly version.</span></span> <span data-ttu-id="31cac-112">Les `-win32resource` options `-win32icon` et s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="31cac-112">The `-win32resource` and `-win32icon` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="31cac-113">Consultez [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) pour référencer un fichier de ressources .NET Framework, ou [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) pour attacher un fichier de ressources de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="31cac-113">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a .NET Framework resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a .NET Framework resource file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31cac-114">L' `-win32resource` option n’est pas disponible dans l’environnement de développement Visual Studio; elle est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="31cac-114">The `-win32resource` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31cac-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="31cac-115">Example</span></span>  
 <span data-ttu-id="31cac-116">Le code suivant compile `In.vb` et joint un `Rf.res`fichier de ressources Win32:</span><span class="sxs-lookup"><span data-stu-id="31cac-116">The following code compiles `In.vb` and attaches a Win32 resource file, `Rf.res`:</span></span>  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="31cac-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31cac-117">See also</span></span>

- [<span data-ttu-id="31cac-118">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="31cac-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="31cac-119">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="31cac-119">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
