---
title: Bibliothèques Source Link et .NET
description: Bonnes pratiques relatives à l’utilisation de Source Link pour améliorer le débogage des bibliothèques .NET
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: 89f9e3b1fd70003c528465f29a143b157468d539
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089282"
---
# <a name="source-link"></a><span data-ttu-id="a0432-103">Source Link</span><span class="sxs-lookup"><span data-stu-id="a0432-103">Source Link</span></span>

<span data-ttu-id="a0432-104">Source Link est une technologie qui permet aux développeurs de déboguer le code source des assemblys .NET dans NuGet.</span><span class="sxs-lookup"><span data-stu-id="a0432-104">Source Link is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="a0432-105">Source Link s’exécute lors de la création du package NuGet et incorpore des métadonnées de contrôle de code source à l’intérieur des assemblys et du package.</span><span class="sxs-lookup"><span data-stu-id="a0432-105">Source Link executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="a0432-106">Les développeurs qui téléchargent le package et activent Source Link dans Visual Studio peuvent effectuer un pas à pas détaillé dans son code source.</span><span class="sxs-lookup"><span data-stu-id="a0432-106">Developers who download the package and have Source Link enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="a0432-107">Source Link fournit des métadonnées de contrôle de code source qui améliorent grandement le débogage.</span><span class="sxs-lookup"><span data-stu-id="a0432-107">Source Link provides source control metadata to create a great debugging experience.</span></span>

## <a name="source-link-demo"></a><span data-ttu-id="a0432-108">Démonstration de Source Link</span><span class="sxs-lookup"><span data-stu-id="a0432-108">Source Link demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a><span data-ttu-id="a0432-109">Utilisation de Source Link</span><span class="sxs-lookup"><span data-stu-id="a0432-109">Using Source Link</span></span>

<span data-ttu-id="a0432-110">Vous trouverez des instructions sur l’utilisation de Source Link dans le dépôt GitHub [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md).</span><span class="sxs-lookup"><span data-stu-id="a0432-110">Instructions for using Source Link can be found on the [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="a0432-111">Vous pouvez utiliser [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) pour vérifier que les métadonnées Source Link ont été correctement incorporées dans le package.</span><span class="sxs-lookup"><span data-stu-id="a0432-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the Source Link metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="a0432-112">Vérifiez que les métadonnées `Repository` sont présentes avec un identificateur de validation et que les fichiers. pdb sont situés avec le fichier. dll de chaque cible.</span><span class="sxs-lookup"><span data-stu-id="a0432-112">Check the `Repository` metadata is present with a commit identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="a0432-113">![Lien source dans l’Explorateur de package NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "Lien source dans l’Explorateur de package NuGet")</span><span class="sxs-lookup"><span data-stu-id="a0432-113">![Source Link in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "Source Link in NuGet Package Explorer")</span></span>

<span data-ttu-id="a0432-114">**✔️ À ENVISAGER** : Utiliser Source Link pour ajouter des métadonnées de contrôle de code source à vos assemblys et packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="a0432-114">**✔️ CONSIDER** using Source Link to add source control metadata to your assemblies and NuGet packages.</span></span>

> [!TIP]
> <span data-ttu-id="a0432-115">Vous pouvez améliorer davantage l’expérience de débogage d’un développeur en ajoutant des attributs de débogueur à vos types.</span><span class="sxs-lookup"><span data-stu-id="a0432-115">You can further enhance a developer's debugging experience by adding debugger attributes to your types.</span></span>
>
> * <span data-ttu-id="a0432-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> peut personnaliser la façon dont une classe ou un champ s’affiche dans les fenêtres de variables du débogueur.</span><span class="sxs-lookup"><span data-stu-id="a0432-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> can customize how a class or field is displayed in the debugger variable windows.</span></span>
> * <span data-ttu-id="a0432-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> demande au débogueur de parcourir le code au lieu d’y effectuer un pas à pas détaillé.</span><span class="sxs-lookup"><span data-stu-id="a0432-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instructs the debugger to step through the code instead of stepping into the code.</span></span>
> * <span data-ttu-id="a0432-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> contrôle si un membre est affiché dans les fenêtres de variables du débogueur.</span><span class="sxs-lookup"><span data-stu-id="a0432-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controls whether a member is displayed in the debugger variable windows.</span></span>

<span data-ttu-id="a0432-119">**✔️ À ENVISAGER** : publication des fichiers de symboles (`*.pdb`).</span><span class="sxs-lookup"><span data-stu-id="a0432-119">**✔️ CONSIDER** publishing symbol files (`*.pdb`).</span></span>

> <span data-ttu-id="a0432-120">Pour une meilleure expérience de débogage, votre bibliothèque doit publier les fichiers de symboles et utiliser Source Link.</span><span class="sxs-lookup"><span data-stu-id="a0432-120">For the best debugging experience your library should publish symbol files as well as use Source Link.</span></span> <span data-ttu-id="a0432-121">Pour plus d’informations sur les fichiers de symboles et les packages de symboles, consultez [Packages de symboles](./nuget.md#symbol-packages).</span><span class="sxs-lookup"><span data-stu-id="a0432-121">For more information about symbol files and symbol packages, see [Symbol packages](./nuget.md#symbol-packages).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a0432-122">[Précédent](dependencies.md)
>[Suivant](publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="a0432-122">[Previous](dependencies.md)
[Next](publish-nuget-package.md)</span></span>
