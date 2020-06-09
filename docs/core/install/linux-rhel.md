---
title: Installer .NET Core sur RHEL-.NET Core
description: Montre les différentes façons d’installer kit SDK .NET Core et le Runtime .NET Core sur RHEL.
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 7ae55f881cd0c877cf1db24be7a4ee23320e21a8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603040"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-rhel"></a>Installer kit SDK .NET Core ou le Runtime .NET Core sur RHEL

.NET Core est pris en charge sur RHEL. Cet article explique comment installer .NET Core sur RHEL.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a>Inscrire votre abonnement Red Hat

Pour installer .NET Core à partir de Red Hat sur RHEL, vous devez d’abord vous inscrire à l’aide du gestionnaire d’abonnements Red Hat. Si cela n’a pas été fait sur votre système ou si vous n’en êtes pas sûr, consultez la [documentation du produit Red Hat pour .net Core](https://access.redhat.com/documentation/net_core/).

## <a name="supported-distributions"></a>Distributions prises en charge

Le tableau suivant répertorie les versions de .NET Core actuellement prises en charge sur RHEL 7 et RHEL 8. Ces versions restent prises en charge jusqu’à ce que la version de [.net Core ait atteint la fin du support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou que la version de RHEL ne soit plus prise en charge.

- Une ✔️ indique que la version de RHEL ou de .NET Core est toujours prise en charge.
- Une ❌ indique que la version de RHEL ou de .net Core n’est pas prise en charge sur cette version de RHEL.
- Quand une version de RHEL et une version de .NET Core ont ✔️, cette combinaison de système d’exploitation et .NET sont prises en charge.

| RHEL                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (installation manuelle uniquement) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](#rhel-8-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ✔️ [7](#rhel-7-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |

Les versions suivantes de .NET Core ne sont plus prises en charge. Les téléchargements sont toujours publiés :

- 3.0
- 2.2
- 2.0

## <a name="how-to-install-other-versions"></a>Comment installer d’autres versions

Consultez la [documentation de Red Hat pour .net Core](https://access.redhat.com/documentation/net_core/) sur les étapes requises pour installer d’autres versions de .net core.

## <a name="rhel-8-"></a>✔️ RHEL 8

.NET Core est inclus dans les dépôts FluxApp pour RHEL 8.

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="rhel-7-"></a>✔️ RHEL 7

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

La commande suivante installe le `scl-utils` Package :

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a>Installer le Kit de développement logiciel (SDK)

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
scl enable rh-dotnet31-aspnetcore-runtime-3.1 bash
```

Red Hat ne recommande pas l’activation permanente `rh-dotnet31-aspnetcore-runtime-3.1` , car cela peut affecter d’autres programmes. Par exemple, `rh-dotnet31-aspnetcore-runtime-3.1` comprend une version de `libcurl` qui diffère de la version de base de RHEL. Cela peut entraîner des problèmes dans les programmes qui n’attendent pas une version différente de `libcurl` . Si vous souhaitez activer `rh-dotnet31-aspnetcore-runtime-3.1` définitivement, ajoutez la ligne suivante à votre fichier _~ fichier/.bashrc_ .

```bash
source scl_source enable rh-dotnet31-aspnetcore-runtime-3.1
```

Comme alternative au runtime ASP.NET Core, vous pouvez installer le Runtime .NET Core qui n’inclut pas la prise en charge de ASP.NET Core : remplacez `rh-dotnet31-aspnetcore-runtime-3.1` dans les commandes ci-dessus par `rh-dotnet31-dotnet-runtime-3.1` .

## <a name="snap"></a>Snap

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a>Dépendances

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a>Installation par script

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>Installation manuelle

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>Étapes suivantes

- [Didacticiel : créer une application console avec kit SDK .NET Core à l’aide de Visual Studio Code](../tutorials/with-visual-studio-code.md)
