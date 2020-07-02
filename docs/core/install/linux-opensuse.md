---
title: Installer .NET Core sur openSUSE-.NET Core
description: Montre les différentes façons d’installer kit SDK .NET Core et le Runtime .NET Core sur openSUSE.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 24f0a5b5278d038c2f941b0984efcacd91dcbe31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619466"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-opensuse"></a>Installer kit SDK .NET Core ou le Runtime .NET Core sur openSUSE

.NET Core est pris en charge sur openSUSE. Cet article explique comment installer .NET Core sur openSUSE.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a>Distributions prises en charge

Le tableau suivant répertorie les versions de .NET Core actuellement prises en charge sur openSUSE 15. Ces versions restent prises en charge jusqu’à ce que la version de [.net Core ait atteint la fin du support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou que la version de openSUSE ne soit plus prise en charge.

- Une ✔️ indique que la version de openSUSE ou de .NET Core est toujours prise en charge.
- Une ❌ indique que la version de openSUSE ou de .net Core n’est pas prise en charge sur cette version de openSUSE.
- Quand une version de openSUSE et une version de .NET Core ont ✔️, cette combinaison de système d’exploitation et .NET sont prises en charge.

| OpenSUSE                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (installation manuelle uniquement) |
|----------------------------|---------------|---------------|----------------|
| ✔️ [15](#opensuse-15-)     | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |

Les versions suivantes de .NET Core ne sont plus prises en charge. Les téléchargements sont toujours publiés :

- 3.0
- 2.2
- 2.0

## <a name="how-to-install-other-versions"></a>Comment installer d’autres versions

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="opensuse-15-"></a>openSUSE 15 ✔️

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a>Résoudre les problèmes liés au gestionnaire de package

Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation du gestionnaire de package pour installer .NET Core.

### <a name="failed-to-fetch"></a>Échec de la récupération

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a>Snap

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a>Les dépendances

Lorsque vous installez avec un gestionnaire de package, ces bibliothèques sont installées pour vous. Toutefois, si vous installez manuellement .NET Core ou si vous publiez une application autonome, vous devez vous assurer que ces bibliothèques sont installées :

- krb5
- libicu
- libopenssl1_0_0

Si la version OpenSSL de l’environnement d’exécution cible est 1,1 ou une version plus récente, vous devez installer **compat-openssl10**.

Pour plus d’informations sur les dépendances, consultez [applications Linux autonomes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

Pour les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :

- [libgdiplus (version 6.0.1 ou ultérieure)](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > Vous pouvez installer une version récente de *libgdiplus* en ajoutant le référentiel mono à votre système. Pour plus d’informations, consultez <https://www.mono-project.com/download/stable/>.

## <a name="scripted-install"></a>Installation par script

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>Installation manuelle

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>Étapes suivantes

- [Didacticiel : créer une application console avec kit SDK .NET Core à l’aide de Visual Studio Code](../tutorials/with-visual-studio-code.md)
