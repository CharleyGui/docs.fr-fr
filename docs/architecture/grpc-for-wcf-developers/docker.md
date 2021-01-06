---
title: Docker-gRPC pour les développeurs WCF
description: Création d’images d’ancrage pour les applications ASP.NET Core gRPC
ms.date: 12/15/2020
ms.openlocfilehash: f662dbd67f00b828f3e1dfa47359a450dd1c5900
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938414"
---
# <a name="create-docker-images"></a>Créer des images d’ancrage

Cette section traite de la création d’images de l’arrimeur pour les applications ASP.NET Core gRPC, prêtes à être exécutées dans les environnements d’ancrage, Kubernetes ou d’autres conteneurs. L’exemple d’application utilisé, avec une application Web ASP.NET Core MVC et un service gRPC, est disponible sur le référentiel [dotnet-architecture/gRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) sur GitHub.

## <a name="microsoft-base-images-for-aspnet-core-applications"></a>Images de base Microsoft pour les applications ASP.NET Core

Microsoft fournit une gamme d’images de base pour la création et l’exécution d’applications .NET Core. Pour créer une image ASP.NET Core 3,0, vous utilisez deux images de base :

- Image du kit de développement logiciel (SDK) pour générer et publier l’application.
- Image d’exécution pour le déploiement.

| Image | Description |
| ----- | ----------- |
| [mcr.microsoft.com/dotnet/sdk](https://hub.docker.com/_/microsoft-dotnet-sdk/) | Pour créer des applications avec `docker build` . À ne pas utiliser en production. |
| [mcr.microsoft.com/dotnet/aspnet](https://hub.docker.com/_/microsoft-dotnet-aspnet/) | Contient le runtime et les dépendances de ASP.NET Core. Pour la production. |

Pour chaque image, il existe quatre variantes basées sur différentes distributions Linux, distinguées par des balises.

| Balise (s) d’image | Linux | Notes |
| --------- | ----- | ----- |
| 5,0-Buster, 5,0 | Debian 10 | Image par défaut si aucun variant de système d’exploitation n’est spécifié. |
| 5,0-Alpine | Alpine 3,9 | Les images de base Alpine sont plus petites que les images Debian ou Ubuntu. |
| 5,0-Disco | Ubuntu 19.04 | |
| 5,0-Bionic | Ubuntu 18.04 | |

L’image de base alpine est d’environ 100 Mo, par rapport à 200 Mo pour les images Debian et Ubuntu. Certains packages ou bibliothèques de logiciels peuvent ne pas être disponibles dans la gestion des packages de Alpine. Si vous ne savez pas quelle image utiliser, vous devez probablement choisir le Debian par défaut.

> [!IMPORTANT]
> Veillez à utiliser la même variante de Linux pour la build et le Runtime. Les applications générées et publiées sur une seule variante peuvent ne pas fonctionner sur une autre.

## <a name="create-a-docker-image"></a>Créer une image Docker

Une image de l’ancrage est définie par un *fichier dockerfile*. Ce *fichier dockerfile* est un fichier texte qui contient toutes les commandes nécessaires à la génération de l’application et à l’installation des dépendances nécessaires à la création ou à l’exécution de l’application. L’exemple suivant illustre la fichier dockerfile la plus simple pour une application ASP.NET Core 5,0 :

```dockerfile
FROM mcr.microsoft.com/dotnet/sdk:5.0 as build

WORKDIR /src

COPY ./StockKube.sln .
COPY ./src/StockData/StockData.csproj ./src/StockData/
COPY ./src/StockWeb/StockWeb.csproj ./src/StockWeb/

RUN dotnet restore

COPY . .

RUN dotnet publish --no-restore -c Release -o /published src/StockData/StockData.csproj

FROM mcr.microsoft.com/dotnet/aspnet:5.0 as runtime

# Uncomment the line below if running with HTTPS
# ENV ASPNETCORE_URLS=https://+:443

WORKDIR /app

COPY --from=build /published .

ENTRYPOINT [ "dotnet", "StockData.dll" ]
```

Le fichier dockerfile comporte deux parties : la première utilise l' `sdk` image de base pour générer et publier l’application ; la deuxième crée une image d’exécution à partir de la `aspnet` base. Cela est dû au fait que l' `sdk` image est d’environ 900 Mo, par rapport à environ 200 Mo pour l’image d’exécution, et que la majeure partie de son contenu n’est pas nécessaire au moment de l’exécution.

### <a name="the-build-steps"></a>Étapes de génération

| Étape | Description |
| ---- | ----------- |
| `FROM ...` | Déclare l’image de base et assigne l' `builder` alias. |
| `WORKDIR /src` | Crée le `/src` répertoire et le définit comme répertoire de travail actuel. |
| `COPY . .` | Copie tout ce qui se trouve sous le répertoire actif sur l’hôte dans le répertoire actif de l’image. |
| `RUN dotnet restore` | Restaure tous les packages externes (ASP.NET Core 3,0 Framework est préinstallé avec le kit de développement logiciel (SDK)). |
| `RUN dotnet publish ...` | Génère et publie une version Release. Notez que l' `--runtime` indicateur n’est pas obligatoire. |

### <a name="the-runtime-image-steps"></a>Étapes de l’image d’exécution

| Étape | Description |
| ---- | ----------- |
| `FROM ...` | Déclare une nouvelle image de base. |
| `WORKDIR /app` | Crée le `/app` répertoire et le définit comme répertoire de travail actuel. |
| `COPY --from=builder ...` | Copie l’application publiée à partir de l’image précédente, à l’aide `builder` de l’alias de la première `FROM` ligne. |
| `ENTRYPOINT [ ... ]` | Définit la commande à exécuter lorsque le conteneur démarre. La `dotnet` commande dans l’image d’exécution peut uniquement exécuter des fichiers dll. |

### <a name="https-in-docker"></a>HTTPs dans l’ancrage

Les images de base Microsoft pour l’arrimeur définissent la `ASPNETCORE_URLS` variable d’environnement sur `http://+:80` , ce qui signifie que Kestrel s’exécute sans https sur ce port. Si vous utilisez le protocole HTTPs avec un certificat personnalisé (comme décrit dans [applications GRPC auto-hébergées](self-hosted.md)), vous devez remplacer cette configuration. Définissez la variable d’environnement dans la partie création de l’image du runtime de votre fichier dockerfile.

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/aspnet:5.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a>Fichier. dockerignore

À l’instar `.gitignore` des fichiers qui excluent certains fichiers et répertoires du contrôle de code source, le `.dockerignore` fichier peut être utilisé pour exclure des fichiers et des répertoires d’être copiés dans l’image pendant la génération. Ce fichier permet non seulement de gagner du temps, mais également d’éviter certaines erreurs qui se produisent lors de la `obj` copie du répertoire de votre ordinateur dans l’image. Au minimum, vous devez ajouter des entrées pour `bin` et `obj` à votre `.dockerignore` fichier.

```console
bin/
obj/
```

## <a name="build-the-image"></a>Créer l’image

Pour une `StockKube.sln` solution contenant deux applications différentes `StockData` et `StockWeb` , il est plus simple de placer les fichier dockerfile pour chacune d’elles dans le répertoire de base. Dans ce cas, pour générer l’image, utilisez la `docker build` commande suivante à partir du répertoire où `.sln` se trouve le fichier.

```console
docker build -t stockdata:1.0.0 -f .\src\StockData\Dockerfile .
```

L' `--tag` indicateur de nom confus (qui peut être raccourci `-t` ) spécifie le nom complet de l’image, y compris la balise réelle si elle est spécifiée. Le `.` à la fin spécifie le contexte dans lequel la build sera exécutée ; le répertoire de travail actuel pour les `COPY` commandes dans fichier dockerfile.

Si vous avez plusieurs applications au sein d’une même solution, vous pouvez conserver les fichier dockerfile pour chaque application dans son propre dossier, en regard du `.csproj` fichier. Vous devez toujours exécuter la `docker build` commande à partir du répertoire de base pour vous assurer que la solution et tous les projets sont copiés dans l’image. Vous pouvez spécifier un fichier dockerfile sous le répertoire actif à l’aide de l' `--file` indicateur (ou `-f` ).

```console
docker build -t stockdata:1.0.0 -f .\src\StockData\Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a>Exécuter l’image dans un conteneur sur votre ordinateur

Pour exécuter l’image dans votre instance de l’arrimeur local, utilisez la `docker run` commande.

```console
docker run -ti -p 5000:80 stockdata:1.0.0
```

L' `-ti` indicateur connecte votre terminal actuel au terminal du conteneur et s’exécute en mode interactif. Le `-p 5000:80` publie (links) le port 80 sur le conteneur vers le port 5000 sur l’interface réseau localhost.

## <a name="push-the-image-to-a-registry"></a>Envoyer l’image dans un registre

Une fois que vous avez vérifié que l’image fonctionne, transmettez-la à un registre de l’arrimeur pour la rendre disponible sur d’autres systèmes. Les réseaux internes devront approvisionner un registre Dockr. Cette activité peut être aussi simple que l’exécution [de l' `registry` image de l’arrimeur](https://docs.docker.com/registry/deploying/) (le registre de l’arrimeur s’exécute dans un conteneur d’ancrage), mais il existe plusieurs solutions plus complètes disponibles. Pour le partage externe et l’utilisation du Cloud, plusieurs registres gérés sont disponibles, tels que [Azure Container Registry](/azure/container-registry/) ou le [hub d’ancrage](https://docs.docker.com/docker-hub/repos/).

Pour effectuer une transmission de type push vers le hub d’ancrage, préfixez le nom de l’image avec votre nom d’utilisateur ou d’organisation.

```console
docker tag stockdata:1.0.0 <myorg>/stockdata:1.0.0
docker push <myorg>/stockdata:1.0.0
```

Pour effectuer une transmission de type push vers un registre privé, préfixez le nom de l’image avec le nom d’hôte du Registre et le nom de l’organisation.

```console
docker tag stockdata <internal-registry:5000>/<myorg>/stockdata:1.0.0
docker push <internal-registry:5000>/<myorg>/stockdata:1.0.0
```

Une fois que l’image se trouve dans un registre, vous pouvez la déployer sur des hôtes de l’arrimeur individuel ou sur un moteur d’orchestration de conteneur comme Kubernetes.

>[!div class="step-by-step"]
>[Précédent](self-hosted.md) 
> [Suivant](kubernetes.md)
