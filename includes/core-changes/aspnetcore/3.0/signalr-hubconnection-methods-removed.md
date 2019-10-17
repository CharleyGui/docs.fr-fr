---
ms.openlocfilehash: a56c5fc32b5fd274d5da0d9b295918f5ea3b345e
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394199"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a>Signalr : les méthodes HubConnection ResetSendPing et ResetTimeout ont été supprimées

Les méthodes `ResetSendPing` et `ResetTimeout` ont été supprimées de l’API Signalr `HubConnection`. Ces méthodes étaient initialement destinées à un usage interne uniquement mais rendues publiques dans ASP.NET Core 2,2. Ces méthodes ne seront pas disponibles à partir de la version ASP.NET Core 3,0 Preview 4. Pour plus d’informations, consultez [ASPNET/AspNetCore # 8543](https://github.com/aspnet/AspNetCore/issues/8543).

#### <a name="version-introduced"></a>Version introduite

3,0

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
