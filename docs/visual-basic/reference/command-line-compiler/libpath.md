---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: a91bd74d0be4f1cb223091ee2527f9567b4ca5db
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058467"
---
# <a name="-libpath"></a><span data-ttu-id="9b8dc-102">-libpath</span><span class="sxs-lookup"><span data-stu-id="9b8dc-102">-libpath</span></span>

<span data-ttu-id="9b8dc-103">Spécifie l’emplacement des assemblys référencés.</span><span class="sxs-lookup"><span data-stu-id="9b8dc-103">Specifies the location of referenced assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b8dc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b8dc-104">Syntax</span></span>  
  
```console  
-libpath:dirList  
```  
  
## <a name="arguments"></a><span data-ttu-id="9b8dc-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9b8dc-105">Arguments</span></span>  
  
|<span data-ttu-id="9b8dc-106">Terme</span><span class="sxs-lookup"><span data-stu-id="9b8dc-106">Term</span></span>|<span data-ttu-id="9b8dc-107">Définition</span><span class="sxs-lookup"><span data-stu-id="9b8dc-107">Definition</span></span>|  
|---|---|  
|`dirList`|<span data-ttu-id="9b8dc-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="9b8dc-108">Required.</span></span> <span data-ttu-id="9b8dc-109">Liste de répertoires délimités par des points-virgules pour le compilateur à examiner si un assembly référencé est introuvable dans le répertoire de travail actuel (le répertoire à partir duquel vous appelez le compilateur) ou le répertoire système de l’common language runtime.</span><span class="sxs-lookup"><span data-stu-id="9b8dc-109">Semicolon-delimited list of directories for the compiler to look in if a referenced assembly is not found in either the current working directory (the directory from which you are invoking the compiler) or the common language runtime's system directory.</span></span> <span data-ttu-id="9b8dc-110">Si le nom du répertoire contient un espace, mettez-le entre guillemets ("").</span><span class="sxs-lookup"><span data-stu-id="9b8dc-110">If the directory name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b8dc-111">Notes</span><span class="sxs-lookup"><span data-stu-id="9b8dc-111">Remarks</span></span>  

 <span data-ttu-id="9b8dc-112">L' `-libpath` option spécifie l’emplacement des assemblys référencés par l’option [-Reference](reference.md) .</span><span class="sxs-lookup"><span data-stu-id="9b8dc-112">The `-libpath` option specifies the location of assemblies referenced by the [-reference](reference.md) option.</span></span>  
  
 <span data-ttu-id="9b8dc-113">Le compilateur recherche les références d’assembly qui ne sont pas complètes dans l’ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="9b8dc-113">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1. <span data-ttu-id="9b8dc-114">Répertoire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="9b8dc-114">Current working directory.</span></span> <span data-ttu-id="9b8dc-115">Il s’agit du répertoire à partir duquel le compilateur est appelé.</span><span class="sxs-lookup"><span data-stu-id="9b8dc-115">This is the directory from which the compiler is invoked.</span></span>  
  
2. <span data-ttu-id="9b8dc-116">Répertoire système du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="9b8dc-116">The common language runtime system directory.</span></span>  
  
3. <span data-ttu-id="9b8dc-117">Répertoires spécifiés par `-libpath` .</span><span class="sxs-lookup"><span data-stu-id="9b8dc-117">Directories specified by `-libpath`.</span></span>  
  
4. <span data-ttu-id="9b8dc-118">Répertoires spécifiés par la variable d’environnement LIB.</span><span class="sxs-lookup"><span data-stu-id="9b8dc-118">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="9b8dc-119">L' `-libpath` option est additive ; si vous la spécifiez plusieurs fois, elle est ajoutée à toutes les valeurs précédentes.</span><span class="sxs-lookup"><span data-stu-id="9b8dc-119">The `-libpath` option is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="9b8dc-120">Utilisez `-reference` pour spécifier une référence d’assembly.</span><span class="sxs-lookup"><span data-stu-id="9b8dc-120">Use `-reference` to specify an assembly reference.</span></span>  
  
|<span data-ttu-id="9b8dc-121">Pour définir-LIBPATH dans l’environnement de développement intégré Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9b8dc-121">To set -libpath in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="9b8dc-122">1. Sélectionnez un projet dans **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="9b8dc-122">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="9b8dc-123">Dans le menu **Projet** , cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="9b8dc-123">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="9b8dc-124">2. cliquez sur l’onglet **références** .</span><span class="sxs-lookup"><span data-stu-id="9b8dc-124">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="9b8dc-125">3. cliquez sur le bouton **chemins d’accès des références..** ..</span><span class="sxs-lookup"><span data-stu-id="9b8dc-125">3.  Click the **Reference Paths...** button.</span></span><br /><span data-ttu-id="9b8dc-126">4. dans la boîte de dialogue **chemins d’accès des références** , entrez le nom du répertoire dans la zone **dossier :** .</span><span class="sxs-lookup"><span data-stu-id="9b8dc-126">4.  In the **Reference Paths** dialog box, enter the directory name in the **Folder:** box.</span></span><br /><span data-ttu-id="9b8dc-127">5. cliquez sur **Ajouter un dossier**.</span><span class="sxs-lookup"><span data-stu-id="9b8dc-127">5.  Click **Add Folder**.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9b8dc-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="9b8dc-128">Example</span></span>  

 <span data-ttu-id="9b8dc-129">Le code suivant compile `T2.vb` pour créer un fichier. exe.</span><span class="sxs-lookup"><span data-stu-id="9b8dc-129">The following code compiles `T2.vb` to create an .exe file.</span></span> <span data-ttu-id="9b8dc-130">Le compilateur recherche les références d’assembly dans le répertoire de travail, dans le répertoire racine du lecteur C : et dans le nouveau répertoire des assemblys du lecteur C :.</span><span class="sxs-lookup"><span data-stu-id="9b8dc-130">The compiler looks in the working directory, in the root directory of the C: drive, and in the New Assemblies directory of the C: drive for assembly references.</span></span>  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="9b8dc-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b8dc-131">See also</span></span>

- [<span data-ttu-id="9b8dc-132">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="9b8dc-132">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="9b8dc-133">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9b8dc-133">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="9b8dc-134">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="9b8dc-134">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
