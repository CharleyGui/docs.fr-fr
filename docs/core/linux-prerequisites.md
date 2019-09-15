---
title: Prérequis pour .NET Core sur Linux
description: Versions Linux et dépendances .NET Core prises en charge pour développer, déployer et exécuter des applications .NET Core sur des ordinateurs Linux.
author: thraka
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: 5fcf931572f3c7e9b9857d2e91e9d620c7aad0bd
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969867"
---
# <a name="prerequisites-for-net-core-on-linux"></a>Prérequis pour .NET Core sur Linux

Cet article montre les dépendances nécessaires pour développer des applications .NET Core sur Linux. Les distributions/versions Linux et les dépendances prises en charge ci-après s’appliquent aux deux façons de développer des applications .NET Core sur Linux :

* [Ligne de commande avec votre éditeur favori](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

> [!NOTE]
> Le kit SDK .NET Core n’est pas nécessaire pour les environnements/serveurs de production. Seul le package du Runtime .NET Core est nécessaire pour les applications déployées dans des environnements de production. Le Runtime .NET Core est déployé avec les applications dans le cadre d’un déploiement autonome, mais il doit être déployé séparément pour des applications déployées qui dépendent du framework. Pour plus d’informations sur les types de déploiements autonomes et dépendants du framework, consultez [Déploiement d’applications .NET Core](./deploying/index.md). Consultez également [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) pour obtenir des instructions spécifiques.

## <a name="supported-linux-versions"></a>Versions de Linux prises en charge

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

.NET Core 2.x traite Linux comme un seul système d’exploitation. Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge. 

Pour obtenir des liens de téléchargement et plus d’informations, voir [Téléchargements .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) ou [Téléchargements .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1).

.NET Core 2.x est pris en charge sur les distributions/versions Linux suivantes :

* Red Hat Enterprise Linux 7, 6 - 64 bits (`x86_64` ou `amd64`)
* CentOS 7 - 64 bits (`x86_64` ou `amd64`) 
* Oracle Linux 7 - 64 bits (`x86_64` ou `amd64`) 
* Fedora 28, 27 - 64 bits (`x86_64` ou `amd64`) 
* Debian 9 (64 bits, `amd64`), 8.7 ou une version ultérieure – 64 bits (`arm32` ou `x86_64`)
* Ubuntu 18.04 (64 bits, `arm32`), 16.04, 14.04 – 64 bits (`x86_64` ou `amd64`)
* Linux Mint 18, 17 - 64 bits (`x86_64` ou `amd64`)
* openSUSE 42.3 ou version ultérieure - 64 bits (`x86_64` ou `amd64`)
* SUSE Enterprise Linux (SLES) 12 Service Pack 2 ou version ultérieure - 64 bits (`x86_64` ou `amd64`)
* Alpine Linux 3.7 ou version ultérieure - 64 bits (`x86_64` ou `amd64`)

Pour obtenir la liste complète des systèmes d’exploitation, distributions et versions pris en charge par .NET Core 2.1 et .NET Core 2.2, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie, voir [Versions des systèmes d’exploitation prises en charge par .NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) et [Versions des systèmes d’exploitation prises en charge par .NET Core 2.2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Pour obtenir des liens de téléchargement et plus d’informations, voir [Téléchargements .NET Core 1.1](https://dotnet.microsoft.com/download/dotnet-core/1.1) ou [Téléchargements .NET Core 1.0](https://dotnet.microsoft.com/download/dotnet-core/1.0).

.NET Core 1.x est pris en charge sur les distributions/versions Linux 64 bits suivantes (`x86_64` ou `amd64`) :

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* Fedora 28 (.NET Core 1.1), 27
* Debian 8.2 ou versions ultérieures
* Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04
* Linux Mint 17
* openSUSE 42.3 ou versions ultérieures (.NET Core 1.1)

Consultez [.NET Core 1.x - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation pris en charge par .NET Core 1.x, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.

# <a name="net-core-30-preview-1tabnetcore30"></a>[.NET Core 3.0 préversion 1](#tab/netcore30)

.NET Core 3.0 préversion 1 traite Linux comme un seul système d’exploitation. Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge. 

Pour obtenir des liens de téléchargement et plus d’informations, voir [Téléchargements .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).

NET Core 3.0 préversion 1 est pris en charge sur les distributions/versions Linux suivantes. 

SE                            | Version               | Architectures  
------------------------------|-----------------------|----------------
Red Hat Enterprise Linux      | 6\.                     | X64
Red Hat Enterprise Linux<br>CentOS<br>Oracle Linux  | 7                     | X64
Fedora                        | 28                    | X64
Debian                        | 9                     | x64, ARM32\*, ARM64\*
Ubuntu                        | 16.04+, 18.04+        | x64, ARM32\*, ARM64\*
Linux Mint                    | 18                    | X64
openSUSE                      | 42.3+                 | X64
SUSE Enterprise Linux (SLES)  | 12 SP2+               | X64
Alpine Linux                  | 3.8+                  | x64, ARM64

\* La prise en charge ARM32 et ARM64 commence par 9 Debian et Ubuntu 16.04. Les versions antérieures de ces distributions ne sont pas prises en charge sur les processeurs ARM.

Consultez [.NET Core 3.0 - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation, distributions et versions pris en charge par .NET Core 3.0, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.

Pour plus d’informations sur l’installation de .NET Core 3.0 sur ARM64, consultez [Installation de .NET Core 3.0 sur Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

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

## <a name="installing-net-core-dependencies-with-the-native-installers"></a>Installation des dépendances .NET Core avec les programmes d’installation natifs

Les programmes d’installation natifs .NET Core sont disponibles pour les distributions/versions Linux prises en charge. Les programmes d’installation natifs requièrent un accès administrateur (sudo) au serveur. L’avantage d’utiliser un programme d’installation natif est que toutes les dépendances natives .NET Core sont installées. En outre, les programmes d’installation natifs installent le SDK .NET Core à l’échelle du système.

Sur Linux, il existe deux choix pour le package de programme d’installation :

* Utilisation d’un gestionnaire de package basé sur le flux, tel qu’apt-get pour Ubuntu, ou yum pour CentOS/RHEL.
* Utilisation des packages eux-mêmes, DEB ou RPM

### <a name="scripting-installs-with-the-net-core-installer-script"></a>Script d’installation avec le script de programme d’installation de .NET Core

Les [scripts dotnet-install](./tools/dotnet-install-script.md) sont utilisés pour effectuer une installation non administrateur de la chaîne d’outils CLI et du runtime partagé. Vous pouvez télécharger le script depuis <https://dot.net/v1/dotnet-install.sh>.

Le script installe par défaut la dernière version de « LTS », qui correspond à .NET Core 1.1. Pour installer .NET Core 2.1.x, exécutez le script avec le commutateur suivant :

```console
./dotnet-install.sh -c Current
```

Le script bash du programme d’installation est utilisé dans les scénarios d’automatisation et dans les installations non administratives. Comme ce script lit également les commutateurs PowerShell, ces derniers peuvent être utilisés avec le script sur les systèmes Linux/OS X.

## <a name="troubleshoot"></a>Résolution des problèmes

En cas de problème avec une installation de .NET Core sur une distribution/version de Linux prise en charge, consultez les rubriques suivantes correspondant à vos distributions/versions installées :

* [Problèmes connus avec .NET Core 3.0](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [Problèmes connus avec .NET Core 2.2](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [Problèmes connus avec .NET Core 2.1](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [Problèmes connus avec .NET Core 1.1](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [Problèmes connus avec .NET Core 1.0](https://github.com/dotnet/core/blob/master/release-notes/1.0)
