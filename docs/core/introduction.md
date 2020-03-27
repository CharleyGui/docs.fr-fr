---
title: .NET Core intro et aperçu
description: .NET Core est une implémentation modulaire et haute performance de .NET pour créer des applications Windows, Linux et macOS. Découvrez .NET Core pour démarrer.
author: richlander
ms.date: 03/25/2020
ms.custom: updateeachrelease
ms.openlocfilehash: edd3864d3c3c5c0e9fd8c26ee806ffc9e100423d
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80351700"
---
# <a name="introduction-to-net-core"></a>Introduction à .NET Core

[.NET Core](about.md) est une plateforme de développement généraliste [open source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT) qui est tenue à jour par Microsoft et la communauté .NET sur [GitHub](https://github.com/dotnet/core). Cette multiplateforme prend en charge Windows, macOS et Linux. Elle permet de générer des applications destinées à des appareils, au cloud et à l’Internet des objets.

## <a name="download-net-core"></a>Télécharger .NET Core

Téléchargez le [.NET Core SDK](https://dotnet.microsoft.com/download) pour essayer .NET Core sur votre Windows, macOS ou Linux machine. Si vous préférez utiliser des conteneurs Docker, visitez le [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).

## <a name="net-core-31"></a>.NET Core 3.1

La dernière version est .NET Core 3.1. 3.1 comprend des améliorations mineures au-dessus de .NET Core 3.0, cependant, .NET Core 3.1 est une [version soutenue à long terme](https://dotnet.microsoft.com/platform/support/policy/dotnet-core). Pour plus d’informations sur la version .NET Core 3.1, voir [Ce qui est nouveau dans .NET Core 3.1](./whats-new/dotnet-core-3-1.md).

Si vous êtes à la recherche d’une autre version de .NET Core, toutes les versions sont disponibles à [.NET Core téléchargements](https://dotnet.microsoft.com/download/dotnet-core).

## <a name="create-your-first-application"></a>Créer votre première application

Après avoir installé le SDK .NET Core, ouvrez une invite de commandes. Entrez `dotnet` les commandes suivantes pour créer et exécuter une application CMD :

```dotnetcli
dotnet new console
dotnet run
```

Vous devez normalement voir la sortie suivante.

```output
Hello World!
```

## <a name="support"></a>Support

.NET Core est [pris en charge par Microsoft](https://dotnet.microsoft.com/platform/support/policy) sur Windows, macOS et Linux. La sécurité et la qualité sont mises à jour plusieurs fois par an, en général, tous les mois.

Les distributions binaires .NET Core sont générées et testées sur des serveurs managés par Microsoft dans Azure et elles sont prises en charge comme tous les produits Microsoft.

[Red Hat prend en charge .NET Core](http://redhatloves.net/) sur Red Hat Enterprise Linux (RHEL). Red Hat génère .NET Core à partir de la source et le rend disponible dans les [collections logicielles Red Hat](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat et Microsoft collaborent pour s’assurer que .NET Core fonctionne correctement sur RHEL.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [tutoriels .NET Core](tutorials/index.md)

> [!div class="nextstepaction"]
> [Essayez .NET Core dans votre navigateur](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
