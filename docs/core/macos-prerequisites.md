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
# <a name="prerequisites-for-net-core-on-macos"></a><span data-ttu-id="4db75-103">Configuration requise pour .NET Core sur macOS</span><span class="sxs-lookup"><span data-stu-id="4db75-103">Prerequisites for .NET Core on macOS</span></span>

<span data-ttu-id="4db75-104">Cet article vous présente les versions macOS et les dépendances .NET Core prises en charge nécessaires pour développer, déployer et exécuter des applications .NET Core sur des ordinateurs macOS.</span><span class="sxs-lookup"><span data-stu-id="4db75-104">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="4db75-105">Les versions de système d’exploitation et dépendances prises en charge suivantes s’appliquent aux trois méthodes de développement des applications .NET Core sur un Mac : via la [ligne de commande de votre éditeur favori](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/) et [Visual Studio pour Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="4db75-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span>

## <a name="supported-macos-versions"></a><span data-ttu-id="4db75-106">Versions macOS prises en charge</span><span class="sxs-lookup"><span data-stu-id="4db75-106">Supported macOS versions</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="4db75-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="4db75-107">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="4db75-108">.NET Core 2.x est pris en charge par les versions suivantes de macOS :</span><span class="sxs-lookup"><span data-stu-id="4db75-108">.NET Core 2.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="4db75-109">macOS 10.12 « Sierra » et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="4db75-109">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="4db75-110">Consultez [.NET Core 2.1 - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) et [.NET Core 2.2 - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation, distributions et versions pris en charge par .NET Core 2.1 et .NET Core 2.2, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.</span><span class="sxs-lookup"><span data-stu-id="4db75-110">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) and [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.1 and .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="4db75-111">Pour obtenir des liens de téléchargement et plus d’informations, consultez [Téléchargements .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) ou [Téléchargements .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="4db75-111">For download links and more information, see [.NET Core 2.2 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.2) or [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4db75-112">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4db75-112">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="4db75-113">.NET Core 1.x est pris en charge par les versions suivantes de macOS :</span><span class="sxs-lookup"><span data-stu-id="4db75-113">.NET Core 1.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="4db75-114">macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="4db75-114">macOS 10.12 "Sierra"</span></span>
* <span data-ttu-id="4db75-115">macOS 10.11 "El Capitan"</span><span class="sxs-lookup"><span data-stu-id="4db75-115">macOS 10.11 "El Capitan"</span></span>

<span data-ttu-id="4db75-116">Consultez [.NET Core 1.1 - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) et [.NET Core 1.0 - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation, distributions et versions pris en charge par .NET Core 1.1 et .NET Core 1.0, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.</span><span class="sxs-lookup"><span data-stu-id="4db75-116">See [.NET Core 1.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) and [.NET Core 1.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.1 and .NET Core 1.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="4db75-117">Pour obtenir des liens de téléchargement et plus d’informations, voir [Téléchargements .NET Core 1.1](https://dotnet.microsoft.com/download/dotnet-core/1.1) ou [Téléchargements .NET Core 1.0](https://dotnet.microsoft.com/download/dotnet-core/1.0).</span><span class="sxs-lookup"><span data-stu-id="4db75-117">For download links and more information, see [.NET Core 1.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/1.1) or [.NET Core 1.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/1.0).</span></span>

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="4db75-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="4db75-118">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="4db75-119">.NET Core 3.0 est pris en charge par les versions suivantes de macOS :</span><span class="sxs-lookup"><span data-stu-id="4db75-119">.NET Core 3.0 is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="4db75-120">macOS 10.13 « High Sierra » et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="4db75-120">macOS 10.13 "High Sierra" and later versions</span></span>

<span data-ttu-id="4db75-121">Consultez [.NET Core 3.0 - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation, distributions et versions pris en charge par .NET Core 3.0, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.</span><span class="sxs-lookup"><span data-stu-id="4db75-121">See [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="4db75-122">Pour obtenir des liens de téléchargement et plus d’informations, voir [Téléchargements .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="4db75-122">For download links and more information, see [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

---

## <a name="net-core-dependencies"></a><span data-ttu-id="4db75-123">Dépendances .NET Core</span><span class="sxs-lookup"><span data-stu-id="4db75-123">.NET Core dependencies</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="4db75-124">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="4db75-124">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="4db75-125">Téléchargez et installez le kit SDK .NET Core à partir de la page de [téléchargements .net](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="4db75-125">Download and install the .NET Core SDK from the [.NET Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="4db75-126">Si vous rencontrez des problèmes d’installation sur macOS, consultez la rubrique [Problèmes connus](https://github.com/dotnet/core/tree/master/release-notes/2.1) associée à la version installée.</span><span class="sxs-lookup"><span data-stu-id="4db75-126">If you have problems with the installation on macOS, consult the [Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.1) topic for the version you have installed.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4db75-127">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4db75-127">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="4db75-128">.NET Core 1.x nécessite OpenSSL lors d’une exécution sous macOS.</span><span class="sxs-lookup"><span data-stu-id="4db75-128">.NET Core 1.x requires OpenSSL when running on macOS.</span></span> <span data-ttu-id="4db75-129">Un moyen simple d’obtenir OpenSSL consiste à utiliser le gestionnaire de package [Homebrew (« brew »)](https://brew.sh/) pour macOS.</span><span class="sxs-lookup"><span data-stu-id="4db75-129">An easy way to obtain OpenSSL is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="4db75-130">Après avoir installé *brew*, installez OpenSSL en exécutant les commandes suivantes dans une invite de Terminal (commande) :</span><span class="sxs-lookup"><span data-stu-id="4db75-130">After installing *brew*, install OpenSSL by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

<span data-ttu-id="4db75-131">Téléchargez et installez le kit SDK .NET Core à partir de la page de [téléchargements .net](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="4db75-131">Download and install the .NET Core SDK from the [.NET Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="4db75-132">Si vous rencontrez des problèmes d’installation sur macOS, consultez les rubriques [Problèmes connus 1.0.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) et [Problèmes connus 1.0.1](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="4db75-132">If you have problems with the installation on macOS, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics.</span></span>

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="4db75-133">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="4db75-133">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="4db75-134">Téléchargez et installez le kit SDK .NET Core à partir de la page de [téléchargements .net](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="4db75-134">Download and install the .NET Core SDK from the [.NET Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="4db75-135">Si vous rencontrez des problèmes d’installation sur macOS, consultez la rubrique [Notes de publication](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) associée à la version installée.</span><span class="sxs-lookup"><span data-stu-id="4db75-135">If you have problems with the installation on macOS, consult the [Release notes](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) topic for the version you have installed.</span></span>

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a><span data-ttu-id="4db75-136">Augmentez la limite maximale d’ouverture de fichier (dans les versions .NET Core antérieures à .NET Core SDK 2.0.2)</span><span class="sxs-lookup"><span data-stu-id="4db75-136">Increase the maximum open file limit (.NET Core versions before .NET Core SDK 2.0.2)</span></span>

<span data-ttu-id="4db75-137">Dans les versions de .NET Core antérieures à .NET Core SDK 2.0.2, la limite d’ouverture de fichier par défaut sur macOS peut ne pas suffire pour certaines charges de travail .NET Core, telles que la restauration de projets ou l’exécution de tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="4db75-137">In older .NET Core versions (before .NET Core SDK 2.0.2), the default open file limit on macOS may not be sufficient for some .NET Core workloads, such as restoring projects or running unit tests.</span></span>

<span data-ttu-id="4db75-138">Vous pouvez augmenter cette limite en effectuant les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="4db75-138">You can increase this limit by following these steps:</span></span>

1. <span data-ttu-id="4db75-139">À l’aide d’un éditeur de texte, créez un fichier _/Library/LaunchDaemons/limit.maxfiles.plist_ et enregistrez le fichier avec le contenu suivant :</span><span class="sxs-lookup"><span data-stu-id="4db75-139">Using a text editor, create a new file _/Library/LaunchDaemons/limit.maxfiles.plist_, and save the file with this content:</span></span>

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

2. <span data-ttu-id="4db75-140">Dans une fenêtre de terminal, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="4db75-140">In a terminal window, run the following command:</span></span>

   ```console
   echo 'ulimit -n 2048' | sudo tee -a /etc/profile
   ```

3. <span data-ttu-id="4db75-141">Redémarrez votre Mac pour appliquer ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="4db75-141">Reboot your Mac to apply these settings.</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="4db75-142">Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="4db75-142">Visual Studio for Mac</span></span>

<span data-ttu-id="4db75-143">Vous pouvez utiliser l’éditeur de votre choix pour développer des applications .NET Core à l’aide du Kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4db75-143">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="4db75-144">Toutefois, si vous voulez développer des applications .NET Core sous Mac dans un environnement de développement intégré, vous pouvez utiliser [Visual Studio pour Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="4db75-144">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span>

<span data-ttu-id="4db75-145">Le développement .NET Core sur macOS avec Visual Studio pour Mac nécessite :</span><span class="sxs-lookup"><span data-stu-id="4db75-145">.NET Core development on macOS with Visual Studio for Mac requires:</span></span>

* <span data-ttu-id="4db75-146">Une version prise en charge du système d’exploitation macOS</span><span class="sxs-lookup"><span data-stu-id="4db75-146">A supported version of the macOS operating system</span></span>
* <span data-ttu-id="4db75-147">OpenSSL (.NET Core 1.x uniquement ; .NET Core 2.x utilise les services de sécurité disponibles en mode natif dans macOS)</span><span class="sxs-lookup"><span data-stu-id="4db75-147">OpenSSL (.NET Core 1.x only; .NET Core 2.x uses security services available natively in macOS)</span></span>
* <span data-ttu-id="4db75-148">.NET Core SDK pour Mac</span><span class="sxs-lookup"><span data-stu-id="4db75-148">.NET Core SDK for Mac</span></span>
* [<span data-ttu-id="4db75-149">Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="4db75-149">Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
