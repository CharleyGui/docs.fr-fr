---
title: Tutoriel Conteneuriser une application avec Docker
description: Dans ce didacticiel, vous allez apprendre à créer un conteneur pour une application .NET Core avec l’arrimeur.
ms.date: 04/27/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: b6775c760ef3f5bf1c9519430b038f149c9cf30f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538499"
---
# <a name="tutorial-containerize-a-net-core-app"></a>Didacticiel : conteneur d’une application .NET Core

Dans ce didacticiel, vous allez apprendre à créer un conteneur pour une application .NET Core avec l’arrimeur. Les conteneurs présentent de nombreuses fonctionnalités et avantages, tels que la mise en place d’une infrastructure immuable, la fourniture d’une architecture portable et l’évolutivité. L’image vous permettra de créer des conteneurs pour votre environnement de développement local, votre cloud privé ou votre cloud public.

Dans ce tutoriel, vous allez :

> [!div class="checklist"]
>
> - Créer et publier une application .NET Core simple
> - Créer et configurer un Dockerfile pour .NET Core
> - Générer une image Docker
> - Créer et exécuter un conteneur Docker

Vous découvrirez la création d’un conteneur Docker et les tâches de déploiement pour une application .NET Core. La *plateforme d’ancrage* utilise le *moteur* de l’ancrage pour générer et empaqueter rapidement des applications en tant qu’images de l' *ancrage*. Ces images sont écrites au format *Dockerfile* pour être déployées et exécutées dans un conteneur en couches.

> [!NOTE]
> Ce didacticiel ne concerne **pas** les applications ASP.net core. Si vous utilisez ASP.NET Core, consultez le didacticiel [apprendre à déconteneurr une application ASP.net Core](/aspnet/core/host-and-deploy/docker/building-net-docker-images) .

## <a name="prerequisites"></a>Prérequis

Installez les éléments requis suivants :

- [SDK .NET Core 3,1](https://dotnet.microsoft.com/download)\
Si .NET Core est installé, utilisez la commande `dotnet --info` pour identifier le Kit SDK que vous utilisez.
- [Dockr Community Edition](https://www.docker.com/products/docker-desktop)
- Un dossier de travail temporaire pour le *Dockerfile* et un exemple d’application .NET Core. Dans ce didacticiel, le nom *docker-Worker* est utilisé comme dossier de travail.

## <a name="create-net-core-app"></a>Créer une application .NET Core

Vous avez besoin d’une application .NET Core que le conteneur Docker exécutera. Ouvrez votre terminal, créez un dossier de travail si ce n’est déjà fait, et accédez-y. Dans le dossier de travail, exécutez la commande suivante pour créer un nouveau projet dans un sous-répertoire nommé *app*:

```dotnetcli
dotnet new console -o App -n NetCore.Docker
```

Votre arborescence de dossiers doit ressembler à ce qui suit :

```
docker-working
    └──App
        ├──NetCore.Docker.csproj
        ├──Program.cs
        └──obj
            ├──NetCore.Docker.csproj.nuget.dgspec.json
            ├──NetCore.Docker.csproj.nuget.g.props
            ├──NetCore.Docker.csproj.nuget.g.targets
            ├──project.assets.json
            └──project.nuget.cache
```

La `dotnet new` commande crée un dossier nommé *app* et génère une application console « Hello World ». Modifiez les répertoires et accédez au dossier de l' *application* , à partir de votre session terminal. Utilisez la `dotnet run` commande pour démarrer l’application. L’application s’exécute et s’affiche `Hello World!` sous la commande :

```dotnetcli
dotnet run
Hello World!
```

Le modèle par défaut crée une application qui s’imprime sur le terminal, puis se termine immédiatement. Pour ce tutoriel, vous utiliserez une application qui effectue une boucle indéfiniment. Ouvrez le fichier *Program.cs* dans un éditeur de texte.

> [!TIP]
> Si vous utilisez Visual Studio Code, à partir de la session Terminal précédente, tapez la commande suivante :
>
> ```console
> code .
> ```
>
> Le dossier d' *application* qui contient le projet s’ouvre dans Visual Studio code.

Le *Program.cs* doit ressembler au code C# suivant :

```csharp
using System;

namespace NetCore.Docker
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
using System.Threading.Tasks;

namespace NetCore.Docker
{
    class Program
    {
        static async Task Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while (max == -1 || counter < max)
            {
                Console.WriteLine($"Counter: {++counter}");
                await Task.Delay(1000);
            }
        }
    }
}
```

Enregistrez le fichier et effectuez un nouveau avec `dotnet run`. N’oubliez pas que cette application s’exécute indéfiniment. Utilisez la commande Annuler <kbd>Ctrl + C</kbd> pour l’arrêter. Voici un exemple de sortie :

```dotnetcli
dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

Si vous envoyez un nombre à l’application sur la ligne de commande, l’application comptera uniquement jusqu’à ce montant puis se fermera. Effectuez un test avec `dotnet run -- 5` pour compter jusqu’à cinq.

> [!IMPORTANT]
> Tous les paramètres après `--` sont transmis à votre application au lieu d’être transmis à la commande `dotnet run`.

## <a name="publish-net-core-app"></a>Publier une application .NET Core

Avant d’ajouter l’application .NET Core à l’image de l’ancrer, vous devez d’abord la publier. Il est préférable que le conteneur exécute la version publiée de l’application. Pour publier l’application, exécutez la commande suivante :

```dotnetcli
dotnet publish -c Release
```

Cette commande compile votre application dans le dossier *publish*. Le chemin du dossier *publish* à partir du dossier de travail doit être `.\App\bin\Release\netcoreapp3.1\publish\`

#### <a name="windows"></a>[Windows](#tab/windows)

Dans le dossier de l' *application* , accédez à la liste des répertoires du dossier de publication pour vérifier que le fichier de *NetCore.Docker.dll* a été créé.

```powershell
dir .\bin\Release\netcoreapp3.1\publish\

    Directory: C:\Users\dapine\App\bin\Release\netcoreapp3.1\publish

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        4/27/2020   8:27 AM            434 NetCore.Docker.deps.json
-a----        4/27/2020   8:27 AM           6144 NetCore.Docker.dll
-a----        4/27/2020   8:27 AM         171520 NetCore.Docker.exe
-a----        4/27/2020   8:27 AM            860 NetCore.Docker.pdb
-a----        4/27/2020   8:27 AM            154 NetCore.Docker.runtimeconfig.json
```

#### <a name="linux"></a>[Linux](#tab/linux)

Utilisez la `ls` commande pour obtenir une liste de répertoires et vérifier que le fichier *NetCore.Docker.dll* a été créé.

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
```

---

## <a name="create-the-dockerfile"></a>Créer le Dockerfile

Le fichier *Dockerfile* est utilisé par la commande `docker build` pour créer une image de conteneur. Ce fichier est un fichier texte nommé *fichier dockerfile* qui n’a pas d’extension.

Créez un fichier nommé *fichier dockerfile* dans le répertoire contenant le fichier *. csproj* et ouvrez-le dans un éditeur de texte. Ce didacticiel utilise l’image d’exécution ASP.NET Core (qui contient l’image du Runtime .NET Core) et correspond à l’application console .NET Core.

```dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
```

> [!NOTE]
> L’image ASP.NET Core Runtime est utilisée intentionnellement ici, bien que l' `mcr.microsoft.com/dotnet/core/runtime:3.1` image puisse avoir été utilisée.

Le `FROM` mot clé requiert un nom d’image de conteneur d’ancrage complet. Le Container Registry Microsoft (mcr.microsoft.com) est un syndicat de l’arrimeur d’ancrage, qui héberge des conteneurs accessibles publiquement. Le `dotnet/core` segment est le référentiel de conteneurs, où le `aspnet` segment est le nom de l’image de conteneur. L’image est marquée avec `3.1` , qui est utilisé pour le contrôle de version. Par conséquent, `mcr.microsoft.com/dotnet/core/aspnet:3.1` est le Runtime .net Core 3,1. Veillez à extraire la version du runtime qui correspond au runtime ciblé par votre kit de développement logiciel (SDK). Par exemple, l’application créée dans la section précédente utilisait le kit de développement logiciel (SDK) .NET Core 3,1 et l’image de base référencée dans le *fichier dockerfile* est marquée avec **3,1**.

Enregistrez le fichier *Dockerfile*. La structure de répertoires du dossier de travail doit ressembler à ce qui suit. Certains fichiers et dossiers de niveau supérieur ont été omis pour économiser de l’espace dans l’article :

```
docker-working
    └──App
        ├──Dockerfile
        ├──NetCore.Docker.csproj
        ├──Program.cs
        ├──bin
        │   └──Release
        │       └──netcoreapp3.1
        │           └──publish
        │               ├──NetCore.Docker.deps.json
        │               ├──NetCore.Docker.exe
        │               ├──NetCore.Docker.dll
        │               ├──NetCore.Docker.pdb
        │               └──NetCore.Docker.runtimeconfig.json
        └──obj
            └──...
```

Dans votre terminal, exécutez la commande suivante :

```console
docker build -t counter-image -f Dockerfile .
```

Docker traitera chaque ligne du *Dockerfile*. L’élément `.` de la commande `docker build` indique à Docker d’utiliser le dossier actif pour rechercher un *Dockerfile*. Cette commande génère l’image et crée un référentiel local nommé **Counter-image** qui pointe vers cette image. Une fois cette commande terminée, exécutez `docker images` pour afficher une liste des images installées :

```console
docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              e6780479db63        4 days ago          190MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 e6780479db63        4 days ago          190MB
```

Notez que les deux images partagent la même valeur **IMAGE ID**. La valeur est la même dans les deux images, car la seule commande dans le *Dockerfile* basait la nouvelle image sur une image existante. Nous allons ajouter trois commandes au *fichier dockerfile*. Chaque commande crée une nouvelle couche d’image avec la commande finale représentant le point d’entrée de dépôt d' **image de compteur** vers.

```dockerfile
COPY bin/Release/netcoreapp3.1/publish/ App/
WORKDIR /App
ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
```

La commande `COPY` indique à Docker de copier le dossier spécifié sur votre ordinateur, dans un dossier du conteneur. Dans cet exemple, le dossier *Publish* est copié dans un dossier nommé *app* dans le conteneur.

La `WORKDIR` commande modifie le **répertoire actif** à l’intérieur du conteneur en *app*.

La commande suivante, `ENTRYPOINT`, indique à Docker de configurer le conteneur afin de l’exécuter comme un fichier exécutable. Au démarrage du conteneur, la commande `ENTRYPOINT` s’exécute. Lorsque cette commande se termine, le conteneur s’arrête automatiquement.

Dans votre terminal, exécutez `docker build -t counter-image -f Dockerfile .` puis, une fois la commande terminée, exécutez `docker images`.

```console
docker build -t counter-image -f Dockerfile .
Sending build context to Docker daemon  1.117MB
Step 1/4 : FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
 ---> e6780479db63
Step 2/4 : COPY bin/Release/netcoreapp3.1/publish/ App/
 ---> d1732740eed2
Step 3/4 : WORKDIR /App
 ---> Running in b1701a42f3ff
Removing intermediate container b1701a42f3ff
 ---> 919aab5b95e3
Step 4/4 : ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
 ---> Running in c12aebd26ced
Removing intermediate container c12aebd26ced
 ---> cd11c3df9b19
Successfully built cd11c3df9b19
Successfully tagged counter-image:latest

docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              cd11c3df9b19        41 seconds ago      190MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 e6780479db63        4 days ago          190MB
```

Chaque commande dans le *Dockerfile* a généré une couche et créé une valeur **IMAGE ID**. L’ID de l' **image** finale (la vôtre sera différente) est **cd11c3df9b19** et suivant, vous allez créer un conteneur basé sur cette image.

## <a name="create-a-container"></a>Créez un conteneur.

Maintenant que vous disposez d’une image qui contient votre application, vous pouvez créer un conteneur. Vous pouvez créer un conteneur de deux manières. Tout d’abord, créez un conteneur arrêté.

```console
docker create --name core-counter counter-image
0f281cb3af994fba5d962cc7d482828484ea14ead6bfe386a35e5088c0058851
```

La `docker create` commande ci-dessus crée un conteneur basé sur l’image **Counter-image** . Le résultat de cette commande affiche la valeur **CONTAINER ID** (la vôtre sera différente) du conteneur créé. Pour afficher une liste de *tous* les conteneurs, utilisez la commande `docker ps -a` :

```console
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED           STATUS     PORTS    NAMES
0f281cb3af99    counter-image    "dotnet NetCore.Dock…"    40 seconds ago    Created             core-counter
```

### <a name="manage-the-container"></a>Gérer le conteneur

Le conteneur a été créé avec un nom spécifique `core-counter` , ce nom est utilisé pour gérer le conteneur. L’exemple suivant utilise la commande `docker start` pour démarrer le conteneur, puis la commande `docker ps` pour afficher uniquement les conteneurs en cours d’exécution :

```console
docker start core-counter
core-counter

docker ps
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS          PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    2 minutes ago    Up 11 seconds            core-counter
```

De même, la commande `docker stop` arrêtera le conteneur. L’exemple suivant utilise la `docker stop` commande pour arrêter le conteneur, puis utilise la `docker ps` commande pour indiquer qu’aucun conteneur n’est en cours d’exécution :

```console
docker stop core-counter
core-counter

docker ps
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="connect-to-a-container"></a>Se connecter à un conteneur

Lorsqu’un conteneur est en cours d’exécution, vous pouvez vous connecter à ce dernier pour afficher le résultat. Utilisez les commandes `docker start` et `docker attach` pour démarrer le conteneur et observer le flux de sortie. Dans cet exemple, la combinaison de touches <kbd>Ctrl + C</kbd> est utilisée pour se détacher du conteneur en cours d’exécution. Cette séquence de touches met fin au processus dans le conteneur, sauf spécification contraire, qui arrête le conteneur. Le `--sig-proxy=false` paramètre garantit que <kbd>Ctrl + C</kbd> n’arrête pas le processus dans le conteneur.

Après vous être déconnecté du conteneur, reconnectez-vous pour vérifier qu’il est toujours en cours d’exécution et de comptage.

```console
docker start core-counter
core-counter

docker attach --sig-proxy=false core-counter
Counter: 7
Counter: 8
Counter: 9
^C

docker attach --sig-proxy=false core-counter
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a>Supprimer un conteneur

Dans le cadre de cet article, vous devez éviter de vous retrouver avec des conteneurs inactifs. Supprimez le conteneur que vous avez créé précédemment. Si le conteneur est en cours d’exécution, arrêtez-le.

```console
docker stop core-counter
```

L’exemple suivant répertorie tous les conteneurs. Il utilise ensuite la commande `docker rm` pour supprimer le conteneur, puis recherche une deuxième fois si des conteneurs sont en cours d’exécution.

```console
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS                        PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    7 minutes ago    Exited (143) 20 seconds ago            core-counter

docker rm core-counter
core-counter

docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="single-run"></a>Exécution unique

Docker fournit la commande `docker run` pour créer et exécuter le conteneur comme une commande unique. Cette commande vous évite de devoir exécuter `docker create` , puis `docker start`. Vous pouvez également définir cette commande pour supprimer automatiquement le conteneur lorsque le conteneur s’arrête. Par exemple, utilisez `docker run -it --rm` pour effectuer deux opérations : utiliser automatiquement le terminal actuel pour se connecter au conteneur, puis supprimer ce conteneur une fois qu’il est terminé :

```console
docker run -it --rm counter-image
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

Le conteneur transmet également des paramètres dans l’exécution de l’application .NET Core. Pour ordonner à l’application .NET Core de compter uniquement jusqu’à 3 passe 3.

```console
docker run -it --rm counter-image 3
Counter: 1
Counter: 2
Counter: 3
```

Avec `docker run -it` , la commande <kbd>Ctrl + C</kbd> arrête le processus en cours d’exécution dans le conteneur qui, à son tour, arrête le conteneur. Comme le paramètre `--rm` a été fourni, le conteneur est automatiquement supprimé lorsque le processus est arrêté. Vérifiez qu’il n’existe pas :

```console
docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="change-the-entrypoint"></a>Modifier la commande ENTRYPOINT

La commande `docker run` vous permet également de modifier la commande `ENTRYPOINT` depuis le *Dockerfile* , puis d’exécuter un autre élément, mais uniquement pour ce conteneur. Par exemple, utilisez la commande suivante pour exécuter `bash` ou `cmd.exe`. Modifiez la commande selon vos besoins.

#### <a name="windows"></a>[Windows](#tab/windows)

Dans cet exemple, `ENTRYPOINT` est remplacé par `cmd.exe`. Appuyez sur <kbd>Ctrl + C</kbd> pour terminer le processus et arrêter le conteneur.

```console
docker run -it --rm --entrypoint "cmd.exe" counter-image

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

#### <a name="linux"></a>[Linux](#tab/linux)

Dans cet exemple, `ENTRYPOINT` est remplacé par `bash`. La commande `exit` est exécutée, ce qui interrompt le processus et arrête le conteneur.

```bash
docker run -it --rm --entrypoint "bash" counter-image
root@b735b9799abf:/App# ls
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.exe  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
root@b735b9799abf:/App# dotnet NetCore.Docker.dll 3
Counter: 1
Counter: 2
Counter: 3
root@b735b9799abf:/App# exit
exit
```

---

## <a name="essential-commands"></a>Commandes essentielles

L’ancrage possède de nombreuses commandes différentes qui créent, gèrent et interagissent avec les conteneurs et les images. Ces commandes Docker sont essentielles à la gestion de vos conteneurs :

- [docker build](https://docs.docker.com/engine/reference/commandline/build/)
- [docker run](https://docs.docker.com/engine/reference/commandline/run/)
- [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
- [docker stop](https://docs.docker.com/engine/reference/commandline/stop/)
- [docker rm](https://docs.docker.com/engine/reference/commandline/rm/)
- [docker rmi](https://docs.docker.com/engine/reference/commandline/rmi/)
- [image de l’ancrage](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a>Nettoyer les ressources

Au cours de ce didacticiel, vous avez créé des conteneurs et des images. Si vous le souhaitez, supprimez ces ressources. Utilisez les commandes suivantes pour

01. Lister tous les conteneurs

    ```console
    docker ps -a
    ```

02. Arrêtez les conteneurs qui s’exécutent par leur nom.

    ```console
    docker stop counter-image
    ```

03. Supprimer un conteneur

    ```console
    docker rm counter-image
    ```

Supprimez ensuite toutes les images que vous ne souhaitez plus conserver sur votre ordinateur. Supprimez l’image créée par votre *Dockerfile*, puis l’image .NET Core sur laquelle le *Dockerfile* était basé. Vous pouvez utiliser la valeur **IMAGE ID** ou la chaîne mise en forme **REPOSITORY:TAG**.

```console
docker rmi counter-image:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

Utilisez la commande `docker images` pour afficher la liste des images installées.

> [!TIP]
> Les fichiers image peuvent être volumineux. En règle générale, vous supprimez les conteneurs temporaires que vous avez créés lors des tests et du développement de votre app. Vous conservez normalement les images de base avec le runtime installé si vous envisagez de créer d’autres images basées sur ce runtime.

## <a name="next-steps"></a>Étapes suivantes

- [Apprenez à conteneuriser une application ASP.NET Core.](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [Essayez le tutoriel sur le microservice ASP.NET Core.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [Passez en revue les services Azure qui prennent en charge des conteneurs.](https://azure.microsoft.com/overview/containers/)
- [En savoir plus sur les commandes Dockerfile.](https://docs.docker.com/engine/reference/builder/)
- [Explorez les outils de conteneur pour Visual Studio](/visualstudio/containers/overview)
