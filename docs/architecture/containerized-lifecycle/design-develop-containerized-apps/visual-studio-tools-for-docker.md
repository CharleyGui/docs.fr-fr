---
title: Visual Studio Tools pour Docker sur Windows
description: Familiarisez-vous avec les outils Docker disponibles dans Visual Studio 2017 versions 15.7 et ultérieures.
ms.date: 02/15/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 2b6fdc33f9cf850cf9e52fca4a1a9754cd412567
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "68673876"
---
# <a name="use-docker-tools-in-visual-studio-2017-on-windows"></a>Utilisez les outils Docker dans Visual Studio 2017 sur Windows

Le workflow du développeur quand vous utilisez les outils Docker inclus dans Visual Studio 2017 versions 15.7 et ultérieures est similaire à l’utilisation de Visual Studio Code et de l’interface CLI Docker (en fait, il se base sur la même interface CLI Docker), mais il est plus facile à démarrer, il simplifie le processus et il permet une plus grande productivité pour les tâches de création, exécution et composition. Il permet également d’exécuter et de déboguer vos conteneurs par le biais des touches `F5` et `Ctrl+F5` habituelles depuis Visual Studio. Vous pouvez même déboguer une solution entière si ses conteneurs sont définis dans le même fichier `docker-compose.yml` au niveau de la solution.

## <a name="configure-your-local-environment"></a>Configurer votre environnement local

Avec les dernières versions de Docker pour Windows, il est plus facile que jamais de développer des applications Docker, car le programme d’installation est simple, comme décrit dans les références suivantes.

> [!TIP]
> Pour en savoir plus sur l’installation de Docker pour Windows, accédez à (<https://docs.docker.com/docker-for-windows/>).

## <a name="docker-support-in-visual-studio-2017"></a>Prise en charge de Docker dans Visual Studio 2017

Il existe deux niveaux de prise en charge de Docker que vous pouvez ajouter à un projet. Dans les projets ASP.NET Core, vous pouvez simplement ajouter un fichier `Dockerfile` au projet en activant la prise en charge de Docker. Le niveau suivant est la prise en charge de l’orchestration des conteneurs, qui ajoute un `Dockerfile` au projet (s’il n’existe pas déjà) et un fichier `docker-compose.yml` au niveau de la solution. La prise en charge de l’orchestration des conteneurs, par le biais de Docker Compose, est ajoutée par défaut dans Visual Studio 2017 versions 15.0 à 15.7. La prise en charge de l’orchestration des conteneurs est une fonctionnalité à accepter dans Visual Studio 2017 versions 15.8 ou ultérieures. Les versions 15.8 et ultérieures prennent en charge Docker Compose et Service Fabric.

Les commandes **Ajouter > Prise en charge de Docker** et **Ajouter > Prise en charge des orchestrateurs de conteneurs** se trouvent dans le menu contextuel du nœud du projet pour un projet ASP.NET Core dans l’**Explorateur de solutions**, comme l’illustre la figure 4-31 :

![Option de menu Ajouter la prise en charge de Docker dans Visual Studio](./media/add-docker-support-menu.png)

**Figure 4-31**. Ajout de la prise en charge de Docker à un projet Visual Studio 2017

### <a name="add-docker-support"></a>Ajouter la prise en charge Docker

Vous pouvez ajouter le support Docker à un projet de base ASP.NET existant en sélectionnant **Add** > **Docker Support** dans Solution **Explorer**. Vous pouvez également activer la prise en charge de Docker lors de la création du projet en sélectionnant **Activer la prise en charge de Docker** dans la boîte de dialogue **nouvelle Application de Web ASP.NET Core** qui s’ouvre après avoir cliqué sur **OK** dans la boîte de dialogue **Nouveau projet**, comme l’illustre la figure 4-32.

![Activer la prise en charge de Docker pour une nouvelle application web ASP.NET Core dans Visual Studio](./media/enable-docker-support-visual-studio.png)

**Figure 4-32**. Activer la prise en charge de Docker lors de la création du projet dans Visual Studio 2017

Lorsque vous ajoutez ou activez la prise en charge de Docker, Visual Studio ajoute un fichier *Dockerfile* au projet.

> [!NOTE]
> Lorsque vous activez la prise en charge de Docker Compose lors de la création d’un projet ASP.NET (.NET Framework, et non pas .NET Core) comme l’illustre la figure 4-33, la prise en charge de l’orchestration de conteneurs est également ajoutée.

![Activer la prise en charge de Docker Compose pour un projet ASP.NET](media/enable-docker-compose-support.png)

**Figure 4-33**. Activation de la prise en charge de Docker Compose pour un projet ASP.NET dans Visual Studio 2017

### <a name="add-container-orchestration-support"></a>Ajouter la prise en charge de l’orchestration de conteneurs

Pour composer une solution à plusieurs conteneurs, ajoutez la prise en charge de l’orchestration de conteneurs à vos projets. Cela vous permet d’exécuter et de déboguer simultanément un groupe de conteneurs (une solution complète), si ces conteneurs sont définis dans le même fichier *docker-compose.yml*.

Pour ajouter la prise en charge de l’orchestration de conteneurs, cliquez sur le nœud de la solution ou du projet dans l’**Explorateur de solutions**, puis choisissez **Ajouter > Prise en charge des orchestrateurs de conteneurs**. Choisissez ensuite **Docker Compose** ou **Service Fabric** pour gérer les conteneurs.

Après avoir ajouté la prise en charge de l’orchestration de conteneurs à votre projet, vous voyez un fichier Dockerfile ajouté au projet et un dossier **docker-compose** ajouté à la solution dans l’**Explorateur de solutions**, comme l’illustre la figure 4-34 :

![Fichiers Docker dans l’Explorateur de solutions de Visual Studio](media/docker-support-solution-explorer.png)

**Figure 4-34**. Fichiers Docker dans l’Explorateur de solutions de Visual Studio 2017

Si le fichier *docker-compose.yml* existe déjà, Visual Studio ajoute simplement les lignes de code de configuration requises.

## <a name="configure-docker-tools"></a>Configurer les outils Docker

Dans le menu principal, choisissez **Outils > Options**, puis développez **Outils de conteneur > Paramètres**. Les paramètres des outils de conteneur s’affichent.

![Visual Studio Docker outils options, montrant: Tirer automatiquement les images Docker nécessaires sur la charge du projet, démarrer automatiquement les conteneurs en arrière-plan, tuer automatiquement les conteneurs sur la solution à proximité, et ne pas inciter à faire confiance certificat SSL.](./media/visual-studio-docker-tools-options.png)

**Figure 4-35**. Options des outils Docker

Le tableau suivant peut vous aider à déterminer comment définir ces options.

| Nom | Paramètre par défaut | S'applique à | Description |
| -----|:---------------:|:----------:| ----------- |
| Extraire automatiquement des images Docker nécessaires lors du chargement du projet | Il en va | Docker Compose | Pour améliorer les performances lors du chargement des projets, Visual Studio démarre une opération d’extraction Docker en arrière-plan de sorte que lorsque vous êtes prêt à exécuter votre code, l’image est déjà téléchargée ou en cours de téléchargement. Si vous chargez simplement des projets et parcourez du code, vous pouvez désactiver cette option pour éviter le téléchargement des images conteneur dont vous n’avez pas besoin. |
| Démarrer automatiquement les conteneurs en arrière-plan | Il en va | Docker Compose | De nouveau pour améliorer les performances, Visual Studio crée un conteneur avec des montages de volume déjà prêts quand vous créez et exécutez votre conteneur. Si vous voulez contrôler le moment auquel est créé votre conteneur, désactivez cette option. |
| Tuer automatiquement les conteneurs lors de la fermeture de la solution | Il en va | Docker Compose | Désactivez cette option si vous voulez que les conteneurs de votre solution continuent à s’exécuter après la fermeture de la solution ou la fermeture de Visual Studio. |
| Ne pas demander l’approbation du certificat SSL localhost | Off | Projets ASP.NET Core 2.2 | Si le certificat SSL localhost n’est pas approuvé, Visual Studio vous invite à le faire chaque fois que vous exécutez votre projet, sauf si cette case est cochée. |

> [!WARNING]
> Si le certificat SSL localhost n’est pas approuvé et que vous cochez la case pour supprimer l’invite, les requêtes web HTTPS risquent d’échouer au moment de l’exécution dans votre application ou service. Dans ce cas, décochez la case **Ne pas demander**, exécutez votre projet et confirmez l’approbation à l’invite.

> [!TIP]
> Pour plus d’informations sur l’implémentation des services et l’utilisation des outils Visual Studio pour Docker, lisez les articles suivants :
>
>Débogage d’applications dans un conteneur Docker local : <https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh>
>
>Déployer un conteneur ASP.NET sur un registre de conteneurs avec Visual Studio : <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

>[!div class="step-by-step"]
>[Suivant précédent](docker-apps-inner-loop-workflow.md)
>[Next](set-up-windows-containers-with-powershell.md)
