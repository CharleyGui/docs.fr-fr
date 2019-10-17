---
ms.openlocfilehash: f95c3916f4da8164cf927344f60f2845f04ddc5c
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394166"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a>Kestrel : les abstractions de transport ont été supprimées et rendues publiques

Dans le cadre du déplacement des API « pubternal », les API de la couche de transport Kestrel sont exposées en tant qu’interface publique dans la bibliothèque `Microsoft.AspNetCore.Connections.Abstractions`.

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="old-behavior"></a>Ancien comportement

- Les abstractions relatives au transport étaient disponibles dans la bibliothèque `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions`.
- La propriété `ListenOptions.NoDelay` était disponible.

#### <a name="new-behavior"></a>Nouveau comportement

- L’interface `IConnectionListener` a été introduite dans la bibliothèque `Microsoft.AspNetCore.Connections.Abstractions` pour exposer les fonctionnalités les plus utilisées à partir de la bibliothèque `...Transport.Abstractions`.
- La `NoDelay` est désormais disponible dans options de transport (`LibuvTransportOptions` et `SocketTransportOptions`).
- `SchedulingMode` n’est plus disponible.

#### <a name="reason-for-change"></a>Motif de modification

ASP.NET Core 3,0 a été déplacée hors des API « pubternal ».

#### <a name="recommended-action"></a>Action recommandée

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

aucune.

<!-- 

### Affected APIs

Not detectable via API analysis

-->
