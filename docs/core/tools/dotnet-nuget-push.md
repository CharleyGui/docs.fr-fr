---
title: Commande dotnet nuget push
description: La commande dotnet nuget push exécute un envoi (push) d’un package sur le serveur et le publie.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 50a4a542c2d192bfbd927845489d04fd1b6c6cf3
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555121"
---
# <a name="dotnet-nuget-push"></a>dotnet nuget push

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 2. x et versions ultérieures

## <a name="name"></a>Nom

`dotnet nuget push` - Exécute un push d’un package sur le serveur et le publie.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output]
    [--interactive] [-k|--api-key <API_KEY>] [-n|--no-symbols true]
    [--no-service-endpoint] [-s|--source <SOURCE>] [--skip-duplicate]
    [-sk|--symbol-api-key <API_KEY>] [-ss|--symbol-source <SOURCE>]
    [-t|--timeout <TIMEOUT>]

dotnet nuget push -h|--help
```

## <a name="description"></a>Description

La commande `dotnet nuget push` exécute un push d’un package sur le serveur et le publie. La commande push utilise les informations serveur et d’identification trouvées dans le fichier ou la chaîne de fichiers de configuration NuGet du système. Pour plus d’informations sur les fichiers de configuration, consultez [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior) (Configuration du comportement de NuGet ). La configuration par défaut de NuGet est obtenue en chargeant *%AppData%\NuGet\NuGet.config* (Windows) ou *$HOME/.local/share* (Linux/macOS), puis en chargeant tout fichier *nuget.config* ou *.nuget\nuget.config* à partir de la racine du lecteur jusqu’au répertoire actif.

La commande exécute un push d’un package existant. Il ne crée pas de package. Pour créer un package, utilisez [`dotnet pack`](dotnet-pack.md) .

## <a name="arguments"></a>Arguments

- **`ROOT`**

  Spécifie le chemin de fichier au package devant faire l’objet d’un envoi (push).

## <a name="options"></a>Options

- **`-d|--disable-buffering`**

  Désactive la mise en mémoire tampon pendant le transfert push vers un serveur HTTP(S) afin de réduire l’utilisation de la mémoire.

- **`--force-english-output`**

  Force l’application à s’exécuter avec les paramètres régionaux Anglais (culture indifférente).

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`--interactive`**

  Autorise la commande pour bloquer et exige une action manuelle pour des opérations comme l'authentification. Option disponible à partir du SDK .NET Core 2.2.

- **`-k|--api-key <API_KEY>`**

  Clé d’API pour le serveur.

- **`-n|--no-symbols true`**

  N’envoie pas les symboles (même s’ils sont présents).

- **`--no-service-endpoint`**

  N’ajoute pas « api/v2/package » à l’URL source. Option disponible à partir du kit SDK .NET Core 2.1.

- **`-s|--source <SOURCE>`**

  Spécifie l’URL du serveur. Cette option est obligatoire, sauf si la valeur de configuration de `DefaultPushSource` est définie dans le fichier de configuration NuGet.

- **`--skip-duplicate`**

  Lors du push de plusieurs packages sur un serveur HTTP (S), traite toute réponse de conflit 409 comme un avertissement afin que l’envoi puisse continuer. Disponible depuis le kit de développement logiciel (SDK) .NET Core 3,1.

- **`-sk|--symbol-api-key <API_KEY>`**

  Clé d’API pour le serveur de symboles.

- **`-ss|--symbol-source <SOURCE>`**

  Spécifie l’URL du serveur de symboles.

- **`-t|--timeout <TIMEOUT>`**

  Spécifie le délai d’attente, en secondes, pour effectuer un push vers un serveur. La valeur par défaut est 300 secondes (5 minutes). Si vous spécifiez 0 (zéro seconde), la valeur par défaut s’applique.

## <a name="examples"></a>Exemples

- Envoyez *foo. nupkg* à la source push par défaut, en spécifiant une clé API :

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

- Appuyez sur *foo. nupkg* sur le serveur NuGet officiel, en spécifiant une clé API :

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://api.nuget.org/v3/index.json
  ```
  
  * Envoyez (push) *foo.nupkg* à la source de push personnalisée `https://customsource`, en spécifiant une clé API :

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

- Envoyez *foo. nupkg* vers la source de push par défaut :

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

- Envoyer *foo. Symbols. nupkg* vers la source de symboles par défaut :

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

- Envoyez *foo. nupkg* à la source de push par défaut, en spécifiant un délai de 360 seconde :

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

- Envoyer tous les fichiers *. nupkg* du répertoire actif vers la source de push par défaut :

  ```dotnetcli
  dotnet nuget push "*.nupkg"
  ```

  > [!NOTE]
  > Si cette commande ne fonctionne pas, cela peut être dû à un bogue qui existait dans les versions antérieures du SDK (Kit SDK .NET Core 2.1 et versions antérieures).
  > Pour résoudre ce problème, mettez à niveau votre version du SDK ou exécutez la commande suivante à la place : `dotnet nuget push "**/*.nupkg"`
  
  > [!NOTE]
  > Les guillemets englobantes sont requis pour les shells tels que bash qui effectuent des globbing de fichier. Pour plus d’informations, consultez [NuGet/page de démarrage # 4393](https://github.com/NuGet/Home/issues/4393#issuecomment-667618120).

- Envoyer tous les fichiers *. nupkg* même si une réponse de conflit 409 est retournée par un serveur http (S) :

  ```dotnetcli
  dotnet nuget push "*.nupkg" --skip-duplicate
  ```

- Envoyer tous les fichiers *. nupkg* du répertoire actif vers un répertoire de flux local :

  ```dotnetcli
  dotnet nuget push "*.nupkg" -s c:\mydir
  ```

  Cette commande ne stocke pas les packages dans une structure de dossiers hiérarchique, ce qui est recommandé pour optimiser les performances. Pour plus d’informations, consultez [flux locaux](/nuget/hosting-packages/local-feeds).  
