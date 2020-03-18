---
title: Docker - gRPC pour WCF Developers
description: Création d’images Docker pour ASP.NET applications Core gRPC
ms.date: 09/02/2019
ms.openlocfilehash: e67c43f9486fbfe9a5d3e84e3b74770eb621f604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148112"
---
# <a name="create-docker-images"></a>Créez des images Docker

Cette section couvre la création d’images Docker pour ASP.NET applications Core gRPC, prêtes à fonctionner dans des environnements Docker, Kubernetes ou autres conteneurs. L’application d’échantillon utilisée, avec une application Web ASP.NET Core MVC et un service gRPC, est disponible sur le référentiel [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) sur GitHub.

## <a name="microsoft-base-images-for-aspnet-core-applications"></a>Images de base Microsoft pour les applications ASP.NET Core

Microsoft fournit une gamme d’images de base pour la construction et l’exécution d’applications .NET Core. Pour créer une image ASP.NET Core 3.0, vous utilisez deux images de base :

- Une image SDK pour construire et publier l’application.
- Une image de temps d’exécution pour le déploiement.

| Image | Description |
| ----- | ----------- |
| [mcr.microsoft.com/dotnet/core/sdk](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | Pour les `docker build`applications de construction avec . Ne pas être utilisé en production. |
| [mcr.microsoft.com/dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | Contient l’heure d’exécution et ASP.NET dépendances de base. Pour la production. |

Pour chaque image, il existe quatre variantes basées sur différentes distributions Linux, distinguées par des balises.

| Étiquette d’image(s) | Linux | Notes |
| --------- | ----- | ----- |
| 3.0-buster, 3.0 | Debian 10 | L’image par défaut si aucune variante OS n’est spécifiée. |
| 3.0-alpine | Alpine 3.9 | Les images de base alpines sont beaucoup plus petites que les images de base de Debian ou d’Ubuntu. |
| 3.0-disco | Ubuntu 19.04 | |
| 3.0-bionique | Ubuntu 18.04 | |

L’image de base alpine est d’environ 100 Mo, contre 200 Mo pour les images Debian et Ubuntu. Certains progiciels ou bibliothèques peuvent ne pas être disponibles dans la gestion des paquets d’Alpine. Si vous ne savez pas quelle image utiliser, vous devez probablement choisir le Debian par défaut.

> [!IMPORTANT]
> Assurez-vous d’utiliser la même variante de Linux pour la construction et le temps d’exécution. Les applications construites et publiées sur une variante peuvent ne pas fonctionner sur une autre.

## <a name="create-a-docker-image"></a>Créer une image Docker

Une image Docker est définie par un *Dockerfile*. Il s’agit d’un fichier texte qui contient toutes les commandes nécessaires pour construire l’application et installer toutes les dépendances qui sont nécessaires pour la construction ou l’exécution de l’application. L’exemple suivant montre le Dockerfile le plus simple pour une application ASP.NET Core 3.0 :

```dockerfile
# Application build steps
FROM mcr.microsoft.com/dotnet/core/sdk:3.0 as builder

WORKDIR /src

COPY . .

RUN dotnet restore

RUN dotnet publish -c Release -o /published src/StockData/StockData.csproj

# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

# Uncomment the line below if running with HTTPS
# ENV ASPNETCORE_URLS=https://+:443

WORKDIR /app

COPY --from=builder /published .

ENTRYPOINT [ "dotnet", "StockData.dll" ]
```

Le Dockerfile comporte deux parties `sdk` : la première utilise l’image de base pour construire et publier l’application ; la seconde crée une image `aspnet` de temps d’exécution à partir de la base. C’est `sdk` parce que l’image est d’environ 900 Mo, par rapport à environ 200 Mo pour l’image de temps d’exécution, et la plupart de son contenu sont inutiles au moment de l’exécution.

### <a name="the-build-steps"></a>Les étapes de construction

| Étape | Description |
| ---- | ----------- |
| `FROM ...` | Déclare l’image de base `builder` et assigne l’alias. |
| `WORKDIR /src` | Crée `/src` le répertoire et le définit comme le répertoire de travail actuel. |
| `COPY . .` | Copie tout en dessous de l’annuaire actuel sur l’hôte dans l’annuaire actuel sur l’image. |
| `RUN dotnet restore` | Restaure tous les paquets externes (ASP.NET cadre Core 3.0 est préinstallé avec le SDK). |
| `RUN dotnet publish ...` | Construit et publie une version release. Notez `--runtime` que le drapeau n’est pas nécessaire. |

### <a name="the-runtime-image-steps"></a>Les étapes d’image de temps d’exécution

| Étape | Description |
| ---- | ----------- |
| `FROM ...` | Déclare une nouvelle image de base. |
| `WORKDIR /app` | Crée `/app` le répertoire et le définit comme le répertoire de travail actuel. |
| `COPY --from=builder ...` | Copie de l’application publiée de `builder` l’image `FROM` précédente, en utilisant le pseudonyme de la première ligne. |
| `ENTRYPOINT [ ... ]` | Définit la commande pour fonctionner lorsque le conteneur démarre. La `dotnet` commande dans l’image de temps d’exécution ne peut exécuter que des fichiers DLL. |

### <a name="https-in-docker"></a>HTTPS à Docker

Les images de base `ASPNETCORE_URLS` de `http://+:80`Microsoft pour Docker définissent la variable d’environnement à , ce qui signifie que Kestrel fonctionne sans HTTPS sur ce port. Si vous utilisez HTTPS avec un certificat personnalisé (tel que décrit dans [les applications IPM),](self-hosted.md)vous devez passer outre à ce sujet. Définissez la variable d’environnement dans la partie de création d’images en temps d’exécution de votre Dockerfile.

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a>Le fichier .dockerignore

Tout `.gitignore` comme les fichiers qui excluent certains `.dockerignore` fichiers et répertoires du contrôle source, le fichier peut être utilisé pour exclure les fichiers et les répertoires d’être copiés à l’image pendant la construction. Cela permet non seulement d’économiser la copie de temps, mais peut également éviter certaines erreurs qui découlent d’avoir le `obj` répertoire de votre PC copié dans l’image. Au minimum, vous devez `bin` ajouter `obj` des `.dockerignore` entrées pour et à votre fichier.

```console
bin/
obj/
```

## <a name="build-the-image"></a>Créer l’image

Pour une solution avec une seule application, et donc un seul Dockerfile, il est plus simple de mettre le Dockerfile dans le répertoire de base. En d’autres termes, mettez-le `.sln` dans le même répertoire que le fichier. Dans ce cas, pour construire l’image, utilisez la commande suivante `docker build` de l’annuaire contenant le Dockerfile.

```console
docker build --tag stockdata .
```

Le drapeau `--tag` de façon confuse (qui `-t`peut être raccourci à ) spécifie le nom entier de l’image, y compris l’étiquette réelle si spécifié. La `.` fin précise le contexte dans lequel la construction sera exécutée; l’annuaire de travail `COPY` actuel pour les commandes dans le Dockerfile.

Si vous avez plusieurs applications dans une seule solution, vous pouvez conserver le Dockerfile pour chaque application dans son propre dossier, à côté du `.csproj` fichier. Vous devez toujours `docker build` exécuter la commande à partir du répertoire de base pour vous assurer que la solution et tous les projets sont copiés dans l’image. Vous pouvez spécifier un Dockerfile `--file` en `-f`dessous de l’annuaire actuel en utilisant le (ou) drapeau.

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a>Exécutez l’image dans un conteneur sur votre machine

Pour exécuter l’image dans votre `docker run` instance Docker locale, utilisez la commande.

```console
docker run -ti -p 5000:80 stockdata
```

Le `-ti` drapeau relie votre terminal actuel au terminal du conteneur et fonctionne en mode interactif. Le `-p 5000:80` port 80 publie (liens) sur le conteneur jusqu’au port 5000 sur l’interface réseau localhost.

## <a name="push-the-image-to-a-registry"></a>Envoyer l’image dans un registre

Une fois que vous avez vérifié que l’image fonctionne, poussez-la à un registre Docker pour la rendre disponible sur d’autres systèmes. Les réseaux internes devront fournir un registre Docker. Cela peut être aussi simple que [l’exécution `registry` de l’image de Docker](https://docs.docker.com/registry/deploying/) (le registre Docker fonctionne dans un conteneur Docker), mais il existe diverses solutions plus complètes disponibles. Pour le partage externe et l’utilisation du cloud, il existe différents registres gérés disponibles, tels que [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) ou [Docker Hub](https://docs.docker.com/docker-hub/repos/).

Pour vous en rendre à Docker Hub, préfixez le nom de l’image avec votre nom d’utilisateur ou d’organisation.

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

Pour passer à un registre privé, préfixer le nom de l’image avec le nom de l’hôte du registre et le nom de l’organisation.

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

Une fois que l’image est dans un registre, vous pouvez la déployer à des hôtes Docker individuels, ou à un moteur d’orchestration de conteneurs comme Kubernetes.

>[!div class="step-by-step"]
>[Suivant précédent](self-hosted.md)
>[Next](kubernetes.md)
