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
ms.openlocfilehash: 6f90ce6c1590784cefbd5f15ca8a36941aad77ed
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91193775"
---
# <a name="-resource-c-compiler-options"></a><span data-ttu-id="c12c2-103">-resource (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="c12c2-103">-resource (C# Compiler Options)</span></span>

<span data-ttu-id="c12c2-104">Incorpore la ressource spécifiée dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="c12c2-104">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c12c2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c12c2-105">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c12c2-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="c12c2-106">Arguments</span></span>  

 `filename`  
 <span data-ttu-id="c12c2-107">Fichier de ressources .NET que vous souhaitez incorporer dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="c12c2-107">The .NET resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="c12c2-108">`identifier` (facultatif)</span><span class="sxs-lookup"><span data-stu-id="c12c2-108">`identifier` (optional)</span></span>  
 <span data-ttu-id="c12c2-109">Nom logique de la ressource. Il s’agit du nom utilisé pour charger la ressource.</span><span class="sxs-lookup"><span data-stu-id="c12c2-109">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="c12c2-110">La valeur par défaut est le nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="c12c2-110">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="c12c2-111">`accessibility-modifier` (facultatif)</span><span class="sxs-lookup"><span data-stu-id="c12c2-111">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="c12c2-112">Accessibilité de la ressource : publique ou privée.</span><span class="sxs-lookup"><span data-stu-id="c12c2-112">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="c12c2-113">La valeur par défaut est public.</span><span class="sxs-lookup"><span data-stu-id="c12c2-113">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c12c2-114">Notes</span><span class="sxs-lookup"><span data-stu-id="c12c2-114">Remarks</span></span>  

 <span data-ttu-id="c12c2-115">Utilisez [-linkresource](./linkresource-compiler-option.md) pour lier une ressource à un assembly sans ajouter le fichier de ressources au fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="c12c2-115">Use [-linkresource](./linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="c12c2-116">Par défaut, les ressources sont publiques dans l’assembly quand elles sont créées à l’aide du compilateur C#.</span><span class="sxs-lookup"><span data-stu-id="c12c2-116">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="c12c2-117">Pour rendre les ressources privées, spécifiez le modificateur d’accessibilité `private`.</span><span class="sxs-lookup"><span data-stu-id="c12c2-117">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="c12c2-118">Aucune accessibilité autre `public` ou `private` n’est autorisée.</span><span class="sxs-lookup"><span data-stu-id="c12c2-118">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="c12c2-119">Si `filename` est un fichier de ressources .net créé, par exemple par [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) ou dans l’environnement de développement, il est accessible à l’aide des membres de l' <xref:System.Resources> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="c12c2-119">If `filename` is a .NET resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="c12c2-120">Pour plus d'informations, consultez <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c12c2-120">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c12c2-121">Pour toutes les autres ressources, utilisez les méthodes `GetManifestResource` dans la classe <xref:System.Reflection.Assembly> pour accéder à la ressource au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="c12c2-121">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="c12c2-122">**-res** est la forme abrégée de **-resource**.</span><span class="sxs-lookup"><span data-stu-id="c12c2-122">**-res** is the short form of **-resource**.</span></span>  
  
 <span data-ttu-id="c12c2-123">L’ordre des ressources dans le fichier de sortie est déterminé par l’ordre spécifié sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="c12c2-123">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="c12c2-124">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c12c2-124">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="c12c2-125">Ajoutez un fichier de ressources à votre projet.</span><span class="sxs-lookup"><span data-stu-id="c12c2-125">Add a resource file to your project.</span></span>  
  
2. <span data-ttu-id="c12c2-126">Sélectionnez le fichier que vous souhaitez incorporer dans l’**Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="c12c2-126">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3. <span data-ttu-id="c12c2-127">Sélectionnez **Action de génération** pour le fichier dans la fenêtre **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="c12c2-127">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4. <span data-ttu-id="c12c2-128">Définissez \*\*Action de génération \*\* sur **Ressource incorporée**.</span><span class="sxs-lookup"><span data-stu-id="c12c2-128">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="c12c2-129">Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span><span class="sxs-lookup"><span data-stu-id="c12c2-129">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c12c2-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="c12c2-130">Example</span></span>  

 <span data-ttu-id="c12c2-131">Compilez `in.cs` et attachez le fichier de ressources `rf.resource` :</span><span class="sxs-lookup"><span data-stu-id="c12c2-131">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="c12c2-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c12c2-132">See also</span></span>

- [<span data-ttu-id="c12c2-133">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="c12c2-133">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="c12c2-134">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="c12c2-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
