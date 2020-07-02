---
title: Installer .NET Core sur Fedora-.NET Core
description: Montre les différentes façons d’installer kit SDK .NET Core et le Runtime .NET Core sur Fedora.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: c90c08eefa074fa139642a268f879af79d7280da
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619479"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-fedora"></a>Installer kit SDK .NET Core ou le Runtime .NET Core sur Fedora

.NET Core est pris en charge sur Fedora. Cet article explique comment installer .NET Core sur Fedora. Quand une version de Fedora n’est plus prise en charge, .NET Core n’est plus pris en charge avec cette version. Toutefois, ces instructions peuvent vous aider à obtenir .NET Core s’exécutant sur ces versions, même s’il n’est pas pris en charge.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a>Distributions prises en charge

Le tableau suivant répertorie les versions de .NET Core actuellement prises en charge et les versions de Fedora sur lesquelles elles sont prises en charge. Ces versions restent prises en charge jusqu’à la fin de la [prise en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de la version de .net Core, ou la version de [Fedora atteint la fin de vie](https://fedoraproject.org/wiki/End_of_life).

- Une ✔️ indique que la version de Fedora ou de .NET Core est toujours prise en charge.
- Une ❌ indique que la version de Fedora ou de .net Core n’est pas prise en charge sur cette version de Fedora.
- Quand une version de Fedora et une version de .NET Core ont ✔️, cette combinaison de système d’exploitation et .NET sont prises en charge.

| Fedora                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (installation manuelle uniquement) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [32](linux-fedora.md#fedora-32-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ✔️ [31](linux-fedora.md#fedora-31-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ❌ [30](linux-fedora.md#fedora-30-) | ✔️ 2,1        | ✔️ 3,1        | ❌version préliminaire 5,0 |
| ❌[29](linux-fedora.md#fedora-29-) | ✔️ 2,1        | ✔️ 3,1        | ❌version préliminaire 5,0 |
| ❌[28](linux-fedora.md#fedora-28-) | ✔️ 2,1        | ❌3,1        | ❌version préliminaire 5,0 |
| ❌[27](linux-fedora.md#fedora-27-) | ✔️ 2,1        | ❌3,1        | ❌version préliminaire 5,0 |

Les versions suivantes de .NET Core ne sont plus prises en charge. Les téléchargements sont toujours publiés :

- 3.0
- 2.2
- 2.0

## <a name="how-to-install-other-versions"></a>Comment installer d’autres versions

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="fedora-32-"></a>Fedora 32 ✔️

.NET Core 3,1 est disponible dans les référentiels de packages par défaut pour Fedora 32.

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-31-"></a>Fedora 31 ✔️

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-30-"></a>Fedora 30❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/30/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-29-"></a>Fedora 29❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

[!INCLUDE [linux-dnf-install-30](includes/linux-install-30-dnf.md)]

## <a name="fedora-28-"></a>Fedora 28❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/28/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="fedora-27-"></a>Fedora 27❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/27/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="troubleshoot-the-package-manager"></a>Résoudre les problèmes liés au gestionnaire de package

Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation du gestionnaire de package pour installer .NET Core.

### <a name="failed-to-fetch"></a>Échec de la récupération

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a>Snap

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a>Les dépendances

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a>Installation par script

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>Installation manuelle

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>Étapes suivantes

- [Didacticiel : créer une application console avec kit SDK .NET Core à l’aide de Visual Studio Code](../tutorials/with-visual-studio-code.md)
