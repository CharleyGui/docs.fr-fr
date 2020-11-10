---
title: 'NETSDK1079 : le package Microsoft. AspNetCore. All n’est pas pris en charge quand vous ciblez .NET Core 3,0 ou une version ultérieure.'
description: Comment résoudre la migration à partir de Microsoft. AspNetCore. app
author: dsplaisted
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1079
ms.openlocfilehash: e0b7aba909dbd2931f755238a2de2418d294751d
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445779"
---
# <a name="netsdk1079-the-microsoftaspnetcoreall-package-is-not-supported-when-targeting-net-core-30-or-higher"></a>NETSDK1079 : le package Microsoft. AspNetCore. All n’est pas pris en charge quand vous ciblez .NET Core 3,0 ou une version ultérieure.

**Cet article s’applique à :** ✔️ kit SDK .net Core 3.1.100 et versions ultérieures

Vous pouvez recevoir ce message d’erreur dans les cas suivants :

- Vous reciblez un projet de ASP.NET Core à partir de .NET Core 2,2 ou d’une version antérieure vers .NET Core 3,0 ou version ultérieure.
- Le projet utilise le package Microsoft. AspNetCore. All.

Supprimez `PackageReference` pour Microsoft. AspNetCore. All.  Vous devrez peut-être également ajouter des références de package pour les packages qui ont été référencés à partir de Microsoft. AspNetCore. All, mais qui ne sont pas inclus dans le ASP.NET Core Framework partagé.  Ces packages sont répertoriés ici : [migration de Microsoft. AspNetCore. All vers Microsoft. AspNetCore. app](/aspnet/core/fundamentals/metapackage#migrating-from-microsoftaspnetcoreall-to-microsoftaspnetcoreapp).

Voir aussi [migrer de ASP.NET Core 2,2 à 3,0](/aspnet/core/migration/22-to-30)
