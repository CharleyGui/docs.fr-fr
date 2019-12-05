---
title: Installer .NET Core sur Linux RHEL 7 Package Manager-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur RHEL 7.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: cc7865727927eda1406da26e64b89325fd5665a4
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801961"
---
# <a name="rhel-7-package-manager---install-net-core"></a>RHEL 7 Package Manager-installer .NET Core

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur RHEL 7.

## <a name="register-your-red-hat-subscription"></a>Inscrire votre abonnement Red Hat

Pour installer .NET Core à partir de Red Hat sur RHEL, vous devez d’abord vous inscrire à l’aide du gestionnaire d’abonnements Red Hat. Si cela n’a pas été fait sur votre système ou si vous n’en êtes pas sûr, consultez la [documentation du produit Red Hat pour .net Core](https://access.redhat.com/documentation/net_core/).

## <a name="install-the-net-core-sdk"></a>Installer le kit SDK .NET Core

Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le kit SDK .NET Core. Sur votre terminal, exécutez les commandes suivantes pour activer le canal dotnet RHEL 7 et l’installer.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-aspnet-core-runtime"></a>Installer le runtime ASP.NET Core

Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le runtime ASP.NET Core. Dans votre terminal, exécutez les commandes suivantes.

<!-- TODO: is this the correct value? Taken from the webpage but it doesn't have aspnet in the name -->
```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-aspnetcore-runtime-3.0 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-net-core-runtime"></a>Installer le Runtime .NET Core

Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le Runtime .NET Core. Dans votre terminal, exécutez les commandes suivantes.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-dotnet-runtime-3.0 -y
scl enable rh-dotnet30 bash
```

## <a name="see-also"></a>Voir aussi

- [Utilisation de .NET Core 3,0 sur Red Hat Enterprise Linux 7](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide/gs_install_dotnet)
