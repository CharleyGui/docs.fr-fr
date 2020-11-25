---
title: 'Modification avec rupture : Signalr : type d’options de protocole MessagePack Hub modifié'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 signalé par Signalr : type d’options de protocole MessagePack Hub modifié'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: b75dbec834699472f18b3058052274476bd9751d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761262"
---
# <a name="signalr-messagepack-hub-protocol-options-type-changed"></a>Signalr : type d’options de protocole MessagePack Hub modifié

Le type d’options de Protocole ASP.NET Core Signalr MessagePack Hub est passé de `IList<MessagePack.IFormatterResolver>` au type de la bibliothèque [MessagePack](https://www.nuget.org/packages/MessagePack) `MessagePackSerializerOptions` .

Pour plus d’informations sur cette modification, consultez [dotnet/aspnetcore # 20506](https://github.com/dotnet/aspnetcore/issues/20506).

## <a name="version-introduced"></a>Version introduite

5,0 Preview 4

## <a name="old-behavior"></a>Ancien comportement

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

## <a name="new-behavior"></a>Nouveau comportement

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

## <a name="reason-for-change"></a>Motif de modification

Cette modification fait partie du passage à MessagePack v2. x, qui a été annoncé dans [ASPNET/announcements # 404](https://github.com/aspnet/Announcements/issues/404). La bibliothèque v2. x a ajouté une API options qui est plus facile à utiliser et fournit plus de fonctionnalités que la liste de `MessagePack.IFormatterResolver` qui a été exposée auparavant.

## <a name="recommended-action"></a>Action recommandée

Cette modification avec rupture affecte tous les utilisateurs qui configurent des valeurs sur <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions> . Si vous utilisez le Protocole ASP.NET Core Signalr MessagePack Hub et modifiez les options, mettez à jour votre utilisation pour utiliser la nouvelle API options, comme indiqué ci-dessus.

## <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
