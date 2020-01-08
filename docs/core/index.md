---
title: Guide .NET Core
description: .NET Core est une implémentation modulaire et hautement performante de .NET pour la création d’applications Windows, Linux et macOS. Découvrez .NET Core pour démarrer.
author: richlander
ms.date: 12/04/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 80a3b12972e24c3022ac2aa14406aa60635815a3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341368"
---
# <a name="net-core-guide"></a>Guide .NET Core

[.NET Core](about.md) est une plateforme de développement généraliste [open source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT) qui est tenue à jour par Microsoft et la communauté .NET sur [GitHub](https://github.com/dotnet/core). Cette multiplateforme prend en charge Windows, macOS et Linux. Elle permet de générer des applications destinées à des appareils, au cloud et à l’Internet des objets.

Consultez [À propos de .NET Core](about.md) pour en savoir plus sur .NET Core, notamment ses caractéristiques, les langues et frameworks pris en charge et les API clés.

Consultez les [Tutoriels .NET Core](tutorials/index.md) pour apprendre à créer une application .NET Core simple. Il suffit de quelques minutes pour créer votre première application et la rendre opérationnelle. Si vous souhaitez tester .NET Core dans votre navigateur, consultez le tutoriel en ligne [Nombres en C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml).

## <a name="download-net-core"></a>Télécharger .NET Core

Téléchargez le [Kit SDK .net Core](https://www.microsoft.com/net/download) pour essayer .net Core sur votre ordinateur Windows, MacOS ou Linux. Et si vous préférez utiliser les conteneurs de l’ancrage, visitez le hub de l' [ancreur .net Core](https://hub.docker.com/_/microsoft-dotnet-core/).

Toutes les versions de .NET Core sont disponibles sur [Téléchargements de .NET Core](https://dotnet.microsoft.com/download/dotnet-core) si vous recherchez une autre version de .NET Core.

## <a name="net-core-31"></a>.NET Core 3.1

La dernière version est .NET Core 3,1. 3,1 comprend des améliorations mineures par rapport à .NET Core 3,0. Toutefois, .NET Core 3,1 est une [version prise en charge à long terme](https://dotnet.microsoft.com/platform/support/policy/dotnet-core). Pour plus d’informations sur la version 3,1 de .NET Core, consultez [what’s New in .net core 3,1](./whats-new/dotnet-core-3-1.md).

## <a name="create-your-first-application"></a>Créer votre première application

Après avoir installé le SDK .NET Core, ouvrez une invite de commandes. Entrez les commandes de `dotnet` suivantes pour créer et exécuter C# une application :

```dotnetcli
dotnet new console
dotnet run
```

Vous devez voir la sortie suivante :

```output
Hello World!
```

## <a name="support"></a>Prise en charge de

.NET Core est [pris en charge par Microsoft](https://dotnet.microsoft.com/platform/support/policy), sur Windows, MacOS et Linux. La sécurité et la qualité sont mises à jour plusieurs fois par an, en général, tous les mois.

Les distributions binaires .NET Core sont générées et testées sur des serveurs managés par Microsoft dans Azure et elles sont prises en charge comme tous les produits Microsoft.

[Red Hat prend en charge .NET Core](http://redhatloves.net/) sur Red Hat Enterprise Linux (RHEL). Red Hat génère .NET Core à partir de la source et le rend disponible dans les [collections logicielles Red Hat](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat et Microsoft collaborent pour s’assurer que .NET Core fonctionne correctement sur RHEL.
