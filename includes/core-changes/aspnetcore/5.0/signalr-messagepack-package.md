---
ms.openlocfilehash: ca0792a3fd05d28cecceac1d644e3e4bf64722bc
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345218"
---
### <a name="signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package"></a>SignalR: MessagePack Hub Protocol déplacé à MessagePack 2.x paquet

Le protocole ASP.NET Core SignalR [MessagePack Hub](/aspnet/core/signalr/messagepackhubprotocol) utilise le [paquet MessagePack NuGet](https://www.nuget.org/packages/MessagePack) pour la sérialisation De MessagePack. ASP.NET Core 5.0 met à niveau le paquet de 1.x à la dernière version de paquet 2.x.

Pour discussion sur cette question, voir [dotnet/aspnetcore 18692](https://github.com/dotnet/aspnetcore/issues/18692).

#### <a name="version-introduced"></a>Version introduite

5.0 Aperçu 1

#### <a name="old-behavior"></a>Ancien comportement

ASP.NET Core SignalR a utilisé le paquet MessagePack 1.x pour sérialiser et déséialiser les messages MessagePack.

#### <a name="new-behavior"></a>Nouveau comportement

ASP.NET Core SignalR utilise le paquet MessagePack 2.x pour sérialiser et déséialiser les messages MessagePack.

#### <a name="reason-for-change"></a>Raison du changement

Les dernières améliorations apportées au paquet MessagePack 2.x ajoutent des fonctionnalités utiles.

#### <a name="recommended-action"></a>Action recommandée

Ce changement de rupture s’applique lorsque :

* Définir ou configurer <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>des valeurs sur .
* Utiliser directement les API MessagePack et utiliser le protocole ASP.NET Core SignalR MessagePack Hub dans le même projet. La version la plus récente sera chargée au lieu de la version précédente.

Pour les conseils de migration des auteurs du paquet, voir [Migrating de MessagePack v1.x à MessagePack v2.x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md). Certains aspects de la sérialisation des messages et de la désétération sont affectés. Plus précisément, il ya [des changements de comportement à la façon dont les valeurs DateTime sont sérialisés](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes).

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
