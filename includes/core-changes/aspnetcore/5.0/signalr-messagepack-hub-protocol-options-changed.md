---
ms.openlocfilehash: 7a05f60cf1c04d3d73dadb54541254a83b4ea855
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507076"
---
### <a name="signalr-messagepack-hub-protocol-options-type-changed"></a>Signalr : type d’options de protocole MessagePack Hub modifié

Le type d’options de Protocole ASP.NET Core Signalr MessagePack Hub est `IList<MessagePack.IFormatterResolver>` passé de au type de `MessagePackSerializerOptions` la bibliothèque [MessagePack](https://www.nuget.org/packages/MessagePack) .

Pour plus d’informations sur cette modification, consultez [dotnet/aspnetcore # 20506](https://github.com/dotnet/aspnetcore/issues/20506).

#### <a name="version-introduced"></a>Version introduite

5,0 Preview 4

#### <a name="old-behavior"></a>Ancien comportement

Vous pouvez ajouter aux options comme indiqué dans l’exemple suivant :

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers.Add(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

Et remplacez les options comme suit :

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers = new List<MessagePack.IFormatterResolver>()
        {
            MessagePack.Resolvers.StandardResolver.Instance
        };
    });
```

#### <a name="new-behavior"></a>Nouveau comportement

Vous pouvez ajouter aux options comme indiqué dans l’exemple suivant :

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions =
            options.SerializeOptions.WithResolver(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

Et remplacez les options comme suit :

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions = MessagePackSerializerOptions
                .Standard
                .WithResolver(MessagePack.Resolvers.StandardResolver.Instance)
                .WithSecurity(MessagePackSecurity.UntrustedData);
    });
```

#### <a name="reason-for-change"></a>Motif de modification

Cette modification fait partie du passage à MessagePack v2. x, qui a été annoncé dans [ASPNET/announcements # 404](https://github.com/aspnet/Announcements/issues/404). La bibliothèque v2. x a ajouté une API options qui est plus facile à utiliser et fournit plus de fonctionnalités que la `MessagePack.IFormatterResolver` liste de qui a été exposée auparavant.

#### <a name="recommended-action"></a>Action recommandée

Cette modification avec rupture affecte tous les utilisateurs qui configurent des valeurs sur <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>. Si vous utilisez le Protocole ASP.NET Core Signalr MessagePack Hub et modifiez les options, mettez à jour votre utilisation pour utiliser la nouvelle API options, comme indiqué ci-dessus.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
