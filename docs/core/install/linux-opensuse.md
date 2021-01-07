---
title: Installer .NET sur openSUSE-.NET
description: Montre les différentes façons d’installer le kit de développement logiciel (SDK) .NET et le Runtime .NET sur openSUSE.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 7a519f19f708e1f12af1e9715bad4f38a607f9c3
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970809"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-opensuse"></a>Installer le kit de développement logiciel (SDK) .NET ou le Runtime .NET sur openSUSE

.NET est pris en charge sur openSUSE. Cet article explique comment installer .NET sur openSUSE.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a>Distributions prises en charge

Le tableau suivant répertorie les versions .NET actuellement prises en charge sur openSUSE 15. Ces versions restent prises en charge jusqu’à ce que la version de [.net ait atteint la fin du support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou que la version de openSUSE ne soit plus prise en charge.

- Une ✔️ indique que la version de openSUSE ou .NET est toujours prise en charge.
- Une ❌ indique que la version de openSUSE ou .net n’est pas prise en charge sur cette version de openSUSE.
- Quand une version de openSUSE et une version de .NET sont ✔️, cette combinaison de système d’exploitation et .NET est prise en charge.

| OpenSUSE                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|----------------------------|---------------|---------------|----------------|
| ✔️ [15](#opensuse-15-)     | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |

Les versions suivantes de .NET ne sont plus prises en charge. Les téléchargements sont toujours publiés :

- 3.0
- 2.2
- 2.0

## <a name="remove-preview-versions"></a>Supprimer les versions préliminaires

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="opensuse-15-"></a>openSUSE 15 ✔️

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="how-to-install-other-versions"></a>Comment installer d’autres versions

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Résoudre les problèmes liés au gestionnaire de package

Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation du gestionnaire de package pour installer .NET.

### <a name="unable-to-find-package"></a>Impossible de trouver le package

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a>Échec de la récupération

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a>Dépendances

Lorsque vous installez avec un gestionnaire de package, ces bibliothèques sont installées pour vous. Toutefois, si vous installez manuellement .NET ou si vous publiez une application autonome, vous devez vous assurer que ces bibliothèques sont installées :

- krb5
- libicu
- libopenssl1_0_0

Si la version OpenSSL de l’environnement d’exécution cible est 1,1 ou une version plus récente, vous devez installer **compat-openssl10**.

Pour plus d’informations sur les dépendances, consultez [applications Linux autonomes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

Pour les applications .NET qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :

- [libgdiplus (version 6.0.1 ou ultérieure)](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > Vous pouvez installer une version récente de *libgdiplus* en ajoutant le référentiel mono à votre système. Pour plus d'informations, consultez <https://www.mono-project.com/download/stable/>.

## <a name="next-steps"></a>Étapes suivantes

- [Comment activer la saisie semi-automatique via la touche TAB pour .NET CLI](../tools/enable-tab-autocomplete.md)
- [Didacticiel : créer une application console avec le kit de développement logiciel (SDK) .NET à l’aide de Visual Studio Code](../tutorials/with-visual-studio-code.md)
