---
title: Installer .NET Core sur SLES 12-gestionnaire de package-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur SLES 12.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.openlocfilehash: 23578baacaf3b739f57bdf860d980e2921e2c7ef
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450960"
---
# <a name="sles-12-package-manager---install-net-core"></a>SLES 12 Package Manager-installer .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur SLES 12. Si vous installez le runtime, nous vous suggérons d’installer le [runtime ASP.net Core](#install-the-aspnet-core-runtime), car il comprend des runtimes .net Core et ASP.net core.

## <a name="register-microsoft-key-and-feed"></a>Inscrire la clé et le flux Microsoft

Avant d’installer .NET, vous devez :

- Inscrire la clé Microsoft
- inscrire le dépôt du produit
- Installer les dépendances requises

Cette opération ne doit être effectuée qu’une fois par ordinateur.

Ouvrez un terminal et exécutez la commande suivante.

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a>Installer le kit SDK .NET Core

Mettez à jour les produits disponibles pour l’installation, puis installez le kit SDK .NET Core. Dans votre terminal, exécutez la commande suivante.

```bash
sudo zypper install dotnet-sdk-3.0
```

## <a name="install-the-aspnet-core-runtime"></a>Installer le runtime ASP.NET Core

Mettez à jour les produits disponibles pour l’installation, puis installez le runtime ASP.NET. Dans votre terminal, exécutez la commande suivante.

```bash
sudo zypper install aspnetcore-runtime-3.0
```

## <a name="install-the-net-core-runtime"></a>Installer le Runtime .NET Core

Mettez à jour les produits disponibles pour l’installation, puis installez le Runtime .NET Core. Dans votre terminal, exécutez la commande suivante.

```bash
sudo zypper install dotnet-runtime-3.0
```

## <a name="how-to-install-other-versions"></a>Comment installer d’autres versions

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
