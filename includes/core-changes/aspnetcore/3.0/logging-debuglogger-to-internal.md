---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032604"
---
### <a name="logging-debuglogger-class-made-internal"></a>Journalisation : classe DebugLogger rendue interne

Avant ASP.NET Core 3,0, le `DebugLogger` modificateur d’accès était `public` . Dans ASP.NET Core 3,0, le modificateur d’accès a la valeur `internal` .

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="reason-for-change"></a>Motif de modification

La modification est apportée à :

* Garantissez la cohérence avec d’autres implémentations d’enregistreur d’événements telles que `ConsoleLogger` .
* Réduisez la surface de l’API.

#### <a name="recommended-action"></a>Action recommandée

Utilisez la <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` méthode d’extension pour activer la journalisation du débogage. <xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> est également toujours `public` dans le cas où le service doit être inscrit manuellement.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
