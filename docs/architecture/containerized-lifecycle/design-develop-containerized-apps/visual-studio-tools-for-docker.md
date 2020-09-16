---
title: Visual Studio Tools pour Docker sur Windows
description: Familiarisez-vous avec les outils Docker disponibles dans Visual Studio 2017 versions 15.7 et ultérieures.
ms.date: 08/06/2020
ms.custom: vs-dotnet
ms.openlocfilehash: ae20ebf7c3c27d7f2ebe51c33719b82048f86241
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90678925"
---
# <a name="use-docker-tools-in-visual-studio-on-windows"></a>Utiliser les outils de l’outil d’ancrage dans Visual Studio sur Windows

Le workflow du développeur quand vous utilisez les outils Docker inclus dans Visual Studio 2017 versions 15.7 et ultérieures est similaire à l’utilisation de Visual Studio Code et de l’interface CLI Docker (en fait, il se base sur la même interface CLI Docker), mais il est plus facile à démarrer, il simplifie le processus et il permet une plus grande productivité pour les tâches de création, exécution et composition. Il permet également d’exécuter et de déboguer vos conteneurs par le biais des touches `F5` et `Ctrl+F5` habituelles depuis Visual Studio. Vous pouvez même déboguer une solution entière si ses conteneurs sont définis dans le même fichier `docker-compose.yml` au niveau de la solution.

## <a name="configure-your-local-environment"></a>Configurer votre environnement local

Avec les dernières versions de Docker pour Windows, il est plus facile que jamais de développer des applications Docker, car le programme d’installation est simple, comme décrit dans les références suivantes.

> [!TIP]
> Pour en savoir plus sur l’installation de Docker pour Windows, accédez à (<https://docs.docker.com/docker-for-windows/>).

## <a name="docker-support-in-visual-studio"></a>Prise en charge de Docker dans Visual Studio

Il existe deux niveaux de prise en charge de Docker que vous pouvez ajouter à un projet. Dans les projets ASP.NET Core, vous pouvez simplement ajouter un fichier `Dockerfile` au projet en activant la prise en charge de Docker. Le niveau suivant est la prise en charge de l’orchestration des conteneurs, qui ajoute un `Dockerfile` au projet (s’il n’existe pas déjà) et un fichier `docker-compose.yml` au niveau de la solution. La prise en charge de l’orchestration des conteneurs, par le biais de Docker Compose, est ajoutée par défaut dans Visual Studio 2017 versions 15.0 à 15.7. La prise en charge de l’orchestration des conteneurs est une fonctionnalité à accepter dans Visual Studio 2017 versions 15.8 ou ultérieures. Visual Studio 2019 et versions ultérieures prennent également en charge le déploiement **Kubernetes/Helm** .

Les commandes **Ajouter > Prise en charge de Docker** et **Ajouter > Prise en charge des orchestrateurs de conteneurs** se trouvent dans le menu contextuel du nœud du projet pour un projet ASP.NET Core dans l’**Explorateur de solutions**, comme l’illustre la figure 4-31 :

![Option de menu Ajouter la prise en charge de Docker dans Visual Studio](media/add-docker-support-menu.png)

**Figure 4-31**. Ajout de la prise en charge de l’ancrage à un projet Visual Studio 2019

### <a name="add-docker-support"></a>Ajouter la prise en charge Docker

Outre la possibilité d’ajouter la prise en charge de l’ancrage à une application existante, comme indiqué dans la section précédente, vous pouvez également activer la prise en charge de l’ancrage pendant la création du projet en sélectionnant **activer la prise en charge** de l’ancrage dans la boîte de dialogue **nouvelle ASP.net Core application Web** qui s’ouvre lorsque vous cliquez sur **OK** dans la boîte de dialogue **nouveau projet** , comme illustré 4-32 dans la

![Activer la prise en charge de Docker pour une nouvelle application web ASP.NET Core dans Visual Studio](media/enable-docker-support-visual-studio.png)

**Figure 4-32**. Activer la prise en charge de l’ancrage pendant la création du projet dans Visual Studio 2019

Quand vous ajoutez ou activez la prise en charge de l’ancrage, Visual Studio ajoute un fichier _fichier dockerfile_ au projet, qui inclut des références à tous les projets requis de la solution.

### <a name="add-container-orchestration-support"></a>Ajouter la prise en charge de l’orchestration de conteneurs

Pour composer une solution à plusieurs conteneurs, ajoutez la prise en charge de l’orchestration de conteneurs à vos projets. Cela vous permet d’exécuter et de déboguer simultanément un groupe de conteneurs (une solution complète), si ces conteneurs sont définis dans le même fichier _docker-compose.yml_.

Pour ajouter la prise en charge de l’orchestration de conteneurs, cliquez sur le nœud de la solution ou du projet dans l’**Explorateur de solutions**, puis choisissez **Ajouter > Prise en charge des orchestrateurs de conteneurs**. Choisissez ensuite **Kubernetes/Helm** ou **docker compose** pour gérer les conteneurs.

Une fois que vous avez ajouté la prise en charge de l’orchestration de conteneur à votre projet, vous voyez un fichier dockerfile ajouté au projet et un dossier **dockr-compose** ajouté à la solution dans **Explorateur de solutions**, comme illustré dans la figure 4-33 :

![Fichiers Docker dans l’Explorateur de solutions de Visual Studio](media/docker-support-solution-explorer.png)

**Figure 4-33**. Fichiers de l’ancrage dans Explorateur de solutions dans Visual Studio 2019

Si le fichier _docker-compose.yml_ existe déjà, Visual Studio ajoute simplement les lignes de code de configuration requises.

## <a name="configure-docker-tools"></a>Configurer les outils Docker

Dans le menu principal, choisissez **Outils > Options**, puis développez **Outils de conteneur > Paramètres**. Les paramètres des outils de conteneur s’affichent.

![Options des outils de l’outil d’ancrage de Visual Studio, avec trois pages : général, projet unique et Docker Compose, détails dans le texte de l’article.](media/visual-studio-docker-tools-options.png)

**Figure 4-34**. Options des outils Docker

Le tableau suivant peut vous aider à déterminer comment définir ces options.

| Page/paramètre                                |  Paramètre par défaut   | Description                                                                                                                                                                                                                                                                                                                                                                                                           |
| ------------------------------------------- | :----------------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Page général**                            |
| Installer le Bureau de l’arrimeur si nécessaire            |     Me demander      |
| Démarrer le Bureau de l’arrimeur si nécessaire              |     Me demander      |
| Approuver ASP.NET Core certificat SSL          |     Me demander      | Si le certificat SSL localhost n’a pas été marqué comme approuvé (avec `dotnet dev-certs https --trust` ), Visual Studio vous demandera chaque fois que vous exécuterez votre projet.                                                                                                                                                                                                                                                    |
| **Page de projet unique**                     |
| Extraire les images de l’ancrage requis sur le projet ouvert |        Vrai        | Pour accroître les performances lors de l’exécution du projet, Visual Studio démarre une opération d’extraction de l’ancrage en arrière-plan. ainsi, lorsque vous êtes prêt à exécuter votre code, l’image est déjà téléchargée ou en cours de téléchargement. Si vous chargez simplement des projets et parcourez du code, vous pouvez désactiver cette option pour éviter le téléchargement des images conteneur dont vous n’avez pas besoin. Cela peut ralentir l’expérience utilisateur Open Project. |
| Extraire les images ancrables mises à jour lors du chargement du projet  | Projets .NET Core | Extrayez les mises à jour des images existantes pour accéder aux dernières mises à jour sur le projet ouvert. Cela peut ralentir l’expérience utilisateur Open Project.                                                                                                                                                                                                                                                                                          |
| Supprimer les conteneurs à la fermeture du projet          |        Vrai        | Nettoyage à la fermeture du projet, cela peut ralentir l’expérience utilisateur du projet, mais elle est généralement rapide.                                                                                                                                                                                                                                                                                                            |
| Exécuter les conteneurs sur le projet ouvert              |        Vrai        | Pour de meilleures performances lors de l’exécution du projet, Visual Studio démarre tous les conteneurs de la solution. Cela peut ralentir l’expérience utilisateur Open Project.                                                                                                                                                                                                                                                        |
| **Docker Compose**                          |                    | La page Docker Compose contient les mêmes paramètres que la page de projet unique, mais elles s’appliquent aux solutions à plusieurs conteneurs.                                                                                                                                                                                                                                                                                           |

> [!WARNING]
> Si le certificat SSL localhost n’est pas approuvé et que vous affectez à l’option la valeur **jamais**, les requêtes Web HTTPS risquent d’échouer au moment de l’exécution dans votre application ou service. Dans ce cas, redéfinissez la valeur sur **me demander** ou, mieux encore, approuvez les certificats de votre ordinateur de développement à l’aide de la commande `dotnet dev-certs https --trust` .

> [!TIP]
> Pour plus d’informations sur l’implémentation des services et l’utilisation des outils Visual Studio pour Docker, lisez les articles suivants :
>
> Déboguer des applications dans un conteneur d’ancrage local : <https://docs.microsoft.com/visualstudio/containers/edit-and-refresh>
>
> Déployer un conteneur ASP.NET sur un registre de conteneurs avec Visual Studio : <https://docs.microsoft.com/visualstudio/containers/hosting-web-apps-in-docker>

> [!div class="step-by-step"]
> [Précédent](docker-apps-inner-loop-workflow.md) 
>  [Suivant](set-up-windows-containers-with-powershell.md)
