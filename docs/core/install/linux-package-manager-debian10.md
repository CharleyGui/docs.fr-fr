---
title: Installer .NET Core sur Debian 10 - gestionnaire de paquets - .NET Core
description: Utilisez un gestionnaire de paquets pour installer .NET Core SDK et exécuter sur Debian 10.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 94bcb493536bdee71ba83053d9e671d529226ac3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920834"
---
# <a name="debian-10-package-manager---install-net-core"></a>Debian 10 Package Manager - Installer .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Cet article décrit comment utiliser un gestionnaire de paquets pour installer .NET Core sur Debian 10. Si vous installez le temps d’exécution, nous vous suggérons d’installer le [ASP.NET’arrêt Core,](#install-the-aspnet-core-runtime)car il comprend à la fois .NET Core et ASP.NET les temps d’exécution Core.

## <a name="register-microsoft-key-and-feed"></a>Inscrire la clé et le flux Microsoft

Avant d’installer .NET, vous devrez :

- Enregistrez la clé Microsoft.
- Enregistrez le référentiel du produit.
- Installer les dépendances requises.

Vous ne devez faire ces opérations qu’une seule fois par machine.

Ouvrez un terminal et exécutez les commandes suivantes.

```bash
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/debian/10/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a>Installer le kit de développement logiciel (SDK) .NET Core

Mettre à jour les produits disponibles pour l’installation, puis installer le .NET Core SDK. Dans votre terminal, exécutez les commandes suivantes.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>Installer le temps d’exécution ASP.NET Core

Mettre à jour les produits disponibles pour l’installation, puis installer le ASP.NET’heure d’exécution. Dans votre terminal, exécutez les commandes suivantes.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Installer le temps d’exécution .NET Core

Mettre à jour les produits disponibles pour l’installation, puis installer le temps d’exécution .NET Core. Dans votre terminal, exécutez les commandes suivantes.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>Comment installer d’autres versions

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Dépanner le gestionnaire de paquets

Cette section fournit des informations sur les erreurs courantes que vous pouvez obtenir lors de l’utilisation du gestionnaire de paquet pour installer .NET Core.

### <a name="failed-to-fetch"></a>N’est pas allé chercher

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
