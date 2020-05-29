---
title: Bibliothèques Source Link et .NET
description: Bonnes pratiques relatives à l’utilisation de Source Link pour améliorer le débogage des bibliothèques .NET
ms.date: 01/15/2019
ms.openlocfilehash: 5dee2a6b1f77daa641351e02c1dd3e0a38f66550
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201981"
---
# <a name="source-link"></a><span data-ttu-id="f1341-103">Source Link</span><span class="sxs-lookup"><span data-stu-id="f1341-103">Source Link</span></span>

<span data-ttu-id="f1341-104">Source Link est une technologie qui permet aux développeurs de déboguer le code source des assemblys .NET dans NuGet.</span><span class="sxs-lookup"><span data-stu-id="f1341-104">Source Link is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="f1341-105">Source Link s’exécute lors de la création du package NuGet et incorpore des métadonnées de contrôle de code source à l’intérieur des assemblys et du package.</span><span class="sxs-lookup"><span data-stu-id="f1341-105">Source Link executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="f1341-106">Les développeurs qui téléchargent le package et activent Source Link dans Visual Studio peuvent effectuer un pas à pas détaillé dans son code source.</span><span class="sxs-lookup"><span data-stu-id="f1341-106">Developers who download the package and have Source Link enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="f1341-107">Source Link fournit des métadonnées de contrôle de code source qui améliorent grandement le débogage.</span><span class="sxs-lookup"><span data-stu-id="f1341-107">Source Link provides source control metadata to create a great debugging experience.</span></span>

## <a name="source-link-demo"></a><span data-ttu-id="f1341-108">Démonstration de Source Link</span><span class="sxs-lookup"><span data-stu-id="f1341-108">Source Link demo</span></span>

<!--markdownlint-disable MD034 -->
> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a><span data-ttu-id="f1341-109">Utilisation de Source Link</span><span class="sxs-lookup"><span data-stu-id="f1341-109">Using Source Link</span></span>

<span data-ttu-id="f1341-110">Vous trouverez des instructions sur l’utilisation de Source Link dans le dépôt GitHub [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md).</span><span class="sxs-lookup"><span data-stu-id="f1341-110">Instructions for using Source Link can be found on the [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="f1341-111">Vous pouvez utiliser [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) pour vérifier que les métadonnées Source Link ont été correctement incorporées dans le package.</span><span class="sxs-lookup"><span data-stu-id="f1341-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the Source Link metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="f1341-112">Vérifiez `Repository` que les métadonnées sont présentes avec un identificateur de validation et que les fichiers. pdb sont situés avec le fichier. dll de chaque cible.</span><span class="sxs-lookup"><span data-stu-id="f1341-112">Check the `Repository` metadata is present with a commit identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="f1341-113">![Lien source dans l’Explorateur de package NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "Lien source dans l’Explorateur de package NuGet")</span><span class="sxs-lookup"><span data-stu-id="f1341-113">![Source Link in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "Source Link in NuGet Package Explorer")</span></span>

<span data-ttu-id="f1341-114">✔️ À ENVISAGER : Utiliser Source Link pour ajouter des métadonnées de contrôle de code source à vos assemblys et packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="f1341-114">✔️ CONSIDER using Source Link to add source control metadata to your assemblies and NuGet packages.</span></span>

> [!TIP]
> <span data-ttu-id="f1341-115">Vous pouvez améliorer davantage l’expérience de débogage d’un développeur en ajoutant des attributs de débogueur à vos types.</span><span class="sxs-lookup"><span data-stu-id="f1341-115">You can further enhance a developer's debugging experience by adding debugger attributes to your types.</span></span>
>
> * <span data-ttu-id="f1341-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> peut personnaliser la façon dont une classe ou un champ s’affiche dans les fenêtres de variables du débogueur.</span><span class="sxs-lookup"><span data-stu-id="f1341-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> can customize how a class or field is displayed in the debugger variable windows.</span></span>
> * <span data-ttu-id="f1341-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> demande au débogueur de parcourir le code au lieu d’y effectuer un pas à pas détaillé.</span><span class="sxs-lookup"><span data-stu-id="f1341-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instructs the debugger to step through the code instead of stepping into the code.</span></span>
> * <span data-ttu-id="f1341-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> contrôle si un membre est affiché dans les fenêtres de variables du débogueur.</span><span class="sxs-lookup"><span data-stu-id="f1341-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controls whether a member is displayed in the debugger variable windows.</span></span>

<span data-ttu-id="f1341-119">✔️ À ENVISAGER : publication des fichiers de symboles (`*.pdb`).</span><span class="sxs-lookup"><span data-stu-id="f1341-119">✔️ CONSIDER publishing symbol files (`*.pdb`).</span></span>

> <span data-ttu-id="f1341-120">Pour une meilleure expérience de débogage, votre bibliothèque doit publier les fichiers de symboles et utiliser Source Link.</span><span class="sxs-lookup"><span data-stu-id="f1341-120">For the best debugging experience your library should publish symbol files as well as use Source Link.</span></span> <span data-ttu-id="f1341-121">Pour plus d’informations sur les fichiers de symboles et les packages de symboles, consultez [Packages de symboles](./nuget.md#symbol-packages).</span><span class="sxs-lookup"><span data-stu-id="f1341-121">For more information about symbol files and symbol packages, see [Symbol packages](./nuget.md#symbol-packages).</span></span>

<span data-ttu-id="f1341-122">✔️ envisagez d’activer les builds déterministes.</span><span class="sxs-lookup"><span data-stu-id="f1341-122">✔️ CONSIDER enabling deterministic builds.</span></span>

> <span data-ttu-id="f1341-123">Les builds déterministes permettent de vérifier que le fichier binaire résultant a été généré à partir de la source spécifiée et fournit la traçabilité.</span><span class="sxs-lookup"><span data-stu-id="f1341-123">Deterministic builds enable verification that the resulting binary was built from the specified source and provide traceability.</span></span> <span data-ttu-id="f1341-124">Pour plus d’informations sur les builds déterministes et les instructions permettant de les activer, consultez [Builds déterministe](https://github.com/clairernovotny/DeterministicBuilds).</span><span class="sxs-lookup"><span data-stu-id="f1341-124">For more information about deterministic builds and instructions for enabling them, see [Deterministic Builds](https://github.com/clairernovotny/DeterministicBuilds).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f1341-125">[Précédent](dependencies.md) 
> [Suivant](publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="f1341-125">[Previous](dependencies.md)
[Next](publish-nuget-package.md)</span></span>
