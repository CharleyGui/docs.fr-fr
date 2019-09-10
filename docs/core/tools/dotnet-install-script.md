---
title: Scripts dotnet-install
description: Découvrez les scripts dotnet-install pour installer les outils CLI .NET Core et le runtime partagé.
ms.date: 01/16/2019
ms.openlocfilehash: 867be93b5a4c66258df438ce718dabbd4ef2891c
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849576"
---
# <a name="dotnet-install-scripts-reference"></a>Documentation sur les scripts dotnet-install

## <a name="name"></a>Nom

`dotnet-install.ps1` | `dotnet-install.sh` : script utilisé pour installer les outils .NET Core CLI et le runtime partagé.

## <a name="synopsis"></a>Résumé

Windows :

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential] [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]`

Mac OS/Linux :

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential] [--runtime-id] [--skip-non-versioned-files] [--help]`

## <a name="description"></a>Description

Les scripts `dotnet-install` sont utilisés pour effectuer une installation non administrateur du SDK .NET Core, qui inclut les outils .NET Core CLI et le runtime partagé.

Nous vous recommandons d’utiliser la version stable hébergée sur le [site web principal de .NET Core](https://dot.net). Les chemins d’accès directs aux scripts sont :

- <https://dot.net/v1/dotnet-install.sh> (bash, UNIX)
- <https://dot.net/v1/dotnet-install.ps1> (Powershell, Windows)

La principale utilité de ces scripts réside dans les scénarios d’automatisation et les installations non administrateur. Il existe deux scripts : un script PowerShell qui fonctionne sous Windows, et un autre script d’interpréteur de commandes qui fonctionne sous Linux/macOS. Les deux scripts ont le même comportement. Comme le script bash lit également les commutateurs PowerShell, vous pouvez utiliser ces derniers avec le script sur les systèmes Linux/macOS.

Les scripts d’installation téléchargent le fichier ZIP/tarball à partir des cibles de builds CLI, puis poursuivent l’installation dans l’emplacement par défaut ou dans un emplacement spécifié par `-InstallDir|--install-dir`. Par défaut, les scripts d’installation téléchargent et installent le Kit de développement logiciel (SDK). Si vous souhaitez obtenir uniquement le runtime partagé, spécifiez l’argument `--runtime`.

Par défaut, le script ajoute l’emplacement d’installation $PATH pour la session active. Remplacez ce comportement par défaut en spécifiant l’argument `--no-path`.

Avant d’exécuter le script, installez les [dépendances](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) nécessaires.

Vous pouvez installer une version spécifique à l’aide de l’argument `--version`. La version doit être spécifiée en trois parties (par exemple, 1.0.0-13232). Si aucune valeur n’est spécifiée, la version `latest` est utilisée.

## <a name="options"></a>Options

- **`-Channel <CHANNEL>`**

  Spécifie le canal source pour l’installation. Les valeurs possibles sont :

  - `Current` - Version la plus récente.
  - `LTS` - Canal de prise en charge à long terme (dernière version prise en charge).
  - Version en deux parties au format X.Y représentant une version spécifique (par exemple, `2.0` ou `1.0`).
  - Nom de la branche. Par exemple, `release/2.0.0`, `release/2.0.0-preview2` ou `master` (pour les publications de nuit).

  La valeur par défaut est `LTS`. Pour plus d’informations sur les canaux de prise en charge de .NET, consultez la page [Stratégie de prise en charge .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

- **`-Version <VERSION>`**

  Représente une version spécifique. Les valeurs possibles sont :

  - `latest` : dernière version sur le canal (utilisée avec l’option `-Channel`).
  - `coherent` : dernière version cohérente sur le canal ; utilise la dernière combinaison de packages stable (utilisée avec les options `-Channel` de nom de branche).
  - Version en trois parties au format X.Y.Z représentant une version spécifique ; remplace l’option `-Channel`. Par exemple : `2.0.0-preview2-006120`.

  Si aucune valeur n’est spécifiée, `-Version` est définie par défaut sur `latest`.

- **`-InstallDir <DIRECTORY>`**

  Spécifie le chemin d’accès de l’installation. S’il n’existe pas déjà, le répertoire est créé. La valeur par défaut est *%LocalAppData%\Microsoft\dotnet*. Les fichiers binaires sont placés directement dans ce répertoire.

- **`-Architecture <ARCHITECTURE>`**

  Architecture des fichiers binaires .NET Core à installer. Les valeurs possibles sont `<auto>`, `amd64`, `x64`, `x86`, `arm64` et `arm`. La valeur par défaut est `<auto>`, qui représente l’architecture de système d’exploitation en cours d’exécution.

- **`-SharedRuntime`**

  > [!NOTE]
  > Ce paramètre est obsolète et sera peut-être supprimé dans une future version du script. L'alternative recommandée est l’option `Runtime`.

  Installe uniquement les bits du runtime partagé et non l’intégralité du SDK. Cela équivaut à spécifier `-Runtime dotnet`.

- **`-Runtime <RUNTIME>`**

  Installe uniquement le runtime partagé et non l’intégralité du SDK. Les valeurs possibles sont :

  - `dotnet` - le runtime partagé `Microsoft.NETCore.App`.
  - `aspnetcore` - le runtime partagé `Microsoft.AspNetCore.App`.

- **`-DryRun`**

  Si cette option est définie, le script n’effectue pas l’installation. Affiche à la place la ligne de commande à utiliser pour installer la version de l’interface CLI .NET Core actuellement demandée. Par exemple, si vous spécifiez la version `latest`, elle affiche un lien avec la version spécifique, pour que cette commande puisse être utilisée de façon déterministe dans un script de génération. Elle affiche également l’emplacement du fichier binaire si vous préférez l’installer ou le télécharger vous-même.

- **`-NoPath`**

  Si cette option est définie, le dossier d’installation n’est pas exporté dans le chemin de la session actuelle. Par défaut, le script modifie le chemin, ce qui rend les outils CLI disponibles immédiatement après l’installation.

- **`-Verbose`**

  Affiche les informations de diagnostic.

- **`-AzureFeed`**

  Spécifie l’URL du flux Azure à utiliser par ce programme d’installation. Nous recommandons de ne pas modifier cette valeur. La valeur par défaut est `https://dotnetcli.azureedge.net/dotnet`.

- **`-UncachedFeed`**

  Permet de changer l’URL pour le flux non mis en cache utilisé par ce programme d’installation. Nous recommandons de ne pas modifier cette valeur.

- **`-NoCdn`**

  Désactive le téléchargement à partir d’[Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) et utilise directement le flux non mis en cache.

- **`-FeedCredential`**

  Valeur utilisée comme chaîne de requête à ajouter au flux Azure. Elle permet de changer l’URL afin d’utiliser des comptes de stockage d’objets blob non publics.

- **`-ProxyAddress`**

  Si cette option est définie, le programme d’installation utilise le proxy pendant la création de demandes web. (valide uniquement pour Windows)

- **`ProxyUseDefaultCredentials`**

  Si cette option est définie, le programme d’installation utilise les informations d’identification de l’utilisateur actuel lors de l’utilisation de l’adresse proxy. (valide uniquement pour Windows)

- **`-SkipNonVersionedFiles`**

  Ignore l’installation des fichiers sans version, notamment *dotnet.exe*, s’ils existent déjà.

- **`-Help`**

  Affiche l’aide pour le script.

## <a name="examples"></a>Exemples

- Installez la dernière version LTS (Long Term Support) à l’emplacement par défaut :

  Windows :

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  Mac OS/Linux :

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- Installez la dernière version depuis le canal 2.0 à l’emplacement spécifié :

  Windows :

  ```powershell
  ./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli
  ```

  Mac OS/Linux :

  ```bash
  ./dotnet-install.sh --channel 2.0 --install-dir ~/cli
  ```

- Installez la version 1.1.0 du runtime partagé :

  Windows :

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 1.1.0
  ```

  Mac OS/Linux :

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 1.1.0
  ```

- Obtenir le script et installer la version 2.1.2 derrière un proxy d’entreprise (Windows uniquement) :

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- Obtenir le script et installer les exemples unilignes de l’interface CLI .NET Core :

  Windows :

  ```powershell
  @powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  Mac OS/Linux :

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a>Voir aussi

- [Versions de .NET Core](https://github.com/dotnet/core/releases)
- [Archive de téléchargement de .NET Core Runtime et du Kit SDK](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
