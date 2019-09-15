---
title: Configuration requise pour .NET Core sur Mac
description: Versions macOS et dépendances .NET Core prises en charge pour développer, déployer et exécuter des applications .NET Core sur des ordinateurs macOS.
author: mairaw
ms.author: adegeo
ms.custom: updateeachvsrelease
ms.date: 07/13/2019
ms.openlocfilehash: d391c18a371d721419c298f2987894f16ecbd169
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969922"
---
# <a name="prerequisites-for-net-core-on-macos"></a>Configuration requise pour .NET Core sur macOS

Cet article vous présente les versions macOS et les dépendances .NET Core prises en charge nécessaires pour développer, déployer et exécuter des applications .NET Core sur des ordinateurs macOS. Les versions de système d’exploitation et dépendances prises en charge suivantes s’appliquent aux trois méthodes de développement des applications .NET Core sur un Mac : via la [ligne de commande de votre éditeur favori](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/) et [Visual Studio pour Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).

## <a name="supported-macos-versions"></a>Versions macOS prises en charge

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

.NET Core 2.x est pris en charge par les versions suivantes de macOS :

* macOS 10.12 « Sierra » et versions ultérieures

Consultez [.NET Core 2.1 - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) et [.NET Core 2.2 - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation, distributions et versions pris en charge par .NET Core 2.1 et .NET Core 2.2, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.

Pour obtenir des liens de téléchargement et plus d’informations, consultez [Téléchargements .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) ou [Téléchargements .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1).

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

.NET Core 1.x est pris en charge par les versions suivantes de macOS :

* macOS 10.12 "Sierra"
* macOS 10.11 "El Capitan"

Consultez [.NET Core 1.1 - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) et [.NET Core 1.0 - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation, distributions et versions pris en charge par .NET Core 1.1 et .NET Core 1.0, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.

Pour obtenir des liens de téléchargement et plus d’informations, voir [Téléchargements .NET Core 1.1](https://dotnet.microsoft.com/download/dotnet-core/1.1) ou [Téléchargements .NET Core 1.0](https://dotnet.microsoft.com/download/dotnet-core/1.0).

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

.NET Core 3.0 est pris en charge par les versions suivantes de macOS :

* macOS 10.13 « High Sierra » et versions ultérieures

Consultez [.NET Core 3.0 - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation, distributions et versions pris en charge par .NET Core 3.0, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.

Pour obtenir des liens de téléchargement et plus d’informations, voir [Téléchargements .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).

---

## <a name="net-core-dependencies"></a>Dépendances .NET Core

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Téléchargez et installez le kit SDK .NET Core à partir de la page de [téléchargements .net](https://dotnet.microsoft.com/download) . Si vous rencontrez des problèmes d’installation sur macOS, consultez la rubrique [Problèmes connus](https://github.com/dotnet/core/tree/master/release-notes/2.1) associée à la version installée.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

.NET Core 1.x nécessite OpenSSL lors d’une exécution sous macOS. Un moyen simple d’obtenir OpenSSL consiste à utiliser le gestionnaire de package [Homebrew (« brew »)](https://brew.sh/) pour macOS. Après avoir installé *brew*, installez OpenSSL en exécutant les commandes suivantes dans une invite de Terminal (commande) :

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

Téléchargez et installez le kit SDK .NET Core à partir de la page de [téléchargements .net](https://dotnet.microsoft.com/download) . Si vous rencontrez des problèmes d’installation sur macOS, consultez les rubriques [Problèmes connus 1.0.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) et [Problèmes connus 1.0.1](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md).

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

Téléchargez et installez le kit SDK .NET Core à partir de la page de [téléchargements .net](https://dotnet.microsoft.com/download) . Si vous rencontrez des problèmes d’installation sur macOS, consultez la rubrique [Notes de publication](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) associée à la version installée.

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a>Augmentez la limite maximale d’ouverture de fichier (dans les versions .NET Core antérieures à .NET Core SDK 2.0.2)

Dans les versions de .NET Core antérieures à .NET Core SDK 2.0.2, la limite d’ouverture de fichier par défaut sur macOS peut ne pas suffire pour certaines charges de travail .NET Core, telles que la restauration de projets ou l’exécution de tests unitaires.

Vous pouvez augmenter cette limite en effectuant les étapes suivantes :

1. À l’aide d’un éditeur de texte, créez un fichier _/Library/LaunchDaemons/limit.maxfiles.plist_ et enregistrez le fichier avec le contenu suivant :

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1.0">
      <dict>
        <key>Label</key>
        <string>limit.maxfiles</string>
        <key>ProgramArguments</key>
        <array>
          <string>launchctl</string>
          <string>limit</string>
          <string>maxfiles</string>
          <string>2048</string>
          <string>4096</string>
        </array>
        <key>RunAtLoad</key>
        <true/>
        <key>ServiceIPC</key>
        <false/>
      </dict>
    </plist>
    ```

2. Dans une fenêtre de terminal, exécutez la commande suivante :

   ```console
   echo 'ulimit -n 2048' | sudo tee -a /etc/profile
   ```

3. Redémarrez votre Mac pour appliquer ces paramètres.

## <a name="visual-studio-for-mac"></a>Visual Studio pour Mac

Vous pouvez utiliser l’éditeur de votre choix pour développer des applications .NET Core à l’aide du Kit SDK .NET Core. Toutefois, si vous voulez développer des applications .NET Core sous Mac dans un environnement de développement intégré, vous pouvez utiliser [Visual Studio pour Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).

Le développement .NET Core sur macOS avec Visual Studio pour Mac nécessite :

* Une version prise en charge du système d’exploitation macOS
* OpenSSL (.NET Core 1.x uniquement ; .NET Core 2.x utilise les services de sécurité disponibles en mode natif dans macOS)
* .NET Core SDK pour Mac
* [Visual Studio pour Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
