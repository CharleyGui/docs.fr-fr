---
title: Dépendances de kit SDK .NET Core et d’exécution-.NET Core
description: Décrit en détail la configuration requise pour le système d’exploitation et l’architecture de l’UC pour installer le kit SDK .NET Core et le runtime sur Windows, Linux et macOS.
author: leecow
ms.author: leecow
ms.date: 04/30/2020
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 280aa1431686ff99257580bb024a84b1e57f85c0
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895491"
---
# <a name="net-core-dependencies-and-requirements"></a>Dépendances et exigences de .NET Core

Cet article détaille les systèmes d’exploitation et l’architecture du processeur pris en charge par .NET Core.

## <a name="supported-operating-systems"></a>Systèmes d’exploitation pris en charge

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[.NET Core 3.1](#tab/netcore31)

Les versions de Windows suivantes sont prises en charge avec .NET Core 3,1 :

> [!NOTE]
> Un `+` symbole représente la version minimale.

| Système d''exploitation                            | Version                        | Architectures   |
| ----------------------------- | ------------------------------ | --------------- |
| Client Windows                | 7 SP1 +, 8,1                    | x64, x86        |
| Client Windows 10             | Version 1607 +                  | x64, x86        |
| Windows Server                | 2012 R2 +                       | x64, x86        |
| Nano Server                   | Version 1803 +                  | x64, ARM32      |

Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 3,1 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 3,1](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

*.NET Core 3,0 n’est pas pris en charge pour le moment. Pour plus d’informations, consultez la [stratégie de support .net Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

Les versions de Windows suivantes sont prises en charge avec .NET Core 3,0 :

> [!NOTE]
> Un `+` symbole représente la version minimale.

| Système d''exploitation                            | Version                        | Architectures   |
| ----------------------------- | ------------------------------ | --------------- |
| Client Windows                | 7 SP1 +, 8,1                    | x64, x86        |
| Client Windows 10             | Version 1607 +                  | x64, x86        |
| Windows Server                | 2012 R2 +                       | x64, x86        |
| Nano Server                   | Version 1803 +                  | x64, ARM32      |

Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 3,0 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

*.NET Core 2,2 n’est pas pris en charge pour le moment. Pour plus d’informations, consultez la [stratégie de support .net Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

Les versions de Windows suivantes sont prises en charge avec .NET Core 2,2 :

> [!NOTE]
> Un `+` symbole représente la version minimale.

| Système d''exploitation                            | Version                        | Architectures   |
| ----------------------------- | ------------------------------ | --------------- |
| Client Windows                | 7 SP1 +, 8,1                    | x64, x86        |
| Client Windows 10             | Version 1607 +                  | x64, x86        |
| Windows Server                | 2008 R2 SP1 +                   | x64, x86        |
| Nano Server                   | Version 1803 +                   | x64, ARM32      |

Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 2,2 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

Les versions de Windows suivantes sont prises en charge avec .NET Core 2,1 :

> [!NOTE]
> Un `+` symbole représente la version minimale.

| Système d''exploitation                            | Version                        | Architectures   |
| ----------------------------- | ------------------------------ | --------------- |
| Client Windows                | 7 SP1 +, 8,1                    | x64, x86        |
| Client Windows 10             | Version 1607 +                  | x64, x86        |
| Windows Server                | 2008 R2 SP1 +                   | x64, x86        |
| Nano Server                   | Version 1803 +                  | 64x            |

Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 2,1 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a>Windows 7/Vista/8,1/Server 2008 R2/Server 2012 R2

Des dépendances supplémentaires sont requises si vous installez le kit de développement logiciel (SDK) .NET ou le runtime sur les versions suivantes de Windows :

- Windows 7 SP1
- Windows Vista SP 2
- Windows 8.1
- Windows Server 2008 R2
- Windows Server 2012 R2

Installez les éléments suivants :

- [Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).
- [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

La configuration requise ci-dessus est également requise si vous rencontrez l’une des erreurs suivantes :

> Le programme ne peut pas démarrer, car l' *API-MS-Win-CRT-Runtime-L1-1 1/-0. dll* est absente de votre ordinateur. Essayez de réinstaller le programme pour résoudre ce problème.
>
> \- ou -
>
> Le programme ne peut pas démarrer, car l' *API-MS-Win-cor-TimeZone-L1-1 1/-0. dll* est absente de votre ordinateur. Essayez de réinstaller le programme pour résoudre ce problème.
>
> \- ou -
>
> La bibliothèque *hostfxr. dll* a été trouvée, mais son chargement à partir de *C :\\\<path_to_app>\\hostfxr. dll* a échoué.

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[.NET Core 3.1](#tab/netcore31)

.NET Core 3,1 traite Linux comme un système d’exploitation unique. Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge.

.NET Core 3,1 est pris en charge sur les distributions/versions Linux suivantes :

> [!NOTE]
> Un `+` symbole représente la version minimale.

| Système d''exploitation                             | Version               | Architectures    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6, 7, 8               | x64 |
| CentOS                         | 7+                    | x64 |
| Oracle Linux                   | 7+                    | x64 |
| Fedora                         | plus de 30 ans                   | x64 |
| Debian                         | 9+                    | x64, ARM32, ARM64 |
| Ubuntu                         | 16.04+                | x64, ARM32, ARM64 |
| Linux Mint                     | plus de 18 ans                   | x64 |
| OpenSUSE                       | plus de 15                   | x64 |
| SUSE Enterprise Linux (SLES)   | 12 SP2+               | x64 |
| Alpine Linux                   | 3.10 +                 | x64, ARM64 |

Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 3,1 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 3,1](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).

Pour plus d’informations sur l’installation de .NET Core 3,1 sur ARM64 (kernel 4.14 +), consultez [installation de .net core 3,0 sur Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

> [!IMPORTANT]
> La prise en charge de ARM64 nécessite Linux kernel 4,14 ou une version ultérieure. Certaines distributions Linux répondent à cette exigence, contrairement à d’autres. Par exemple, Ubuntu 18,04 est pris en charge, mais Ubuntu 16,04 ne le fait pas.

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

*.NET Core 3,0 n’est pas pris en charge pour le moment. Pour plus d’informations, consultez la [stratégie de support .net Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

.NET Core 3,0 traite Linux comme un système d’exploitation unique. Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge.

.NET Core 3,0 est pris en charge sur les distributions/versions Linux suivantes :

> [!NOTE]
> Un `+` symbole représente la version minimale.

| Système d''exploitation                             | Version               | Architectures    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6, 7, 8               | x64 |
| CentOS                         | 7+                    | x64 |
| Oracle Linux                   | 7+                    | x64 |
| Fedora                         | 29 +                   | x64 |
| Debian                         | 9+                    | x64, ARM32, ARM64 |
| Ubuntu                         | 16.04+                | x64, ARM32, ARM64 |
| Linux Mint                     | plus de 18 ans                   | x64 |
| OpenSUSE                       | plus de 15                   | x64 |
| SUSE Enterprise Linux (SLES)   | 12 SP2+               | x64 |
| Alpine Linux                   | 3.8+                  | x64, ARM64 |

Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 3,0 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).

Pour plus d’informations sur l’installation de .NET Core 3.0 sur ARM64, consultez [Installation de .NET Core 3.0 sur Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

*.NET Core 2,2 n’est pas pris en charge pour le moment. Pour plus d’informations, consultez la [stratégie de support .net Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

.NET Core 2,2 traite Linux comme un système d’exploitation unique. Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge.

.NET Core 2,2 est pris en charge sur les distributions/versions Linux suivantes :

> [!NOTE]
> Un `+` symbole représente la version minimale.

| Système d''exploitation                             |  Version                |  Architectures   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7                   | x64 |
| CentOS                         |  7                      | x64 |
| Oracle Linux                   |  7                      | x64 |
| Fedora                         |  29, 30                 | x64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16,04, 18,04, 18,10    | x64, ARM32 |
| Linux Mint                     |  17, 18                 | x64 |
| OpenSUSE                       |  plus de 15                    | x64 |
| SUSE Enterprise Linux (SLES)   |  12 SP2+                | x64 |
| Alpine Linux                   |  3.8+                   | x64 |

Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 2,2 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

.NET Core 2,1 traite Linux comme un système d’exploitation unique. Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge.

.NET Core 2,1 est pris en charge sur les distributions/versions Linux suivantes :

> [!NOTE]
> Un `+` symbole représente la version minimale.

| Système d''exploitation                             |  Version                |  Architectures   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7, 8                | x64 |
| CentOS                         |  7+                     | x64 |
| Oracle Linux                   |  7+                     | x64 |
| Fedora                         |  plus de 30 ans                    | x64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16,04, 18,04, 19,04, 19,10    | x64, ARM32 |
| Linux Mint                     |  17+                    | x64 |
| OpenSUSE                       |  plus de 15                    | x64 |
| SUSE Enterprise Linux (SLES)   |  12 SP2+                | x64 |
| Alpine Linux                   |  3.8+                   | x64 |

Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 2,1 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).

---

## <a name="linux-distribution-dependencies"></a>Dépendances des distributions Linux

En fonction de votre distribution Linux, vous devrez peut-être installer des dépendances supplémentaires.

> [!IMPORTANT]
> Les versions et les noms exacts peuvent varier légèrement sur la distribution Linux que vous choisissez.

### <a name="ubuntu"></a>Ubuntu

Les distributions Ubuntu requièrent l’installation des bibliothèques suivantes :

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

Pour les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :

- libgdiplus (version 6.0.1 ou ultérieure)

> [!WARNING]
> La plupart des versions d’Ubuntu incluent une version antérieure de libgdiplus. Vous pouvez installer une version récente de libgdiplus en ajoutant le référentiel mono à votre système. Pour plus d'informations, consultez <https://www.mono-project.com/download/stable/>.

### <a name="centos-and-fedora"></a>CentOS et Fedora

Les distributions CentOS nécessitent l’installation des bibliothèques suivantes :

- lttng-ust
- libcurl
- openssl-libs
- krb5-libs
- libicu
- zlib

Utilisateurs Fedora : si la version de votre OpenSSL >= 1,1, vous devez installer **compat-openssl10**.

Pour .NET Core 2,0, les dépendances suivantes sont également requises :

- libunwind
- libuuid

Pour plus d’informations sur les dépendances, consultez [applications Linux autonomes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

Pour les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :

- libgdiplus (version 6.0.1 ou ultérieure)

> [!WARNING]
> La plupart des versions de CentOS et Fedora incluent une version antérieure de libgdiplus. Vous pouvez installer une version récente de libgdiplus en ajoutant le référentiel mono à votre système. Pour plus d'informations, consultez <https://www.mono-project.com/download/stable/>.

### <a name="alpine"></a>Alpine

Les distributions Alpine requièrent l’installation des bibliothèques suivantes :

- ICU-libs (cela n’est pas nécessaire si la globalisation est désactivée)
- krb5-libs
- libcurl
- libintl
- libssl 1.1 (pour Alpine 3,9 ou version ultérieure) ou libssl 1.0 (pour les versions ultérieures)
- libstdc++
- lttng-ust
- numactl (facultatif, utile uniquement pour les appareils avec NUMA activé)
- zlib

Pour les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :

- libgdiplus (disponible uniquement dans le référentiel Edge/test)

::: zone-end

::: zone pivot="os-macos"

.NET Core est pris en charge sur les versions macOS suivantes :

> [!NOTE]
> Un `+` symbole représente la version minimale.

| Version de .NET Core | macOS                 | Architectures |     |
| ----------------- | --------------------- | --------------| --- |
| 3.1               | High Sierra (10.13 +)  | x64 | [Plus d’informations](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| 3.0               | High Sierra (10.13 +)  | x64 | [Plus d’informations](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| 2.2               | Sierra (10.12 +)       | x64 | [Plus d’informations](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| 2.1               | Sierra (10.12 +)       | x64 | [Plus d’informations](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

À partir de macOS Catalina (version 10,15), tous les logiciels générés après le 1er juin 2019, qui sont distribués avec l’ID de développeur, doivent être certifiés. Cette exigence s’applique au Runtime .NET Core, kit SDK .NET Core et aux logiciels créés avec .NET Core.

Les programmes d’installation de .NET Core (Runtime et SDK) versions 3,1, 3,0 et 2,1 ont été certifiés depuis le 18 février 2020. Les versions antérieures publiées ne sont pas certifiées. Si vous exécutez une application non authentifiée, une erreur semblable à l’image suivante s’affiche :

![alerte de notaire Catalina macOS](media/dependencies/macos-notarized-pkg-warning.png)

Pour plus d’informations sur la façon dont l’application de la notaire affecte .NET Core (et vos applications .NET Core), consultez [utilisation de la méthode de notaire Catalina MacOS](macos-notarization-issues.md).

## <a name="libgdiplus"></a>libgdiplus

Les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* nécessitent l’installation de libgdiplus.

Pour obtenir facilement des libgdiplus, vous pouvez utiliser le gestionnaire de package [Homebrew (« Brass »)](https://brew.sh/) pour MacOS. Après l’installation de la commande *infuse*, installez libgdiplus en exécutant les commandes suivantes à une invite de commandes :

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a>Étapes suivantes

- Pour développer et exécuter des applications, installez le [Kit SDK .net Core](sdk.md) (y compris le Runtime).
- Pour exécuter des applications créées par d’autres utilisateurs, installez le [Runtime .net Core](runtime.md).
