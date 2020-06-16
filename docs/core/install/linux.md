---
title: Installer les distributions .NET Core et Linux
description: En savoir plus sur les distributions Linux qui prennent en charge l’installation de .NET Core sur Linux.
author: thraka
ms.author: adegeo
ms.date: 06/01/2020
ms.openlocfilehash: fbb057825395d4e024f99e1abbd1a6e65ba1dce7
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768351"
---
# <a name="install-net-core-on-linux"></a>Installer .NET Core sur Linux

.NET Core est disponible sur différentes distributions Linux. La plupart des plates-formes et distributions Linux ont une version majeure chaque année, et la plupart fournissent un gestionnaire de package qui est utilisé pour installer .NET Core. Cet article décrit ce qui est actuellement pris en charge et le gestionnaire de package utilisé.

Le reste de cet article est une répartition de chaque principale distribution Linux prise en charge par .NET Core. Toutes les versions de .NET Core restent prises en charge jusqu’à la fin de la [prise en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de la version de .net Core ou de la distribution Linux.

Pour une meilleure compatibilité, choisissez une version à long terme (LTS).

## <a name="unsupported-releases"></a>Mises en production non prises en charge

Les versions suivantes de .NET Core ne sont ❌ plus prises en charge. Les téléchargements sont toujours publiés :

- 3.0
- 2.2
- 2.0

Ces versions non prises en charge ne sont pas détaillées dans les sections ci-dessous et votre kilométrage peut varier si vous essayez de les installer.

## <a name="alpine"></a>Alpine

Il n’y a aucun installeur pour Alpine. Vous devez utiliser le [script d’installation](linux-alpine.md#scripted-install) ou suivre les instructions d' [installation manuelle](linux-alpine.md#manual-install) .

Le tableau suivant répertorie les versions de .NET Core actuellement prises en charge et les versions de Alpine sur lesquelles elles sont prises en charge. Ces versions restent prises en charge jusqu’à la [fin de la prise en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de la version de .net Core ou de la version de [Alpine](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).

- Une ✔️ indique que la version de Alpine ou .NET Core est toujours prise en charge.
- Une ❌ indique que la version de Alpine ou .net Core n’est pas prise en charge sur cette version alpine.
- Quand une version de .NET Core et une version de .NET Core sont ✔️, cette combinaison de système d’exploitation et .NET sont prises en charge.

| Alpine                      | .NET Core 2.1 | .NET Core 3.1 | Version préliminaire de .NET 5 |
|-----------------------------|---------------|---------------|----------------|
| ✔️ [3,12](linux-alpine.md)  | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ✔️ [3,11](linux-alpine.md)  | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ✔️ [3,10](linux-alpine.md)  | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ✔️ [3,9](linux-alpine.md)   | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ❌[3,8](linux-alpine.md)   | ✔️ 2,1        | ❌3,1        | ❌version préliminaire 5,0 |

Pour plus d’informations, consultez [installer .net Core sur Alpine](linux-alpine.md).

## <a name="centos"></a>CentOS

CentOS 7 utilise yum en tant que gestionnaire de package et CentOS 8 utilise FND.

Le tableau suivant répertorie les versions de .NET Core actuellement prises en charge sur CentOS 7 et CentOS 8. Ces versions restent prises en charge jusqu’à ce que la version de [.net Core ait atteint la fin du support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou que la version de CentOS ne soit plus prise en charge.

| CentOS                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (installation manuelle uniquement) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](linux-centos.md#centos-8-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ✔️ [7](linux-centos.md#centos-7-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |

Pour plus d’informations, consultez [installer .net Core sur CentOS](linux-centos.md).

## <a name="debian"></a>Debian

Debian utilise APT (outil de package avancé) comme gestionnaire de package.

Le tableau suivant répertorie les versions de .NET Core actuellement prises en charge et les versions de Debian sur lesquelles elles sont prises en charge. Ces versions restent prises en charge jusqu’à la fin de la [prise en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de la version de .net Core ou de la version de [Debian](https://wiki.debian.org/DebianReleases).

- Une ✔️ indique que la version de Debian ou de .NET Core est toujours prise en charge.
- Une ❌ indique que la version de Debian ou de .net Core n’est pas prise en charge sur cette version Debian.
- Quand une version de Debian et une version de .NET Core ont ✔️, cette combinaison de système d’exploitation et .NET sont prises en charge.

| Debian                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (installation manuelle uniquement) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [10](linux-debian.md#debian-10-)     | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ✔️ [9](linux-debian.md#debian-9-)       | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ❌ [8](linux-debian.md#debian-8-)       | ✔️ 2,1        | ❌3,1        | ❌version préliminaire 5,0 |

## <a name="fedora"></a>Fedora

Fedora utilise FND comme gestionnaire de package.

Le tableau suivant répertorie les versions de .NET Core actuellement prises en charge et les versions de Fedora sur lesquelles elles sont prises en charge. Ces versions restent prises en charge jusqu’à la fin de la [prise en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de la version de .net Core, ou la version de [Fedora atteint la fin de vie](https://fedoraproject.org/wiki/End_of_life).

- Une ✔️ indique que la version de Fedora ou de .NET Core est toujours prise en charge.
- Une ❌ indique que la version de Fedora ou de .net Core n’est pas prise en charge sur cette version de Fedora.
- Quand une version de Fedora et une version de .NET Core ont ✔️, cette combinaison de système d’exploitation et .NET sont prises en charge.

| Fedora                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (installation manuelle uniquement) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [32](linux-fedora.md#fedora-32-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ✔️ [31](linux-fedora.md#fedora-31-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ❌[30](linux-fedora.md#fedora-30-) | ✔️ 2,1        | ✔️ 3,1        | ❌version préliminaire 5,0 |
| ❌[29](linux-fedora.md#fedora-29-) | ✔️ 2,1        | ✔️ 3,1        | ❌version préliminaire 5,0 |
| ❌[28](linux-fedora.md#fedora-28-) | ✔️ 2,1        | ❌3,1        | ❌version préliminaire 5,0 |
| ❌[27](linux-fedora.md#fedora-27-) | ✔️ 2,1        | ❌3,1        | ❌version préliminaire 5,0 |

Pour plus d’informations, consultez [installer .net Core sur Fedora](linux-fedora.md).

## <a name="opensuse"></a>OpenSUSE

openSUSE utilise zypper comme gestionnaire de package.

Le tableau suivant répertorie les versions de .NET Core actuellement prises en charge sur openSUSE 15. Ces versions restent prises en charge jusqu’à ce que la version de [.net Core ait atteint la fin du support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou que la version de openSUSE ne soit plus prise en charge.

- Une ✔️ indique que la version de openSUSE ou de .NET Core est toujours prise en charge.
- Une ❌ indique que la version de openSUSE ou de .net Core n’est pas prise en charge sur cette version de openSUSE.
- Quand une version de openSUSE et une version de .NET Core ont ✔️, cette combinaison de système d’exploitation et .NET sont prises en charge.

| OpenSUSE                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (installation manuelle uniquement) |
|----------------------------|---------------|---------------|----------------|
| ✔️ [15](linux-opensuse.md#opensuse-15-)     | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |

## <a name="red-hat"></a>Red Hat

Red Hat Enterprise Linux (RHEL) utilise yum (RHEL 7) et FND (RHEL 8) comme gestionnaire de package.

Le tableau suivant répertorie les versions de .NET Core actuellement prises en charge sur RHEL 7 et RHEL 8. Ces versions restent prises en charge jusqu’à ce que la version de [.net Core ait atteint la fin du support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou que la version de RHEL ne soit plus prise en charge.

- Une ✔️ indique que la version de RHEL ou de .NET Core est toujours prise en charge.
- Une ❌ indique que la version de RHEL ou de .net Core n’est pas prise en charge sur cette version de RHEL.
- Quand une version de RHEL et une version de .NET Core ont ✔️, cette combinaison de système d’exploitation et .NET sont prises en charge.

| RHEL                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (installation manuelle uniquement) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](linux-rhel.md#rhel-8-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ✔️ [7](linux-rhel.md#rhel-7-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |

## <a name="sles"></a>SLES

SLES utilise zypper comme gestionnaire de package.

Le tableau suivant répertorie les versions de .NET Core actuellement prises en charge sur SLES 12 SP2 et SLES 15. Ces versions restent prises en charge jusqu’à ce que la version de [.net Core ait atteint la fin du support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou que la version de SLES ne soit plus prise en charge.

- Une ✔️ indique que la version de SLES ou de .NET Core est toujours prise en charge.
- Une ❌ indique que la version de SLES ou de .net Core n’est pas prise en charge sur cette version SLES.
- Quand une version de SLES et une version de .NET Core ont ✔️, cette combinaison de système d’exploitation et .NET sont prises en charge.

| SLES                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (installation manuelle uniquement) |
|------------------------|---------------|---------------|----------------|
| ✔️ [15](linux-sles.md#sles-15-)     | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ✔️ [12 SP2](linux-sles.md#sles-12-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |

## <a name="ubuntu"></a>Ubuntu

Ubuntu utilise l’outil APT (Advanced Package Tool) comme gestionnaire de package.

Le tableau suivant représente l’état de prise en charge d’Ubuntu et de .NET Core.

- Une ✔️ indique que la version d’Ubuntu ou de .NET Core est toujours prise en charge.
- Une ❌ indique que la version d’Ubuntu ou de .net Core n’est pas prise en charge sur cette version d’Ubuntu.
- Quand une version d’Ubuntu et une version de .NET Core ont ✔️, cette combinaison de système d’exploitation et .NET sont prises en charge.

| Ubuntu                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview (installation manuelle uniquement) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [20,04 (LTS)](linux-ubuntu.md#2004-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ✔️ [19,10](linux-ubuntu.md#1910-)       | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ❌[19,04](linux-ubuntu.md#1904-)       | ✔️ 2,1        | ✔️ 3,1        | ❌version préliminaire 5,0 |
| ❌[18,10](linux-ubuntu.md#1810-)       | ✔️ 2,1        | ❌3,1        | ❌version préliminaire 5,0 |
| ✔️ [18,04 (LTS)](linux-ubuntu.md#1804-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ❌ [17.10](linux-ubuntu.md#1710-)       | ✔️ 2,1        | ❌3,1        | ❌version préliminaire 5,0 |
| ❌ [17.04](linux-ubuntu.md#1704-)       | ✔️ 2,1        | ❌3,1        | ❌version préliminaire 5,0 |
| ❌[16,10](linux-ubuntu.md#1610-)       | ❌2,1        | ❌3,1        | ❌version préliminaire 5,0 |
| ✔️ [16,04 (LTS)](linux-ubuntu.md#1604-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |

Pour plus d’informations, consultez [installer .net Core sur Ubuntu](linux-ubuntu.md).
