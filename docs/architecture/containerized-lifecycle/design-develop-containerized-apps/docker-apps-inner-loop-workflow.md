---
title: Workflow de développement de la boucle interne pour les applications Docker
description: En savoir plus sur le flux de travail de développement « boucle interne » pour les applications Dockr.
ms.date: 08/06/2020
ms.openlocfilehash: d66274a64591f79f242c1e8a63951b51d94a9ecd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676528"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Workflow de développement de la boucle interne pour les applications Docker

Avant de déclencher le workflow de boucle externe qui s’étend sur l’ensemble du cycle DevOps, chaque développeur doit, sur sa propre machine, coder l’application à l’aide de la plateforme et du langage de son choix, puis la tester localement (figure 4-21). Dans tous les cas, les développeurs auront tous un important point en commun, quels que soient le langage, le framework et la plateforme qu’ils auront choisis. Dans ce flux de travail spécifique, vous développez et testez toujours des conteneurs dockers dans aucun autre environnement, mais localement.

![Diagramme montrant le concept d’un environnement de développement de boucles internes.](./media/docker-apps-inner-loop-workflow/inner-loop-development-context.png)

**Figure 4-21**. Contexte du développement de boucle interne

Le conteneur ou l’instance d’une image Docker contiennent les composants suivants :

- Un choix de système d’exploitation (par exemple, une distribution Linux ou Windows)

- Des fichiers ajoutés par le développeur (par exemple, des binaires d’application)

- Des informations de configuration (par exemple, des paramètres d’environnement et des dépendances)

- Instructions sur les processus que Docker doit exécuter

Vous pouvez configurer le workflow du développement de boucle interne qui utilise Docker comme processus (qui est décrit dans la section suivante). Les premières étapes de configuration de l’environnement ne sont pas incluses, car elles ne doivent être effectuées qu’une seule fois.

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>Création d’une application dans un conteneur Docker à l’aide de Visual Studio Code et de l’interface CLI Docker

Les applications se composent de vos propres services et de bibliothèques supplémentaires (dépendances).

La figure 4-22 montre les étapes de base que vous devez généralement effectuer lors de la création d’une application Docker, et fournit une description détaillée de chaque étape.

![Diagramme montrant les sept étapes nécessaires à la création d’une application en conteneur.](./media/docker-apps-inner-loop-workflow/life-cycle-containerized-apps-docker-cli.png)

**Figure 4-22**. Workflow général du cycle de vie des applications Docker conteneurisées dans l’interface CLI Docker

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>Étape 1 : commencer le codage dans Visual Studio Code et créer votre base de référence d’application/de service initiale

Le développement des applications se déroule de façon similaire avec ou sans Docker. La différence est que, lors du développement, vous déployez et testez l’application ou les services exécutés dans des conteneurs Docker qui sont situés dans votre environnement local (comme une machine virtuelle Linux ou Windows).

**Configuration de votre environnement local**

Avec les dernières versions de Desktop Desktop pour Mac et Windows, il est plus facile que jamais de développer des applications Dockr, et l’installation est simple.

> [!TIP]
> Pour obtenir des instructions sur la configuration de Desktop Dockr pour Windows, consultez <https://docs.docker.com/docker-for-windows/> .
>
> Pour obtenir des instructions sur la configuration de Desktop Dockr pour Mac, consultez <https://docs.docker.com/docker-for-mac/> .

Par ailleurs, vous aurez besoin d’un éditeur de code pour développer votre application tout en utilisant l’interface CLI Docker.

Microsoft fournit Visual Studio Code, qui est un éditeur de code léger pris en charge sur Windows, Linux et macOS, et fournit à IntelliSense la [prise en charge de nombreux langages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .net, Go, Java, Ruby, Python et les langages les plus modernes), du [débogage](https://code.visualstudio.com/Docs/editor/debugging), [de l’intégration avec git](https://code.visualstudio.com/Docs/editor/versioncontrol) et des [Extensions](https://code.visualstudio.com/docs/extensions/overview). Cet éditeur convient parfaitement aux développeurs macOS et Linux. Dans Windows, vous pouvez également utiliser Visual Studio.

> [!TIP]
> Pour obtenir des instructions sur l’installation de Visual Studio Code pour Windows, Linux ou macOS, consultez <https://code.visualstudio.com/docs/setup/setup-overview/> .
>
> Pour obtenir des instructions sur la configuration de Docker sur Mac, accédez à <https://docs.docker.com/docker-for-mac/>.

Vous pouvez utiliser l’interface CLI Docker et écrire votre code à l’aide de n’importe quel éditeur de code. Toutefois, l’utilisation de Visual Studio Code avec l’extension Docker facilite la création des fichiers `Dockerfile` et `docker-compose.yml` dans votre espace de travail. Vous pouvez également exécuter des tâches et des scripts à partir de l’IDE de Visual Studio Code pour exécuter des commandes Docker à l’aide de l’interface CLI Docker ci-dessous.

L’extension Docker pour VS Code fournit les fonctionnalités suivantes :

- La génération automatique des fichiers `Dockerfile` et `docker-compose.yml`

- La mise en surbrillance de la syntaxe et des info-bulles pour les fichiers `docker-compose.yml` et `Dockerfile`

- IntelliSense (saisie semi-automatique) pour les fichiers `Dockerfile` et `docker-compose.yml`

- La vérification ou « linting » (erreurs et avertissements) pour les fichiers `Dockerfile`

- L’intégration de la palette de commandes (F1) pour les commandes Docker les plus courantes

- L’intégration de l’explorateur pour la gestion des images et des conteneurs

- Le déploiement des images de DockerHub et des registres de conteneur Azure sur Azure App Service

Pour installer l’extension Docker, appuyez sur Ctrl + Maj + P, tapez `ext install`, puis exécutez la commande Install Extension pour afficher la liste des extensions Marketplace. Ensuite, tapez **docker** pour filtrer les résultats et sélectionnez l’extension Docker Support, comme illustré dans la figure 4-23.

![Vue de l’extension Docker pour VS Code.](media/docker-apps-inner-loop-workflow/install-docker-extension-vs-code.png)

**Figure 4-23**. Installation de l’extension Docker dans Visual Studio Code

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>Étape 2 : créer un fichier dockerfile lié à une image existante (environnements de système d’exploitation ou de développement simples tels que .NET Core, Node.js et Ruby)

Vous aurez besoin qu’un `DockerFile` soit créé pour chaque image personnalisée et déployé pour chaque conteneur. Si votre application est composée d’un seul service personnalisé, vous aurez besoin d’un seul `DockerFile` . Toutefois, si votre application est composée de plusieurs services (comme dans une architecture de microservices), vous aurez besoin d’un `Dockerfile` par service.

Le `DockerFile` est généralement placé dans le dossier racine de votre application ou de votre service. Il contient les commandes dont a besoin Docker pour savoir comment configurer et exécuter l’application ou le service. Vous pouvez créer votre `DockerFile` et l’ajouter à votre projet en même temps que votre code (node.js, .NET Core, etc.). Si vous ne connaissez pas encore bien l’environnement, lisez l’info-bulle suivante.

> [!TIP]
> L’extension Docker peut vous guider lors de l’utilisation des fichiers `Dockerfile` et `docker-compose.yml` associés à vos conteneurs Docker. Vous finirez probablement par écrire ces types de fichiers sans vous aider de cet outil. Toutefois, l’utilisation de l’extension Docker constitue un bon point de départ qui vous permet d’apprendre plus vite.

Dans la figure 4-24, vous pouvez voir les étapes permettant d’ajouter les fichiers de l’ancrage à un projet à l’aide de l’extension de l’ancrage pour VS Code :

1. Ouvrez la palette de commandes, tapez «**docker**», puis sélectionnez «**Ajouter les fichiers de l’ancreur à l’espace de travail**».
2. Sélectionner une plateforme d’application (ASP.NET Core)
3. Sélectionner le système d’exploitation (Linux)
4. Inclure les fichiers Docker Compose facultatifs
5. Entrer les ports à publier (80, 443)
6. Sélectionner le projet

![Procédure d’ajout de fichiers de l’ancrage avec l’extension de l’amarrage](media/docker-apps-inner-loop-workflow/add-docker-files-to-workspace-command.png)

**Figure 4-24**. Fichiers de l’arrimeur ajoutés à l’aide de la commande **Ajouter des fichiers de l’ancrage à l’espace de travail**

Lorsque vous ajoutez un fichier dockerfile, vous spécifiez l’image de base que vous utiliserez (comme avec `FROM mcr.microsoft.com/dotnet/aspnet` ). En général, vous créez votre image personnalisée sur l’image de base que vous pouvez obtenir dans n’importe quel dépôt officiel du [registre Docker Hub](https://hub.docker.com/) (comme une [image pour .NET Core](https://hub.docker.com/_/microsoft-dotnet/) ou [pour Node.js](https://hub.docker.com/_/node/)).

> [!TIP]
> Vous devez répéter cette procédure pour chaque projet dans votre application. Toutefois, l’extension demandera de remplacer le fichier d’ancrage-compose généré après la première fois. Vous devez répondre à ne pas le remplacer. l’extension crée donc des fichiers dockr-compose distincts, que vous pouvez ensuite fusionner manuellement, avant d’exécuter dockr-compose.

**_Utiliser une image officielle de l’Ancreur existante_**

L’utilisation du dépôt officiel d’une pile de langages avec numéro de version garantit que les mêmes fonctionnalités de langage seront disponibles sur toutes les machines (y compris celles de développement, de test et de production).

Voici un exemple de fichier DockerFile pour un conteneur .NET Core :

```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
WORKDIR /src
COPY ["src/WebApi/WebApi.csproj", "src/WebApi/"]
RUN dotnet restore "src/WebApi/WebApi.csproj"
COPY . .
WORKDIR "/src/src/WebApi"
RUN dotnet build "WebApi.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApi.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApi.dll"]
```

Dans ce cas, l’image est basée sur la version 3,1 de l’image officielle de l’Ancreur ASP.NET Core (multi-arch pour Linux et Windows), conformément à la ligne `FROM mcr.microsoft.com/dotnet/aspnet:3.1` . (pour plus d’informations à ce sujet, consultez la page [Image Docker ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-aspnet/) et la page [Image Docker .NET Core](https://hub.docker.com/_/microsoft-dotnet/)).

Dans le fichier dockerfile, vous pouvez également demander à Dockr d’écouter le port TCP que vous allez utiliser lors de l’exécution (par exemple, le port 80 ou 443).

Vous pouvez spécifier des paramètres de configuration supplémentaires dans le fichier Dockerfile, en fonction du langage et du framework que vous utilisez. Par exemple, la ligne `ENTRYPOINT` avec `["dotnet", "WebMvcApplication.dll"]` indique à Docker d’exécuter une application .NET Core. Si vous utilisez le SDK et l’interface CLI .NET Core (`dotnet CLI`) pour créer et exécuter l’application .NET, ce paramètre est différent. L’essentiel à retenir est que la ligne ENTRYPOINT et certains autres paramètres varient selon le langage et la plateforme choisis pour votre application.

> [!TIP]
> Pour plus d’informations sur la création d’images Docker pour les applications .NET Core, accédez à <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.
>
> Pour savoir comment créer vos propres images, accédez à <https://docs.docker.com/engine/tutorials/dockerimages/>.

**Utiliser des dépôts d’images multiarch**

Dans un dépôt, un même nom d’image peut contenir des variantes de plateforme, comme une image Linux et une image Windows. Cette fonctionnalité permet aux fournisseurs comme Microsoft (créateurs d’images de base) de créer un dépôt commun pour plusieurs plateformes (Linux et Windows). Par exemple, le dépôt [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-aspnet/) disponible dans le registre Docker Hub assure la prise en charge de Linux et de Windows Nano Server sous le même nom d’image.

Ainsi, quand vous tirez (pull) une image [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-aspnet/) d’un hôte Windows, la variante Windows est tirée, et quand vous tirez le même nom d’image d’un hôte Linux, la variante Linux est tirée.

**_Créer votre image de base à partir de zéro_**

Vous pouvez créer votre propre image de base Docker à partir de zéro, comme l’explique [cet article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) tiré du site Docker. Ce scénario n’est probablement pas adapté si vous n’êtes pas encore familiarisé avec Docker. Toutefois, si vous souhaitez définir certains aspects de votre propre image de base, vous pouvez le suivre.

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>Étape 3 : créer vos images d’ancrage personnalisées incorporant votre service dans celui-ci

Vous devrez créer une image pour chaque service personnalisé qui compose votre application. Si votre application n’est composée que d’un seul service ou d’une seule application web, vous n’aurez besoin que d’une seule image.

> [!NOTE]
> Avec le « workflow de boucle externe DevOps », les images sont créées par un processus de génération automatique dès que vous poussez (push) votre code source vers un dépôt Git (intégration continue). Les images sont donc créées dans cet environnement global à partir de votre code source.
>
> Mais avant de passer à l’itinéraire de la boucle externe, vous devez vous assurer que l’application de l’arrimeur fonctionne correctement pour ne pas envoyer du code qui risque de ne pas fonctionner correctement dans le système de contrôle de code source (git, etc.).
>
> Par conséquent, chaque développeur doit d’abord effectuer l’intégralité du processus de boucle interne pour effectuer des tests localement et continuer à développer jusqu’à ce qu’il souhaite pousser (push) une fonctionnalité complète ou une modification vers le système de contrôle source.

Pour créer une image dans votre environnement local et à l’aide de fichier dockerfile, vous pouvez utiliser la commande dockr Build, comme le montre la figure 4-25, car elle balise déjà l’image pour vous et génère les images pour tous les services de l’application avec une commande simple.

![Capture d’écran montrant la sortie de la console de la commande dockr-compose Build.](media/docker-apps-inner-loop-workflow/run-docker-build-command.png)

**Figure 4-25**. Exécuter docker build

Si vous le souhaitez, au lieu d’exécuter directement `docker build` à partir du dossier du projet, vous pouvez d’abord générer un dossier déployable avec les bibliothèques .NET nécessaires, en exécutant les commandes `dotnet publish` puis `docker build`.

Cet exemple crée une image Docker portant le nom `explore-docker-vscode/webapi:latest` (`:latest` est une balise, par exemple, une version). Vous pouvez effectuer cette étape pour chaque image personnalisée que vous avez besoin de créer pour l’application Docker à plusieurs conteneurs. Toutefois, nous verrons dans la section suivante qu’il est plus facile de le faire à l’aide de `docker-compose` .

Vous pouvez rechercher les images existantes dans votre dépôt local (votre ordinateur de développement) à l’aide de la `docker images` commande, comme illustré dans la Figure 4-26.

![Sortie de console de la commande docker images, montrant les images existantes.](media/docker-apps-inner-loop-workflow/view-existing-images-with-docker-images.png)

**Figure 4-26**. Affichage des images existantes à l’aide de la commande docker images

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>Étape 4 : définir vos services dans docker-compose. yml lors de la création d’une application d’ancrage composée avec plusieurs services

Avec le fichier `docker-compose.yml`, vous pouvez définir un ensemble de services à déployer sous la forme d’une application composée, avec les commandes de déploiement décrites dans la section suivante.

Créez ce fichier dans le dossier de solution racine ou principal, dont le contenu doit être similaire à celui illustré dans ce fichier `docker-compose.yml` :

```yml
version: "3.4"

services:
  webapi:
    image: webapi
    build:
      context: .
      dockerfile: src/WebApi/Dockerfile
    ports:
      - 51080:80
    depends_on:
      - redis
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://+:80

  webapp:
    image: webapp
    build:
      context: .
      dockerfile: src/WebApp/Dockerfile
    ports:
      - 50080:80
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://+:80
      - WebApiBaseAddress=http://webapi

  redis:
    image: redis
```

Dans ce cas particulier, ce fichier définit trois services : le service API Web (votre service personnalisé), une application Web et le service ReDim (un service de cache connu). Chaque service sera déployé en tant que conteneur. vous devez donc utiliser une image d’ancrage concrète pour chacun d’entre eux. Pour cette application particulière :

- Le service API Web est créé à partir de fichier dockerfile dans le `src/WebApi/Dockerfile` répertoire.

- Le port hôte 51080 est transféré vers le port exposé 80 sur le `webapi` conteneur.

- Le service API Web dépend du service ReDim

- L’application Web accède au service API Web à l’aide de l’adresse interne : `http://webapi` .

- Le service ReDim utilise la [dernière image des redims publics](https://hub.docker.com/_/redis/) extraite du Registre du Hub de l’ancrage. [Redims](https://redis.io/) est un système de cache populaires pour les applications côté serveur.

### <a name="step-5-build-and-run-your-docker-app"></a>Étape 5 : générer et exécuter votre application Dockr

Si votre application ne comprend qu’un seul conteneur, vous pouvez l’exécuter en la déployant sur l’hôte Docker (machine virtuelle ou serveur physique). Toutefois, si votre application est composée de plusieurs services, vous devez également la _composer_. Voyons les différentes options.

**_Option A : exécuter un seul conteneur ou service_**

Vous pouvez exécuter l’image Docker à l’aide de la commande docker run, comme illustré ici :

```console
docker run -t -d -p 50080:80 explore-docker-vscode/webapp:latest
```

Pour ce déploiement particulier, nous allons rediriger les demandes envoyées au port 50080 sur l’hôte vers le port interne 80.

**_Option B : composer et exécuter une application à plusieurs conteneurs_**

Dans la plupart des scénarios d’entreprise, une application Docker est composée de plusieurs services. Dans ce cas, vous pouvez exécuter la `docker-compose up` commande (Figure 4-27), qui utilisera le fichier docker-compose. yml que vous avez créé précédemment. L’exécution de cette commande génère toutes les images personnalisées et déploie l’application composée avec tous ses conteneurs associés.

![Sortie de console de la commande docker-compose up.](media/docker-apps-inner-loop-workflow/results-docker-compose-up.png)

**Figure 4-27**. Résultats de l’exécution de la commande docker-compose up

Après avoir exécuté `docker-compose up`, déployez votre application et ses conteneurs sur votre hôte Docker (comme illustré à la figure 4-28) dans la représentation de machine virtuelle.

![Machine virtuelle exécutant des applications à plusieurs conteneurs.](./media/docker-apps-inner-loop-workflow/vm-with-docker-containers-deployed.png)

**Figure 4-28**. Machine virtuelle avec des conteneurs Docker déployés

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>Étape 6 : tester votre application Dockr (localement, sur votre machine virtuelle CD locale)

Cette étape varie en fonction de ce que fait votre application.

Dans une API web .NET Core de type « Hello World » déployée sous la forme d’un conteneur ou d’un service, vous devez simplement accéder au service en fournissant le port TCP qui est spécifié dans le fichier DockerFile.

Sur l’hôte Docker, ouvrez un navigateur et accédez à ce site. Vous devez y voir votre application ou service s’exécuter, comme illustré à la figure 4-29.

![Vue du navigateur montrant la réponse à localhost/API/values.](media/docker-apps-inner-loop-workflow/test-docker-app-locally-localhost.png)

**Figure 4-29**. Test local de votre application Dockr à l’aide du navigateur

Notez qu’il utilise le port 50080, mais qu’en interne il est redirigé vers le port 80, car c’est la manière dont il a été déployé avec `docker compose` , comme expliqué précédemment.

Vous pouvez tester cela en utilisant le navigateur à l’aide de la boucle, comme illustré à la figure 4-30.

![Résultat de la boucle obtenu à partir de http://localhost:51080/WeatherForecast](media/docker-apps-inner-loop-workflow/test-docker-app-locally-curl.png)

**Figure 4-30**. Test de l’application Docker localement avec CURL

**Débogage d’un conteneur exécuté sur Docker**

Visual Studio Code prend en charge le débogage Docker si vous utilisez Node.js et d’autres plateformes telles que les conteneurs .NET Core.

Vous pouvez également déboguer les conteneurs .NET Core ou .NET Framework dans Docker si vous utilisez Visual Studio pour Windows ou Mac, comme décrit dans la section suivante.

> [!TIP]
> Pour en savoir plus sur le débogage Node.js conteneurs d’ancrage, consultez <https://blog.docker.com/2016/07/live-debugging-docker/> et <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more> .

> [!div class="step-by-step"]
> [Précédent](docker-apps-development-environment.md) 
>  [Suivant](visual-studio-tools-for-docker.md)
