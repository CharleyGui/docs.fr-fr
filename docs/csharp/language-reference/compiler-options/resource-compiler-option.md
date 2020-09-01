---
description: -resource (Options du compilateur C#)
title: -resource (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /resource
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
ms.openlocfilehash: 963004820f56272b4f1b1d92ccc4d0a60493a4a0
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128697"
---
# <a name="-resource-c-compiler-options"></a><span data-ttu-id="d53e3-103">-resource (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="d53e3-103">-resource (C# Compiler Options)</span></span>
<span data-ttu-id="d53e3-104">Incorpore la ressource spécifiée dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="d53e3-104">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d53e3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d53e3-105">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d53e3-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="d53e3-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="d53e3-107">Fichier de ressources .NET Framework que vous voulez incorporer dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="d53e3-107">The .NET Framework resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="d53e3-108">`identifier` (facultatif)</span><span class="sxs-lookup"><span data-stu-id="d53e3-108">`identifier` (optional)</span></span>  
 <span data-ttu-id="d53e3-109">Nom logique de la ressource. Il s’agit du nom utilisé pour charger la ressource.</span><span class="sxs-lookup"><span data-stu-id="d53e3-109">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="d53e3-110">La valeur par défaut est le nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="d53e3-110">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="d53e3-111">`accessibility-modifier` (facultatif)</span><span class="sxs-lookup"><span data-stu-id="d53e3-111">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="d53e3-112">Accessibilité de la ressource : publique ou privée.</span><span class="sxs-lookup"><span data-stu-id="d53e3-112">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="d53e3-113">La valeur par défaut est public.</span><span class="sxs-lookup"><span data-stu-id="d53e3-113">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d53e3-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="d53e3-114">Remarks</span></span>  
 <span data-ttu-id="d53e3-115">Utilisez [-linkresource](./linkresource-compiler-option.md) pour lier une ressource à un assembly sans ajouter le fichier de ressources au fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="d53e3-115">Use [-linkresource](./linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="d53e3-116">Par défaut, les ressources sont publiques dans l’assembly quand elles sont créées à l’aide du compilateur C#.</span><span class="sxs-lookup"><span data-stu-id="d53e3-116">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="d53e3-117">Pour rendre les ressources privées, spécifiez le modificateur d’accessibilité `private`.</span><span class="sxs-lookup"><span data-stu-id="d53e3-117">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="d53e3-118">Aucune accessibilité autre `public` ou `private` n’est autorisée.</span><span class="sxs-lookup"><span data-stu-id="d53e3-118">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="d53e3-119">Si `filename` est un fichier de ressources .NET Framework créé, par exemple, par [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) ou dans l'environnement de développement, il est accessible à l'aide des membres de l'espace de noms <xref:System.Resources>.</span><span class="sxs-lookup"><span data-stu-id="d53e3-119">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="d53e3-120">Pour plus d'informations, consultez <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d53e3-120">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d53e3-121">Pour toutes les autres ressources, utilisez les méthodes `GetManifestResource` dans la classe <xref:System.Reflection.Assembly> pour accéder à la ressource au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d53e3-121">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="d53e3-122">**-res** est la forme abrégée de **-resource**.</span><span class="sxs-lookup"><span data-stu-id="d53e3-122">**-res** is the short form of **-resource**.</span></span>  
  
 <span data-ttu-id="d53e3-123">L’ordre des ressources dans le fichier de sortie est déterminé par l’ordre spécifié sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="d53e3-123">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d53e3-124">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d53e3-124">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="d53e3-125">Ajoutez un fichier de ressources à votre projet.</span><span class="sxs-lookup"><span data-stu-id="d53e3-125">Add a resource file to your project.</span></span>  
  
2. <span data-ttu-id="d53e3-126">Sélectionnez le fichier que vous souhaitez incorporer dans l’**Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="d53e3-126">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3. <span data-ttu-id="d53e3-127">Sélectionnez **Action de génération** pour le fichier dans la fenêtre **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="d53e3-127">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4. <span data-ttu-id="d53e3-128">Définissez \*\*Action de génération \*\* sur **Ressource incorporée**.</span><span class="sxs-lookup"><span data-stu-id="d53e3-128">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="d53e3-129">Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span><span class="sxs-lookup"><span data-stu-id="d53e3-129">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d53e3-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="d53e3-130">Example</span></span>  
 <span data-ttu-id="d53e3-131">Compilez `in.cs` et attachez le fichier de ressources `rf.resource` :</span><span class="sxs-lookup"><span data-stu-id="d53e3-131">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="d53e3-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d53e3-132">See also</span></span>

- [<span data-ttu-id="d53e3-133">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="d53e3-133">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="d53e3-134">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="d53e3-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
