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
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="8b581-103">Options de configuration au moment de l’exécution pour la mise en réseau</span><span class="sxs-lookup"><span data-stu-id="8b581-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="8b581-104">Protocole HTTP/2</span><span class="sxs-lookup"><span data-stu-id="8b581-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="8b581-105">Configure si la prise en charge du protocole HTTP/2 est activée.</span><span class="sxs-lookup"><span data-stu-id="8b581-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>
- <span data-ttu-id="8b581-106">Valeur par défaut : désactivé (`false`).</span><span class="sxs-lookup"><span data-stu-id="8b581-106">Default: Disabled (`false`).</span></span>
- <span data-ttu-id="8b581-107">Introduit dans .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="8b581-107">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="8b581-108">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="8b581-108">Setting name</span></span> | <span data-ttu-id="8b581-109">Valeurs</span><span class="sxs-lookup"><span data-stu-id="8b581-109">Values</span></span> |
| - | - |
| <span data-ttu-id="8b581-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="8b581-110">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="8b581-111">`false`-désactivé</span><span class="sxs-lookup"><span data-stu-id="8b581-111">`false` - disabled</span></span><br/><span data-ttu-id="8b581-112">activé `true`</span><span class="sxs-lookup"><span data-stu-id="8b581-112">`true` - enabled</span></span> |
| <span data-ttu-id="8b581-113">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="8b581-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="8b581-114">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="8b581-114">`0` - disabled</span></span><br/><span data-ttu-id="8b581-115">activé `1`</span><span class="sxs-lookup"><span data-stu-id="8b581-115">`1` - enabled</span></span> |

## <a name="sockets-http-handler"></a><span data-ttu-id="8b581-116">Gestionnaire HTTP de Sockets</span><span class="sxs-lookup"><span data-stu-id="8b581-116">Sockets HTTP handler</span></span>

- <span data-ttu-id="8b581-117">Configure si les API de mise en réseau de haut niveau, telles que <xref:System.Net.Http.HttpClient>, utilisent <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> ou l’implémentation de <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> basée sur [libbouclé](https://curl.haxx.se/libcurl/).</span><span class="sxs-lookup"><span data-stu-id="8b581-117">Configures whether high-level networking APIs, such as <xref:System.Net.Http.HttpClient>, use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or the implementation of <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> that's based on [libcurl](https://curl.haxx.se/libcurl/).</span></span>
- <span data-ttu-id="8b581-118">Valeur par défaut : utilisez <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> (`true`).</span><span class="sxs-lookup"><span data-stu-id="8b581-118">Default: Use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> (`true`).</span></span>
- <span data-ttu-id="8b581-119">Vous pouvez configurer ce paramètre par programmation en appelant la méthode <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8b581-119">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="8b581-120">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="8b581-120">Setting name</span></span> | <span data-ttu-id="8b581-121">Valeurs</span><span class="sxs-lookup"><span data-stu-id="8b581-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="8b581-122">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="8b581-122">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="8b581-123">`true` : active l’utilisation de <xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="8b581-123">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="8b581-124">`false` : active l’utilisation de <xref:System.Net.Http.HttpClientHandler></span><span class="sxs-lookup"><span data-stu-id="8b581-124">`false` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |
| <span data-ttu-id="8b581-125">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="8b581-125">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="8b581-126">`1` : active l’utilisation de <xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="8b581-126">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="8b581-127">`0` : active l’utilisation de <xref:System.Net.Http.HttpClientHandler></span><span class="sxs-lookup"><span data-stu-id="8b581-127">`0` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |
