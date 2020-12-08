---
title: Installer .NET sur RHEL-.NET
description: Montre les différentes façons d’installer le kit de développement logiciel (SDK) .NET et le Runtime .NET sur RHEL.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 0b6138185bfd3e2f50c1b31e82779165715a5b6e
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851638"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-rhel"></a>Installer le kit de développement logiciel (SDK) .NET ou le Runtime .NET sur RHEL

.NET est pris en charge sur RHEL. Cet article explique comment installer .NET sur RHEL.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a>Inscrire votre abonnement Red Hat

Pour installer .NET à partir de Red Hat sur RHEL, vous devez d’abord vous inscrire à l’aide du gestionnaire d’abonnements Red Hat. Si cela n’a pas été fait sur votre système ou si vous n’en êtes pas sûr, consultez la [documentation du produit Red Hat pour .net](https://access.redhat.com/documentation/net/5.0/).

## <a name="supported-distributions"></a>Distributions prises en charge

Le tableau suivant répertorie les versions .NET actuellement prises en charge sur RHEL 7 et RHEL 8. Ces versions restent prises en charge jusqu’à ce que la version de [.net ait atteint la fin du support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou que la version de RHEL ne soit plus prise en charge.

- Une ✔️ indique que la version de RHEL ou .NET est toujours prise en charge.
- Une ❌ indique que la version de RHEL ou de .net n’est pas prise en charge sur cette version de RHEL.
- Quand une version de RHEL et une version de .NET sont ✔️, cette combinaison de système d’exploitation et .NET est prise en charge.

| RHEL                     | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](#rhel-8-)        | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ✔️ [7](#rhel-7--net-50) | ✔️ 2,1        | ✔️ [3,1](#rhel-7--net-core-31)        | ✔️ [5,0](#rhel-7--net-50) |

Les versions suivantes de .NET ne sont plus prises en charge. Les téléchargements sont toujours publiés :

- 3.0
- 2.2
- 2.0

## <a name="remove-preview-versions"></a>Supprimer les versions préliminaires

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a>Comment installer d’autres versions

Consultez la [documentation de Red Hat pour .net](https://access.redhat.com/documentation/net/5.0/) sur les étapes requises pour installer d’autres versions de .net.

## <a name="rhel-8-"></a>✔️ RHEL 8

.NET est inclus dans les dépôts FluxApp pour RHEL 8.

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="rhel-7--net-50"></a>RHEL 7 ✔️ .NET 5,0

La commande suivante installe le `scl-utils` Package :

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a>Installer le SDK

Le kit de développement logiciel (SDK) .NET vous permet de développer des applications avec .NET. Si vous installez le kit de développement logiciel (SDK) .NET, vous n’avez pas besoin d’installer le runtime correspondant. Pour installer le kit de développement logiciel (SDK) .NET, exécutez les commandes suivantes :

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet50 -y
scl enable rh-dotnet50 bash
```

Red Hat ne recommande pas l’activation permanente `rh-dotnet50` , car cela peut affecter d’autres programmes. Si vous souhaitez activer `rh-dotnet` définitivement, ajoutez la ligne suivante à votre fichier _~ fichier/.bashrc_ .

```bash
source scl_source enable rh-dotnet50
```

### <a name="install-the-runtime"></a>Installer le runtime

Le Runtime .NET vous permet d’exécuter des applications qui ont été créées avec .NET et qui n’incluent pas le Runtime. Les commandes ci-dessous installent le runtime ASP.NET Core, qui est le runtime le plus compatible pour .NET Core. Dans votre terminal, exécutez les commandes suivantes.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet50-aspnetcore-runtime-5.0 -y
scl enable rh-dotnet50 bash
```

Red Hat ne recommande pas l’activation permanente `rh-dotnet50` , car cela peut affecter d’autres programmes. Si vous souhaitez activer `rh-dotnet50` définitivement, ajoutez la ligne suivante à votre fichier _~ fichier/.bashrc_ .

```bash
source scl_source enable rh-dotnet50
```

Comme alternative au runtime ASP.NET Core, vous pouvez installer le Runtime .NET qui n’inclut pas ASP.NET Core prise en charge : remplacez `rh-dotnet50-aspnetcore-runtime-5.0` dans les commandes ci-dessus par `rh-dotnet50-dotnet-runtime-5.0` .

## <a name="rhel-7--net-core-31"></a>RHEL 7 ✔️ .NET Core 3,1

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

La commande suivante installe le `scl-utils` Package :

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a>Installer le SDK

Kit SDK .NET Core vous permet de développer des applications avec .NET Core. Si vous installez kit SDK .NET Core, vous n’avez pas besoin d’installer le runtime correspondant. Pour installer kit SDK .NET Core, exécutez les commandes suivantes :

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

Red Hat ne recommande pas l’activation permanente `rh-dotnet31` , car cela peut affecter d’autres programmes. Par exemple, `rh-dotnet31` comprend une version de `libcurl` qui diffère de la version de base de RHEL. Cela peut entraîner des problèmes dans les programmes qui n’attendent pas une version différente de `libcurl` . Si vous souhaitez activer `rh-dotnet` définitivement, ajoutez la ligne suivante à votre fichier _~ fichier/.bashrc_ .

```bash
source scl_source enable rh-dotnet31
```

### <a name="install-the-runtime"></a>Installer le runtime

Le Runtime .NET Core vous permet d’exécuter des applications qui ont été créées avec .NET Core et qui ne comportent pas le Runtime. Les commandes ci-dessous installent le runtime ASP.NET Core, qui est le runtime le plus compatible pour .NET Core. Dans votre terminal, exécutez les commandes suivantes.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

Red Hat ne recommande pas l’activation permanente `rh-dotnet31` , car cela peut affecter d’autres programmes. Par exemple, `rh-dotnet31` comprend une version de `libcurl` qui diffère de la version de base de RHEL. Cela peut entraîner des problèmes dans les programmes qui n’attendent pas une version différente de `libcurl` . Si vous souhaitez activer `rh-dotnet31` définitivement, ajoutez la ligne suivante à votre fichier _~ fichier/.bashrc_ .

```bash
source scl_source enable rh-dotnet31
```

Comme alternative au runtime ASP.NET Core, vous pouvez installer le Runtime .NET Core qui n’inclut pas la prise en charge de ASP.NET Core : remplacez `rh-dotnet31-aspnetcore-runtime-3.1` dans les commandes ci-dessus par `rh-dotnet31-dotnet-runtime-3.1` .

## <a name="snap"></a>Snap

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a>Les dépendances

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a>Installation par script

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>Installation manuelle

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>Étapes suivantes

- [Didacticiel : créer une application console avec le kit de développement logiciel (SDK) .NET à l’aide de Visual Studio Code](../tutorials/with-visual-studio-code.md)
