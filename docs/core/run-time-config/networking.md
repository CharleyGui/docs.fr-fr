---
title: Paramètres de configuration de mise en réseau
description: En savoir plus sur les paramètres d’exécution qui configurent la mise en réseau pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 622c4afbd36d3d9004edbd9219145fa9e5d326ae
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802770"
---
# <a name="run-time-configuration-options-for-networking"></a>Options de configuration au moment de l’exécution pour la mise en réseau

## <a name="http2-protocol"></a>Protocole HTTP/2

- Configure si la prise en charge du protocole HTTP/2 est activée.
- Valeur par défaut : désactivé (`false`).
- Introduit dans .NET Core 3,0.

| | Nom du paramètre | Valeurs |
| - | - |
| **runtimeconfig. JSON** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false`-désactivé<br/>activé `true` |
| **Variable d'environnement** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0`-désactivé<br/>activé `1` |

## <a name="sockets-http-handler"></a>Gestionnaire HTTP de Sockets

- Configure si les API de mise en réseau de haut niveau, telles que <xref:System.Net.Http.HttpClient>, utilisent <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> ou l’implémentation de <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> basée sur [libbouclé](https://curl.haxx.se/libcurl/).
- Valeur par défaut : utilisez <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> (`true`).
- Vous pouvez configurer ce paramètre par programmation en appelant la méthode <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>.

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | `System.Net.Http.UseSocketsHttpHandler` | `true` : active l’utilisation de <xref:System.Net.Http.SocketsHttpHandler><br/>`false` : active l’utilisation de <xref:System.Net.Http.HttpClientHandler> |
| **Variable d'environnement** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1` : active l’utilisation de <xref:System.Net.Http.SocketsHttpHandler><br/>`0` : active l’utilisation de <xref:System.Net.Http.HttpClientHandler> |
