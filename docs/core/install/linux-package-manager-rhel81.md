---
title: Installer .NET Core sur Linux RHEL 8,1 Package Manager-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur RHEL 8,1.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 8674b5d9d0f0ee384ca6798a7ea699bad67c5e5e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341180"
---
# <a name="rhel-81-package-manager---install-net-core"></a>Gestionnaire de package RHEL 8,1-installer .NET Core

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur RHEL 8,1. .NET Core 3,1 n’est pas encore disponible pour RHEL 8,1.

> [!NOTE]
> RHEL 8,0 n’inclut pas .NET Core 3,0. Utilisez la commande `yum upgrade` pour effectuer une mise à jour vers RHEL 8,1.

## <a name="register-your-red-hat-subscription"></a>Inscrire votre abonnement Red Hat

Pour installer .NET Core à partir de Red Hat sur RHEL, vous devez d’abord vous inscrire à l’aide du gestionnaire d’abonnements Red Hat. Si cela n’a pas été fait sur votre système ou si vous n’en êtes pas sûr, consultez la [documentation du produit Red Hat pour .net Core](https://access.redhat.com/documentation/net_core/).

## <a name="install-the-net-core-sdk"></a>Installer le kit SDK .NET Core

Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le kit SDK .NET Core. Dans votre terminal, exécutez les commandes suivantes.

```bash
dnf install dotnet-sdk-3.0
scl enable dotnet-sdk-3.0 bash
```

## <a name="install-the-aspnet-core-runtime"></a>Installer le runtime ASP.NET Core

Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le runtime ASP.NET Core. Dans votre terminal, exécutez les commandes suivantes.

<!-- TODO: is this the correct value? Taken from the webpage but it doesn't have aspnet in the name -->
```bash
dnf install aspnetcore-runtime-3.0
scl enable aspnetcore-runtime-3.0 bash
```

## <a name="install-the-net-core-runtime"></a>Installer le Runtime .NET Core

Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le Runtime .NET Core. Dans votre terminal, exécutez les commandes suivantes.

```bash
sudo dnf install dotnet-runtime-3.0
scl enable dotnet-runtime-3.0 bash
```

## <a name="see-also"></a>Voir aussi

- [Utilisation de .NET Core 3,0 sur Red Hat Enterprise Linux 8](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide_for_rhel_8/gs_install_dotnet)
