---
title: Paramètres de configuration de mise en réseau
description: En savoir plus sur les paramètres d’exécution qui configurent la mise en réseau pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: bda608e83bb1b093d7d9b860de9607f6734720aa
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188300"
---
# <a name="run-time-configuration-options-for-networking"></a>Options de configuration au moment de l’exécution pour la mise en réseau

## <a name="http2-protocol"></a>Protocole HTTP/2

- Configure si la prise en charge du protocole HTTP/2 est activée.

- Introduit dans .NET Core 3,0.

- .NET Core 3,0 uniquement : Si vous omettez ce paramètre, la prise en charge du protocole HTTP/2 est désactivée. Cela équivaut à définir la valeur sur `false` .

- .NET Core 3,1 et .NET 5 + : Si vous omettez ce paramètre, la prise en charge du protocole HTTP/2 est activée. Cela équivaut à définir la valeur sur `true` .

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.js** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false` -désactivé<br/>`true` -activé |
| **Variable d'environnement** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0` -désactivé<br/>`1` -activé |

## <a name="usesocketshttphandler"></a>UseSocketsHttpHandler

- Configure si <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> utilise <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> ou des piles de protocole http plus anciennes ( <xref:System.Net.Http.WinHttpHandler> sur Windows et `CurlHandler` , une classe interne implémentée sur [libbouclé](https://curl.haxx.se/libcurl/), sur Linux).

  > [!NOTE]
  > Vous pouvez utiliser des API de mise en réseau de haut niveau au lieu d’instancier directement la <xref:System.Net.Http.HttpClientHandler> classe. Ce paramètre affecte également la pile de protocole HTTP utilisée par les API de mise en réseau de haut niveau, y compris <xref:System.Net.Http.HttpClient> et [HttpClientFactory](/previous-versions/aspnet/hh995280(v=vs.118)).

- Si vous omettez ce paramètre, <xref:System.Net.Http.HttpClientHandler> utilise <xref:System.Net.Http.SocketsHttpHandler> . Cela équivaut à définir la valeur sur `true` .

- Vous pouvez configurer ce paramètre par programmation en appelant la <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> méthode.

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.js** | `System.Net.Http.UseSocketsHttpHandler` | `true` -active l’utilisation de <xref:System.Net.Http.SocketsHttpHandler><br/>`false` -active l’utilisation de <xref:System.Net.Http.WinHttpHandler> sur Windows ou [libbouclé](https://curl.haxx.se/libcurl/) sur Linux |
| **Variable d'environnement** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1` -active l’utilisation de <xref:System.Net.Http.SocketsHttpHandler><br/>`0` -active l’utilisation de <xref:System.Net.Http.WinHttpHandler> sur Windows ou [libbouclé](https://curl.haxx.se/libcurl/) sur Linux |

> [!NOTE]
> À compter de .NET 5, le `System.Net.Http.UseSocketsHttpHandler` paramètre n’est plus disponible.

## <a name="latin1-headers-net-core-31-only"></a>En-têtes latin1 (.NET Core 3,1 uniquement)

- Ce commutateur permet de détendre la validation de l’en-tête HTTP, ce qui permet <xref:System.Net.Http.SocketsHttpHandler> à d’envoyer des caractères encodés ISO-8859-1 (latin-1) dans les en-têtes.

- Si vous omettez ce paramètre, une tentative d’envoi d’un caractère non-ASCII se traduira par <xref:System.Net.Http.HttpRequestException> . Cela équivaut à définir la valeur sur `false` .

| | Nom du paramètre | Valeurs |
| - | - | - |
| **runtimeconfig.js** | `System.Net.Http.SocketsHttpHandler.AllowLatin1Headers` | `false` -désactivé<br/>`true` -activé |
| **Variable d'environnement** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_ALLOWLATIN1HEADERS` | `0` -désactivé<br/>`1` -activé |

> [!NOTE]
> Cette option est disponible uniquement dans .NET Core 3,1 depuis la version 3.1.9, et non dans les versions antérieures ou ultérieures. Dans .NET 5, nous vous recommandons d’utiliser <xref:System.Net.Http.SocketsHttpHandler.RequestHeaderEncodingSelector> .
