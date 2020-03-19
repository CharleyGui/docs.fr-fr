---
title: Installer F#
description: Apprenez à installer le Fmd de différentes façons.
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400245"
---
# <a name="install-f"></a>Installer F\#

Vous pouvez installer F de multiples façons, en fonction de votre environnement.

## <a name="install-f-with-visual-studio"></a>Installer FMD avec Visual Studio

1. Si vous téléchargez [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) pour la première fois, il installera d’abord Visual Studio Install. Installez l’édition appropriée de Visual Studio à partir de l’installateur.

   Si vous avez déjà Visual Studio installé, choisissez **Modifier** à côté de l’édition que vous souhaitez ajouter F ' à.

2. Sur la page Charges de travail, sélectionnez la charge de travail **de ASP.NET et de développement Web,** qui comprend le support de base de F et .NET pour ASP.NET projets de base.

3. Choisissez **Modifier** dans le coin inférieur droit pour installer tout ce que vous avez sélectionné.

   Vous pouvez ensuite ouvrir Visual Studio avec Fmd en choisissant **Launch** in Visual Studio Install.

## <a name="install-f-with-visual-studio-code"></a>Installer FMD avec code visual studio

1. Assurez-vous d’avoir [git](https://git-scm.com/download) installé et disponible sur votre PATH. Vous pouvez vérifier qu’il est `git --version` installé correctement en entrant à une invite de commande et en appuyant **sur Enter**.

2. Installez le [code SDK core et](https://dotnet.microsoft.com/download) Visual Studio [.NET](https://code.visualstudio.com).

3. Sélectionnez l’icône Extensions et recherchez "Ionide":

   Le seul plugin requis pour le support F dans Visual Studio Code est [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). Cependant, vous pouvez également installer [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) pour obtenir le support [FAKE](https://fake.build/) et [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) pour obtenir le soutien [de Paket.](https://fsprojects.github.io/Paket/) FAKE et Paket sont des outils communautaires supplémentaires pour la construction de projets et la gestion des dépendances, respectivement.

## <a name="install-f-with-visual-studio-for-mac"></a>Installer F AVEC Visual Studio pour Mac

F est installé par défaut dans [Visual Studio pour Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), quelle que soit la configuration que vous choisissez.

Une fois l’installation terminée, choisissez **Start Visual Studio**. Vous pouvez également ouvrir Visual Studio via Finder sur macOS.

## <a name="install-f-on-a-build-server"></a>Installer F sur un serveur de construction

Si vous utilisez .NET Core ou .NET Framework via le .NET SDK, vous avez simplement besoin d’installer le .NET SDK sur votre serveur de construction. Il a tout ce dont vous avez besoin.

Si vous utilisez .NET Framework et que vous **n’utilisez pas** le .NET SDK, vous devrez installer les outils de construction de studio [visuel SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) sur votre serveur Windows. Dans l’installateur, sélectionnez des **outils de construction de bureau .NET,** puis sélectionnez le composant **compilateur F sur** le côté droit du menu de l’installateur.
