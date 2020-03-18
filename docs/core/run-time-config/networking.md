---
title: Paramètres de config de réseautage
description: Renseignez-vous sur les paramètres de course qui configurent le réseautage pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 622c4afbd36d3d9004edbd9219145fa9e5d326ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74802770"
---
# <a name="run-time-configuration-options-for-networking"></a>Options de configuration en temps d’exécution pour le réseautage

## <a name="http2-protocol"></a>Protocole HTTP/2

- Configure si le support pour le protocole HTTP/2 est activé.
- Défaut: Désactivé`false`( ).
- Introduit dans .NET Core 3.0.

| | Nom du paramètre | Valeurs |
| - | - |
| **runtimeconfig.json** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false`- désactivé<br/>`true`- activé |
| **Variable de l’environnement** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0`- désactivé<br/>`1`- activé |

## <a name="sockets-http-handler"></a>Sockets HTTP gestionnaire

- Configure si les API de réseautage <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> de haut <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> niveau, telles que <xref:System.Net.Http.HttpClient>, l’utilisation ou la mise en œuvre de qui est basée sur [libcurl](https://curl.haxx.se/libcurl/).
- Défaut : <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> `true`Utilisation ( ).
- Vous pouvez configurer ce paramètre <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> programmatiquement en appelant la méthode.

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.UseSocketsHttpHandler` | `true`- permet l’utilisation de<xref:System.Net.Http.SocketsHttpHandler><br/>`false`- permet l’utilisation de<xref:System.Net.Http.HttpClientHandler> |
| **Variable de l’environnement** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1`- permet l’utilisation de<xref:System.Net.Http.SocketsHttpHandler><br/>`0`- permet l’utilisation de<xref:System.Net.Http.HttpClientHandler> |
