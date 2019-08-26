---
title: 'Procédure : ajouter des références aux bibliothèques de types'
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f0f254b7794ce1cd4c765bee70c78e3c60a14aa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946496"
---
# <a name="how-to-add-references-to-type-libraries"></a><span data-ttu-id="3ed5d-102">Procédure : ajouter des références aux bibliothèques de types</span><span class="sxs-lookup"><span data-stu-id="3ed5d-102">How to: Add References to Type Libraries</span></span>
<span data-ttu-id="3ed5d-103">Quand vous ajoutez une référence à une bibliothèque de types, Visual Studio génère un assembly d'interopérabilité contenant des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="3ed5d-103">Visual Studio generates an interop assembly containing metadata when you add a reference to a type library.</span></span> <span data-ttu-id="3ed5d-104">Si un assembly PIA (Primary Interop Assembly) est disponible, Visual Studio utilise l'assembly existant avant de générer un nouvel assembly d'interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="3ed5d-104">If a primary interop assembly is available, Visual Studio uses the existing assembly before generating a new interop assembly.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a><span data-ttu-id="3ed5d-105">Pour ajouter une référence dans une bibliothèque de types Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3ed5d-105">To add a reference to a type library in Visual Studio</span></span>  
  
1. <span data-ttu-id="3ed5d-106">Installez le fichier COM DLL ou EXE sur votre ordinateur, à moins que le fichier Setup.exe de Windows n'exécute l'installation à votre place.</span><span class="sxs-lookup"><span data-stu-id="3ed5d-106">Install the COM DLL or EXE file on your computer, unless a Windows Setup.exe file performs the installation for you.</span></span>  
  
2. <span data-ttu-id="3ed5d-107">Choisissez **Projet**, **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="3ed5d-107">Choose **Project**, **Add Reference**.</span></span>  
  
3. <span data-ttu-id="3ed5d-108">Dans le Gestionnaire de références, choisissez **COM**.</span><span class="sxs-lookup"><span data-stu-id="3ed5d-108">In the Reference Manager, choose **COM**.</span></span>  
  
4. <span data-ttu-id="3ed5d-109">Sélectionnez la bibliothèque de types dans la liste, ou naviguez jusqu'au fichier .tlb.</span><span class="sxs-lookup"><span data-stu-id="3ed5d-109">Select the type library from the list, or browse for the .tlb file.</span></span>  
  
5. <span data-ttu-id="3ed5d-110">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3ed5d-110">Choose **OK**.</span></span>  
  
6. <span data-ttu-id="3ed5d-111">Dans l’Explorateur de solutions, ouvrez le menu contextuel pour afficher la référence que vous venez d’ajouter, puis choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="3ed5d-111">In Solution Explorer, open the shortcut menu for the reference you just added, and then choose **Properties**.</span></span>  
  
7. <span data-ttu-id="3ed5d-112">Dans la fenêtre **Propriétés**, vérifiez que la propriété **Incorporer les types interop** a la valeur **True**.</span><span class="sxs-lookup"><span data-stu-id="3ed5d-112">In the **Properties** window, make sure that the **Embed Interop Types** property is set to **True**.</span></span> <span data-ttu-id="3ed5d-113">Visual Studio incorpore alors les informations de type pour les types COM dans vos fichiers exécutables, en éliminant le besoin de déployer des assemblys PIA (Primary Interop Assembly) avec votre application.</span><span class="sxs-lookup"><span data-stu-id="3ed5d-113">This causes Visual Studio to embed type information for COM types in your executables, eliminating the need to deploy primary interop assemblies with your app.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3ed5d-114">Les options de menu et de boîte de dialogue peuvent varier en fonction de la version de Visual Studio utilisée.</span><span class="sxs-lookup"><span data-stu-id="3ed5d-114">The menu and dialog box options may vary depending on the version of Visual Studio you're using.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a><span data-ttu-id="3ed5d-115">Pour ajouter une référence à une bibliothèque de types pour la compilation en ligne de commande</span><span class="sxs-lookup"><span data-stu-id="3ed5d-115">To add a reference to a type library for command-line compilation</span></span>  
  
1. <span data-ttu-id="3ed5d-116">Générez un assembly d’interopérabilité comme décrit dans [Guide pratique pour générer des assemblys d’interopérabilité à partir de bibliothèques de types](how-to-generate-interop-assemblies-from-type-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="3ed5d-116">Generate an interop assembly as described in [How to: Generate Interop Assemblies from Type Libraries](how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>  
  
2. <span data-ttu-id="3ed5d-117">Utilisez l’option du compilateur [/link (Options du compilateur C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) ou [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) avec le nom de l’assembly d’interopérabilité afin d’incorporer les informations de type pour les types COM dans vos fichiers exécutables.</span><span class="sxs-lookup"><span data-stu-id="3ed5d-117">Use the [/link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler option with the interop assembly name to embed type information for COM types in your executables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ed5d-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ed5d-118">See also</span></span>

- [<span data-ttu-id="3ed5d-119">Importation d'une bibliothèque de types sous la forme d'un assembly</span><span class="sxs-lookup"><span data-stu-id="3ed5d-119">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="3ed5d-120">Exposition de composants COM au .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3ed5d-120">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="3ed5d-121">Procédure pas à pas : Incorporation de types provenant d’assemblys managés dans Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="3ed5d-121">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>](../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md) 
- [<span data-ttu-id="3ed5d-122">Procédure pas à pas : Incorporation de types provenant d’assemblys managés dans Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ed5d-122">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [<span data-ttu-id="3ed5d-123">/link (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="3ed5d-123">/link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="3ed5d-124">/link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ed5d-124">/link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
