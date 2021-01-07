---
title: Installer .NET sur Fedora-.NET
description: Montre les différentes façons d’installer le kit de développement logiciel (SDK) .NET et le Runtime .NET sur Fedora.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 9dd8c6264831e2a9382960be505639f1eba95151
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970822"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-fedora"></a>Installer le kit de développement logiciel (SDK) .NET ou le Runtime .NET sur Fedora

.NET est pris en charge sur Fedora et cet article explique comment installer .NET sur Fedora. Quand une version de Fedora n’est plus prise en charge, .NET n’est plus pris en charge avec cette version.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="install-net-50"></a>Installer .NET 5,0

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

**Fedora 32**

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/32/prod.repo
```

**Fedora 33**

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/33/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="install-net-core-31"></a>Installer .NET Core 3,1

La dernière version de .NET disponible dans les référentiels de packages par défaut pour Fedora est .NET Core 3,1.

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="supported-distributions"></a>Distributions prises en charge

Le tableau suivant répertorie les versions de .NET actuellement prises en charge et les versions de Fedora sur lesquelles elles sont prises en charge. Ces versions restent prises en charge jusqu’à la [fin de la prise en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de la version de .net ou de la version de [Fedora](https://fedoraproject.org/wiki/End_of_life).

- Une ✔️ indique que la version de Fedora ou .NET est toujours prise en charge.
- Une ❌ indique que la version de Fedora ou .net n’est pas prise en charge sur cette version de Fedora.
- Quand une version de Fedora et une version de .NET sont ✔️, cette combinaison de système d’exploitation et .NET est prise en charge.

| Version .NET  | Fedora 33 ✔️ | 32 ✔️ | 31 ❌ | 30 ❌ | 28 ❌ | 28/08/03 ❌ | 26 ❌ |
| ------------  | ---------: | --: | --: | --: | --: | --: | --: |
| .NET 5.0      | ✔️        | ✔️ | ❌|❌ |❌ |❌  |❌ |
| .NET Core 3.1 | ✔️        | ✔️ | ✔️|✔️ |✔️ |❌  |❌ |
| .NET Core 2.1 | ✔️        | ✔️ | ✔️|✔️ |✔️ |✔️  |✔️ |

Les versions suivantes de .NET ne sont plus prises en charge. Les téléchargements sont toujours publiés :

- 3.0
- 2.2
- 2.0

## <a name="remove-preview-versions"></a>Supprimer les versions préliminaires

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="dependencies"></a>Dépendances

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="install-on-older-distributions"></a>Installer sur des distributions plus anciennes

Les versions antérieures de Fedora ne contiennent pas .NET Core dans les référentiels de packages par défaut. Vous pouvez installer .NET avec le [composant logiciel enfichable](linux-snap.md), via le [script _dotnet-install.sh_](linux-scripted-manual.md#scripted-install), ou utiliser le référentiel Microsoft pour installer .net :

01. Tout d’abord, ajoutez la clé de signature Microsoft à votre liste de clés approuvées.

    ```bash
    sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
    ```

02. Ensuite, ajoutez le dépôt de packages Microsoft. La source du référentiel est basée sur votre version de Fedora.

    | Version de Fedora | Référentiel de packages |
    | -------------- | ------- |
    | 31             | `https://packages.microsoft.com/config/fedora/31/prod.repo` |
    | 30             | `https://packages.microsoft.com/config/fedora/30/prod.repo` |
    | 29             | `https://packages.microsoft.com/config/fedora/29/prod.repo` |
    | 28             | `https://packages.microsoft.com/config/fedora/28/prod.repo` |
    | 27             | `https://packages.microsoft.com/config/fedora/27/prod.repo` |

    ```bash
    sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
    ```

[!INCLUDE [linux-dnf-install-31](./includes/linux-install-31-dnf.md)]

## <a name="how-to-install-other-versions"></a>Comment installer d’autres versions

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Résoudre les problèmes liés au gestionnaire de package

Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation du gestionnaire de package pour installer .NET ou .NET Core.

### <a name="unable-to-find-package"></a>Impossible de trouver le package

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a>Échec de la récupération

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="next-steps"></a>Étapes suivantes

- [Comment activer la saisie semi-automatique via la touche TAB pour .NET CLI](../tools/enable-tab-autocomplete.md)
- [Didacticiel : créer une application console avec le kit de développement logiciel (SDK) .NET à l’aide de Visual Studio Code](../tutorials/with-visual-studio-code.md)
