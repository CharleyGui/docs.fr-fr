---
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
ms.openlocfilehash: e14bf59f5922a918b627af22c052c8efd9081e84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602527"
---
# <a name="-resource-c-compiler-options"></a><span data-ttu-id="f1277-102">-resource (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="f1277-102">-resource (C# Compiler Options)</span></span>
<span data-ttu-id="f1277-103">Incorpore la ressource spécifiée dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="f1277-103">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1277-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1277-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="f1277-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f1277-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="f1277-106">Fichier de ressources .NET Framework que vous voulez incorporer dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="f1277-106">The .NET Framework resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="f1277-107">`identifier` (facultatif)</span><span class="sxs-lookup"><span data-stu-id="f1277-107">`identifier` (optional)</span></span>  
 <span data-ttu-id="f1277-108">Nom logique de la ressource. Il s’agit du nom utilisé pour charger la ressource.</span><span class="sxs-lookup"><span data-stu-id="f1277-108">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="f1277-109">La valeur par défaut est le nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="f1277-109">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="f1277-110">`accessibility-modifier` (facultatif)</span><span class="sxs-lookup"><span data-stu-id="f1277-110">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="f1277-111">Accessibilité de la ressource : publique ou privée.</span><span class="sxs-lookup"><span data-stu-id="f1277-111">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="f1277-112">La valeur par défaut est public.</span><span class="sxs-lookup"><span data-stu-id="f1277-112">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1277-113">Notes </span><span class="sxs-lookup"><span data-stu-id="f1277-113">Remarks</span></span>  
 <span data-ttu-id="f1277-114">Utilisez [-linkresource](./linkresource-compiler-option.md) pour lier une ressource à un assembly sans ajouter le fichier de ressources au fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="f1277-114">Use [-linkresource](./linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="f1277-115">Par défaut, les ressources sont publiques dans l’assembly quand elles sont créées à l’aide du compilateur C#.</span><span class="sxs-lookup"><span data-stu-id="f1277-115">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="f1277-116">Pour rendre les ressources privées, spécifiez le modificateur d’accessibilité `private`.</span><span class="sxs-lookup"><span data-stu-id="f1277-116">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="f1277-117">Aucune accessibilité autre `public` ou `private` n’est autorisée.</span><span class="sxs-lookup"><span data-stu-id="f1277-117">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="f1277-118">Si `filename` est un fichier de ressources .NET Framework créé, par exemple, par [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) ou dans l'environnement de développement, il est accessible à l'aide des membres de l'espace de noms <xref:System.Resources>.</span><span class="sxs-lookup"><span data-stu-id="f1277-118">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="f1277-119">Pour plus d’informations, consultez <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f1277-119">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f1277-120">Pour toutes les autres ressources, utilisez les méthodes `GetManifestResource` dans la classe <xref:System.Reflection.Assembly> pour accéder à la ressource au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f1277-120">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="f1277-121">**-res** est la forme abrégée de **-resource**.</span><span class="sxs-lookup"><span data-stu-id="f1277-121">**-res** is the short form of **-resource**.</span></span>  
  
 <span data-ttu-id="f1277-122">L’ordre des ressources dans le fichier de sortie est déterminé par l’ordre spécifié sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="f1277-122">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="f1277-123">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f1277-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="f1277-124">Ajoutez un fichier de ressources à votre projet.</span><span class="sxs-lookup"><span data-stu-id="f1277-124">Add a resource file to your project.</span></span>  
  
2. <span data-ttu-id="f1277-125">Sélectionnez le fichier que vous souhaitez incorporer dans l’**Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="f1277-125">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3. <span data-ttu-id="f1277-126">Sélectionnez **Action de génération** pour le fichier dans la fenêtre **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f1277-126">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4. <span data-ttu-id="f1277-127">Définissez \*\*Action de génération \*\* sur **Ressource incorporée**.</span><span class="sxs-lookup"><span data-stu-id="f1277-127">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="f1277-128">Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span><span class="sxs-lookup"><span data-stu-id="f1277-128">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1277-129"> Exemple</span><span class="sxs-lookup"><span data-stu-id="f1277-129">Example</span></span>  
 <span data-ttu-id="f1277-130">Compilez `in.cs` et attachez le fichier de ressources `rf.resource` :</span><span class="sxs-lookup"><span data-stu-id="f1277-130">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="f1277-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1277-131">See also</span></span>

- [<span data-ttu-id="f1277-132">Options de compilateur C</span><span class="sxs-lookup"><span data-stu-id="f1277-132">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="f1277-133">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="f1277-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
