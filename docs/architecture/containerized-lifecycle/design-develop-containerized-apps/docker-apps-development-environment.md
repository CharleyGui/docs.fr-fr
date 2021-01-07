---
title: Environnement de développement pour les applications Docker
description: Découvrez les options les plus importantes des outils de développement qui prennent en charge le cycle de développement Docker.
ms.date: 01/06/2021
ms.openlocfilehash: c6c4a1fda41131c00ba87808ed408f1d3250cabf
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970523"
---
# <a name="development-environment-for-docker-apps"></a>Environnement de développement pour les applications Docker

## <a name="development-tools-choices-ide-or-editor"></a>Choix des outils de développement : IDE ou éditeur

Que vous préfériez un IDE complet et puissant ou un éditeur léger et agile, Microsoft met à votre disposition tout ce dont vous avez besoin pour développer des applications Docker.

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>Visual Studio Code et Docker CLI (outils multiplateformes pour Mac, Linux et Windows)

Si vous préférez un éditeur léger et multiplateforme prenant en charge n’importe quel langage de développement, vous pouvez utiliser Visual Studio Code et l’interface de ligne de commande Docker CLI. Ces produits offrent une expérience simple mais robuste, ce qui est indispensable pour simplifier le workflow du développeur. En installant « Docker pour Mac » ou « Docker pour Windows » (environnement de développement), les développeurs Docker peuvent utiliser une interface de ligne de commande Docker unique pour créer des applications pour Windows ou Linux (environnement d’exécution). De plus, Visual Studio Code prend en charge les extensions pour Docker avec IntelliSense pour les fichiers Dockerfile et les tâches de raccourci afin d’exécuter des commandes Docker à partir de l’éditeur.

> [!NOTE]
> Pour télécharger Visual Studio Code, accédez à <https://code.visualstudio.com/download>.
>
> Pour télécharger Docker pour Mac et Windows, accédez à <https://www.docker.com/products/docker>.

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a>Visual Studio avec les outils Docker (machine de développement Windows)

Il est recommandé d’utiliser Visual Studio 2019 avec les outils d’ancrage intégrés activés. Avec Visual Studio, vous pouvez développer, exécuter et valider vos applications directement dans l’environnement Docker de votre choix. Appuyez sur F5 pour déboguer votre application (à un ou plusieurs conteneurs) directement dans un hôte Docker ou appuyez sur Ctrl+F5 pour modifier et actualiser votre application sans avoir à regénérer le conteneur. Il s’agit du choix le plus simple et le plus robuste pour les développeurs Windows qui souhaitent créer des conteneurs Docker pour Linux ou Windows.

### <a name="visual-studio-for-mac-mac-development-machine"></a>Visual Studio pour Mac (machine de développement Mac)

Vous pouvez utiliser [Visual Studio pour Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) pour développer des applications basées sur Docker. Visual Studio pour Mac offre un environnement de développement intégré (IDE) plus riche par rapport à Visual Studio Code pour Mac.

## <a name="language-and-framework-choices"></a>Choix en matière de langage et de framework

Vous pouvez développer des applications Docker en utilisant les outils Microsoft avec les langages les plus modernes. En voici une liste non exhaustive :

- .NET et ASP.NET Core
- Node.js
- Go
- Java
- Ruby
- Python

En fait, vous pouvez utiliser n’importe quel langage moderne pris en charge par Docker dans Linux ou Windows.

>[!div class="step-by-step"]
>[Précédent](deploy-azure-kubernetes-service.md) 
> [Suivant](docker-apps-inner-loop-workflow.md)
