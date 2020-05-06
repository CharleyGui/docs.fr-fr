---
ms.openlocfilehash: f95c3916f4da8164cf927344f60f2845f04ddc5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394166"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a>Kestrel : les abstractions de transport ont été supprimées et rendues publiques

Dans le cadre du déplacement des API « pubternal », les API de la couche de transport Kestrel sont exposées en tant qu' `Microsoft.AspNetCore.Connections.Abstractions` interface publique dans la bibliothèque.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

- Des abstractions relatives au transport étaient disponibles dans `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` la bibliothèque.
- La `ListenOptions.NoDelay` propriété était disponible.

#### <a name="new-behavior"></a>Nouveau comportement

- L' `IConnectionListener` interface a été introduite `Microsoft.AspNetCore.Connections.Abstractions` dans la bibliothèque pour exposer la fonctionnalité la plus `...Transport.Abstractions` utilisée à partir de la bibliothèque.
- Le `NoDelay` est désormais disponible dans les options de`LibuvTransportOptions` transport `SocketTransportOptions`(et).
- `SchedulingMode`n’est plus disponible.

#### <a name="reason-for-change"></a>Motif de modification

ASP.NET Core 3,0 a été déplacée hors des API « pubternal ».

#### <a name="recommended-action"></a>Action recommandée

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

Aucun

<!-- 

### Affected APIs

Not detectable via API analysis

-->
