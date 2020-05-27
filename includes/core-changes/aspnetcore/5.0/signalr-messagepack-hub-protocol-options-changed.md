---
ms.openlocfilehash: 7a05f60cf1c04d3d73dadb54541254a83b4ea855
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507076"
---
### <a name="signalr-messagepack-hub-protocol-options-type-changed"></a><span data-ttu-id="deed2-101">Signalr : type d’options de protocole MessagePack Hub modifié</span><span class="sxs-lookup"><span data-stu-id="deed2-101">SignalR: MessagePack Hub Protocol options type changed</span></span>

<span data-ttu-id="deed2-102">Le type d’options de Protocole ASP.NET Core Signalr MessagePack Hub est passé de `IList<MessagePack.IFormatterResolver>` au type de la bibliothèque [MessagePack](https://www.nuget.org/packages/MessagePack) `MessagePackSerializerOptions` .</span><span class="sxs-lookup"><span data-stu-id="deed2-102">The ASP.NET Core SignalR MessagePack Hub Protocol options type has changed from `IList<MessagePack.IFormatterResolver>` to the [MessagePack](https://www.nuget.org/packages/MessagePack) library's `MessagePackSerializerOptions` type.</span></span>

<span data-ttu-id="deed2-103">Pour plus d’informations sur cette modification, consultez [dotnet/aspnetcore # 20506](https://github.com/dotnet/aspnetcore/issues/20506).</span><span class="sxs-lookup"><span data-stu-id="deed2-103">For discussion on this change, see [dotnet/aspnetcore#20506](https://github.com/dotnet/aspnetcore/issues/20506).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="deed2-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="deed2-104">Version introduced</span></span>

<span data-ttu-id="deed2-105">5,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="deed2-105">5.0 Preview 4</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="deed2-106">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="deed2-106">Old behavior</span></span>

<span data-ttu-id="deed2-107">Vous pouvez ajouter aux options comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="deed2-107">You can add to the options as shown in the following example:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers.Add(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

<span data-ttu-id="deed2-108">Et remplacez les options comme suit :</span><span class="sxs-lookup"><span data-stu-id="deed2-108">And replace the options as follows:</span></span>

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

#### <a name="new-behavior"></a><span data-ttu-id="deed2-109">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="deed2-109">New behavior</span></span>

<span data-ttu-id="deed2-110">Vous pouvez ajouter aux options comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="deed2-110">You can add to the options as shown in the following example:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions =
            options.SerializeOptions.WithResolver(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

<span data-ttu-id="deed2-111">Et remplacez les options comme suit :</span><span class="sxs-lookup"><span data-stu-id="deed2-111">And replace the options as follows:</span></span>

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

#### <a name="reason-for-change"></a><span data-ttu-id="deed2-112">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="deed2-112">Reason for change</span></span>

<span data-ttu-id="deed2-113">Cette modification fait partie du passage à MessagePack v2. x, qui a été annoncé dans [ASPNET/announcements # 404](https://github.com/aspnet/Announcements/issues/404).</span><span class="sxs-lookup"><span data-stu-id="deed2-113">This change is part of moving to MessagePack v2.x, which was announced in [aspnet/Announcements#404](https://github.com/aspnet/Announcements/issues/404).</span></span> <span data-ttu-id="deed2-114">La bibliothèque v2. x a ajouté une API options qui est plus facile à utiliser et fournit plus de fonctionnalités que la liste de `MessagePack.IFormatterResolver` qui a été exposée auparavant.</span><span class="sxs-lookup"><span data-stu-id="deed2-114">The v2.x library has added an options API that's easier to use and provides more features than the list of `MessagePack.IFormatterResolver` that was exposed before.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="deed2-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="deed2-115">Recommended action</span></span>

<span data-ttu-id="deed2-116">Cette modification avec rupture affecte tous les utilisateurs qui configurent des valeurs sur <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions> .</span><span class="sxs-lookup"><span data-stu-id="deed2-116">This breaking change affects anyone who is configuring values on <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span></span> <span data-ttu-id="deed2-117">Si vous utilisez le Protocole ASP.NET Core Signalr MessagePack Hub et modifiez les options, mettez à jour votre utilisation pour utiliser la nouvelle API options, comme indiqué ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="deed2-117">If you're using the ASP.NET Core SignalR MessagePack Hub Protocol and modifying the options, update your usage to use the new options API as shown above.</span></span>

#### <a name="category"></a><span data-ttu-id="deed2-118">Category</span><span class="sxs-lookup"><span data-stu-id="deed2-118">Category</span></span>

<span data-ttu-id="deed2-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="deed2-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="deed2-120">API affectées</span><span class="sxs-lookup"><span data-stu-id="deed2-120">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
