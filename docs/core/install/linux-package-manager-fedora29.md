---
title: Installer .NET Core sur Fedora 29 - gestionnaire de paquets - .NET Core
description: Utilisez un gestionnaire de paquets pour installer .NET Core SDK et l’exécution sur Fedora 29.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: bf75231ddf1cbf96668e949e20b24a0c0f6b4154
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134283"
---
# <a name="fedora-29-package-manager---install-net-core"></a>Fedora 29 Package Manager - Installer .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Cet article décrit comment utiliser un gestionnaire de paquets pour installer .NET Core sur Fedora 29.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-microsoft-key-and-feed"></a>Inscrire la clé et le flux Microsoft

Avant d’installer .NET, vous devrez :

- Enregistrez la clé Microsoft.
- Enregistrez le référentiel du produit.
- Installer les dépendances requises.

Vous ne devez faire ces opérations qu’une seule fois par machine.

Ouvrez un terminal et exécutez les commandes suivantes.

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

## <a name="install-the-net-core-sdk"></a>Installer le kit de développement logiciel (SDK) .NET Core

Mettre à jour les produits disponibles pour l’installation, puis installer le .NET Core SDK. Dans votre terminal, exécutez la commande suivante.

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>Installer le temps d’exécution ASP.NET Core

Mettre à jour les produits disponibles pour l’installation, puis installer le ASP.NET’heure d’exécution. Dans votre terminal, exécutez la commande suivante.

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Installer le temps d’exécution .NET Core

Mettre à jour les produits disponibles pour l’installation, puis installer le temps d’exécution .NET Core. Dans votre terminal, exécutez la commande suivante.

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>Comment installer d’autres versions

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Dépanner le gestionnaire de paquets

Cette section fournit des informations sur les erreurs courantes que vous pouvez obtenir lors de l’utilisation du gestionnaire de paquet pour installer .NET Core.

### <a name="failed-to-fetch"></a>N’est pas allé chercher

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
