---
title: Installer .NET Core sur Alpine-.NET Core
description: Montre les différentes façons d’installer kit SDK .NET Core et le Runtime .NET Core sur Alpine.
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: bbaf4ee9020dcd33c894b5376bf04ad65db8d378
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84771502"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-alpine"></a>Installer kit SDK .NET Core ou le Runtime .NET Core sur Alpine

Cet article explique comment installer .NET Core sur Alpine. Quand une version Alpine n’est plus prise en charge, .NET Core n’est plus pris en charge avec cette version. Toutefois, ces instructions peuvent vous aider à obtenir .NET Core s’exécutant sur ces versions, même s’il n’est pas pris en charge.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

Il n’y a aucun installeur pour Alpine. Vous devez utiliser le [script d’installation](#scripted-install) ou suivre les instructions d' [installation manuelle](#manual-install) .

## <a name="supported-distributions"></a>Distributions prises en charge

Le tableau suivant répertorie les versions de .NET Core actuellement prises en charge et les versions de Alpine sur lesquelles elles sont prises en charge. Ces versions restent prises en charge jusqu’à la [fin de la prise en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de la version de .net Core ou de la version de [Alpine](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).

- Une ✔️ indique que la version de Alpine ou .NET Core est toujours prise en charge.
- Une ❌ indique que la version de Alpine ou .net Core n’est pas prise en charge sur cette version alpine.
- Quand une version de .NET Core et une version de .NET Core sont ✔️, cette combinaison de système d’exploitation et .NET sont prises en charge.

| Alpine                   | .NET Core 2.1 | .NET Core 3.1 | Version préliminaire de .NET 5 |
|--------------------------|---------------|---------------|----------------|
| ✔️ 3,12  | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ✔️ 3,11  | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ✔️ 3,10  | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ✔️ 3,9   | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ❌3,8   | ✔️ 2,1        | ❌3,1        | ❌version préliminaire 5,0 |

Les versions suivantes de .NET Core ne sont plus prises en charge. Les téléchargements sont toujours publiés :

- 3.0
- 2.2
- 2.0

## <a name="dependencies"></a>Les dépendances

.NET Core sur Alpine Linux nécessite l’installation des dépendances suivantes :

- ICU-libs
- krb5-libs
- libintl
- libssl 1.1 (Alpine v 3.9 ou supérieur)
- libssl 1.0 (Alpine v 3.8)
- libstdc++
- lttng-ust
- numactl (facultatif)
- zlib

## <a name="scripted-install"></a>Installation par script

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>Installation manuelle

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>Étapes suivantes

- [Didacticiel : créer une application console avec kit SDK .NET Core à l’aide de Visual Studio Code](../tutorials/with-visual-studio-code.md)
