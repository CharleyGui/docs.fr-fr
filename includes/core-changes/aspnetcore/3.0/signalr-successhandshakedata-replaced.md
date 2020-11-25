---
ms.openlocfilehash: 05aec429e28ef74515ef6988d5b064e6d16b7c1b
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032675"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a>Signalr : HandshakeProtocol. SuccessHandshakeData remplacé

Le champ [HandshakeProtocol. SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) a été supprimé et remplacé par une méthode d’assistance qui génère une réponse de négociation réussie en fonction d’un spécifique `IHubProtocol` .

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

`HandshakeProtocol.SuccessHandshakeData` était un `public static ReadOnlyMemory<byte>` champ.

#### <a name="new-behavior"></a>Nouveau comportement

`HandshakeProtocol.SuccessHandshakeData` a été remplacé par une `static` `GetSuccessfulHandshake(IHubProtocol protocol)` méthode qui retourne un `ReadOnlyMemory<byte>` basé sur le protocole spécifié.

#### <a name="reason-for-change"></a>Motif de modification

Des champs supplémentaires ont été ajoutés à la _réponse_ de négociation qui sont non constantes et changent selon le protocole sélectionné.

#### <a name="recommended-action"></a>Action recommandée

Aucun. Ce type n’est pas conçu pour être utilisé à partir du code utilisateur. Il `public` peut donc être partagé entre le serveur signalr et le client. Il peut également être utilisé par les clients Signalr de clients écrits en .NET. **Les utilisateurs** de signalr ne doivent pas être affectés par cette modification.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=nameWithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
