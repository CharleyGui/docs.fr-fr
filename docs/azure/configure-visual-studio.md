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
# <a name="configure-visual-studio-for-azure-development-with-net"></a>Configurer Visual Studio pour le développement Azure avec .NET

Visual Studio propose des outils pour faciliter le développement et le déploiement d’applications sur Azure.  Ce guide vous permet de vous assurer que Visual Studio est correctement configuré pour le développement Azure.

### <a name="download-visual-studio-2019"></a>Télécharger Visual Studio 2019

Si vous avez déjà installé Visual Studio 2019, vous pouvez ignorer cette étape.

> [!div class="nextstepaction"]
> [Télécharger Visual Studio 2019](https://www.visualstudio.com/downloads/)

### <a name="install-azure-workloads"></a>Installer des charges de travail Azure

Lancez le **Visual Studio installer** et vérifiez que les charges de travail **Azure Development** et **ASP.net et le développement Web** sont installés.  Si l’une de ces charges de travail n’est pas installée, sélectionnez ces charges de travail pour les installer.

![Capture d’écran de la Visual Studio Installer montrant les charges de travail de développement Azure et de développement Web sélectionnées](./media/visual-studio-installer-azure-development.png)

### <a name="authenticate-visual-studio-with-azure"></a>Authentifier Visual Studio avec Azure

Lors du débogage d’applications à l’aide de Visual Studio, Visual Studio peut utiliser votre compte Azure pour authentifier et accéder aux ressources Azure avec.  Ce compte est également utilisé lorsque vous publiez des applications directement depuis Visual Studio vers Azure.

Pour authentifier votre compte Azure à partir de Visual Studio, sélectionnez le menu **Outils**  >  **options** pour ouvrir la boîte de dialogue **options** . Accédez aux `Azure Service Authentication` options et connectez-vous à l’aide de votre compte Azure.

![Capture d’écran de la boîte de dialogue Options de Visual Studio montrant la connexion Azure](./media/visual-studio-azure-login-dialog.png)

### <a name="next-steps"></a>Étapes suivantes

Si vous utilisez également [Visual Studio code](https://code.visualstudio.com/) pour le développement dans .net ou dans d’autres langages, vous devez également [configurer Visual Studio code pour le développement Azure](./configure-vs-code.md). Dans le cas contraire, passez à l' [installation du Azure CLI](./install-azure-cli.md).
