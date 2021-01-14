---
title: Processus de développement pour les applications basées sur un ancrage
description: Obtenir une vue d’ensemble globale des options de développement d’applications basées sur un ancrage. À l’aide de votre choix de Visual Studio pour Windows, Visual Studio pour Mac ou Visual Studio Code pour la prise en charge multiplateforme (Windows, macOS et Linux).
ms.date: 01/13/2021
ms.openlocfilehash: 3a4f4078e745c52e8eca46473668e3319917bfd2
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188294"
---
# <a name="development-process-for-docker-based-applications"></a>Processus de développement pour les applications basées sur un ancrage

*Développez des applications .NET en conteneur comme vous le souhaitez, dans un environnement de développement intégré (IDE), axé sur Visual Studio et Visual Studio Tools for Dockr ou sur l’interface de commande CLI/Editor qui se concentrent sur l’interface CLI et les Visual Studio Code.*

## <a name="development-environment-for-docker-apps"></a>Environnement de développement pour les applications Docker

### <a name="development-tool-choices-ide-or-editor"></a>Choix des outils de développement : IDE ou éditeur

Que vous préfériez un IDE complet et puissant ou un éditeur léger et agile, Microsoft propose des outils que vous pouvez utiliser pour développer des applications Docker.

**Visual Studio (pour Windows).** Le développement d’applications .NET 5 basées sur un ancrage avec Visual Studio nécessite Visual Studio 2019 version 16,4 ou ultérieure. Visual Studio 2019 est fourni avec des outils pour l’arrimeur déjà intégré. Les outils pour Docker vous permettent de développer, exécuter et valider vos applications directement dans l’environnement Docker cible. Vous pouvez appuyer sur F5 pour exécuter et déboguer votre application (conteneur unique ou plusieurs conteneurs) directement dans un hôte Docker, ou appuyer sur Ctrl+F5 pour modifier et actualiser votre application sans avoir à régénérer le conteneur. Cet IDE est le choix de développement le plus puissant pour les applications basées sur l’ancrage.

**Visual Studio pour Mac.** Il s’agit d’un IDE, de l’évolution de Xamarin Studio, exécuté dans macOS. Pour le développement .NET 5, il requiert la version 8,4 ou une version ultérieure. Cet outil doit être le choix préféré pour les développeurs qui travaillent sur des ordinateurs macOS qui souhaitent également utiliser un IDE puissant.

**Visual Studio Code et interface CLI Docker**. Si vous préférez un éditeur léger et multiplateforme qui prend en charge n’importe quel langage de développement, vous pouvez utiliser Visual Studio Code et l’interface de commande de l’ancrage. Cet IDE est une approche de développement multiplateforme pour macOS, Linux et Windows. De plus, Visual Studio Code prend en charge les extensions pour Docker comme IntelliSense pour les Dockerfiles et les tâches de raccourci afin d’exécuter des commandes Docker à partir de l’éditeur.

En installant [Docker Desktop Community Edition (CE)](https://hub.docker.com/search/?type=edition&offering=community), vous pouvez utiliser une seule interface CLI Docker pour générer des applications pour Windows et Linux.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Visual Studio**. Site officiel. \
  [https://visualstudio.microsoft.com/vs/](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

- **Visual Studio Code**. Site officiel. \
  <https://code.visualstudio.com/download>

- **Bureau de station d’accueil pour Windows Community Edition (CE)** \
  [https://hub.docker.com/editions/community/docker-ce-desktop-windows](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

- **Station d’accueil Desktop pour Mac édition Community (CE)** \
  [https://hub.docker.com/editions/community/docker-ce-desktop-mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>Langages et frameworks .NET pour conteneurs Docker

Comme mentionné dans les sections précédentes de ce guide, vous pouvez utiliser .NET Framework, .NET 5 ou le projet mono Open source lorsque vous développez des applications .NET en conteneur d’ancrage. Vous pouvez développer en C\#, F\# ou Visual Basic quand vous ciblez des conteneurs Linux ou Windows, selon le .NET Framework en cours d’utilisation. Pour plus d’informations sur les langages .NET, consultez le billet de blog [Stratégie de langage .NET](https://devblogs.microsoft.com/dotnet/the-net-language-strategy/).

>[!div class="step-by-step"]
>[Précédent](../architect-microservice-container-applications/scalable-available-multi-container-microservice-applications.md) 
> [Suivant](docker-app-development-workflow.md)
