---
title: .NET Core SDK et dépendances de temps d’exécution - .NET Core
description: Détaille le système d’exploitation et les conditions préalables à l’architecture CPU pour installer le SDK core .NET et l’heure d’exécution sur Windows, Linux et macOS.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca86b3c158bb38c1293cd4303dcf4c00ea9175b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157806"
---
# <a name="net-core-dependencies-and-requirements"></a>.NET Dépendances et exigences de base

Cet article détaille quels systèmes d’exploitation et l’architecture CPU sont pris en charge par .NET Core.

## <a name="supported-operating-systems"></a>Systèmes d’exploitation pris en charge

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[.NET Core 3.1](#tab/netcore31)

Les versions Windows suivantes sont prises en charge avec .NET Core 3.1:

> [!NOTE]
> Un `+` symbole représente la version minimale.

| Système d''exploitation                            | Version                        | Architectures   |
| ----------------------------- | ------------------------------ | --------------- |
| Client Windows                | 7 SP1, 8,1                    | x64, x86        |
| Windows 10 Client             | Version 1607                  | x64, x86        |
| Windows Server                | R2 2012                       | x64, x86        |
| Nano Server                   | Version 1803                  | x64, ARM32      |

Pour plus d’informations sur .NET Core 3.1 systèmes d’exploitation pris en charge, les distributions et la politique du cycle de vie, voir [.NET Core 3.1 Versions OS prises en charge](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

Les versions Windows suivantes sont prises en charge avec .NET Core 3.0:

> [!NOTE]
> Un `+` symbole représente la version minimale.

| Système d''exploitation                            | Version                        | Architectures   |
| ----------------------------- | ------------------------------ | --------------- |
| Client Windows                | 7 SP1, 8,1                    | x64, x86        |
| Windows 10 Client             | Version 1607                  | x64, x86        |
| Windows Server                | R2 2012                       | x64, x86        |
| Nano Server                   | Version 1803                  | x64, ARM32      |

Pour plus d’informations sur les systèmes d’exploitation supportés .NET Core 3.0, les distributions et la politique du cycle de vie, voir [.NET Core 3.0 Versions OS prises en charge](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

Les versions Windows suivantes sont prises en charge avec .NET Core 2.2:

> [!NOTE]
> Un `+` symbole représente la version minimale.

| Système d''exploitation                            | Version                        | Architectures   |
| ----------------------------- | ------------------------------ | --------------- |
| Client Windows                | 7 SP1, 8,1                    | x64, x86        |
| Windows 10 Client             | Version 1607                  | x64, x86        |
| Windows Server                | R2 SP1 2008                   | x64, x86        |
| Nano Server                   | Version 1803                   | x64, ARM32      |

Pour plus d’informations sur .NET Core 2.2 systèmes d’exploitation pris en charge, les distributions et la politique du cycle de vie, voir [.NET Core 2.2 Versions OS pris en charge](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

Les versions Windows suivantes sont prises en charge avec .NET Core 2.1:

> [!NOTE]
> Un `+` symbole représente la version minimale.

| Système d''exploitation                            | Version                        | Architectures   |
| ----------------------------- | ------------------------------ | --------------- |
| Client Windows                | 7 SP1, 8,1                    | x64, x86        |
| Windows 10 Client             | Version 1607                  | x64, x86        |
| Windows Server                | R2 SP1 2008                   | x64, x86        |
| Nano Server                   | Version 1803                  | x64,            |

Pour plus d’informations sur .NET Core 2.1 systèmes d’exploitation pris en charge, les distributions et la politique du cycle de vie, voir [.NET Core 2.1 Versions OS prises en charge](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a>Windows 7 / Vista / 8.1 / Serveur 2008 R2

Des dépendances supplémentaires sont nécessaires si vous installez le SDK .NET ou l’heure d’exécution sur les versions Windows suivantes :

- Windows 7 SP1
- Windows Vista SP 2
- Windows 8.1
- Windows Server 2008 R2
- Windows Server 2012 R2

Installez les éléments suivants :

- [Microsoft Visual C 2015 Red redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).
- [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

Les exigences ci-dessus sont également requises si vous tombez sur l’une des erreurs suivantes :

> Le programme ne peut pas commencer parce que *api-ms-win-crt-runtime-l1-1-0.dll* est absent de votre ordinateur. Essayez de réinstaller le programme pour résoudre ce problème.
>
> \- ou -
>
> La bibliothèque *hostfxr.dll* a été trouvée, mais le chargement de *C:\\\<path_to_app>\\hostfxr.dll* échoué.

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[.NET Core 3.1](#tab/netcore31)

.NET Core 3.1 traite Linux comme un système d’exploitation unique. Il existe une seule build Linux (par architecture de puce) pour les distributions Linux prises en charge.

.NET Core 3.1 est pris en charge sur les distributions/versions Linux suivantes :

> [!NOTE]
> Un `+` symbole représente la version minimale.

| Système d''exploitation                             | Version               | Architectures    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6, 7, 8               | x64 |
| CentOS                         | 7+                    | x64 |
| Oracle Linux                   | 7+                    | x64 |
| Fedora                         | 29 ans et plus                   | x64 |
| Debian                         | 9+                    | x64, ARM32, ARM64 |
| Ubuntu                         | 16.04+                | x64, ARM32, ARM64 |
| Linux Mint                     | 18 ans et plus                   | x64 |
| OpenSUSE                       | 15 ans et plus                   | x64 |
| SUSE Enterprise Linux (SLES)   | 12 SP2+               | x64 |
| Alpine Linux                   | 3.10                 | x64, ARM64 |

Pour plus d’informations sur .NET Core 3.1 systèmes d’exploitation pris en charge, les distributions et la politique du cycle de vie, voir [.NET Core 3.1 Versions OS prises en charge](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).

Pour plus d’informations sur la façon d’installer .NET Core 3.1 sur ARM64 (noyau 4.14), voir [Installing .NET Core 3.0 sur Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

> [!IMPORTANT]
> Le support ARM64 nécessite un noyau Linux 4.14 ou plus. Certaines distributions linux satisfont à cette exigence tandis que d’autres ne le font pas. Par exemple, Ubuntu 18.04 est pris en charge, mais Ubuntu 16.04 ne le fait pas.

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

.NET Core 3.0 traite Linux comme un système d’exploitation unique. Il existe une seule build Linux (par architecture de puce) pour les distributions Linux prises en charge.

.NET Core 3.0 est pris en charge sur les distributions/versions Linux suivantes :

> [!NOTE]
> Un `+` symbole représente la version minimale.

| Système d''exploitation                             | Version               | Architectures    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6, 7, 8               | x64 |
| CentOS                         | 7+                    | x64 |
| Oracle Linux                   | 7+                    | x64 |
| Fedora                         | 29 ans et plus                   | x64 |
| Debian                         | 9+                    | x64, ARM32, ARM64 |
| Ubuntu                         | 16.04+                | x64, ARM32, ARM64 |
| Linux Mint                     | 18 ans et plus                   | x64 |
| OpenSUSE                       | 15 ans et plus                   | x64 |
| SUSE Enterprise Linux (SLES)   | 12 SP2+               | x64 |
| Alpine Linux                   | 3.8+                  | x64, ARM64 |

Pour plus d’informations sur les systèmes d’exploitation supportés .NET Core 3.0, les distributions et la politique du cycle de vie, voir [.NET Core 3.0 Versions OS prises en charge](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).

Pour plus d’informations sur l’installation de .NET Core 3.0 sur ARM64, consultez [Installation de .NET Core 3.0 sur Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

.NET Core 2.2 traite Linux comme un système d’exploitation unique. Il existe une seule build Linux (par architecture de puce) pour les distributions Linux prises en charge.

.NET Core 2.2 est pris en charge sur les distributions/versions Linux suivantes :

> [!NOTE]
> Un `+` symbole représente la version minimale.

| Système d''exploitation                             |  Version                |  Architectures   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7                   | x64 |
| CentOS                         |  7                      | x64 |
| Oracle Linux                   |  7                      | x64 |
| Fedora                         |  29, 30                 | x64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16.04, 18.04, 18.10    | x64, ARM32 |
| Linux Mint                     |  17, 18                 | x64 |
| OpenSUSE                       |  15 ans et plus                    | x64 |
| SUSE Enterprise Linux (SLES)   |  12 SP2+                | x64 |
| Alpine Linux                   |  3.8+                   | x64 |

Pour plus d’informations sur .NET Core 2.2 systèmes d’exploitation pris en charge, les distributions et la politique du cycle de vie, voir [.NET Core 2.2 Versions OS pris en charge](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

.NET Core 2.1 traite Linux comme un système d’exploitation unique. Il existe une seule build Linux (par architecture de puce) pour les distributions Linux prises en charge.

.NET Core 2.1 est pris en charge sur les distributions/versions Linux suivantes :

> [!NOTE]
> Un `+` symbole représente la version minimale.

| Système d''exploitation                             |  Version                |  Architectures   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7, 8                | x64 |
| CentOS                         |  7+                     | x64 |
| Oracle Linux                   |  7+                     | x64 |
| Fedora                         |  29 ans et plus                    | x64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16.04, 18.04, 19.04, 19.10    | x64, ARM32 |
| Linux Mint                     |  17+                    | x64 |
| OpenSUSE                       |  15 ans et plus                    | x64 |
| SUSE Enterprise Linux (SLES)   |  12 SP2+                | x64 |
| Alpine Linux                   |  3.8+                   | x64 |

Pour plus d’informations sur .NET Core 2.1 systèmes d’exploitation pris en charge, les distributions et la politique du cycle de vie, voir [.NET Core 2.1 Versions OS prises en charge](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).

---

## <a name="linux-distribution-dependencies"></a>Dépendances des distributions Linux

En fonction de votre distribution linux, vous devrez peut-être installer des dépendances supplémentaires.

> [!IMPORTANT]
> Les versions et les noms exacts peuvent varier légèrement sur la distribution Linux que vous choisissez.

### <a name="ubuntu"></a>Ubuntu

Les distributions Ubuntu exigent l’installation des bibliothèques suivantes :

- liblttng-ust0
- libcurl3 (pour 14.x et 16.x)
- libcurl4 (pour 18.x)
- libssl1.0.0
- libkrb5-3
- zlib1g
- libicu52 (pour 14.x)
- libicu55 (pour 16.x)
- libicu57 (pour 17.x)
- libicu60 (pour 18.x)

Pour les applications .NET Core qui utilisent l’assemblage *System.Drawing.Common,* vous avez également besoin de la dépendance suivante :

- libgdiplus (version 6.0.1 ou plus tard)

> [!WARNING]
> La plupart des versions d’Ubuntu comprennent une version antérieure de libgdiplus. Vous pouvez installer une version récente de libgdiplus en ajoutant le référentiel Mono à votre système. Pour plus d’informations, consultez <https://www.mono-project.com/download/stable/>.

### <a name="centos-and-fedora"></a>CentOS et Fedora

Les distributions CentOS nécessitent l’installation des bibliothèques suivantes :

- lttng-ust
- libcurl
- openssl-libs
- krb5-libs
- libicu
- zlib

Utilisateurs fedora: Si la version de votre OpenSSL >1,1, vous aurez besoin d’installer **compat-openssl10**.

Pour .NET Core 2.0, les dépendances suivantes sont également requises :

- libunwind
- libuuid

Pour plus d’informations sur les dépendances, voir [applications Linux autonomes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

Pour les applications .NET Core qui utilisent l’assemblage *System.Drawing.Common,* vous aurez également besoin de la dépendance suivante :

- libgdiplus (version 6.0.1 ou plus tard)

> [!WARNING]
> La plupart des versions de CentOS et Fedora comprennent une version antérieure de libgdiplus. Vous pouvez installer une version récente de libgdiplus en ajoutant le référentiel Mono à votre système. Pour plus d’informations, consultez <https://www.mono-project.com/download/stable/>.

::: zone-end

::: zone pivot="os-macos"

.NET Core est pris en charge sur les versions macOS suivantes :

> [!NOTE]
> Un `+` symbole représente la version minimale.

| Version de base .NET | macOS                 | Architectures |     |
| ----------------- | --------------------- | --------------| --- |
| 3.1               | High Sierra (10.13 ')  | x64 | [Plus d’informations](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| 3.0               | High Sierra (10.13 ')  | x64 | [Plus d’informations](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| 2.2               | Sierra (10.12 ')       | x64 | [Plus d’informations](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| 2.1               | Sierra (10.12 ')       | x64 | [Plus d’informations](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

À partir de macOS Catalina (version 10.15), tous les logiciels construits après le 1er juin 2019 qui sont distribués avec Developer ID, doivent être notariés. Cette exigence s’applique au temps d’exécution .NET Core, .NET Core SDK, et au logiciel créé avec .NET Core.

Les installateurs pour les versions .NET Core (à la fois en runtime et SDK) 3.1, 3.0 et 2.1, ont été notariés depuis le 18 février 2020. Les versions publiées antérieurement ne sont pas notariées. Si vous exécutez une application non notariée, vous verrez une erreur similaire à l’image suivante :

![alerte de notarisation macOS Catalina](media/dependencies/macos-notarized-pkg-warning.png)

Pour plus d’informations sur la façon dont la notarisation forcée affecte .NET Core (et vos applications .NET Core), voir [Travailler avec macOS Catalina Notarization](macos-notarization-issues.md).

## <a name="libgdiplus"></a>Libgdiplus

.NET Applications de base qui utilisent *l’assemblage System.Drawing.Common* nécessitent libgdiplus pour être installé.

Un moyen facile d’obtenir libgdiplus est en utilisant le gestionnaire de paquet [Homebrew ("brew")](https://brew.sh/) pour macOS. Après l’installation de *l’infusion,* installez libgdiplus en exécutant les commandes suivantes à une invite terminale (commande) :

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a>Étapes suivantes

- Pour développer et exécuter des applications, installez le [SDK core .NET](sdk.md) (inclut le temps d’exécution).
- Pour exécuter des applications que d’autres ont créées, installez le [temps d’exécution .NET Core](runtime.md).
