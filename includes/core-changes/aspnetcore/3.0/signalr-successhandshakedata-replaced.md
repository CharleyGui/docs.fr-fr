---
ms.openlocfilehash: 1d8bcaf68d44f27642048c1c207b52c55b604690
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902062"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a>SignalR: HandshakeProtocol.SuccessHandshakeData remplacé

Le champ [HandshakeProtocol.SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) a été enlevé et remplacé par une méthode d’aide `IHubProtocol`qui génère une réponse de poignée de main réussie étant donné un spécifique .

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

`HandshakeProtocol.SuccessHandshakeData`était `public static ReadOnlyMemory<byte>` un champ.

#### <a name="new-behavior"></a>Nouveau comportement

`HandshakeProtocol.SuccessHandshakeData`a été remplacé `static` `GetSuccessfulHandshake(IHubProtocol protocol)` par une `ReadOnlyMemory<byte>` méthode qui renvoie un basé sur le protocole spécifié.

#### <a name="reason-for-change"></a>Raison du changement

D’autres champs ont été ajoutés à la _réponse_ de poignée de main qui ne sont pas constantes et changent selon le protocole choisi.

#### <a name="recommended-action"></a>Action recommandée

Aucun. Ce type n’est pas conçu pour une utilisation à partir du code utilisateur. C’est, `public`de sorte qu’il peut être partagé entre le serveur SignalR et le client. Il peut également être utilisé par les clients SignalR client écrit en .NET. **Les utilisateurs** de SignalR ne devraient pas être affectés par ce changement.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
