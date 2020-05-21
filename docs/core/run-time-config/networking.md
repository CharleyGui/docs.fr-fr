---
title: Paramètres de configuration de mise en réseau
description: En savoir plus sur les paramètres d’exécution qui configurent la mise en réseau pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 6b5e03b127f95911b712b66c0be8a4f5a2929fc2
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761939"
---
# <a name="run-time-configuration-options-for-networking"></a>Options de configuration au moment de l’exécution pour la mise en réseau

## <a name="http2-protocol"></a>Protocole HTTP/2

- Configure si la prise en charge du protocole HTTP/2 est activée.

- Si vous omettez ce paramètre, la prise en charge du protocole HTTP/2 est désactivée. Cela équivaut à définir la valeur sur `false` .

- Introduit dans .NET Core 3,0.

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false`-désactivé<br/>`true`-activé |
| **Variable d’environnement** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0`-désactivé<br/>`1`-activé |

## <a name="usesocketshttphandler"></a>UseSocketsHttpHandler

- Configure si <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> utilise <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> ou des piles de protocole http plus anciennes ( <xref:System.Net.Http.WinHttpHandler> sur Windows et `CurlHandler` , une classe interne implémentée sur [libbouclé](https://curl.haxx.se/libcurl/), sur Linux).

  > [!NOTE]
  > Vous pouvez utiliser des API de mise en réseau de haut niveau au lieu d’instancier directement la <xref:System.Net.Http.HttpClientHandler> classe. Ce paramètre affecte également la pile de protocole HTTP utilisée par les API de mise en réseau de haut niveau, y compris <xref:System.Net.Http.HttpClient> et [HttpClientFactory](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118)).

- Si vous omettez ce paramètre, <xref:System.Net.Http.HttpClientHandler> utilise <xref:System.Net.Http.SocketsHttpHandler> . Cela équivaut à définir la valeur sur `true` .

- Vous pouvez configurer ce paramètre par programmation en appelant la <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> méthode.

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig. JSON** | `System.Net.Http.UseSocketsHttpHandler` | `true`-active l’utilisation de<xref:System.Net.Http.SocketsHttpHandler><br/>`false`-active l’utilisation de <xref:System.Net.Http.WinHttpHandler> sur Windows ou [libbouclé](https://curl.haxx.se/libcurl/) sur Linux |
| **Variable d’environnement** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1`-active l’utilisation de<xref:System.Net.Http.SocketsHttpHandler><br/>`0`-active l’utilisation de <xref:System.Net.Http.WinHttpHandler> sur Windows ou [libbouclé](https://curl.haxx.se/libcurl/) sur Linux |

> [!NOTE]
> À compter de .NET 5, le `System.Net.Http.UseSocketsHttpHandler` paramètre n’est plus disponible.
