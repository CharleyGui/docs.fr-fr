---
title: Configurer Visual Studio Code pour le développement Azure avec .NET
description: Cet article vous aide à configurer Visual Studio Code pour le développement Azure, y compris l’installation et la configuration de plug-ins appropriés dans VS Code
ms.date: 11/30/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: 65ced99befe12d137062b4ea6a59a1ccd3099e0b
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97701157"
---
# <a name="configure-visual-studio-code-for-azure-development"></a>Configurer Visual Studio Code pour le développement Azure

Si vous utilisez Visual Studio Code, que ce soit pour le développement .NET, pour la création d’applications à page unique à l’aide d’infrastructures comme l’angulaire, la réaction ou la vue, ou pour l’écriture d’applications dans un autre langage comme Python, vous souhaiterez configurer Visual Studio Code pour le développement Azure.

### <a name="download-visual-studio-code"></a>Télécharger Visual Studio Code

Si Visual Studio Code est déjà installé, vous pouvez ignorer cette étape

> [!div class="nextstepaction"]
> [Télécharger Visual Studio Code](https://code.visualstudio.com/download)

### <a name="install-the-azure-tools-extension-pack"></a>Installer le pack d’extension Azure Tools

Le [Pack d’extension Azure Tools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack) contient des extensions pour l’utilisation de Azure App Service, Azure functions, stockage azure, Cosmos DB et des machines virtuelles Azure, le tout dans un seul et même package pratique.

Pour installer l’extension à partir de Visual Studio Code :

1. Appuyez sur <kbd>Ctrl + Maj + X</kbd> pour ouvrir la fenêtre **Extensions** .
1. Recherchez l’extension *Azure Tools* .
1. Sélectionnez le bouton **Installer**.

![Capture d’écran de l’Visual Studio Code montrant le panneau extensions recherche du pack d’extension Azure Tools](./media/visual-studio-code-azure-tools.png)

Pour en savoir plus sur l’installation des extensions dans Visual Studio Code, reportez-vous au document [Marketplace d’extension](https://code.visualstudio.com/docs/editor/extension-gallery) sur le site Web Visual Studio code.

### <a name="sign-in-to-your-azure-account-with-azure-tools"></a>Connectez-vous à votre compte Azure avec Azure Tools

Dans le volet gauche, une icône Azure s’affiche. Sélectionnez cette icône. un panneau de configuration pour les services Azure s’affiche. Choisissez **se connecter à Azure...** sous n’importe quel service pour terminer le processus d’authentification pour les outils azure dans Visual Studio code.

![Capture d’écran de la Visual Studio Code montrant comment ouvrir une session Azure Tools sur Azure](./media/visual-studio-code-azure-login.png)

### <a name="next-steps"></a>Étapes suivantes

Ensuite, vous devez installer le Azure CLI sur votre station de travail.

> [!div class="nextstepaction"]
> [Installer l’interface de ligne de commande Microsoft Azure](./install-azure-cli.md)
