---
title: Docker-gRPC pour les développeurs WCF
description: Création d’images d’ancrage pour les applications ASP.NET Core gRPC
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 6e9d4956077286d133d09ab8e681ba5e82ab1aa4
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184476"
---
# <a name="docker"></a>Docker

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Cette section traite de la création d’images de l’arrimeur pour les applications ASP.NET Core gRPC, prêtes à être exécutées dans un environnement d’ancrage, de Kubernetes ou d’autres conteneurs. L’exemple d’application utilisé, avec une application Web ASP.NET Core MVC et un service gRPC, est disponible sur le référentiel [RendleLabs/gRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) sur GitHub.

## <a name="microsoft-base-images-for-aspnet-core-applications"></a>Images de base Microsoft pour les applications ASP.NET Core

Microsoft fournit une gamme d’images de base pour la création et l’exécution d’applications .NET Core. Pour créer une image ASP.NET Core 3,0, deux images de base sont utilisées : une image du kit de développement logiciel (SDK) pour générer et publier l’application, ainsi qu’une image d’exécution pour le déploiement.

| Image | Description |
| ----- | ----------- |
| [mcr.microsoft.com/dotnet/core/sdk](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | Pour créer des applications `docker build`avec. À ne pas utiliser en production. |
| [mcr.microsoft.com/dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | Contient le runtime et les dépendances de ASP.NET Core. Pour la production. |

Pour chaque image, il existe quatre variantes basées sur différentes distributions Linux, distinguées par des balises.

| Balise (s) d’image | Linux | Notes |
| --------- | ----- | ----- |
| 3,0-Buster, 3,0 | Debian 10 | Image par défaut si aucun variant de système d’exploitation n’est spécifié. |
| 3,0-Alpine | Alpine 3,9 | Les images de base Alpine sont plus petites que les images Debian ou Ubuntu. |
| 3,0-Disco | Ubuntu 19,04 | |
| 3,0-Bionic | Ubuntu 18.04 | |

L’image de base alpine est d’environ 100 Mo, par rapport à 200 Mo pour les images Debian et Ubuntu, mais certains packages ou bibliothèques logicielles peuvent ne pas être disponibles dans la gestion des packages de Alpine. Si vous n’êtes pas certain de l’image à utiliser, il est préférable de respecter le Debian par défaut, sauf si vous avez besoin d’utiliser un autre distribution.

> [!IMPORTANT]
> Veillez à utiliser la même variante de Linux pour la build et le Runtime. Les applications générées et publiées sur une seule variante peuvent ne pas fonctionner sur une autre.

## <a name="create-a-docker-image"></a>Créer une image d’ancrage

Une image de l’arrimeur est définie par un *fichier dockerfile*, un fichier texte qui contient toutes les commandes nécessaires à la génération de l’application et à l’installation des dépendances requises pour la génération ou l’exécution de l’application. L’exemple suivant illustre la fichier dockerfile la plus simple pour une application ASP.NET Core 3,0 :

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

Le fichier dockerfile comporte deux parties : la première utilise l' `sdk` image de base pour générer et publier l’application ; la deuxième crée une image d’exécution `aspnet` à partir de la base. Cela est dû au `sdk` fait que l’image est d’environ 900 Mo par rapport à environ 200 Mo pour l’image d’exécution, et que la majeure partie de son contenu n’est pas nécessaire au moment de l’exécution.

### <a name="the-build-steps"></a>Étapes de génération

| Étape | Description |
| ---- | ----------- |
| `FROM ...` | Déclare l’image de base et assigne l' `builder` alias (voir la section suivante pour obtenir des explications). |
| `WORKDIR /src` | Crée le `/src` répertoire et le définit comme répertoire de travail actuel. |
| `COPY . .` | Copie tout ce qui se trouve sous le répertoire actif sur l’hôte dans le répertoire actif de l’image. |
| `RUN dotnet restore` | Restaure tous les packages externes (ASP.NET Core 3,0 Framework est préinstallé avec le kit de développement logiciel (SDK)). |
| `RUN dotnet publish ...` | Génère et publie une version Release. Notez que l' `--runtime` indicateur n’est pas obligatoire. |

### <a name="the-runtime-image-steps"></a>Étapes de l’image d’exécution

| Étape | Description |
| ---- | ----------- |
| `FROM ...` | Déclare une nouvelle image de base. |
| `WORKDIR /app` | Crée le `/app` répertoire et le définit comme répertoire de travail actuel. |
| `COPY --from=builder ...` | Copie l’application publiée à partir de l’image précédente, `builder` à l’aide de `FROM` l’alias de la première ligne. |
| `ENTRYPOINT [ ... ]` | Définit la commande à exécuter lorsque le conteneur démarre. La `dotnet` commande dans l’image d’exécution peut uniquement exécuter des fichiers dll. |

### <a name="https-in-docker"></a>HTTPs dans l’ancrage

Les images de base de Microsoft pour l’arrimeur définissent la `ASPNETCORE_URLS` variable d’environnement sur `http://+:80`, ce qui signifie que Kestrel s’exécutera sans https sur ce port. Si vous utilisez le protocole HTTPs avec un certificat personnalisé (comme décrit dans [la section précédente](self-hosted.md)), vous devez le remplacer en définissant la variable **d’environnement dans la partie création** de l’image du runtime de votre fichier dockerfile.

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a>Fichier. dockerignore

À l' `.gitignore` instar des fichiers qui excluent certains fichiers et répertoires `.dockerignore` du contrôle de code source, le fichier peut être utilisé pour exclure des fichiers et des répertoires d’être copiés dans l’image pendant la génération. Cela permet non seulement de gagner du temps, mais également d’éviter certaines erreurs confuses dues à l’utilisation ( `obj` en particulier) du répertoire de votre ordinateur copié dans l’image. Vous devez ajouter au moins des entrées `bin` pour `obj` et à `.dockerignore` votre fichier.

```console
bin/
obj/
```

## <a name="build-the-image"></a>Générer l’image

Pour une solution avec une seule application, et donc une seule fichier dockerfile, il est plus simple de placer le fichier dockerfile dans le répertoire de base. autrement dit, le même répertoire que le `.sln` fichier. Dans ce cas, pour générer l’image, utilisez la commande `docker build` suivante à partir du répertoire contenant fichier dockerfile.

```console
docker build --tag stockdata .
```

L' `--tag` indicateur de nom confus (qui peut être raccourci `-t`) spécifie le nom complet de l’image, *y compris* la balise réelle si elle est spécifiée. Le `.` à la fin spécifie le *contexte* dans lequel la build sera exécutée ; le répertoire de travail actuel `COPY` pour les commandes dans fichier dockerfile.

Si vous avez plusieurs applications au sein d’une même solution, vous pouvez conserver le fichier dockerfile pour chaque application dans son propre dossier, `.csproj` en regard du fichier, mais vous devez `docker build` toujours exécuter la commande à partir du répertoire de base pour vous assurer que la solution et tous les projets sont copiés dans l’image. Vous pouvez spécifier un fichier dockerfile sous le répertoire actif à l' `--file` aide de `-f`l’indicateur (ou).

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a>Exécuter l’image dans un conteneur sur votre ordinateur

Pour exécuter l’image dans votre instance de l’arrimeur local, `docker run` utilisez la commande.

```console
docker run -ti -p 5000:80 stockdata
```

L' `-ti` indicateur connecte votre terminal actuel au terminal du conteneur et s’exécute en mode interactif. Le `-p 5000:80` publie (links) le port 80 sur le conteneur vers le port 80 sur l’interface réseau localhost.

## <a name="push-the-image-to-a-registry"></a>Envoyer l’image vers un registre

Une fois que vous avez vérifié que l’image fonctionne, vous devez la transmettre à un registre de l’arrimeur pour la rendre disponible sur d’autres systèmes. Les réseaux internes devront approvisionner un registre Dockr. Cela peut être aussi simple que l’exécution [de l' `registry` image de l’arrimeur](https://docs.docker.com/registry/deploying/) (ce qui est correct, le registre de l’arrimeur s’exécute dans un conteneur d’ancrage), mais il existe plusieurs solutions plus complètes disponibles. Pour le partage externe et l’utilisation du Cloud, plusieurs registres gérés sont disponibles, tels que [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) ou le [hub d’ancrage](https://docs.docker.com/docker-hub/repos/).

Pour effectuer une transmission de type push vers le Hub Dockr, préfixez le nom de l’image avec votre nom d’utilisateur ou d’organisation.

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

Pour effectuer une transmission de type push vers un registre privé, préfixez le nom de l’image avec le nom d’hôte du Registre et le nom de l’organisation.

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

Une fois que l’image se trouve dans un registre, vous pouvez la déployer sur des hôtes de l’arrimeur ou sur un moteur d’orchestration de conteneur comme Kubernetes.

>[!div class="step-by-step"]
>[Précédent](self-hosted.md)
>[Suivant](kubernetes.md)
