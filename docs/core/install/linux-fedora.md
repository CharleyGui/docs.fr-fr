---
title: Installer .NET sur Fedora-.NET
description: Montre les différentes façons d’installer le kit de développement logiciel (SDK) .NET et le Runtime .NET sur Fedora.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: f7422941af7e39d69d286a0f79920b025c1bf9c0
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031902"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-fedora"></a>Installer le kit de développement logiciel (SDK) .NET ou le Runtime .NET sur Fedora

.NET est pris en charge sur Fedora. Cet article explique comment installer .NET sur Fedora. Quand une version de Fedora n’est plus prise en charge, .NET n’est plus pris en charge avec cette version. Toutefois, ces instructions peuvent vous aider à faire fonctionner .NET sur ces versions, même si elles ne sont pas prises en charge.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a>Distributions prises en charge

Le tableau suivant répertorie les versions de .NET actuellement prises en charge et les versions de Fedora sur lesquelles elles sont prises en charge. Ces versions restent prises en charge jusqu’à la [fin de la prise en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de la version de .net ou de la version de [Fedora](https://fedoraproject.org/wiki/End_of_life).

- Une ✔️ indique que la version de Fedora ou .NET est toujours prise en charge.
- Une ❌ indique que la version de Fedora ou .net n’est pas prise en charge sur cette version de Fedora.
- Quand une version de Fedora et une version de .NET sont ✔️, cette combinaison de système d’exploitation et .NET est prise en charge.

| Fedora               | .NET Core 2.1 | .NET Core 3.1 | .NET 5,0 |
|----------------------|---------------|---------------|----------|
| ✔️ [33](#fedora-33-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ✔️ [32](#fedora-32-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ❌[31](#fedora-31-) | ✔️ 2,1        | ✔️ 3,1        | ❌ 5,0 |
| ❌ [30](#fedora-30-) | ✔️ 2,1        | ✔️ 3,1        | ❌ 5,0 |
| ❌[29](#fedora-29-) | ✔️ 2,1        | ✔️ 3,1        | ❌ 5,0 |
| ❌[28](#fedora-28-) | ✔️ 2,1        | ❌ 3,1        | ❌ 5,0 |
| ❌[27](#fedora-27-) | ✔️ 2,1        | ❌ 3,1        | ❌ 5,0 |

Les versions suivantes de .NET ne sont plus prises en charge. Les téléchargements sont toujours publiés :

- 3.0
- 2.2
- 2.0

## <a name="remove-preview-versions"></a>Supprimer les versions préliminaires

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a>Comment installer d’autres versions

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="fedora-33-"></a>Fedora 33 ✔️

> [!TIP]
> .NET Core 3,1 est disponible dans les référentiels de packages par défaut pour Fedora 33. Pour installer .NET Core 3,1, utilisez la `dnf install` commande avec le package approprié, tel que `aspnetcore-runtime-3.1` ou `dotnet-sdk-3.1` . .NET 5,0 n’est pas encore disponible dans les référentiels de packages par défaut.

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/33/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="fedora-32-"></a>Fedora 32 ✔️

> [!TIP]
> .NET Core 3,1 est disponible dans les référentiels de packages par défaut pour Fedora 32. Pour installer .NET Core 3,1, utilisez la `dnf install` commande avec le package approprié, tel que `aspnetcore-runtime-3.1` ou `dotnet-sdk-3.1` . .NET 5,0 n’est pas encore disponible dans les référentiels de packages par défaut.

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/32/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="fedora-31-"></a>Fedora 31 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-30-"></a>Fedora 30 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/30/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-29-"></a>Fedora 29 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

[!INCLUDE [linux-dnf-install-30](includes/linux-install-30-dnf.md)]

## <a name="fedora-28-"></a>Fedora 28 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/28/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="fedora-27-"></a>Fedora 27 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/27/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="troubleshoot-the-package-manager"></a>Résoudre les problèmes liés au gestionnaire de package

Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation du gestionnaire de package pour installer .NET Core.

### <a name="unable-to-find-package"></a>Impossible de trouver le package

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a>Échec de la récupération

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a>Snap

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a>Dépendances

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a>Installation par script

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>Installation manuelle

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>Étapes suivantes

- [Didacticiel : créer une application console avec le kit de développement logiciel (SDK) .NET à l’aide de Visual Studio Code](../tutorials/with-visual-studio-code.md)
