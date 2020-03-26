---
ms.openlocfilehash: 329ef39c7626ecd743577f336a4c8cd4a38fb082
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291638"
---
### <a name="signalr-usesignalr-and-useconnections-methods-removed"></a>SignalR: UtilisationSignalR et UseConnections méthodes supprimées

Dans ASP.NET Core 3.0, SignalR a adopté le routage de point final. Dans le cadre de <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A> <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>ce changement, le , et certaines méthodes connexes ont été marqués comme obsolètes. Dans ASP.NET Core 5.0, ces méthodes obsolètes ont été supprimées. Pour la liste complète des méthodes, voir [API affectées](#affected-apis).

Pour discussion sur cette question, voir [dotnet/aspnetcore-20082](https://github.com/dotnet/aspnetcore/issues/20082).

#### <a name="version-introduced"></a>Version introduite

5.0 Aperçu 3

#### <a name="old-behavior"></a>Ancien comportement

Les hubs SignalR et les gestionnaires de connexion `UseSignalR` peuvent `UseConnections` être enregistrés dans le pipeline middleware en utilisant le ou les méthodes.

#### <a name="new-behavior"></a>Nouveau comportement

Les hubs SignalR et les <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> gestionnaires <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> de <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> connexion <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>doivent être enregistrés à l’intérieur à l’aide des méthodes et des méthodes d’extension sur .

#### <a name="reason-for-change"></a>Raison du changement

Les anciennes méthodes avaient une logique de routage personnalisée qui n’interagissait pas avec d’autres composants de routage dans ASP.NET Core. Dans ASP.NET Core 3.0, un nouveau système de routage à usage général, appelé itinéraire par point final, a été introduit. Le routage de point de terminaison a permis à SignalR d’interagir avec d’autres composants de routage. Le passage à ce modèle permet aux utilisateurs de réaliser tous les avantages du routage par point final. Par conséquent, les anciennes méthodes ont été supprimées.

#### <a name="recommended-action"></a>Action recommandée

Supprimez le `UseSignalR` `UseConnections` code qui appelle `Startup.Configure` ou de la méthode de votre projet. Remplacez-le `MapHub` par `MapConnectionHandler`des appels vers ou, `UseEndpoints`respectivement, dans le corps d’un appel à . Par exemple :

**Ancien code:**

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

En général, `MapHub` vos `MapConnectionHandler` appels précédents et peuvent `UseSignalR` être `UseConnections` `UseEndpoints` transférés directement du corps de et vers avec peu ou pas de changement nécessaire.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections`
- `Overload:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler`
- `Overload:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub`

-->
