---
title: Installer .NET Core sur Linux RHEL 8 package manager - .NET Core
description: Utilisez un gestionnaire de paquets pour installer .NET Core SDK et l’exécution sur RHEL 8.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 054494a9b77e1c7803e42c947e067d3eb290f73c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78849809"
---
# <a name="rhel-8-package-manager---install-net-core"></a>RHEL 8 Package Manager - Installer .NET Core

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

Cet article décrit comment utiliser un gestionnaire de paquets pour installer .NET Core sur RHEL 8.

## <a name="register-your-red-hat-subscription"></a>Enregistrez votre abonnement Red Hat

Pour installer .NET Core de Red Hat sur RHEL, vous devez d’abord vous inscrire à l’aide du Red Hat Subscription Manager. Si cela n’a pas été fait sur votre système, ou si vous n’êtes pas sûr, consultez la [documentation du produit Red Hat pour .NET Core](https://access.redhat.com/documentation/net_core/).

## <a name="install-the-net-core-sdk"></a>Installer le kit de développement logiciel (SDK) .NET Core

Après vous être inscrit auprès du Responsable De l’Abonnement, vous êtes prêt à installer et à activer le SDK .NET Core. Dans votre terminal, exécutez les commandes suivantes.

```bash
sudo dnf update
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>Installer le ASP.NET Core Runtime

Après vous être inscrit auprès du Responsable De l’Abonnement, vous êtes prêt à installer et à activer le ASP.NET Core Runtime. Dans votre terminal, exécutez les commandes suivantes.

```bash
sudo dnf update
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Installer le .NET Core Runtime

Après vous être inscrit auprès du responsable de l’abonnement, vous êtes prêt à installer et à activer le .NET Core Runtime. Dans votre terminal, exécutez les commandes suivantes.

```bash
sudo dnf update
sudo dnf install dotnet-runtime-3.1
```

## <a name="see-also"></a>Voir aussi

- [Utilisation de .NET Core 3.1 sur Red Hat Enterprise Linux 8](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/developing_.net_applications_in_rhel_8/index)
