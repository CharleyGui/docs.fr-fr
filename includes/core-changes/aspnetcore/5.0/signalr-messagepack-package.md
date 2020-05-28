---
ms.openlocfilehash: ca0792a3fd05d28cecceac1d644e3e4bf64722bc
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345218"
---
### <a name="signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package"></a>Signalr : protocole MessagePack Hub déplacé vers le package MessagePack 2. x

Le Protocole ASP.NET Core Signalr [MessagePack Hub](/aspnet/core/signalr/messagepackhubprotocol) utilise le [package NuGet MessagePack](https://www.nuget.org/packages/MessagePack) pour la sérialisation MessagePack. ASP.NET Core 5,0 met à niveau le package de 1. x vers la dernière version du package 2. x.

Pour plus d’informations sur ce problème, consultez [dotnet/aspnetcore # 18692](https://github.com/dotnet/aspnetcore/issues/18692).

#### <a name="version-introduced"></a>Version introduite

5,0 Preview 1

#### <a name="old-behavior"></a>Ancien comportement

ASP.NET Core Signalr a utilisé le package MessagePack 1. x pour sérialiser et désérialiser les messages MessagePack.

#### <a name="new-behavior"></a>Nouveau comportement

ASP.NET Core Signalr utilise le package MessagePack 2. x pour sérialiser et désérialiser les messages MessagePack.

#### <a name="reason-for-change"></a>Motif de modification

Les dernières améliorations du package MessagePack 2. x ajoutent des fonctionnalités utiles.

#### <a name="recommended-action"></a>Action recommandée

Cette modification avec rupture s’applique dans les cas suivants :

* Définition ou configuration des valeurs sur <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions> .
* Utilisation directe des API MessagePack et utilisation du Protocole ASP.NET Core Signalr MessagePack Hub dans le même projet. La version la plus récente sera chargée à la place de la version précédente.

Pour obtenir des conseils sur la migration à partir des auteurs de package, consultez [migration de MessagePack v1. x vers MessagePack v2. x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md). Certains aspects de la sérialisation et de la désérialisation des messages sont affectés. Plus précisément, il existe des [changements de comportement dans la manière dont les valeurs DateTime sont sérialisées](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes).

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
