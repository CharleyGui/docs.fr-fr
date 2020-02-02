---
title: Installer .NET Core sur Debian 9-gestionnaire de package-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur Debian 9.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 32b152ff9be5135cf0ca7f8914bc9ee4f78000be
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920849"
---
# <a name="debian-9-package-manager---install-net-core"></a>Gestionnaire de package Debian 9-installer .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur Debian 9. Si vous installez le runtime, nous vous suggérons d’installer le [runtime ASP.net Core](#install-the-aspnet-core-runtime), car il comprend des runtimes .net Core et ASP.net core.

## <a name="register-microsoft-key-and-feed"></a>Inscrire la clé et le flux Microsoft

Avant d’installer .NET, vous devez :

- Enregistrez la clé Microsoft.
- Enregistrez le dépôt du produit.
- Installez les dépendances requises.

Cette opération ne doit être effectuée qu’une fois par ordinateur.

Ouvrez un terminal et exécutez les commandes suivantes.

```bash
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a>Installer le kit SDK .NET Core

Mettez à jour les produits disponibles pour l’installation, puis installez le kit SDK .NET Core. Dans votre terminal, exécutez les commandes suivantes.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>Installer le runtime ASP.NET Core

Mettez à jour les produits disponibles pour l’installation, puis installez le runtime ASP.NET. Dans votre terminal, exécutez les commandes suivantes.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Installer le Runtime .NET Core

Mettez à jour les produits disponibles pour l’installation, puis installez le Runtime .NET Core. Dans votre terminal, exécutez les commandes suivantes.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>Comment installer d’autres versions

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Résoudre les problèmes liés au gestionnaire de package

Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation du gestionnaire de package pour installer .NET Core.

### <a name="failed-to-fetch"></a>Échec de la récupération

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
