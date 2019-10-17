---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394101"
---
### <a name="logging-debuglogger-class-made-internal"></a>Journalisation : classe DebugLogger rendue interne

Avant le ASP.NET Core 3,0, le modificateur d’accès de `DebugLogger` était `public`. Dans ASP.NET Core 3,0, le modificateur d’accès est passé à `internal`.

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="reason-for-change"></a>Motif de modification

La modification est apportée à :

* Garantissez la cohérence avec d’autres implémentations d’enregistreur d’événements telles que `ConsoleLogger`.
* Réduisez la surface de l’API.

#### <a name="recommended-action"></a>Action recommandée

Utilisez la méthode d’extension <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` pour activer la journalisation du débogage. <xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> est également `public` dans le cas où le service doit être inscrit manuellement.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
