---
title: Installer .NET sur Alpine-.NET
description: Montre les différentes façons d’installer le kit de développement logiciel (SDK) .NET et le Runtime .NET sur Alpine.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 29901cc24ddd4bbe8200a36765ddd29f501394c0
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506817"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-alpine"></a>Installer le kit de développement logiciel (SDK) .NET ou le Runtime .NET sur Alpine

Cet article explique comment installer .NET sur Alpine. Quand une version Alpine n’est plus prise en charge, .NET n’est plus pris en charge avec cette version. Toutefois, ces instructions peuvent vous aider à faire fonctionner .NET sur ces versions, même si elles ne sont pas prises en charge.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

Il n’y a aucun installeur pour Alpine. Vous devez utiliser le [script d’installation](#scripted-install) ou suivre les instructions d' [installation manuelle](#manual-install) .

## <a name="supported-distributions"></a>Distributions prises en charge

Le tableau suivant répertorie les versions de .NET actuellement prises en charge et les versions de Alpine sur lesquelles elles sont prises en charge. Ces versions restent prises en charge jusqu’à la [fin de la prise en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de la version de .net ou de la version de [Alpine](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).

- Une ✔️ indique que la version de Alpine ou .NET est toujours prise en charge.
- Une ❌ indique que la version de Alpine ou .net n’est pas prise en charge sur cette version alpine.
- Quand une version de .NET alpine et une version de .NET sont ✔️, cette combinaison de système d’exploitation et .NET est prise en charge.

| Alpine  | .NET Core 2.1 | .NET Core 3.1 | .NET 5,0 |
|-------- |---------------|---------------|----------------|
| ✔️ 3,12 | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ✔️ 3,11 | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ✔️ 3,10 | ✔️ 2,1        | ✔️ 3,1        | ❌ 5,0 |
| ❌ 3,9  | ✔️ 2,1        | ✔️ 3,1        | ❌ 5,0 |
| ❌ 3,8  | ✔️ 2,1        | ✔️ 3,1        | ❌ 5,0 |

Les versions suivantes de .NET ne sont plus prises en charge. Les téléchargements sont toujours publiés :

- 3.0
- 2.2
- 2.0

## <a name="dependencies"></a>Dépendances

.NET sur Alpine Linux nécessite l’installation des dépendances suivantes :

- ICU-libs
- krb5-libs
- libgcc
- libintl
- libssl 1.1 (Alpine v 3.9 ou supérieur)
- libssl 1.0 (Alpine v 3.8 ou version antérieure)
- libstdc++
- zlib

## <a name="scripted-install"></a>Installation par script

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>Installation manuelle

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>Étapes suivantes

- [Didacticiel : créer une application console avec le kit de développement logiciel (SDK) .NET à l’aide de Visual Studio Code](../tutorials/with-visual-studio-code.md)
