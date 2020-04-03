---
title: Paramètres de config de réseautage
description: Renseignez-vous sur les paramètres de course qui configurent le réseautage pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: f5ea47f0444a911dc2347a66817cabf585fd8e70
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635423"
---
# <a name="run-time-configuration-options-for-networking"></a>Options de configuration en temps d’exécution pour le réseautage

## <a name="http2-protocol"></a>Protocole HTTP/2

- Configure si le support pour le protocole HTTP/2 est activé.
- Défaut: Désactivé`false`( ).
- Introduit dans .NET Core 3.0.

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false`- désactivé<br/>`true`- activé |
| **Variable de l’environnement** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0`- désactivé<br/>`1`- activé |

## <a name="usesocketshttphandler"></a>UtilisationSocketsHttpHandler

- Configure si les API de réseautage <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> de haut <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> niveau, telles que <xref:System.Net.Http.HttpClient>, l’utilisation ou la mise en œuvre de qui est basée sur [libcurl](https://curl.haxx.se/libcurl/).
- Défaut : <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> `true`Utilisation ( ).
- Vous pouvez configurer ce paramètre <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> programmatiquement en appelant la méthode.

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.UseSocketsHttpHandler` | `true`- permet l’utilisation de<xref:System.Net.Http.SocketsHttpHandler><br/>`false`- permet l’utilisation de<xref:System.Net.Http.HttpClientHandler> |
| **Variable de l’environnement** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1`- permet l’utilisation de<xref:System.Net.Http.SocketsHttpHandler><br/>`0`- permet l’utilisation de<xref:System.Net.Http.HttpClientHandler> |

> [!NOTE]
> À partir de .NET `System.Net.Http.UseSocketsHttpHandler` 5, le réglage n’est plus disponible.
