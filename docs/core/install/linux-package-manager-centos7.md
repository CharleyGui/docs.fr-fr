---
title: Installer .NET Core sur CentOS 7-gestionnaire de package-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur CentOS 7.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.openlocfilehash: 62b07342197addaa5c7d962c08c4ff1d7121eff8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451079"
---
# <a name="centos-7-package-manager---install-net-core"></a>Gestionnaire de package CentOS 7-installer .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur CentOS 7. Si vous installez le runtime, nous vous suggérons d’installer le [runtime ASP.net Core](#install-the-aspnet-core-runtime), car il comprend des runtimes .net Core et ASP.net core.

## <a name="register-microsoft-key-and-feed"></a>Inscrire la clé et le flux Microsoft

Avant d’installer .NET, vous devez :

- Inscrire la clé Microsoft
- inscrire le dépôt du produit
- Installer les dépendances requises

Cette opération ne doit être effectuée qu’une fois par ordinateur.

Ouvrez un terminal et exécutez la commande suivante.

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a>Installer le kit SDK .NET Core

Mettez à jour les produits disponibles pour l’installation, puis installez le kit SDK .NET Core. Dans votre terminal, exécutez la commande suivante.

```bash
sudo yum install dotnet-sdk-3.0
```

## <a name="install-the-aspnet-core-runtime"></a>Installer le runtime ASP.NET Core

Mettez à jour les produits disponibles pour l’installation, puis installez le runtime ASP.NET. Dans votre terminal, exécutez la commande suivante.

```bash
sudo yum install aspnetcore-runtime-3.0
```

## <a name="install-the-net-core-runtime"></a>Installer le Runtime .NET Core

Mettez à jour les produits disponibles pour l’installation, puis installez le Runtime .NET Core. Dans votre terminal, exécutez la commande suivante.

```bash
sudo yum install dotnet-runtime-3.0
```

## <a name="how-to-install-other-versions"></a>Comment installer d’autres versions

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
