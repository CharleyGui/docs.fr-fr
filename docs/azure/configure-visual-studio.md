---
title: Configurer Visual Studio pour le développement Azure avec .NET
description: Cet article vous aide à configurer Visual Studio pour le développement Azure, y compris l’obtention des charges de travail appropriées installées et la connexion de Visual Studio à votre compte Azure.
ms.date: 11/30/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: 986469bd07657d968045465803047dc21d76dd62
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97701162"
---
# <a name="configure-visual-studio-for-azure-development-with-net"></a><span data-ttu-id="30911-103">Configurer Visual Studio pour le développement Azure avec .NET</span><span class="sxs-lookup"><span data-stu-id="30911-103">Configure Visual Studio for Azure development with .NET</span></span>

<span data-ttu-id="30911-104">Visual Studio propose des outils pour faciliter le développement et le déploiement d’applications sur Azure.</span><span class="sxs-lookup"><span data-stu-id="30911-104">Visual Studio includes tooling to help with the development and deployment of applications on Azure.</span></span>  <span data-ttu-id="30911-105">Ce guide vous permet de vous assurer que Visual Studio est correctement configuré pour le développement Azure.</span><span class="sxs-lookup"><span data-stu-id="30911-105">This guide will help you make sure that you have Visual Studio properly configured for Azure development.</span></span>

### <a name="download-visual-studio-2019"></a><span data-ttu-id="30911-106">Télécharger Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="30911-106">Download Visual Studio 2019</span></span>

<span data-ttu-id="30911-107">Si vous avez déjà installé Visual Studio 2019, vous pouvez ignorer cette étape.</span><span class="sxs-lookup"><span data-stu-id="30911-107">If you already have Visual Studio 2019 installed, you can skip this step.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="30911-108">Télécharger Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="30911-108">Download Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads/)

### <a name="install-azure-workloads"></a><span data-ttu-id="30911-109">Installer des charges de travail Azure</span><span class="sxs-lookup"><span data-stu-id="30911-109">Install Azure workloads</span></span>

<span data-ttu-id="30911-110">Lancez le **Visual Studio installer** et vérifiez que les charges de travail **Azure Development** et **ASP.net et le développement Web** sont installés.</span><span class="sxs-lookup"><span data-stu-id="30911-110">Launch the **Visual Studio Installer** and validate that you have the workloads **Azure development** and **ASP.NET and web development** are installed.</span></span>  <span data-ttu-id="30911-111">Si l’une de ces charges de travail n’est pas installée, sélectionnez ces charges de travail pour les installer.</span><span class="sxs-lookup"><span data-stu-id="30911-111">If either of these workloads is not installed, select these workloads to install them.</span></span>

![Capture d’écran de la Visual Studio Installer montrant les charges de travail de développement Azure et de développement Web sélectionnées](./media/visual-studio-installer-azure-development.png)

### <a name="authenticate-visual-studio-with-azure"></a><span data-ttu-id="30911-113">Authentifier Visual Studio avec Azure</span><span class="sxs-lookup"><span data-stu-id="30911-113">Authenticate Visual Studio with Azure</span></span>

<span data-ttu-id="30911-114">Lors du débogage d’applications à l’aide de Visual Studio, Visual Studio peut utiliser votre compte Azure pour authentifier et accéder aux ressources Azure avec.</span><span class="sxs-lookup"><span data-stu-id="30911-114">When debugging apps through Visual Studio, Visual Studio can use your Azure account to authenticate and access Azure Resources with.</span></span>  <span data-ttu-id="30911-115">Ce compte est également utilisé lorsque vous publiez des applications directement depuis Visual Studio vers Azure.</span><span class="sxs-lookup"><span data-stu-id="30911-115">This account is also used when you publish apps directly from Visual Studio to Azure.</span></span>

<span data-ttu-id="30911-116">Pour authentifier votre compte Azure à partir de Visual Studio, sélectionnez le menu **Outils**  >  **options** pour ouvrir la boîte de dialogue **options** .</span><span class="sxs-lookup"><span data-stu-id="30911-116">To authenticate your Azure account from Visual Studio, select the **Tools** > **Options** menu to launch the **Options** dialog.</span></span> <span data-ttu-id="30911-117">Accédez aux `Azure Service Authentication` options et connectez-vous à l’aide de votre compte Azure.</span><span class="sxs-lookup"><span data-stu-id="30911-117">Navigate to the `Azure Service Authentication` options and sign in using your Azure account.</span></span>

![Capture d’écran de la boîte de dialogue Options de Visual Studio montrant la connexion Azure](./media/visual-studio-azure-login-dialog.png)

### <a name="next-steps"></a><span data-ttu-id="30911-119">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="30911-119">Next steps</span></span>

<span data-ttu-id="30911-120">Si vous utilisez également [Visual Studio code](https://code.visualstudio.com/) pour le développement dans .net ou dans d’autres langages, vous devez également [configurer Visual Studio code pour le développement Azure](./configure-vs-code.md).</span><span class="sxs-lookup"><span data-stu-id="30911-120">If you also use [Visual Studio Code](https://code.visualstudio.com/) for development in .NET or any other language, you should also [configure Visual Studio Code for Azure development](./configure-vs-code.md).</span></span> <span data-ttu-id="30911-121">Dans le cas contraire, passez à l' [installation du Azure CLI](./install-azure-cli.md).</span><span class="sxs-lookup"><span data-stu-id="30911-121">Otherwise, proceed to [Installing the Azure CLI](./install-azure-cli.md).</span></span>
