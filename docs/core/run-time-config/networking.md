---
title: Paramètres de config de réseautage
description: Renseignez-vous sur les paramètres de course qui configurent le réseautage pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 8d02087ad7260cc78c096090bf3b06a716d34678
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989101"
---
# <a name="run-time-configuration-options-for-networking"></a>Options de configuration en temps d’exécution pour le réseautage

## <a name="http2-protocol"></a>Protocole HTTP/2

- Configure si le support pour le protocole HTTP/2 est activé.

- Défaut: Désactivé`false`( ).

- Introduit dans .NET Core 3.0.

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false`- désactivé<br/>`true`- activé |
| **Variable d’environnement** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0`- désactivé<br/>`1`- activé |

## <a name="usesocketshttphandler"></a>UtilisationSocketsHttpHandler

- Configurer <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> si <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> les utilisations ou<xref:System.Net.Http.WinHttpHandler> les `CurlHandler`anciennes piles de protocole HTTP (sur Windows et , une classe interne implémentée sur le dessus de [libcurl](https://curl.haxx.se/libcurl/), sur Linux).

  > [!NOTE]
  > Vous pouvez utiliser des API de réseautage de <xref:System.Net.Http.HttpClientHandler> haut niveau au lieu d’instantanéiser directement la classe. Ce paramètre affecte également la pile de protocole HTTP <xref:System.Net.Http.HttpClient> est utilisé par les API de réseautage de haut niveau, y compris et [HttpClientFactory](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118)).

- Défaut : <xref:System.Net.Http.SocketsHttpHandler> `true`Utilisation ( ).

- Vous pouvez configurer ce paramètre <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> programmatiquement en appelant la méthode.

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.UseSocketsHttpHandler` | `true`- permet l’utilisation de<xref:System.Net.Http.SocketsHttpHandler><br/>`false`- permet l’utilisation de <xref:System.Net.Http.WinHttpHandler> Windows ou [libcurl](https://curl.haxx.se/libcurl/) sur Linux |
| **Variable d’environnement** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1`- permet l’utilisation de<xref:System.Net.Http.SocketsHttpHandler><br/>`0`- permet l’utilisation de <xref:System.Net.Http.WinHttpHandler> Windows ou [libcurl](https://curl.haxx.se/libcurl/) sur Linux |

> [!NOTE]
> À partir de .NET `System.Net.Http.UseSocketsHttpHandler` 5, le réglage n’est plus disponible.
