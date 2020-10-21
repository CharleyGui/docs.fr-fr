---
title: Installer F#
description: 'Découvrez comment installer F # de différentes manières.'
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224291"
---
# <a name="install-f"></a>Installer F\#

Vous pouvez installer F # de plusieurs façons, en fonction de votre environnement.

## <a name="install-f-with-visual-studio"></a>Installer F # avec Visual Studio

1. Si vous téléchargez [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) pour la première fois, vous devez d’abord installer Visual Studio installer. Installez l’édition appropriée de Visual Studio à partir du programme d’installation.

   Si vous avez déjà installé Visual Studio, choisissez **modifier** en regard de l’édition à laquelle vous souhaitez ajouter le langage F #.

2. Sur la page charges de travail, sélectionnez la charge de travail **développement ASP.net et Web** , qui comprend la prise en charge de F # et de .net Core pour les projets ASP.net core.

3. Choisissez **modifier** dans le coin inférieur droit pour installer tout ce que vous avez sélectionné.

   Vous pouvez ensuite ouvrir Visual Studio avec F # en choisissant **lancer** dans Visual Studio installer.

## <a name="install-f-with-visual-studio-code"></a>Installer F # avec Visual Studio Code

1. Vérifiez que [git](https://git-scm.com/download) est installé et disponible sur votre chemin d’accès. Vous pouvez vérifier qu’il est correctement installé en entrant `git --version` à une invite de commandes et en appuyant sur **entrée**.

2. Installez les [Kit SDK .net Core](https://dotnet.microsoft.com/download) et [Visual Studio code](https://code.visualstudio.com).

3. Sélectionnez l’icône extensions et recherchez « Ionide » :

   Le seul plug-in requis pour la prise en charge de F # dans Visual Studio Code est [Ionide-FSharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). Toutefois, vous pouvez également installer [Ionide-factice](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) pour avoir une prise en charge [factice](https://fake.build/) et [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) pour bénéficier de la prise en charge d' [Paket](https://fsprojects.github.io/Paket/) . FACTICE et Paket sont des outils de la communauté F # supplémentaires pour la génération de projets et la gestion des dépendances, respectivement.

## <a name="install-f-with-visual-studio-for-mac"></a>Installer F # avec Visual Studio pour Mac

F # est installé par défaut dans [Visual Studio pour Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), quelle que soit la configuration choisie.

Une fois l’installation terminée, choisissez **démarrer Visual Studio**. Vous pouvez également ouvrir Visual Studio à l’aide de la recherche sur macOS.

## <a name="install-f-on-a-build-server"></a>Installer F # sur un serveur de builds

Si vous utilisez .NET Core ou .NET Framework via le kit de développement logiciel (SDK) .NET, il vous suffit d’installer le kit de développement logiciel (SDK) .NET sur votre serveur de builds. C’est tout ce dont vous avez besoin.

Si vous utilisez .NET Framework et que vous n’utilisez **pas** le kit de développement logiciel (SDK) .net, vous devez installer la [référence SKU Visual Studio Build Tools](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) sur votre serveur Windows. Dans le programme d’installation, sélectionnez **outils de génération de bureaux .net**, puis sélectionnez le composant **compilateur F #** sur le côté droit du menu installer.
