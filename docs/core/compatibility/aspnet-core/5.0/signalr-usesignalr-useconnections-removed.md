---
title: 'Modification avec rupture : Signalr : les méthodes UseSignalR et UseConnections ont été supprimées'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 Signalr : les méthodes UseSignalR et UseConnections ont été supprimées'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 1b1fce04518e69927cdc1650cc1e19107cc81e3b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760892"
---
# <a name="signalr-usesignalr-and-useconnections-methods-removed"></a>Signalr : les méthodes UseSignalR et UseConnections ont été supprimées

Dans ASP.NET Core 3,0, Signalr a adopté le routage du point de terminaison. Dans le cadre de cette modification, <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A> , <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A> et certaines méthodes associées ont été marquées comme obsolètes. Dans ASP.NET Core 5,0, ces méthodes obsolètes ont été supprimées. Pour obtenir la liste complète des méthodes, consultez [API affectées](#affected-apis).

Pour plus d’informations sur ce problème, consultez [dotnet/aspnetcore # 20082](https://github.com/dotnet/aspnetcore/issues/20082).

## <a name="version-introduced"></a>Version introduite

5,0 Preview 3

## <a name="old-behavior"></a>Ancien comportement

Les hubs signalr et les gestionnaires de connexions peuvent être enregistrés dans le pipeline de l’intergiciel (middleware) à l’aide des `UseSignalR` `UseConnections` méthodes ou.

## <a name="new-behavior"></a>Nouveau comportement

Les hubs et les gestionnaires de connexion signalr doivent être inscrits dans <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> à l’aide des <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> méthodes d’extension et sur <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder> .

## <a name="reason-for-change"></a>Motif de modification

Les anciennes méthodes ont une logique de routage personnalisée qui n’interagit pas avec d’autres composants de routage dans ASP.NET Core. Dans ASP.NET Core 3,0, un nouveau système de routage à usage général, appelé routage des points de terminaison, a été introduit. Routage des points de terminaison activé Signalr pour interagir avec d’autres composants de routage. Le passage à ce modèle permet aux utilisateurs de bénéficier de tous les avantages du routage des points de terminaison. Par conséquent, les anciennes méthodes ont été supprimées.

## <a name="recommended-action"></a>Action recommandée

Supprimez le code qui appelle `UseSignalR` ou `UseConnections` de la méthode de votre projet `Startup.Configure` . Remplacez-le par des appels à `MapHub` ou `MapConnectionHandler` , respectivement, dans le corps d’un appel à `UseEndpoints` . Par exemple :

**Ancien code :**

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

**Nouveau code :**

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

En général, vos `MapHub` appels précédents et `MapConnectionHandler` peuvent être transférés directement à partir du corps de `UseSignalR` et `UseConnections` vers avec un minimum de `UseEndpoints` modifications nécessaires.

## <a name="affected-apis"></a>API affectées

- <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections`
- `Overload:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler`
- `Overload:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub`

-->
