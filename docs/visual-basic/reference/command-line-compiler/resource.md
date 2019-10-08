---
title: -ressource (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
ms.openlocfilehash: 5bedc346381f6de293933dce14a8c5c3044b246f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005188"
---
# <a name="-resource-visual-basic"></a><span data-ttu-id="5f612-102">-ressource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f612-102">-resource (Visual Basic)</span></span>
<span data-ttu-id="5f612-103">Incorpore une ressource managée dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="5f612-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f612-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f612-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,public|private]]  
```

<span data-ttu-id="5f612-105">ou</span><span class="sxs-lookup"><span data-stu-id="5f612-105">or</span></span>  

```console
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5f612-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="5f612-106">Arguments</span></span>  
  
|<span data-ttu-id="5f612-107">Terme</span><span class="sxs-lookup"><span data-stu-id="5f612-107">Term</span></span>|<span data-ttu-id="5f612-108">Définition</span><span class="sxs-lookup"><span data-stu-id="5f612-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="5f612-109">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="5f612-109">Required.</span></span> <span data-ttu-id="5f612-110">Nom du fichier de ressources à incorporer dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="5f612-110">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="5f612-111">Par défaut, `filename` est public dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="5f612-111">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="5f612-112">Placez le nom de fichier entre guillemets ("") s’il contient un espace.</span><span class="sxs-lookup"><span data-stu-id="5f612-112">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="5f612-113">facultatif.</span><span class="sxs-lookup"><span data-stu-id="5f612-113">Optional.</span></span> <span data-ttu-id="5f612-114">Nom logique de la ressource ; nom utilisé pour le charger.</span><span class="sxs-lookup"><span data-stu-id="5f612-114">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="5f612-115">La valeur par défaut est le nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="5f612-115">The default is the name of the file.</span></span> <span data-ttu-id="5f612-116">Si vous le souhaitez, vous pouvez spécifier si la ressource est publique ou privée dans le manifeste de l’assembly, comme suit : `-res:filename.res, myname.res, public`</span><span class="sxs-lookup"><span data-stu-id="5f612-116">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `-res:filename.res, myname.res, public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f612-117">Notes</span><span class="sxs-lookup"><span data-stu-id="5f612-117">Remarks</span></span>  
 <span data-ttu-id="5f612-118">Utilisez `-linkresource` pour lier une ressource à un assembly sans placer le fichier de ressources dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="5f612-118">Use `-linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="5f612-119">Si `filename` est un fichier de ressources .NET Framework créé, par exemple, par [Resgen. exe (générateur de fichiers de ressources)](../../../framework/tools/resgen-exe-resource-file-generator.md) ou dans l’environnement de développement, il est possible d’y accéder avec les membres de l’espace de noms <xref:System.Resources> (pour plus d’informations, consultez <xref:System.Resources.ResourceManager>).</span><span class="sxs-lookup"><span data-stu-id="5f612-119">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="5f612-120">Pour accéder à toutes les autres ressources au moment de l’exécution, utilisez l’une des méthodes suivantes : <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> ou <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="5f612-120">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="5f612-121">La forme abrégée de `-resource` est `-res`.</span><span class="sxs-lookup"><span data-stu-id="5f612-121">The short form of `-resource` is `-res`.</span></span>  
  
 <span data-ttu-id="5f612-122">Pour plus d’informations sur la façon de définir `-resource` dans l’IDE de Visual Studio, consultez [gestion des ressources d’application (.net)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="5f612-122">For information about how to set `-resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f612-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="5f612-123">Example</span></span>  
 <span data-ttu-id="5f612-124">Le code suivant compile `In.vb` et joint le fichier de ressources `Rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="5f612-124">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="5f612-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f612-125">See also</span></span>

- [<span data-ttu-id="5f612-126">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5f612-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="5f612-127">-win32resource</span><span class="sxs-lookup"><span data-stu-id="5f612-127">-win32resource</span></span>](../../../visual-basic/reference/command-line-compiler/win32resource.md)
- [<span data-ttu-id="5f612-128">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f612-128">-linkresource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/linkresource.md)
- [<span data-ttu-id="5f612-129">-cible (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f612-129">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="5f612-130">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="5f612-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
