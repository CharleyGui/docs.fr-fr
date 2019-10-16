---
title: Prérequis pour .NET Core sur Linux
description: Versions Linux et dépendances .NET Core prises en charge pour développer, déployer et exécuter des applications .NET Core sur des ordinateurs Linux.
author: leecow
ms.author: leecow
ms.date: 10/11/2019
ms.openlocfilehash: bb9049059de9d8208fc92234b28acdfb3d7f0cb3
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318325"
---
# <a name="prerequisites-for-net-core-on-linux"></a>Prérequis pour .NET Core sur Linux

Cet article montre les dépendances nécessaires pour développer des applications .NET Core sur Linux. Les distributions/versions Linux et les dépendances prises en charge ci-après s’appliquent aux deux façons de développer des applications .NET Core sur Linux :

* [Ligne de commande avec votre éditeur favori](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

> [!NOTE]
> Le kit SDK .NET Core n’est pas nécessaire pour les environnements/serveurs de production. Seul le package du Runtime .NET Core est nécessaire pour les applications déployées dans des environnements de production. Le Runtime .NET Core est déployé avec les applications dans le cadre d’un déploiement autonome, mais il doit être déployé séparément pour des applications déployées qui dépendent du framework. Pour plus d’informations sur les types de déploiements autonomes et dépendants du framework, consultez [Déploiement d’applications .NET Core](./deploying/index.md). Consultez également [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) pour obtenir des instructions spécifiques.

## <a name="supported-linux-versions"></a>Versions de Linux prises en charge

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

.NET Core 3,0 traite Linux comme un système d’exploitation unique. Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge. 

Pour obtenir des liens de téléchargement et plus d’informations, voir [Téléchargements .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).

.NET Core 3,0 est pris en charge sur les distributions/versions Linux suivantes :

> [!NOTE]
> Un symbole `+` représente la version minimale.

| Système d’exploitation                             | Version               | Architectures    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6 +, 7                 | X64 |
| Oracle Linux                   | 7                     | X64 |
| CentOS                         | 7                     | X64 |
| Fedora                         | 29 +                   | X64 |
| Debian                         | 9+                    | x64, ARM32, ARM64 |
| Ubuntu                         | 16.04+                | x64, ARM32, ARM64 |
| Linux Mint                     | plus de 18 ans                   | X64 |
| openSUSE                       | plus de 15                   | X64 |
| SUSE Enterprise Linux (SLES)   | 12 SP2+               | X64 |
| Alpine Linux                   | 3.8+                  | x64, ARM64 |

Consultez [.NET Core 3.0 - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation, distributions et versions pris en charge par .NET Core 3.0, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.

Pour plus d’informations sur l’installation de .NET Core 3.0 sur ARM64, consultez [Installation de .NET Core 3.0 sur Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2.2](#tab/netcore22)

.NET Core 2,2 traite Linux comme un système d’exploitation unique. Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge.

Pour obtenir des liens de téléchargement et plus d’informations, consultez [.net Core 2,2 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.2).

.NET Core 2,2 est pris en charge sur les distributions/versions Linux suivantes :

> [!NOTE]
> Un symbole `+` représente la version minimale.

| Système d’exploitation                             |  Version                |  Architectures   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7                   | X64 |
| Oracle Linux                   |  7                      | X64 |
| CentOS                         |  7                      | X64 |
| Fedora                         |  29, 30                 | X64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16,04, 18,04, 18,10    | x64, ARM32 |
| Linux Mint                     |  17, 18                 | X64 |
| openSUSE                       |  plus de 15                    | X64 |
| SUSE Enterprise Linux (SLES)   |  12 SP2+                | X64 |
| Alpine Linux                   |  3.7 +                   | X64 |

Consultez [.net core 2,2 versions de système d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation, distributions et versions pris en charge par .net Core 2,2, versions de système d’exploitation non prises en charge et liens de stratégie de cycle de vie.

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

.NET Core 2,1 traite Linux comme un système d’exploitation unique. Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge.

Pour obtenir des liens de téléchargement et plus d’informations, consultez [.net Core 2,1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1).

.NET Core 2,1 est pris en charge sur les distributions/versions Linux suivantes :

| Système d’exploitation                             |  Version                |  Architectures   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7, 8                | X64 |
| Oracle Linux                   |  7                      | X64 |
| CentOS                         |  7                      | X64 |
| Fedora                         |  29, 30                 | X64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16,04, 18,04, 19,04    | x64, ARM32 |
| Linux Mint                     |  17, 18                 | X64 |
| openSUSE                       |  42.3+                  | X64 |
| SUSE Enterprise Linux (SLES)   |  12 SP2+                | X64 |
| Alpine Linux                   |  3.7 +                   | X64 |

Consultez [.NET Core 2.1 - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation, distributions et versions pris en charge par .NET Core 2.1, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.

---

## <a name="linux-distribution-dependencies"></a>Dépendances des distributions Linux

Les éléments suivants sont destinés à être des exemples. Les versions et les noms exacts peuvent varier légèrement sur la distribution Linux que vous choisissez.

### <a name="ubuntu"></a>Ubuntu

Les distributions Ubuntu nécessitent l’installation des bibliothèques suivantes :

* liblttng-ust0
* libcurl3 (pour 14.x et 16.x)
* libcurl4 (pour 18.x)
* libssl1.0.0
* libkrb5-3
* zlib1g
* libicu52 (pour 14.x)
* libicu55 (pour 16.x)
* libicu57 (pour 17.x)
* libicu60 (pour 18.x)

Pour les versions antérieures à .NET Core 2.1, les dépendances suivantes sont également requises :

* libunwind8
* libuuid1

Pour les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :

* libgdiplus (version 6.0.1 ou ultérieure)

> [!NOTE]
> La plupart des versions d’Ubuntu incluent une version antérieure de libgdiplus. Vous pouvez installer une version récente de libgdiplus en ajoutant le référentiel mono à votre système. Pour plus d'informations, consultez <https://www.mono-project.com/download/stable/>.

### <a name="centos-and-fedora"></a>CentOS et Fedora

Les distributions CentOS nécessitent l’installation des bibliothèques suivantes :

* lttng-ust
* libcurl
* openssl-libs
* krb5-libs
* libicu
* zlib

Utilisateurs de Fedora : si votre version d’openssl >= 1.1, vous devez installer compat-openssl10.

Pour les versions antérieures à .NET Core 2.1, les dépendances suivantes sont également requises :

* libunwind
* libuuid

Pour plus d’informations sur les dépendances, consultez [Applications Linux autonomes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) (en anglais).

Pour les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :

* libgdiplus (version 6.0.1 ou ultérieure)

> [!NOTE]
> La plupart des versions de CentOS et Fedora incluent une version antérieure de libgdiplus. Vous pouvez installer une version récente de libgdiplus en ajoutant le référentiel mono à votre système. Pour plus d'informations, consultez <https://www.mono-project.com/download/stable/>.

## <a name="installing-net-core-dependencies-with-the-native-installers"></a>Installation des dépendances .NET Core avec les programmes d’installation natifs

Les programmes d’installation natifs .NET Core sont disponibles pour les distributions/versions Linux prises en charge. Les programmes d’installation natifs requièrent un accès administrateur (sudo) au serveur. L’avantage d’utiliser un programme d’installation natif est que toutes les dépendances natives .NET Core sont installées. En outre, les programmes d’installation natifs installent le SDK .NET Core à l’échelle du système.

Sur Linux, il existe deux choix pour le package de programme d’installation :

* Utilisation d’un gestionnaire de package basé sur le flux, tel qu’apt-get pour Ubuntu, ou yum pour CentOS/RHEL.
* Utilisation des packages eux-mêmes, DEB ou RPM

### <a name="scripting-installs-with-the-net-core-installer-script"></a>Script d’installation avec le script de programme d’installation de .NET Core

Les [scripts dotnet-install](./tools/dotnet-install-script.md) sont utilisés pour effectuer une installation non administrateur de la chaîne d’outils CLI et du runtime partagé. Vous pouvez télécharger le script depuis <https://dot.net/v1/dotnet-install.sh>.

Le script installe par défaut la dernière version de « LTS », qui correspond à .NET Core 1.1. Pour installer .NET Core 2.1.x, exécutez le script avec le commutateur suivant :

```bash
./dotnet-install.sh -c Current
```

Le script bash du programme d’installation est utilisé dans les scénarios d’automatisation et dans les installations non administratives. Comme ce script lit également les commutateurs PowerShell, ces derniers peuvent être utilisés avec le script sur les systèmes Linux/OS X.

## <a name="troubleshoot"></a>Résoudre les problèmes

En cas de problème avec une installation de .NET Core sur une distribution/version de Linux prise en charge, consultez les rubriques suivantes correspondant à vos distributions/versions installées :

* [Problèmes connus avec .NET Core 3.0](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [Problèmes connus avec .NET Core 2.2](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [Problèmes connus avec .NET Core 2.1](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [Problèmes connus avec .NET Core 1.1](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [Problèmes connus avec .NET Core 1.0](https://github.com/dotnet/core/blob/master/release-notes/1.0)
