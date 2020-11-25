---
ms.openlocfilehash: fb23418816abcae125106c93b339a546aa9bc2ee
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032584"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a>Kestrel : les abstractions de transport ont été supprimées et rendues publiques

Dans le cadre du déplacement des API « pubternal », les API de la couche de transport Kestrel sont exposées en tant qu’interface publique dans la `Microsoft.AspNetCore.Connections.Abstractions` bibliothèque.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

- Des abstractions relatives au transport étaient disponibles dans la `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` bibliothèque.
- La `ListenOptions.NoDelay` propriété était disponible.

#### <a name="new-behavior"></a>Nouveau comportement

- L' `IConnectionListener` interface a été introduite dans la `Microsoft.AspNetCore.Connections.Abstractions` bibliothèque pour exposer la fonctionnalité la plus utilisée à partir de la `...Transport.Abstractions` bibliothèque.
- Le `NoDelay` est désormais disponible dans les options de transport ( `LibuvTransportOptions` et `SocketTransportOptions` ).
- `SchedulingMode` n’est plus disponible.

#### <a name="reason-for-change"></a>Motif de modification

ASP.NET Core 3,0 a été déplacée hors des API « pubternal ».

#### <a name="recommended-action"></a>Action recommandée

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
