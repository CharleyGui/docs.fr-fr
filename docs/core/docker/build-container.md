---
title: Tutoriel Conteneuriser une application avec Docker
description: Dans ce tutoriel, vous apprendrez à conteneuriser une application .NET Core avec Docker.
ms.date: 01/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 8be12792e4a9e8511dba87e657f700cc4ec97a16
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546573"
---
# <a name="tutorial-containerize-a-net-core-app"></a>Tutorial: Containerize a .NET Core app

Ce tutoriel explique comment élaborer une image Docker contenant une application .NET Core existante. L’image vous permettra de créer des conteneurs pour votre environnement de développement local, votre cloud privé ou votre cloud public.

Vous apprendrez à :

> [!div class="checklist"]
>
> - Créer et publier une application .NET Core simple
> - Créer et configurer un Dockerfile pour .NET Core
> - Générer une image Docker
> - Créer et exécuter un conteneur Docker

Vous découvrirez la création d’un conteneur Docker et les tâches de déploiement pour une application .NET Core. La *plate-forme Docker* utilise le *moteur Docker* pour construire et emballer rapidement des applications comme des *images Docker*. Ces images sont écrites au format *Dockerfile* pour être déployées et exécutées dans un conteneur en couches.

> [!WARNING]
> **Ce tutoriel n’est pas pour ASP.NET applications Core.** Si vous utilisez ASP.NET Core, lisez le Apprendre à conteneuriser un tutoriel [d’application ASP.NET Core.](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

## <a name="prerequisites"></a>Prérequis

Installez les éléments requis suivants :

- [.NET Core 3.1 SDK](https://dotnet.microsoft.com/download)\
Si .NET Core est installé, utilisez la commande `dotnet --info` pour identifier le Kit SDK que vous utilisez.

- [Docker Community Edition](https://www.docker.com/products/docker-desktop)

- Un dossier de travail temporaire pour le *Dockerfile* et un exemple d’application .NET Core. Dans ce tutoriel, le nom *docker-travail* est utilisé comme le dossier de travail.

## <a name="create-net-core-app"></a>Créer une application .NET Core

Vous avez besoin d’une application .NET Core que le conteneur Docker exécutera. Ouvrez votre terminal, créez un dossier de travail si ce n’est déjà fait, et accédez-y. Dans le dossier de travail, exécutez la commande suivante pour créer un nouveau projet dans une sous-direction nommée *application*:

```dotnetcli
dotnet new console -o app -n myapp
```

Votre arborescence de dossiers doit ressembler à ce qui suit :

```
docker-working
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    └───obj
            myapp.csproj.nuget.cache
            myapp.csproj.nuget.dgspec.json
            myapp.csproj.nuget.g.props
            myapp.csproj.nuget.g.targets
            project.assets.json
```

La commande `dotnet new` crée un dossier nommé *app* et génère une application « Hello World ». Accédez au dossier *app* et exécutez la commande `dotnet run`. Le résultat suivant s’affiche :

```console
> dotnet run
Hello World!
```

Le modèle par défaut crée une application qui affiche les données dans le terminal, puis se ferme. Pour ce tutoriel, vous utiliserez une application qui effectue une boucle indéfiniment. Ouvrez le fichier *Program.cs* dans un éditeur de texte. Il devrait ressembler au code suivant :

```csharp
using System;

namespace myapp
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

Remplacez le fichier par le code suivant qui compte les nombres chaque seconde :

```csharp
using System;

namespace myapp
{
    class Program
    {
        static void Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while (max == -1 || counter < max)
            {
                counter++;
                Console.WriteLine($"Counter: {counter}");
                System.Threading.Tasks.Task.Delay(1000).Wait();
            }
        }
    }
}
```

Enregistrez le fichier et effectuez un nouveau avec `dotnet run`. N’oubliez pas que cette application s’exécute indéfiniment. Utilisez la commande d’annulation <kbd>CTRL</kbd>+<kbd>C</kbd> pour l’arrêter. Le résultat suivant s’affiche :

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

Si vous envoyez un nombre à l’application sur la ligne de commande, l’application comptera uniquement jusqu’à ce montant puis se fermera. Effectuez un test avec `dotnet run -- 5` pour compter jusqu’à cinq.

> [!NOTE]
> Tous les paramètres après `--` sont transmis à votre application au lieu d’être transmis à la commande `dotnet run`.

## <a name="publish-net-core-app"></a>Publier une application .NET Core

Avant d’ajouter votre application .NET Core à l’image Docker, publiez-la. Vous souhaitez vous assurer que le conteneur exécute la version publiée de l’application quand elle est démarrée.

Dans le dossier de travail, accédez au dossier *app* contenant l’exemple de code source, puis exécutez la commande suivante :

```dotnetcli
dotnet publish -c Release
```

Cette commande compile votre application dans le dossier *publish*. Le chemin du dossier *publish* à partir du dossier de travail doit être `.\app\bin\Release\netcoreapp3.1\publish\`

Du dossier *d’application,* obtenez une liste d’annuaire du dossier de publication pour vérifier que le fichier *myapp.dll* a été créé.

```console
> dir bin\Release\netcoreapp3.1\publish

    Directory:  C:\docker-working\app\bin\Release\netcoreapp3.1\publish

01/09/2020  11:41 AM    <DIR>          .
01/09/2020  11:41 AM    <DIR>          ..
01/09/2020  11:41 AM               407 myapp.deps.json
01/09/2020  12:15 PM             4,608 myapp.dll
01/09/2020  12:15 PM           169,984 myapp.exe
01/09/2020  12:15 PM               736 myapp.pdb
01/09/2020  11:41 AM               154 myapp.runtimeconfig.json
```

Si vous utilisez Linux ou macOS, utilisez la `ls` commande pour obtenir une liste d’annuaire et vérifiez que le fichier *myapp.dll* a été créé.

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

## <a name="create-the-dockerfile"></a>Créer le Dockerfile

Le fichier *Dockerfile* est utilisé par la commande `docker build` pour créer une image de conteneur. Ce fichier est un fichier texte nommé *Dockerfile* qui n’a pas d’extension.

Dans votre terminal, accédez au dossier de travail que vous avez créé au début. Créez un fichier nommé *Dockerfile* dans votre dossier de travail et ouvrez-le dans un éditeur de texte. Selon le type d’application que vous allez conteneuriser, vous choisirez soit le ASP.NET’exécution Core ou le temps d’exécution .NET Core. En cas de doute, choisissez le ASP.NET’exécution Core, qui comprend le temps d’exécution .NET Core. Ce tutoriel utilisera l’image ASP.NET Core runtime, mais l’application créée dans les sections précédentes est une application .NET Core.

- ASP.NET période d’exécution de base

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
  ```

- Runtime .NET Core

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/runtime:3.1
  ```

La `FROM` commande indique à Docker de retirer l’image étiquetée **3.1** du dépôt spécifié. Assurez-vous que vous tirez la version runtime qui correspond au temps d’exécution ciblé par votre SDK. Par exemple, l’application créée dans la section précédente a utilisé le .NET Core 3.1 SDK et l’image de base mentionnée dans le *Dockerfile* est étiquetée avec **3.1**.

Enregistrez le fichier *Dockerfile*. La structure de répertoires du dossier de travail doit ressembler à ce qui suit. Certains des fichiers et dossiers de niveau plus profond ont été supprimés pour économiser de l’espace dans l’article :

```
docker-working
│   Dockerfile
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    ├───bin
    │   └───Release
    │       └───netcoreapp3.1
    │           └───publish
    │                   myapp.deps.json
    │                   myapp.exe
    │                   myapp.dll
    │                   myapp.pdb
    │                   myapp.runtimeconfig.json
    │
    └───obj
```

Dans votre terminal, exécutez la commande suivante :

```console
docker build -t myimage -f Dockerfile .
```

Docker traitera chaque ligne du *Dockerfile*. L’élément `.` de la commande `docker build` indique à Docker d’utiliser le dossier actif pour rechercher un *Dockerfile*. Cette commande génère l’image et crée un référentiel local nommé **myimage** qui pointe vers cette image. Une fois cette commande terminée, exécutez `docker images` pour afficher une liste des images installées :

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              38db0eb8f648        4 weeks ago         346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

Notez que les deux images partagent la même valeur **IMAGE ID**. La valeur est la même dans les deux images, car la seule commande dans le *Dockerfile* basait la nouvelle image sur une image existante. Ajoutons deux commandes au *Dockerfile*. Chaque commande crée une nouvelle couche d’image avec la commande finale représentant l’image à qui le référentiel **myimage** indique.

```dockerfile
COPY app/bin/Release/netcoreapp3.1/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

La commande `COPY` indique à Docker de copier le dossier spécifié sur votre ordinateur, dans un dossier du conteneur. Dans cet exemple, le dossier *publish* est copié vers un dossier nommé *app* dans le conteneur.

La commande suivante, `ENTRYPOINT`, indique à Docker de configurer le conteneur afin de l’exécuter comme un fichier exécutable. Au démarrage du conteneur, la commande `ENTRYPOINT` s’exécute. Lorsque cette commande se termine, le conteneur s’arrête automatiquement.

Dans votre terminal, exécutez `docker build -t myimage -f Dockerfile .` puis, une fois la commande terminée, exécutez `docker images`.

```console
> docker build -t myimage -f Dockerfile .
Sending build context to Docker daemon  1.624MB
Step 1/3 : FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
 ---> 38db0eb8f648
Step 2/3 : COPY app/bin/Release/netcoreapp3.1/publish/ app/
 ---> 37873673e468
Step 3/3 : ENTRYPOINT ["dotnet", "app/myapp.dll"]
 ---> Running in d8deb7b3aa9e
Removing intermediate container d8deb7b3aa9e
 ---> 0d602ca35c1d
Successfully built 0d602ca35c1d
Successfully tagged myimage:latest

> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              0d602ca35c1d        4 seconds ago       346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

Chaque commande dans le *Dockerfile* a généré une couche et créé une valeur **IMAGE ID**. La valeur **IMAGE ID** finale (la vôtre sera différente) est **ddcc6646461b**, et vous allez ensuite créer un conteneur basé sur cette image.

## <a name="create-a-container"></a>Créez un conteneur.

Maintenant que vous disposez d’une image qui contient votre application, vous pouvez créer un conteneur. Vous pouvez créer un conteneur de deux manières. Tout d’abord, créez un conteneur arrêté.

```console
> docker create myimage
ceda87b219a4e55e9ad5d833ee1a7ea4da21b5ea7ce5a7d08f3051152e784944
```

La commande `docker create` ci-dessus crée un conteneur basé sur l’image **myimage**. Le résultat de cette commande affiche la valeur **CONTAINER ID** (la vôtre sera différente) du conteneur créé. Pour afficher une liste de *tous* les conteneurs, utilisez la commande `docker ps -a` :

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               gallant_lehmann
```

### <a name="manage-the-container"></a>Gérer le conteneur

Chaque conteneur reçoit un nom aléatoire que vous pouvez utiliser pour faire référence à cette instance de conteneur. Par exemple, le conteneur qui a été créé a automatiquement choisi le nom **gallant_lehmann** (le vôtre sera différent) et ce nom peut être utilisé pour démarrer le conteneur. Vous remplacez le nom automatique par une valeur spécifique à l’aide du paramètre `docker create --name`.

L’exemple suivant utilise la commande `docker start` pour démarrer le conteneur, puis la commande `docker ps` pour afficher uniquement les conteneurs en cours d’exécution :

```console
> docker start gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           gallant_lehmann
```

De même, la commande `docker stop` arrêtera le conteneur. L’exemple suivant `docker stop` utilise la commande pour arrêter `docker ps` le conteneur, puis utilise la commande pour montrer qu’aucun conteneur n’est en marche :

```console
> docker stop gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a>Se connecter à un conteneur

Lorsqu’un conteneur est en cours d’exécution, vous pouvez vous connecter à ce dernier pour afficher le résultat. Utilisez les commandes `docker start` et `docker attach` pour démarrer le conteneur et observer le flux de sortie. Dans cet exemple, la frappe <kbd>CTRL C</kbd> est utilisée pour se détacher du conteneur en marche. Ce coup de clés peut effectivement mettre fin au processus dans le conteneur, ce qui arrêtera le conteneur. Le paramètre `--sig-proxy=false` garantit que la commande <kbd>Ctrl + C</kbd> n’arrêtera pas le processus dans le conteneur.

Après vous être déconnecté du conteneur, reconnectez-vous pour vérifier qu’il est toujours en cours d’exécution et de comptage.

```console
> docker start gallant_lehmann
gallant_lehmann

> docker attach --sig-proxy=false gallant_lehmann
Counter: 7
Counter: 8
Counter: 9
^C

> docker attach --sig-proxy=false gallant_lehmann
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a>Supprimer un conteneur

Dans le cadre de cet article, vous devez éviter de vous retrouver avec des conteneurs inactifs. Supprimez le conteneur que vous avez créé précédemment. Si le conteneur est en cours d’exécution, arrêtez-le.

```console
> docker stop gallant_lehmann
```

L’exemple suivant répertorie tous les conteneurs. Il utilise ensuite la commande `docker rm` pour supprimer le conteneur, puis recherche une deuxième fois si des conteneurs sont en cours d’exécution.

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             gallant_lehmann

> docker rm gallant_lehmann
gallant_lehmann

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a>Exécution unique

Docker fournit la commande `docker run` pour créer et exécuter le conteneur comme une commande unique. Cette commande vous évite de devoir exécuter `docker create` , puis `docker start`. Vous pouvez également définir cette commande pour supprimer automatiquement le conteneur lorsque le conteneur s’arrête. Par exemple, utilisez `docker run -it --rm` pour effectuer deux opérations : utiliser automatiquement le terminal actuel pour se connecter au conteneur, puis supprimer ce conteneur une fois qu’il est terminé :

```console
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

Avec `docker run -it`, la commande <kbd>CTRL + C</kbd> interrompt le processus en cours d’exécution dans le conteneur, qui à son tour, arrête le conteneur. Comme le paramètre `--rm` a été fourni, le conteneur est automatiquement supprimé lorsque le processus est arrêté. Vérifiez qu’il n’existe pas :

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a>Modifier la commande ENTRYPOINT

La commande `docker run` vous permet également de modifier la commande `ENTRYPOINT` depuis le *Dockerfile* , puis d’exécuter un autre élément, mais uniquement pour ce conteneur. Par exemple, utilisez la commande suivante pour exécuter `bash` ou `cmd.exe`. Modifiez la commande selon vos besoins.

#### <a name="windows"></a>Windows

Dans cet exemple, `ENTRYPOINT` est remplacé par `cmd.exe`. <kbd>CTRL</kbd>+<kbd>C</kbd> est pressé pour mettre fin au processus et arrêter le conteneur.

```console
> docker run -it --rm --entrypoint "cmd.exe" myimage

Microsoft Windows [Version 10.0.17763.379]
(c) 2018 Microsoft Corporation. All rights reserved.

C:\>dir
 Volume in drive C has no label.
 Volume Serial Number is 3005-1E84

 Directory of C:\

04/09/2019  08:46 AM    <DIR>          app
03/07/2019  10:25 AM             5,510 License.txt
04/02/2019  01:35 PM    <DIR>          Program Files
04/09/2019  01:06 PM    <DIR>          Users
04/02/2019  01:35 PM    <DIR>          Windows
               1 File(s)          5,510 bytes
               4 Dir(s)  21,246,517,248 bytes free

C:\>^C
```

#### <a name="linux"></a>Linux

Dans cet exemple, `ENTRYPOINT` est remplacé par `bash`. La commande `quit` est exécutée, ce qui interrompt le processus et arrête le conteneur.

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a>Commandes essentielles

Docker propose différentes commandes qui couvrent vos besoins en matière de conteneurs et d’images. Ces commandes Docker sont essentielles à la gestion de vos conteneurs :

- [docker build](https://docs.docker.com/engine/reference/commandline/build/)
- [docker run](https://docs.docker.com/engine/reference/commandline/run/)
- [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
- [docker stop](https://docs.docker.com/engine/reference/commandline/stop/)
- [docker rm](https://docs.docker.com/engine/reference/commandline/rm/)
- [docker rmi](https://docs.docker.com/engine/reference/commandline/rmi/)
- [image docker](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a>Nettoyer les ressources

Au cours de ce tutoriel, vous avez créé des conteneurs et des images. Si vous le souhaitez, supprimez ces ressources. Utilisez les commandes suivantes pour

01. Lister tous les conteneurs

    ```console
    > docker ps -a
    ```

02. Arrêtez les conteneurs en cours d’exécution. `CONTAINER_NAME` représente le nom automatiquement attribué au conteneur.

    ```console
    > docker stop CONTAINER_NAME
    ```

03. Supprimer un conteneur

    ```console
    > docker rm CONTAINER_NAME
    ```

Supprimez ensuite toutes les images que vous ne souhaitez plus conserver sur votre ordinateur. Supprimez l’image créée par votre *Dockerfile*, puis l’image .NET Core sur laquelle le *Dockerfile* était basé. Vous pouvez utiliser la valeur **IMAGE ID** ou la chaîne mise en forme **REPOSITORY:TAG**.

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

Utilisez la commande `docker images` pour afficher la liste des images installées.

> [!NOTE]
> Les fichiers image peuvent être volumineux. En règle générale, vous supprimez les conteneurs temporaires que vous avez créés lors des tests et du développement de votre app. Vous conservez normalement les images de base avec le runtime installé si vous envisagez de créer d’autres images basées sur ce runtime.

## <a name="next-steps"></a>Étapes suivantes

- [Apprenez à conteneuriser une application ASP.NET Core.](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [Essayez le tutoriel sur le microservice ASP.NET Core.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [Passez en revue les services Azure qui prennent en charge des conteneurs.](https://azure.microsoft.com/overview/containers/)
- [En savoir plus sur les commandes Dockerfile.](https://docs.docker.com/engine/reference/builder/)
- [Explorez les outils de conteneur pour Visual Studio](/visualstudio/containers/overview)
