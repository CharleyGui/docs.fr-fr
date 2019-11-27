---
title: -resource
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
ms.openlocfilehash: a781d543dd32ffb3d0ac0b11c544dbfd8cd5d806
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348565"
---
# <a name="-resource-visual-basic"></a><span data-ttu-id="4bd5d-102">-ressource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4bd5d-102">-resource (Visual Basic)</span></span>
<span data-ttu-id="4bd5d-103">Incorpore une ressource managée dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="4bd5d-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bd5d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4bd5d-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,public|private]]  
```

<span data-ttu-id="4bd5d-105">or</span><span class="sxs-lookup"><span data-stu-id="4bd5d-105">or</span></span>  

```console
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="4bd5d-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="4bd5d-106">Arguments</span></span>  
  
|<span data-ttu-id="4bd5d-107">Terme</span><span class="sxs-lookup"><span data-stu-id="4bd5d-107">Term</span></span>|<span data-ttu-id="4bd5d-108">Définition</span><span class="sxs-lookup"><span data-stu-id="4bd5d-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="4bd5d-109">Requis.</span><span class="sxs-lookup"><span data-stu-id="4bd5d-109">Required.</span></span> <span data-ttu-id="4bd5d-110">Nom du fichier de ressources à incorporer dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="4bd5d-110">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="4bd5d-111">Par défaut, `filename` est public dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="4bd5d-111">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="4bd5d-112">Placez le nom de fichier entre guillemets ("") s’il contient un espace.</span><span class="sxs-lookup"><span data-stu-id="4bd5d-112">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="4bd5d-113">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="4bd5d-113">Optional.</span></span> <span data-ttu-id="4bd5d-114">Nom logique de la ressource ; nom utilisé pour le charger.</span><span class="sxs-lookup"><span data-stu-id="4bd5d-114">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="4bd5d-115">La valeur par défaut est le nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="4bd5d-115">The default is the name of the file.</span></span> <span data-ttu-id="4bd5d-116">Si vous le souhaitez, vous pouvez spécifier si la ressource est publique ou privée dans le manifeste de l’assembly, comme dans l’exemple suivant : `-res:filename.res, myname.res, public`</span><span class="sxs-lookup"><span data-stu-id="4bd5d-116">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `-res:filename.res, myname.res, public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bd5d-117">Notes</span><span class="sxs-lookup"><span data-stu-id="4bd5d-117">Remarks</span></span>  
 <span data-ttu-id="4bd5d-118">Utilisez `-linkresource` pour lier une ressource à un assembly sans placer le fichier de ressources dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="4bd5d-118">Use `-linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="4bd5d-119">Si `filename` est un fichier de ressources .NET Framework créé, par exemple, par [Resgen. exe (générateur de fichiers de ressources)](../../../framework/tools/resgen-exe-resource-file-generator.md) ou dans l’environnement de développement, il est accessible à l’aide des membres de l’espace de noms <xref:System.Resources> (pour plus d’informations, consultez <xref:System.Resources.ResourceManager>).</span><span class="sxs-lookup"><span data-stu-id="4bd5d-119">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="4bd5d-120">Pour accéder à toutes les autres ressources au moment de l’exécution, utilisez l’une des méthodes suivantes : <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>ou <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="4bd5d-120">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="4bd5d-121">La forme abrégée de `-resource` est `-res`.</span><span class="sxs-lookup"><span data-stu-id="4bd5d-121">The short form of `-resource` is `-res`.</span></span>  
  
 <span data-ttu-id="4bd5d-122">Pour plus d’informations sur la façon de définir `-resource` dans l’IDE de Visual Studio, consultez [gestion des ressources d’application (.net)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="4bd5d-122">For information about how to set `-resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bd5d-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="4bd5d-123">Example</span></span>  
 <span data-ttu-id="4bd5d-124">Le code suivant compile `In.vb` et joint le `Rf.resource`de fichier de ressources.</span><span class="sxs-lookup"><span data-stu-id="4bd5d-124">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="4bd5d-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4bd5d-125">See also</span></span>

- [<span data-ttu-id="4bd5d-126">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4bd5d-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="4bd5d-127">-win32resource</span><span class="sxs-lookup"><span data-stu-id="4bd5d-127">-win32resource</span></span>](../../../visual-basic/reference/command-line-compiler/win32resource.md)
- [<span data-ttu-id="4bd5d-128">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4bd5d-128">-linkresource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/linkresource.md)
- [<span data-ttu-id="4bd5d-129">-cible (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4bd5d-129">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="4bd5d-130">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="4bd5d-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
