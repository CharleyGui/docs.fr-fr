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
# <a name="configure-visual-studio-code-for-azure-development"></a><span data-ttu-id="b19a5-103">Configurer Visual Studio Code pour le développement Azure</span><span class="sxs-lookup"><span data-stu-id="b19a5-103">Configure Visual Studio Code for Azure development</span></span>

<span data-ttu-id="b19a5-104">Si vous utilisez Visual Studio Code, que ce soit pour le développement .NET, pour la création d’applications à page unique à l’aide d’infrastructures comme l’angulaire, la réaction ou la vue, ou pour l’écriture d’applications dans un autre langage comme Python, vous souhaiterez configurer Visual Studio Code pour le développement Azure.</span><span class="sxs-lookup"><span data-stu-id="b19a5-104">If you are using Visual Studio Code, whether for .NET development, for building single page applications using frameworks like Angular, React or Vue, or for writing applications in another language like Python, you will want to configure Visual Studio Code for Azure development.</span></span>

### <a name="download-visual-studio-code"></a><span data-ttu-id="b19a5-105">Télécharger Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b19a5-105">Download Visual Studio Code</span></span>

<span data-ttu-id="b19a5-106">Si Visual Studio Code est déjà installé, vous pouvez ignorer cette étape</span><span class="sxs-lookup"><span data-stu-id="b19a5-106">If you already have Visual Studio Code installed, you can skip this step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b19a5-107">Télécharger Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b19a5-107">Download Visual Studio Code</span></span>](https://code.visualstudio.com/download)

### <a name="install-the-azure-tools-extension-pack"></a><span data-ttu-id="b19a5-108">Installer le pack d’extension Azure Tools</span><span class="sxs-lookup"><span data-stu-id="b19a5-108">Install the Azure Tools Extension Pack</span></span>

<span data-ttu-id="b19a5-109">Le [Pack d’extension Azure Tools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack) contient des extensions pour l’utilisation de Azure App Service, Azure functions, stockage azure, Cosmos DB et des machines virtuelles Azure, le tout dans un seul et même package pratique.</span><span class="sxs-lookup"><span data-stu-id="b19a5-109">The [Azure Tools Extension Pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack) contains extensions for working with Azure App Service, Azure Functions, Azure Storage, Cosmos DB, and Azure Virtual Machines all in one convenient package.</span></span>

<span data-ttu-id="b19a5-110">Pour installer l’extension à partir de Visual Studio Code :</span><span class="sxs-lookup"><span data-stu-id="b19a5-110">To install the extension from Visual Studio Code:</span></span>

1. <span data-ttu-id="b19a5-111">Appuyez sur <kbd>Ctrl + Maj + X</kbd> pour ouvrir la fenêtre **Extensions** .</span><span class="sxs-lookup"><span data-stu-id="b19a5-111">Press <kbd>Ctrl+Shift+X</kbd> to open the **Extensions** window.</span></span>
1. <span data-ttu-id="b19a5-112">Recherchez l’extension *Azure Tools* .</span><span class="sxs-lookup"><span data-stu-id="b19a5-112">Search for the *Azure Tools* extension.</span></span>
1. <span data-ttu-id="b19a5-113">Sélectionnez le bouton **Installer**.</span><span class="sxs-lookup"><span data-stu-id="b19a5-113">Select the **Install** button.</span></span>

![Capture d’écran de l’Visual Studio Code montrant le panneau extensions recherche du pack d’extension Azure Tools](./media/visual-studio-code-azure-tools.png)

<span data-ttu-id="b19a5-115">Pour en savoir plus sur l’installation des extensions dans Visual Studio Code, reportez-vous au document [Marketplace d’extension](https://code.visualstudio.com/docs/editor/extension-gallery) sur le site Web Visual Studio code.</span><span class="sxs-lookup"><span data-stu-id="b19a5-115">To learn more about installing extensions in Visual Studio Code, refer to the [Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery) document on the Visual Studio Code website.</span></span>

### <a name="sign-in-to-your-azure-account-with-azure-tools"></a><span data-ttu-id="b19a5-116">Connectez-vous à votre compte Azure avec Azure Tools</span><span class="sxs-lookup"><span data-stu-id="b19a5-116">Sign in to your Azure account with Azure Tools</span></span>

<span data-ttu-id="b19a5-117">Dans le volet gauche, une icône Azure s’affiche.</span><span class="sxs-lookup"><span data-stu-id="b19a5-117">On the left hand panel, you'll see an Azure icon.</span></span> <span data-ttu-id="b19a5-118">Sélectionnez cette icône. un panneau de configuration pour les services Azure s’affiche.</span><span class="sxs-lookup"><span data-stu-id="b19a5-118">Select this icon, and a control panel for Azure services will appear.</span></span> <span data-ttu-id="b19a5-119">Choisissez **se connecter à Azure...** sous n’importe quel service pour terminer le processus d’authentification pour les outils azure dans Visual Studio code.</span><span class="sxs-lookup"><span data-stu-id="b19a5-119">Choose **Sign in to Azure...** under any service to complete the authentication process for the Azure tools in Visual Studio Code.</span></span>

![Capture d’écran de la Visual Studio Code montrant comment ouvrir une session Azure Tools sur Azure](./media/visual-studio-code-azure-login.png)

### <a name="next-steps"></a><span data-ttu-id="b19a5-121">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="b19a5-121">Next steps</span></span>

<span data-ttu-id="b19a5-122">Ensuite, vous devez installer le Azure CLI sur votre station de travail.</span><span class="sxs-lookup"><span data-stu-id="b19a5-122">Next, you will want to install the Azure CLI on your workstation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b19a5-123">Installer l’interface de ligne de commande Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="b19a5-123">Install the Azure CLI</span></span>](./install-azure-cli.md)
