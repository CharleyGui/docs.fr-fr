---
title: Installer .NET Core sur SLES 12 - gestionnaire de paquets - .NET Core
description: Utilisez un gestionnaire de paquets pour installer .NET Core SDK et l’exécution sur SLES 12.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 8358107c682274fc2b75bf72689eaa4b168a86c5
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134216"
---
# <a name="sles-12-package-manager---install-net-core"></a>SLES 12 Package Manager - Installer .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Cet article décrit comment utiliser un gestionnaire de paquets pour installer .NET Core sur SLES 12.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-microsoft-key-and-feed"></a>Inscrire la clé et le flux Microsoft

Avant d’installer .NET, vous devrez :

- Enregistrez la clé Microsoft.
- Enregistrez le référentiel du produit.
- Installer les dépendances requises.

Vous ne devez faire ces opérations qu’une seule fois par machine.

Ouvrez un terminal et exécutez la commande suivante.

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a>Installer le kit de développement logiciel (SDK) .NET Core

Mettre à jour les produits disponibles pour l’installation, puis installer le .NET Core SDK. Dans votre terminal, exécutez la commande suivante.

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>Installer le temps d’exécution ASP.NET Core

Mettre à jour les produits disponibles pour l’installation, puis installer le ASP.NET’heure d’exécution. Dans votre terminal, exécutez la commande suivante.

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Installer le temps d’exécution .NET Core

Mettre à jour les produits disponibles pour l’installation, puis installer le temps d’exécution .NET Core. Dans votre terminal, exécutez la commande suivante.

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>Comment installer d’autres versions

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Dépanner le gestionnaire de paquets

Cette section fournit des informations sur les erreurs courantes que vous pouvez obtenir lors de l’utilisation du gestionnaire de paquet pour installer .NET Core.

### <a name="failed-to-fetch"></a>N’est pas allé chercher

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
