---
title: Guide pratique pour installer Model Builder
description: Découvrir comment installer l’outil Model Builder ML.NET
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.custom: mvc, how-to, mlnet-tooling
ms.openlocfilehash: b944d7f6044553251132824e7e4213119e34500e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848650"
---
# <a name="how-to-install-mlnet-model-builder"></a>Guide pratique pour installer Model Builder ML.NET

Découvrez comment installer Model Builder ML.NET pour ajouter le machine learning à vos applications .NET.

> [!NOTE]
> Model Builder est actuellement en préversion.

## <a name="prerequisites"></a>Conditions préalables requises

- Visual Studio 2017 version 15.9.12 ou plus tard / Visual Studio 2019
- .NET Core 2.1 SDK ou plus tard.

> [!NOTE]
> .NET Core 3.0 SDK n’est pas actuellement pris en charge.

## <a name="limitations"></a>Limites

- L’extension Model Builder ML.NET fonctionne actuellement seulement avec Visual Studio sur Windows.
- La limite du jeu de données d’entraînement est de 1 Go
- SQL Server a une limite de 100 000 lignes pour l’entraînement
- Microsoft SQL Server Data Tools pour Visual Studio 2017 n’est pas pris en charge

## <a name="install"></a>Installer

Model Builder ML.NET peut être installé via Visual Studio Marketplace ou depuis Visual Studio.

### <a name="visual-studio-marketplace"></a>Place de marché Visual Studio

1. Télécharger depuis [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)
1. Suivre les invites pour installer sur les différentes versions de Visual Studio

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. Dans la barre de menu, sélectionnez Des > **extensions et mises à jour** **d’outils**

    ![VS2017 extensions ouvertes dialogue gestionnaire](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. Dans l’invite *Extension et mises à jour*, sélectionnez le nœud *En ligne*.
1. Dans la barre de recherche, recherchez *Model Builder ML.NET* puis, dans les résultats, sélectionnez « Model Builder ML.NET (Préversion) »

    ![VS2017 recherche et installer l’extension Model Builder dans le dialogue gestionnaire d’extensions](./media/install-model-builder/vs2017-install-model-builder.png)

1. Suivez les invites pour effectuer l’installation

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. Sur la barre de menu, sélectionnez **Extensions** > **Manage Extensions**

    ![VS2019 extensions ouvertes dialogue gestionnaire](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. Dans l’invite *Extension et mises à jour*, sélectionnez le nœud *En ligne*.
1. Tapez *Model Builder ML.NET* dans la barre de recherche, puis sélectionnez « Model Builder ML.NET (Préversion) »

    ![VS2019 recherche et installer l’extension Model Builder dans le dialogue gestionnaire d’extensions](./media/install-model-builder/vs2019-install-model-builder.png)

1. Suivez les invites pour effectuer l’installation

## <a name="uninstall"></a>Désinstaller l’interface

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. Sur la barre de menu, sélectionnez des**extensions et mises à jour** **d’outils** > 

    ![VS2017 open manage extensions dialogue](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. Dans l’invite *Extension et mises à jour*, développez le nœud *Installé* et sélectionnez *Outils*
1. Sélectionnez Model Builder ML.NET (Préversion) dans la liste des outils, puis sélectionnez *Désinstaller*.

    ![VS2017 recherche et désinstaller l’extension Model Builder dans le dialogue gestionnaire d’extensions](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. Suivez les invites pour effectuer la désinstallation.

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. Sur la barre de menu, sélectionnez **Extensions** > **Manage Extensions**

    ![VS2019 open manage extensions dialogue](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. Dans l’invite *Extension et mises à jour*, développez le nœud *Installé* et sélectionnez *Outils*
1. Sélectionnez Model Builder ML.NET (Préversion) dans la liste des outils, puis sélectionnez *Désinstaller*.

    ![VS2019 recherche et désinstaller l’extension Model Builder dans le dialogue gestionnaire d’extensions](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. Suivez les invites pour effectuer la désinstallation.

## <a name="upgrade"></a>Mettre à niveau

Le processus de mise à niveau est similaire au processus d’installation. Téléchargez la dernière version à partir de Visual Studio Marketplace ou utilisez le Gestionnaire d’extensions dans Visual Studio.
