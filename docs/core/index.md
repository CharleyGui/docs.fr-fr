---
title: Guide .NET Core
description: .NET Core est une implémentation modulaire et haute performance de .NET pour créer des applications Windows, Linux et macOS. Découvrez .NET Core pour démarrer.
author: richlander
ms.date: 12/04/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 6d2ce5951fa01ca3945ce0e64aa58fbadc8ab5af
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546547"
---
# <a name="net-core-guide"></a>Guide .NET Core

[.NET Core](about.md) est une plateforme de développement généraliste [open source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT) qui est tenue à jour par Microsoft et la communauté .NET sur [GitHub](https://github.com/dotnet/core). Cette multiplateforme prend en charge Windows, macOS et Linux. Elle permet de générer des applications destinées à des appareils, au cloud et à l’Internet des objets.

Consultez [À propos de .NET Core](about.md) pour en savoir plus sur .NET Core, notamment ses caractéristiques, les langues et frameworks pris en charge et les API clés.

Consultez les [Tutoriels .NET Core](tutorials/index.md) pour apprendre à créer une application .NET Core simple. Il suffit de quelques minutes pour créer votre première application et la rendre opérationnelle. Si vous souhaitez tester .NET Core dans votre navigateur, consultez le tutoriel en ligne [Nombres en C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml).

## <a name="download-net-core"></a>Télécharger .NET Core

Téléchargez le [.NET Core SDK](https://dotnet.microsoft.com/download) pour essayer .NET Core sur votre Windows, macOS ou Linux machine. Et si vous préférez utiliser des conteneurs Docker, visitez le [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).

Toutes les versions de .NET Core sont disponibles sur [Téléchargements de .NET Core](https://dotnet.microsoft.com/download/dotnet-core) si vous recherchez une autre version de .NET Core.

## <a name="net-core-31"></a>.NET Core 3.1

La dernière version est .NET Core 3.1. 3.1 comprend des améliorations mineures au-dessus de .NET Core 3.0, cependant, .NET Core 3.1 est une [version soutenue à long terme](https://dotnet.microsoft.com/platform/support/policy/dotnet-core). Pour plus d’informations sur la version .NET Core 3.1, voir [Ce qui est nouveau dans .NET Core 3.1](./whats-new/dotnet-core-3-1.md).

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

.NET Core est [pris en charge par Microsoft](https://dotnet.microsoft.com/platform/support/policy), sur Windows, macOS et Linux. La sécurité et la qualité sont mises à jour plusieurs fois par an, en général, tous les mois.

Les distributions binaires .NET Core sont générées et testées sur des serveurs managés par Microsoft dans Azure et elles sont prises en charge comme tous les produits Microsoft.

[Red Hat prend en charge .NET Core](http://redhatloves.net/) sur Red Hat Enterprise Linux (RHEL). Red Hat génère .NET Core à partir de la source et le rend disponible dans les [collections logicielles Red Hat](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat et Microsoft collaborent pour s’assurer que .NET Core fonctionne correctement sur RHEL.
