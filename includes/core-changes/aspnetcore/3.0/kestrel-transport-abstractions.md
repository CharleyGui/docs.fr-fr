---
ms.openlocfilehash: f95c3916f4da8164cf927344f60f2845f04ddc5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394166"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a>Kestrel: Les abstractions de transport supprimées et rendues publiques

Dans le cadre de l’éloignement des API « pubtérinaires », les API de la couche de transport de Kestrel sont exposées comme une interface publique dans la `Microsoft.AspNetCore.Connections.Abstractions` bibliothèque.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

- Des abstractions liées aux `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` transports étaient disponibles dans la bibliothèque.
- La `ListenOptions.NoDelay` propriété était disponible.

#### <a name="new-behavior"></a>Nouveau comportement

- L’interface `IConnectionListener` a `Microsoft.AspNetCore.Connections.Abstractions` été introduite dans la bibliothèque `...Transport.Abstractions` pour exposer les fonctionnalités les plus utilisées de la bibliothèque.
- Le `NoDelay` est maintenant disponible`LibuvTransportOptions` dans `SocketTransportOptions`les options de transport ( et ).
- `SchedulingMode`n’est plus disponible.

#### <a name="reason-for-change"></a>Raison du changement

ASP.NET Core 3.0 s’est éloigné des API " pubtérinaux »."

#### <a name="recommended-action"></a>Action recommandée

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

None

<!-- 

### Affected APIs

Not detectable via API analysis

-->
