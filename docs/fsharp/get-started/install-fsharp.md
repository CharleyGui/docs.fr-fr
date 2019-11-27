---
title: Installer F#
description: Découvrez comment installer F# en fonction de votre environnement.
ms.date: 09/05/2019
ms.openlocfilehash: 592a4c7763266cee68809fca84f9604d7e96b8f1
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204875"
---
# <a name="install-f"></a>Installer F\#

Vous pouvez installer F# de plusieurs façons, en fonction de votre environnement.

## <a name="install-f-with-visual-studio"></a>Installer F# avec Visual Studio

Si vous téléchargez [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) pour la première fois, le programme d’installation de Visual Studio est tout d’abord installé. Installez la référence SKU appropriée de Visual Studio à partir du programme d’installation. Si vous l’avez déjà installé, cliquez sur **modifier**.

Vous verrez ensuite une liste de charges de travail. Sélectionnez **ASP.net et développement Web** pour installer F# la prise en charge et la prise en charge de .net Core pour les projets ASP.net core.

Ensuite, cliquez sur **modifier** dans la partie inférieure droite.  Cela permet d’installer tout ce que vous avez sélectionné. Vous pouvez ensuite ouvrir Visual Studio 2017 avec F# prise en charge des langues en cliquant sur **lancer**.

## <a name="install-f-with-visual-studio-code"></a>Installer F# avec Visual Studio code

Tout d’abord, assurez-vous que [git est installé](https://git-scm.com/download) et disponible sur votre chemin d’accès. Vous pouvez vérifier qu’il est correctement installé en tapant `git --version` à l’invite de commandes et en appuyant sur **entrée**.

Ensuite, installez le [Kit SDK .net Core](https://dotnet.microsoft.com/download).

Vous devez ensuite [Visual Studio code](https://code.visualstudio.com) installé.

Ensuite, cliquez sur l’icône extensions et recherchez « Ionide » :

Le seul plug-in F# requis pour la prise en charge de Visual Studio code est [Ionide-FSharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). Toutefois, vous pouvez également installer [Ionide-factice](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) pour avoir une prise en charge [factice](https://fake.build/) et [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) pour bénéficier de la prise en charge d' [Paket](https://fsprojects.github.io/Paket/) . FACTICE et Paket sont des F# outils de la communauté supplémentaires pour la génération de projets et la gestion des dépendances, respectivement.

## <a name="install-f-with-visual-studio-for-mac"></a>Installer F# avec Visual Studio pour Mac

F#est installé par défaut dans [Visual Studio pour Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), quelle que soit la configuration choisie.

Une fois l’installation terminée, choisissez « démarrer Visual Studio ». Vous pouvez également le lancer par le biais de Finder sur macOS.

## <a name="install-f-on-a-build-server"></a>Installer F# sur un serveur de builds

Si vous utilisez .NET Core ou .NET Framework via le kit de développement logiciel (SDK) .NET, il vous suffit d’installer le kit de développement logiciel (SDK) .NET sur votre serveur de builds. C’est tout ce dont vous avez besoin.

Si vous utilisez .NET Framework et que vous n’utilisez **pas** le kit de développement logiciel (SDK) .net, vous devez installer la [référence SKU Visual Studio Build Tools](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) sur votre serveur Windows. Dans le programme d’installation, sélectionnez **outils de génération de bureaux .net** , puis sélectionnez le  **F# composant compilateur** sur le côté droit du menu installer.
