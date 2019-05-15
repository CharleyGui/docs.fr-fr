---
title: -linkresource (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: 637a1d4b7a523feb2fc8da10a0c18e68774c480a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586697"
---
# <a name="-linkresource-visual-basic"></a><span data-ttu-id="3206e-102">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3206e-102">-linkresource (Visual Basic)</span></span>
<span data-ttu-id="3206e-103">Crée un lien à une ressource managée.</span><span class="sxs-lookup"><span data-stu-id="3206e-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3206e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3206e-104">Syntax</span></span>  
  
```  
-linkresource:filename[,identifier[,public|private]]  
' -or-  
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="3206e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3206e-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="3206e-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="3206e-106">Required.</span></span> <span data-ttu-id="3206e-107">Le fichier de ressources à lier à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="3206e-107">The resource file to link to the assembly.</span></span> <span data-ttu-id="3206e-108">Si le nom de fichier contient un espace, placez le nom entre guillemets ( » «).</span><span class="sxs-lookup"><span data-stu-id="3206e-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="3206e-109">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="3206e-109">Optional.</span></span> <span data-ttu-id="3206e-110">Le nom logique pour la ressource.</span><span class="sxs-lookup"><span data-stu-id="3206e-110">The logical name for the resource.</span></span> <span data-ttu-id="3206e-111">Le nom qui est utilisé pour charger la ressource.</span><span class="sxs-lookup"><span data-stu-id="3206e-111">The name that is used to load the resource.</span></span> <span data-ttu-id="3206e-112">La valeur par défaut est le nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="3206e-112">The default is the name of the file.</span></span> <span data-ttu-id="3206e-113">Si vous le souhaitez, vous pouvez spécifier si le fichier est public ou privé dans le manifeste d’assembly, par exemple : `-linkres:filename.res,myname.res,public`.</span><span class="sxs-lookup"><span data-stu-id="3206e-113">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `-linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="3206e-114">Par défaut, `filename` est public dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="3206e-114">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3206e-115">Notes</span><span class="sxs-lookup"><span data-stu-id="3206e-115">Remarks</span></span>  
 <span data-ttu-id="3206e-116">Le `-linkresource` option ne pas incorpore le fichier de ressources dans le fichier de sortie ; Utilisez la `-resource` option pour ce faire.</span><span class="sxs-lookup"><span data-stu-id="3206e-116">The `-linkresource` option does not embed the resource file in the output file; use the `-resource` option to do this.</span></span>  
  
 <span data-ttu-id="3206e-117">Le `-linkresource` option requiert l’une de la `-target` autre que `-target:module`.</span><span class="sxs-lookup"><span data-stu-id="3206e-117">The `-linkresource` option requires one of the `-target` options other than `-target:module`.</span></span>  
  
 <span data-ttu-id="3206e-118">Si `filename` est un fichier de ressources .NET Framework créé, par exemple, par le [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) ou dans l’environnement de développement, il est accessible à l’aide des membres de la <xref:System.Resources> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="3206e-118">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="3206e-119">(Pour plus d'informations, consultez <xref:System.Resources.ResourceManager>.) Pour accéder à toutes les autres ressources au moment de l’exécution, utilisez les méthodes qui commencent par `GetManifestResource` dans la <xref:System.Reflection.Assembly> classe.</span><span class="sxs-lookup"><span data-stu-id="3206e-119">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="3206e-120">Le nom de fichier peut être n’importe quel format de fichier.</span><span class="sxs-lookup"><span data-stu-id="3206e-120">The file name can be any file format.</span></span> <span data-ttu-id="3206e-121">C’est le cas, par exemple, si vous voulez qu’une DLL native fasse partie de l'assembly pour qu’elle puisse être installée dans le Global Assembly Cache et accessible à partir du code managé dans l'assembly.</span><span class="sxs-lookup"><span data-stu-id="3206e-121">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="3206e-122">La forme abrégée de `-linkresource` est `-linkres`.</span><span class="sxs-lookup"><span data-stu-id="3206e-122">The short form of `-linkresource` is `-linkres`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3206e-123">Le `-linkresource` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lorsque vous compilez à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="3206e-123">The `-linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3206e-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="3206e-124">Example</span></span>  
 <span data-ttu-id="3206e-125">Le code suivant compile `in.vb` et des liens vers le fichier de ressources `rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="3206e-125">The following code compiles `in.vb` and links to resource file `rf.resource`.</span></span>  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3206e-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3206e-126">See also</span></span>

- [<span data-ttu-id="3206e-127">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3206e-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="3206e-128">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3206e-128">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="3206e-129">-resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3206e-129">-resource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/resource.md)
- [<span data-ttu-id="3206e-130">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="3206e-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
