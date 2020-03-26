---
title: Installer .NET Core sur Ubuntu 18.04 package manager - .NET Core
description: Utilisez un gestionnaire de paquets pour installer .NET Core SDK et l’exécution sur Ubuntu 18.04.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 6265e9b3299af9b4178dbb5d5da057f98d75a63b
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134148"
---
# <a name="ubuntu-1804-package-manager---install-net-core"></a>Ubuntu 18.04 Package Manager - Installer .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Cet article décrit comment utiliser un gestionnaire de paquets pour installer .NET Core sur Ubuntu 18.04.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-microsoft-key-and-feed"></a>Inscrire la clé et le flux Microsoft

Avant d’installer .NET, vous devrez :

- Enregistrez la clé Microsoft.
- Enregistrez le référentiel du produit.
- Installer les dépendances requises.

Vous ne devez faire ces opérations qu’une seule fois par machine.

Ouvrez un terminal et exécutez les commandes suivantes.

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a>Installer le kit de développement logiciel (SDK) .NET Core

Mettre à jour les produits disponibles pour l’installation, puis installer le .NET Core SDK. Dans votre terminal, exécutez les commandes suivantes.

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> Si vous recevez un message d’erreur similaire **à Unable pour localiser le paquet dotnet-sdk-3.1**, consultez le [Dépannage de la](#troubleshoot-the-package-manager) section gestionnaire de paquet.

## <a name="install-the-aspnet-core-runtime"></a>Installer le temps d’exécution ASP.NET Core

Mettre à jour les produits disponibles pour l’installation, puis installer le ASP.NET’arrêt Core. Dans votre terminal, exécutez les commandes suivantes.

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> Si vous recevez un message d’erreur similaire **à Unable pour localiser le package aspnetcore-runtime-3.1**, consultez le [Dépannage de la](#troubleshoot-the-package-manager) section gestionnaire de paquets.

## <a name="install-the-net-core-runtime"></a>Installer le temps d’exécution .NET Core

Mettre à jour les produits disponibles pour l’installation, puis installer le temps d’exécution .NET Core. Dans votre terminal, exécutez les commandes suivantes.

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> Si vous recevez un message d’erreur similaire **à Unable pour localiser le package dotnet-runtime-3.1**, consultez le [Dépannage de la](#troubleshoot-the-package-manager) section gestionnaire de paquet.

## <a name="how-to-install-other-versions"></a>Comment installer d’autres versions

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Dépanner le gestionnaire de paquets

Cette section fournit des informations sur les erreurs courantes que vous pouvez obtenir lors de l’utilisation du gestionnaire de paquet pour installer .NET Core.

### <a name="unable-to-locate"></a>Incapable de localiser

Si vous recevez un message d’erreur similaire **à Unable pour localiser le paquet «le paquet .NET Core»,** exécutez les commandes suivantes.

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

Si cela ne fonctionne pas, vous pouvez exécuter une installation manuelle avec les commandes suivantes.

```bash
sudo apt-get install -y gpg
wget -O- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/18.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a>N’est pas allé chercher

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
