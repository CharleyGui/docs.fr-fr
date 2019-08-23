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
ms.openlocfilehash: d92b0d08daf660880b648875c67c3b78069143d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924855"
---
# <a name="-linkresource-visual-basic"></a><span data-ttu-id="e6e31-102">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6e31-102">-linkresource (Visual Basic)</span></span>
<span data-ttu-id="e6e31-103">Crée un lien à une ressource managée.</span><span class="sxs-lookup"><span data-stu-id="e6e31-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6e31-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6e31-104">Syntax</span></span>  
  
```  
-linkresource:filename[,identifier[,public|private]]  
' -or-  
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e6e31-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e6e31-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="e6e31-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="e6e31-106">Required.</span></span> <span data-ttu-id="e6e31-107">Fichier de ressources à lier à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="e6e31-107">The resource file to link to the assembly.</span></span> <span data-ttu-id="e6e31-108">Si le nom de fichier contient un espace, mettez-le entre guillemets ("").</span><span class="sxs-lookup"><span data-stu-id="e6e31-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="e6e31-109">facultatif.</span><span class="sxs-lookup"><span data-stu-id="e6e31-109">Optional.</span></span> <span data-ttu-id="e6e31-110">Nom logique de la ressource.</span><span class="sxs-lookup"><span data-stu-id="e6e31-110">The logical name for the resource.</span></span> <span data-ttu-id="e6e31-111">Nom utilisé pour charger la ressource.</span><span class="sxs-lookup"><span data-stu-id="e6e31-111">The name that is used to load the resource.</span></span> <span data-ttu-id="e6e31-112">La valeur par défaut est le nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="e6e31-112">The default is the name of the file.</span></span> <span data-ttu-id="e6e31-113">Si vous le souhaitez, vous pouvez spécifier si le fichier est public ou privé dans le manifeste de l’assembly, par exemple: `-linkres:filename.res,myname.res,public`.</span><span class="sxs-lookup"><span data-stu-id="e6e31-113">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `-linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="e6e31-114">Par défaut, `filename` est public dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="e6e31-114">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6e31-115">Notes</span><span class="sxs-lookup"><span data-stu-id="e6e31-115">Remarks</span></span>  
 <span data-ttu-id="e6e31-116">L' `-linkresource` option n’incorpore pas le fichier de ressources dans le fichier de sortie `-resource` ; utilisez l’option pour effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="e6e31-116">The `-linkresource` option does not embed the resource file in the output file; use the `-resource` option to do this.</span></span>  
  
 <span data-ttu-id="e6e31-117">L' `-linkresource` option requiert l’une `-target` des options autres que `-target:module`.</span><span class="sxs-lookup"><span data-stu-id="e6e31-117">The `-linkresource` option requires one of the `-target` options other than `-target:module`.</span></span>  
  
 <span data-ttu-id="e6e31-118">Si `filename` est un fichier de ressources de .NET Framework créé, par exemple, par [Resgen. exe (générateur de fichiers de ressources)](../../../framework/tools/resgen-exe-resource-file-generator.md) ou dans l’environnement de développement, il est accessible avec <xref:System.Resources> les membres de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="e6e31-118">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="e6e31-119">(Pour plus d'informations, consultez <xref:System.Resources.ResourceManager>.) Pour accéder à toutes les autres ressources au moment de l’exécution, utilisez les `GetManifestResource` méthodes qui <xref:System.Reflection.Assembly> commencent par dans la classe.</span><span class="sxs-lookup"><span data-stu-id="e6e31-119">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="e6e31-120">Le nom de fichier peut être n’importe quel format de fichier.</span><span class="sxs-lookup"><span data-stu-id="e6e31-120">The file name can be any file format.</span></span> <span data-ttu-id="e6e31-121">C’est le cas, par exemple, si vous voulez qu’une DLL native fasse partie de l'assembly pour qu’elle puisse être installée dans le Global Assembly Cache et accessible à partir du code managé dans l'assembly.</span><span class="sxs-lookup"><span data-stu-id="e6e31-121">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="e6e31-122">La forme abrégée de `-linkresource` est `-linkres`.</span><span class="sxs-lookup"><span data-stu-id="e6e31-122">The short form of `-linkresource` is `-linkres`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e6e31-123">L' `-linkresource` option n’est pas disponible dans l’environnement de développement Visual Studio; elle est disponible uniquement quand vous compilez à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="e6e31-123">The `-linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6e31-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="e6e31-124">Example</span></span>  
 <span data-ttu-id="e6e31-125">Le code suivant compile `in.vb` et établit un lien vers le fichier `rf.resource`de ressources.</span><span class="sxs-lookup"><span data-stu-id="e6e31-125">The following code compiles `in.vb` and links to resource file `rf.resource`.</span></span>  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6e31-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6e31-126">See also</span></span>

- [<span data-ttu-id="e6e31-127">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e6e31-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="e6e31-128">-cible (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6e31-128">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="e6e31-129">-ressource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6e31-129">-resource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/resource.md)
- [<span data-ttu-id="e6e31-130">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="e6e31-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
