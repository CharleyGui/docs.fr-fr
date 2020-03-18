---
title: Processus de développement pour les applications basées sur Docker
description: Obtenez un aperçu de haut niveau des options de développement d’applications basées sur Docker. En utilisant votre choix de Visual Studio pour Windows, Visual Studio pour Mac, ou Visual Studio Code pour le support multiplateforme (Windows, macOS, et Linux).
ms.date: 01/30/2020
ms.openlocfilehash: 799aa6fc742a8fb763ec5a7ae3cf3f70f89bed6d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77502715"
---
# <a name="development-process-for-docker-based-applications"></a>Processus de développement pour les applications basées sur Docker

*Développez des applications .NET conteneurisées comme vous le souhaitez, soit Integrated Development Environment (IDE) axées sur visual Studio et Visual Studio outils pour Docker ou CLI/Editor axés sur Docker CLI et Visual Studio Code.*

## <a name="development-environment-for-docker-apps"></a>Environnement de développement pour les applications Docker

### <a name="development-tool-choices-ide-or-editor"></a>Choix des outils de développement : IDE ou éditeur

Que vous préfériez un IDE complet et puissant ou un éditeur léger et agile, Microsoft propose des outils que vous pouvez utiliser pour développer des applications Docker.

**Visual Studio (pour Windows).** Le développement d’applications .NET Core 3.1 basé sur Docker avec Visual Studio nécessite visual Studio 2019 version 16.4 ou plus tard. Visual Studio 2019 est livré avec des outils pour Docker déjà intégré. Les outils pour Docker vous permettent de développer, exécuter et valider vos applications directement dans l’environnement Docker cible. Vous pouvez appuyer sur F5 pour exécuter et déboguer votre application (conteneur unique ou plusieurs conteneurs) directement dans un hôte Docker, ou appuyer sur Ctrl+F5 pour modifier et actualiser votre application sans avoir à régénérer le conteneur. Ceci est le meilleur choix pour le développement d’applications basées sur Docker.

**Visual Studio pour Mac.** C’est un IDE, l’évolution de Xamarin Studio, en cours d’exécution en macOS. Pour le développement .NET Core 3.1, il nécessite la version 8.4 ou plus tard. Cela devrait être le choix préféré pour les développeurs travaillant dans les machines macOS qui veulent également utiliser un IDE puissant.

**Visual Studio Code et interface CLI Docker**. Si vous préférez un éditeur léger et multiplateforme qui prend en charge n’importe quel langage de développement, vous pouvez utiliser Visual Studio Code et le Docker CLI. Il s’agit d’une approche de développement multiplateforme pour macOS, Linux et Windows. De plus, Visual Studio Code prend en charge les extensions pour Docker comme IntelliSense pour les Dockerfiles et les tâches de raccourci afin d’exécuter des commandes Docker à partir de l’éditeur.

En installant [Docker Desktop Community Edition (CE)](https://hub.docker.com/search/?type=edition&offering=community), vous pouvez utiliser une seule interface CLI Docker pour générer des applications pour Windows et Linux.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Studio visuel**. Site officiel. \
  [https://visualstudio.microsoft.com/vs/](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

- **Code Studio Visuel**. Site officiel. \
  <https://code.visualstudio.com/download>

- **Bureau Docker pour Windows Community Edition (CE)** \
  [https://hub.docker.com/editions/community/docker-ce-desktop-windows](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

- **Bureau Docker pour Mac Community Edition (CE)** \
  [https://hub.docker.com/editions/community/docker-ce-desktop-mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>Langages et frameworks .NET pour conteneurs Docker

Comme indiqué dans les sections précédentes de ce guide, vous pouvez utiliser .NET Framework, .NET Core ou le projet Mono open source pour développer des applications .NET Docker en conteneur. Vous pouvez développer en C\#, F\# ou Visual Basic quand vous ciblez des conteneurs Linux ou Windows, selon le .NET Framework en cours d’utilisation. Pour plus d’informations sur les langages .NET, consultez le billet de blog [Stratégie de langage .NET](https://devblogs.microsoft.com/dotnet/the-net-language-strategy/).

>[!div class="step-by-step"]
>[Suivant précédent](../architect-microservice-container-applications/scalable-available-multi-container-microservice-applications.md)
>[Next](docker-app-development-workflow.md)
