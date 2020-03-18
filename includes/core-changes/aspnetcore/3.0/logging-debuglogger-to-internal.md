---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394101"
---
### <a name="logging-debuglogger-class-made-internal"></a>Enregistrement: DebugLogger classe rendue interne

Avant ASP.NET Core 3.0, `DebugLogger`« le modificateur d’accès était `public`. Dans ASP.NET Core 3.0, le modificateur `internal`d’accès a changé pour .

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="reason-for-change"></a>Raison du changement

Le changement est apporté à :

* Appliquer la cohérence avec d’autres implémentations d’enregistreur tels que `ConsoleLogger`.
* Réduire la surface de l’API.

#### <a name="recommended-action"></a>Action recommandée

Utilisez <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` la méthode d’extension pour permettre l’exploitation forestière de débogé. <xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider>est également `public` toujours dans le cas où le service doit être enregistré manuellement.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
