---
title: Installer .NET Core sur Ubuntu-.NET Core
description: Montre les différentes façons d’installer kit SDK .NET Core et le Runtime .NET Core sur Ubuntu.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 5c07de20110a1aecf2ec5cb9de88f204625e548d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538450"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-ubuntu"></a>Installer kit SDK .NET Core ou le Runtime .NET Core sur Ubuntu

.NET Core est pris en charge sur Ubuntu. Cet article explique comment installer .NET Core sur Ubuntu. Quand une version d’Ubuntu n’est plus prise en charge, .NET Core n’est plus pris en charge avec cette version. Toutefois, ces instructions peuvent vous aider à obtenir .NET Core s’exécutant sur ces versions, même s’il n’est pas pris en charge.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a>Distributions prises en charge

Le tableau suivant répertorie les versions de .NET Core actuellement prises en charge et les versions d’Ubuntu sur lesquelles elles sont prises en charge. Ces versions restent prises en charge jusqu’à la fin de la [prise en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de la version de .net Core ou de la version d' [Ubuntu](https://wiki.ubuntu.com/Releases).

- Une ✔️ indique que la version d’Ubuntu ou de .NET Core est toujours prise en charge.
- Une ❌ indique que la version d’Ubuntu ou de .net Core n’est pas prise en charge sur cette version d’Ubuntu.
- Quand une version d’Ubuntu et une version de .NET Core ont ✔️, cette combinaison de système d’exploitation et .NET sont prises en charge.

| Ubuntu                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (installation manuelle uniquement) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [20,04 (LTS)](#2004-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ❌[19,10](#1910-)       | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ❌ [19.04](#1904-)       | ✔️ 2,1        | ✔️ 3,1        | ❌ version préliminaire 5,0 |
| ❌ [18.10](#1810-)       | ✔️ 2,1        | ❌ 3,1        | ❌ version préliminaire 5,0 |
| ✔️ [18,04 (LTS)](#1804-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ❌[17,10](#1710-)       | ✔️ 2,1        | ❌ 3,1        | ❌ version préliminaire 5,0 |
| ❌ [17.04](#1704-)       | ✔️ 2,1        | ❌ 3,1        | ❌ version préliminaire 5,0 |
| ❌[16,10](#1610-)       | ❌ 2,1        | ❌ 3,1        | ❌ version préliminaire 5,0 |
| ✔️ [16,04 (LTS)](#1604-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |

Les versions suivantes de .NET Core ne sont plus prises en charge. Les téléchargements sont toujours publiés :

- 3.0
- 2.2
- 2.0

## <a name="how-to-install-other-versions"></a>Comment installer d’autres versions

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="2004-"></a>20,04 ✔️

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1910-"></a>19,10 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a>19,04 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a>18,10 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a>18,04 ✔️

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1710-"></a>17,10 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a>17,04 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a>16,10 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a>16,04 ✔️

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a>Kit de développement logiciel (SDK) APT Update ou Runtime

Quand une nouvelle version de correctif est disponible pour .NET Core, vous pouvez simplement la mettre à niveau via la commande APT avec les commandes suivantes :

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a>Résolution des problèmes de APT

Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation de la fonction APT pour installer .NET Core.

### <a name="unable-to-find-package"></a>Impossible de trouver le package

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a>Impossible d' \\ installer certains packages

[!INCLUDE [package-manager-failed-to-find-deb](includes/package-manager-failed-to-find-deb.md)]

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/{os-version}/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y {dotnet-package}
```

### <a name="failed-to-fetch"></a>Échec de la récupération

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a>Snap

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a>Les dépendances

Lorsque vous installez avec un gestionnaire de package, ces bibliothèques sont installées pour vous. Toutefois, si vous installez manuellement .NET Core ou si vous publiez une application autonome, vous devez vous assurer que ces bibliothèques sont installées :

- libc6
- libgcc1
- libgssapi-krb5-2
- libicu52 (pour 14.x)
- libicu55 (pour 16.x)
- libicu60 (pour 18.x)
- libicu66 (pour 20. x)
- libssl 1.0.0 (pour 14. x, 16. x)
- libssl 1.1 (pour 18. x, 20. x)
- libstdc + + 6
- zlib1g

Pour les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :

- libgdiplus (version 6.0.1 ou ultérieure)

  > [!WARNING]
  > Vous pouvez installer une version récente de *libgdiplus* en ajoutant le référentiel mono à votre système. Pour plus d'informations, consultez <https://www.mono-project.com/download/stable/>.

## <a name="scripted-install"></a>Installation par script

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>Installation manuelle

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>Étapes suivantes

- [Didacticiel : créer une application console avec kit SDK .NET Core à l’aide de Visual Studio Code](../tutorials/with-visual-studio-code.md)
