---
ms.openlocfilehash: 1d8bcaf68d44f27642048c1c207b52c55b604690
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75902062"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a>Signalr : HandshakeProtocol. SuccessHandshakeData remplacé

Le champ [HandshakeProtocol. SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) a été supprimé et remplacé par une méthode d’assistance qui génère une réponse de négociation réussie en fonction d’un `IHubProtocol`spécifique.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

`HandshakeProtocol.SuccessHandshakeData` était un champ de `public static ReadOnlyMemory<byte>`.

#### <a name="new-behavior"></a>Nouveau comportement

`HandshakeProtocol.SuccessHandshakeData` a été remplacé par une méthode de `GetSuccessfulHandshake(IHubProtocol protocol)` `static` qui retourne une `ReadOnlyMemory<byte>` basée sur le protocole spécifié.

#### <a name="reason-for-change"></a>Motif de modification

Des champs supplémentaires ont été ajoutés à la _réponse_ de négociation qui sont non constantes et changent selon le protocole sélectionné.

#### <a name="recommended-action"></a>Action recommandée

Aucun. Ce type n’est pas conçu pour être utilisé à partir du code utilisateur. `public`, il peut être partagé entre le serveur Signalr et le client. Il peut également être utilisé par les clients Signalr de clients écrits en .NET. **Les utilisateurs** de signalr ne doivent pas être affectés par cette modification.

#### <a name="category"></a>Catégorie

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
