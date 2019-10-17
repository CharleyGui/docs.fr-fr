---
ms.openlocfilehash: fa0f54404d1e14afa6ce48a425c984a48498a1ee
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394123"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a>Signalr : HandshakeProtocol. SuccessHandshakeData remplacé

Le champ [HandshakeProtocol. SuccessHandshakeData](https://github.com/aspnet/AspNetCore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) a été supprimé et remplacé par une méthode d’assistance qui génère une réponse de négociation réussie en fonction d’un @no__t spécifique-1. 

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="old-behavior"></a>Ancien comportement

`HandshakeProtocol.SuccessHandshakeData` était un champ `public static ReadOnlyMemory<byte>`.

#### <a name="new-behavior"></a>Nouveau comportement

`HandshakeProtocol.SuccessHandshakeData` a été remplacé par une méthode `static` `GetSuccessfulHandshake(IHubProtocol protocol)` qui retourne un `ReadOnlyMemory<byte>` basé sur le protocole spécifié. 

#### <a name="reason-for-change"></a>Motif de modification

Des champs supplémentaires ont été ajoutés à la _réponse_ de négociation qui sont non constantes et changent selon le protocole sélectionné.

#### <a name="recommended-action"></a>Action recommandée

Aucun(e). Ce type n’est pas conçu pour être utilisé à partir du code utilisateur. @No__t-0, il peut être partagé entre le serveur Signalr et le client. Il peut également être utilisé par les clients Signalr de clients écrits en .NET. **Les utilisateurs** de signalr ne doivent pas être affectés par cette modification.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
