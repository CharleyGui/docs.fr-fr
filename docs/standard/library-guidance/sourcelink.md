---
title: Bibliothèques Source Link et .NET
description: Bonnes pratiques relatives à l’utilisation de Source Link pour améliorer le débogage des bibliothèques .NET
ms.date: 01/15/2019
ms.openlocfilehash: 3d768ae6e79efa23a8402ea37bc34cd58cd52c8c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744541"
---
# <a name="source-link"></a>Source Link

Source Link est une technologie qui permet aux développeurs de déboguer le code source des assemblys .NET dans NuGet. Source Link s’exécute lors de la création du package NuGet et incorpore des métadonnées de contrôle de code source à l’intérieur des assemblys et du package. Les développeurs qui téléchargent le package et activent Source Link dans Visual Studio peuvent effectuer un pas à pas détaillé dans son code source. Source Link fournit des métadonnées de contrôle de code source qui améliorent grandement le débogage.

## <a name="source-link-demo"></a>Démonstration de Source Link

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a>Utilisation de Source Link

Vous trouverez des instructions sur l’utilisation de Source Link dans le dépôt GitHub [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md).

Vous pouvez utiliser [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) pour vérifier que les métadonnées Source Link ont été correctement incorporées dans le package. Vérifiez que les métadonnées `Repository` sont présentes avec un identificateur de validation et que les fichiers. pdb sont situés avec le fichier. dll de chaque cible.

![Lien source dans l’Explorateur de package NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "Lien source dans l’Explorateur de package NuGet")

✔️ envisagez d’utiliser le lien source pour ajouter des métadonnées de contrôle de code source à vos assemblys et packages NuGet.

> [!TIP]
> Vous pouvez améliorer davantage l’expérience de débogage d’un développeur en ajoutant des attributs de débogueur à vos types.
>
> * <xref:System.Diagnostics.DebuggerDisplayAttribute> peut personnaliser la façon dont une classe ou un champ s’affiche dans les fenêtres de variables du débogueur.
> * <xref:System.Diagnostics.DebuggerStepThroughAttribute> demande au débogueur de parcourir le code au lieu d’y effectuer un pas à pas détaillé.
> * <xref:System.Diagnostics.DebuggerBrowsableAttribute> contrôle si un membre est affiché dans les fenêtres de variables du débogueur.

✔️ envisagez de publier des fichiers de symboles (`*.pdb`).

> Pour une meilleure expérience de débogage, votre bibliothèque doit publier les fichiers de symboles et utiliser Source Link. Pour plus d’informations sur les fichiers de symboles et les packages de symboles, consultez [Packages de symboles](./nuget.md#symbol-packages).

>[!div class="step-by-step"]
>[Précédent](dependencies.md)
>[Suivant](publish-nuget-package.md)
