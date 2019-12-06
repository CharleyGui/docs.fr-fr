---
title: Installer .NET Core sur SLES 15-gestionnaire de package-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur SLES 15.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 5551ce8cffa92d4efb6bbe9db2a4887f4b26cd6e
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74836912"
---
# <a name="sles-15-package-manager---install-net-core"></a>SLES 15 Package Manager-installer .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur SLES 15. Si vous installez le runtime, nous vous suggérons d’installer le [runtime ASP.net Core](#install-the-aspnet-core-runtime), car il comprend des runtimes .net Core et ASP.net core.

## <a name="register-microsoft-key-and-feed"></a>Inscrire le flux et la clé Microsoft

Avant d’installer .NET, vous devez :

- Inscrire la clé Microsoft
- inscrire le dépôt du produit
- Installer les dépendances requises

Vous ne devez faire ces opérations qu’une seule fois par machine.

Ouvrez un terminal et exécutez la commande suivante.

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a>Installer le kit SDK .NET Core

Mettez à jour les produits disponibles pour l’installation, puis installez le kit SDK .NET Core. Dans votre terminal, exécutez la commande suivante.

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>Installer le runtime ASP.NET Core

Mettez à jour les produits disponibles pour l’installation, puis installez le runtime ASP.NET. Dans votre terminal, exécutez la commande suivante.

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Installer le Runtime .NET Core

Mettez à jour les produits disponibles pour l’installation, puis installez le Runtime .NET Core. Dans votre terminal, exécutez la commande suivante.

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>Comment installer d’autres versions

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
