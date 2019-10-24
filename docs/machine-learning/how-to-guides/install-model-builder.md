---
title: Guide pratique pour installer Model Builder
description: Découvrir comment installer l’outil Model Builder ML.NET
author: luisquintanilla
ms.author: luquinta
ms.date: 06/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: a1034d294012b8df5ec778fc40602fe52223961d
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774569"
---
# <a name="how-to-install-mlnet-model-builder"></a>Guide pratique pour installer Model Builder ML.NET

Découvrez comment installer Model Builder ML.NET pour ajouter le machine learning à vos applications .NET.

> [!NOTE]
> Model Builder est actuellement en préversion.

## <a name="pre-requisites"></a>Conditions préalables

- Visual Studio 2017 version 15.9.12 ou ultérieure/Visual Studio 2019
- SDK .NET Core 2.1 ou ultérieur

## <a name="limitations"></a>Limitations

- L’extension Model Builder ML.NET fonctionne actuellement seulement avec Visual Studio sur Windows.
- La limite du jeu de données d’entraînement est de 1 Go
- SQL Server a une limite de 100 000 lignes pour l’entraînement
- Microsoft SQL Server Data Tools pour Visual Studio 2017 n’est pas pris en charge

## <a name="install"></a>Installez

Model Builder ML.NET peut être installé via Visual Studio Marketplace ou depuis Visual Studio.

### <a name="visual-studio-marketplace"></a>Visual Studio Marketplace

1. Télécharger depuis [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)
1. Suivre les invites pour installer sur les différentes versions de Visual Studio

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. Dans la barre de menus, sélectionnez **Outils** > **Extensions et mises à jour**.

    ![Boîte de dialogue VS2017 ouvrir le gestionnaire d’extensions](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. Dans l’invite *Extension et mises à jour*, sélectionnez le nœud *En ligne*.
1. Dans la barre de recherche, recherchez *Model Builder ML.NET* puis, dans les résultats, sélectionnez « Model Builder ML.NET (Préversion) »

    ![VS2017 Rechercher et installer l’extension du générateur de modèles dans la boîte de dialogue Gestionnaire d’extensions](./media/install-model-builder/vs2017-install-model-builder.png)

1. Suivez les invites pour effectuer l’installation

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. Dans la barre de menus, sélectionnez **Extensions** > **Gérer les extensions**.

    ![Boîte de dialogue VS2019 ouvrir le gestionnaire d’extensions](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. Dans l’invite *Extension et mises à jour*, sélectionnez le nœud *En ligne*.
1. Tapez *Model Builder ML.NET* dans la barre de recherche, puis sélectionnez « Model Builder ML.NET (Préversion) »

    ![VS2019 Rechercher et installer l’extension du générateur de modèles dans la boîte de dialogue Gestionnaire d’extensions](./media/install-model-builder/vs2019-install-model-builder.png)

1. Suivez les invites pour effectuer l’installation

## <a name="uninstall"></a>Désinstaller

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. Dans la barre de menus, sélectionnez **Outils** > **Extensions et mises à jour**.

    ![VS2017 ouvre la boîte de dialogue gérer les extensions](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. Dans l’invite *Extension et mises à jour*, développez le nœud *Installé* et sélectionnez *Outils*
1. Sélectionnez Model Builder ML.NET (Préversion) dans la liste des outils, puis sélectionnez *Désinstaller*.

    ![VS2017 Rechercher et désinstaller l’extension du générateur de modèles dans la boîte de dialogue Gestionnaire d’extensions](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. Suivez les invites pour effectuer la désinstallation.

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. Dans la barre de menus, sélectionnez **Extensions** > **Gérer les extensions**.

    ![VS2019 ouvre la boîte de dialogue gérer les extensions](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. Dans l’invite *Extension et mises à jour*, développez le nœud *Installé* et sélectionnez *Outils*
1. Sélectionnez Model Builder ML.NET (Préversion) dans la liste des outils, puis sélectionnez *Désinstaller*.

    ![VS2019 Rechercher et désinstaller l’extension du générateur de modèles dans la boîte de dialogue Gestionnaire d’extensions](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. Suivez les invites pour effectuer la désinstallation.

## <a name="upgrade"></a>Mettre à niveau

Le processus de mise à niveau est similaire au processus d’installation. Téléchargez la dernière version à partir de Visual Studio Marketplace ou utilisez le Gestionnaire d’extensions dans Visual Studio.
