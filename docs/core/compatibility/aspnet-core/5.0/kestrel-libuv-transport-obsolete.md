---
title: 'Modification avec rupture : Kestrel : transport Libuv marqué comme obsolète'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulé Kestrel : Libuv transport marqué comme obsolète'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: f66b9b646671e07957e6d30a95333d392eb29617
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761010"
---
# <a name="kestrel-libuv-transport-marked-as-obsolete"></a>Kestrel : transport Libuv marqué comme obsolète

Les versions antérieures de ASP.NET Core utilisé Libuv comme un détail d’implémentation de la façon dont les entrées et sorties asynchrones ont été effectuées. Dans ASP.NET Core 2,0, un transport alternatif <xref:System.Net.Sockets.Socket> a été développé. Dans ASP.NET Core 2,1, Kestrel est passé à l’utilisation du `Socket` transport basé sur-based par défaut. La prise en charge de Libuv a été maintenue pour des raisons de compatibilité.

À ce stade, l’utilisation du `Socket` transport basé sur est bien plus courante que le transport Libuv. Par conséquent, la prise en charge de Libuv est marquée comme obsolète dans .NET 5,0 et sera entièrement supprimée dans .NET 6,0.

Dans le cadre de cette modification, la prise en charge Libuv pour les nouvelles plateformes de système d’exploitation (par exemple, Windows ARM64) ne sera pas ajoutée dans le délai de .NET 5,0.

Pour plus d’informations sur les problèmes de blocage qui nécessitent l’utilisation du transport Libuv, consultez le problème GitHub à l’adresse [dotnet/aspnetcore # 23409](https://github.com/dotnet/aspnetcore/issues/23409).

## <a name="version-introduced"></a>Version introduite

5,0 Preview 8

## <a name="old-behavior"></a>Ancien comportement

Les API Libuv ne sont pas marquées comme obsolètes.

## <a name="new-behavior"></a>Nouveau comportement

Les API Libuv sont marquées comme obsolètes.

## <a name="reason-for-change"></a>Motif de modification

La `Socket` valeur par défaut est le transport basé sur. Il n’existe aucune raison impérieuse de continuer à utiliser le transport Libuv.

## <a name="recommended-action"></a>Action recommandée

Cesser d’utiliser le [package Libuv](https://www.nuget.org/packages/Libuv) et les méthodes d’extension.

## <a name="affected-apis"></a>API affectées

- [WebHostBuilderLibuvExtensions](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions?view=aspnetcore-3.0)
- [WebHostBuilderLibuvExtensions.UseLibuv](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions.uselibuv?view=aspnetcore-3.0)
- [Microsoft. AspNetCore. Server. Kestrel. transport. Libuv. LibuvTransportOptions](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions?view=aspnetcore-3.0)
- [Microsoft. AspNetCore. Server. Kestrel. transport. Libuv. LibuvTransportOptions. ThreadCount](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.threadcount?view=aspnetcore-3.0)
- [Microsoft. AspNetCore. Server. Kestrel. transport. Libuv. LibuvTransportOptions. NoDelay](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.nodelay?view=aspnetcore-3.0)
- [Microsoft. AspNetCore. Server. Kestrel. transport. Libuv. LibuvTransportOptions. MaxWriteBufferSize](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxwritebuffersize?view=aspnetcore-3.0)
- [Microsoft. AspNetCore. Server. Kestrel. transport. Libuv. LibuvTransportOptions. MaxReadBufferSize](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxreadbuffersize?view=aspnetcore-3.0)
- `Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.Backlog`

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.AspNetCore.Hosting.WebHostBuilderLibuvExtensions`
- `Overload:Microsoft.AspNetCore.Hosting.WebHostBuilderLibuvExtensions.UseLibuv`
- `T:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.ThreadCount`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.NoDelay`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxWriteBufferSize`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxReadBufferSize`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.Backlog`

-->
