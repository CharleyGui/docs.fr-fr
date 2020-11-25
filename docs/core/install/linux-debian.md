---
title: Installer .NET sur Debian-.NET
description: Montre les différentes façons d’installer le kit de développement logiciel (SDK) .NET et le Runtime .NET sur Debian.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 683d0a9c47edf3cf9c47426d659e778eeb6f84df
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031889"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-debian"></a>Installer le kit de développement logiciel (SDK) .NET ou le Runtime .NET sur Debian

Cet article explique comment installer .NET sur Debian. Quand une version Debian n’est plus prise en charge, .NET n’est plus pris en charge avec cette version. Toutefois, ces instructions peuvent vous aider à faire fonctionner .NET sur ces versions, même si elles ne sont pas prises en charge.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a>Distributions prises en charge

Le tableau suivant répertorie les versions de .NET actuellement prises en charge et les versions de Debian sur lesquelles elles sont prises en charge. Ces versions restent prises en charge jusqu’à la fin de la [prise en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de la version de .net ou de la version de [Debian](https://wiki.debian.org/DebianReleases).

- Une ✔️ indique que la version de Debian ou .NET est toujours prise en charge.
- Une ❌ indique que la version de Debian ou de .net n’est pas prise en charge sur cette version Debian.
- Quand une version de Debian et une version de .NET sont ✔️, cette combinaison de système d’exploitation et .NET est prise en charge.

| Debian                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5,0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [10](#debian-10-)     | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ✔️ [9](#debian-9-)       | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ❌ [8](#debian-8-)       | ✔️ 2,1        | ❌ 3,1        | ❌ 5,0 |

Les versions suivantes de .NET ne sont plus prises en charge. Les téléchargements sont toujours publiés :

- 3.0
- 2.2
- 2.0

## <a name="remove-preview-versions"></a>Supprimer les versions préliminaires

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a>Comment installer d’autres versions

[!INCLUDE [hack-pkgname](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="debian-10-"></a>✔️ Debian 10

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="debian-9-"></a>✔️ Debian 9

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="debian-8-"></a>Debian 8 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-debian.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/8/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a>Kit de développement logiciel (SDK) APT Update ou Runtime

Quand une nouvelle version de correctif est disponible pour .NET, vous pouvez simplement la mettre à niveau à l’aide de la commande APT avec les commandes suivantes :

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a>Résolution des problèmes de APT

Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation de la fonction APT pour installer .NET.

### <a name="unable-to-find-package"></a>Impossible de trouver le package

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a>Impossible d' \\ installer certains packages

[!INCLUDE [package-manager-failed-to-find-deb](includes/package-manager-failed-to-find-deb.md)]

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/{os-version}/prod.list
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

## <a name="dependencies"></a>Dépendances

Lorsque vous installez avec un gestionnaire de package, ces bibliothèques sont installées pour vous. Toutefois, si vous installez manuellement .NET Core ou si vous publiez une application autonome, vous devez vous assurer que ces bibliothèques sont installées :

- libc6
- libgcc1
- libgssapi-krb5-2
- libicu52 (pour 8. x)
- libicu57 (9. x)
- libicu63 (pour 10. x)
- libicu67 (pour 11. x)
- libssl 1.0.0 (8. x)
- libssl 1.1 (pour 9. x-11. x)
- libstdc + + 6
- zlib1g

Pour les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :

- libgdiplus (version 6.0.1 ou ultérieure)

  > [!WARNING]
  > Vous pouvez installer une version récente de *libgdiplus* en ajoutant le référentiel mono à votre système. Pour plus d’informations, consultez <https://www.mono-project.com/download/stable/>.

## <a name="scripted-install"></a>Installation par script

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>Installation manuelle

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>Étapes suivantes

- [Didacticiel : créer une application console avec le kit de développement logiciel (SDK) .NET à l’aide de Visual Studio Code](../tutorials/with-visual-studio-code.md)
