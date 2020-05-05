---
ms.openlocfilehash: de06825f1031d05bc83183a83bae165e2f9512ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901920"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a>Signalr : les méthodes HubConnection ResetSendPing et ResetTimeout ont été supprimées

Les `ResetSendPing` méthodes `ResetTimeout` et ont été supprimées de l' `HubConnection` API signalr. Ces méthodes étaient initialement destinées à un usage interne uniquement mais rendues publiques dans ASP.NET Core 2,2. Ces méthodes ne seront pas disponibles à partir de la version ASP.NET Core 3,0 Preview 4. Pour plus d’informations, consultez [dotnet/aspnetcore # 8543](https://github.com/dotnet/aspnetcore/issues/8543).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Les API étaient disponibles.

#### <a name="new-behavior"></a>Nouveau comportement

Les API sont supprimées.

#### <a name="reason-for-change"></a>Motif de modification

Ces méthodes étaient initialement destinées à un usage interne uniquement mais rendues publiques dans ASP.NET Core 2,2.

#### <a name="recommended-action"></a>Action recommandée

N’utilisez pas ces méthodes.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing`
- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout`

-->
