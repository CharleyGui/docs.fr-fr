---
title: Installer .NET Core sur Fedora 32-gestionnaire de package-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur Fedora 32.
author: thraka
ms.author: adegeo
ms.date: 04/28/2020
ms.openlocfilehash: e5a69bf00e7e2969143e044aea4c9938fd5a610d
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624965"
---
# <a name="fedora-32-package-manager---install-net-core"></a>Gestionnaire de package Fedora 32-installer .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur Fedora 32.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

À compter de Fedora 32, .NET Core 3,1 est disponible dans les référentiels de packages par défaut dans Fedora.

## <a name="install-the-net-core-sdk"></a>Installer le kit SDK .NET Core

Installez le SDK .NET Core. Dans votre terminal, exécutez la commande suivante.

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>Installer le runtime ASP.NET Core

Installez le runtime ASP.NET. Dans votre terminal, exécutez la commande suivante.

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Installer le Runtime .NET Core

Installez le Runtime .NET Core. Dans votre terminal, exécutez la commande suivante.

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>Comment installer d’autres versions

Pour installer d’autres versions de .NET Core, installez manuellement [le kit SDK .net Core](sdk.md?pivots=os-linux#download-and-manually-install) ou [le Runtime .net Core](runtime.md?pivots=os-linux#download-and-manually-install).
