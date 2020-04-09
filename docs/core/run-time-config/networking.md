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
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="57af4-103">Options de configuration en temps d’exécution pour le réseautage</span><span class="sxs-lookup"><span data-stu-id="57af4-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="57af4-104">Protocole HTTP/2</span><span class="sxs-lookup"><span data-stu-id="57af4-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="57af4-105">Configure si le support pour le protocole HTTP/2 est activé.</span><span class="sxs-lookup"><span data-stu-id="57af4-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>

- <span data-ttu-id="57af4-106">Défaut: Désactivé`false`( ).</span><span class="sxs-lookup"><span data-stu-id="57af4-106">Default: Disabled (`false`).</span></span>

- <span data-ttu-id="57af4-107">Introduit dans .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="57af4-107">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="57af4-108">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="57af4-108">Setting name</span></span> | <span data-ttu-id="57af4-109">Valeurs</span><span class="sxs-lookup"><span data-stu-id="57af4-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="57af4-110">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="57af4-110">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="57af4-111">`false`- désactivé</span><span class="sxs-lookup"><span data-stu-id="57af4-111">`false` - disabled</span></span><br/><span data-ttu-id="57af4-112">`true`- activé</span><span class="sxs-lookup"><span data-stu-id="57af4-112">`true` - enabled</span></span> |
| <span data-ttu-id="57af4-113">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="57af4-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="57af4-114">`0`- désactivé</span><span class="sxs-lookup"><span data-stu-id="57af4-114">`0` - disabled</span></span><br/><span data-ttu-id="57af4-115">`1`- activé</span><span class="sxs-lookup"><span data-stu-id="57af4-115">`1` - enabled</span></span> |

## <a name="usesocketshttphandler"></a><span data-ttu-id="57af4-116">UtilisationSocketsHttpHandler</span><span class="sxs-lookup"><span data-stu-id="57af4-116">UseSocketsHttpHandler</span></span>

- <span data-ttu-id="57af4-117">Configurer <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> si <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> les utilisations ou<xref:System.Net.Http.WinHttpHandler> les `CurlHandler`anciennes piles de protocole HTTP (sur Windows et , une classe interne implémentée sur le dessus de [libcurl](https://curl.haxx.se/libcurl/), sur Linux).</span><span class="sxs-lookup"><span data-stu-id="57af4-117">Configures whether <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> uses <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or older HTTP protocol stacks (<xref:System.Net.Http.WinHttpHandler> on Windows and `CurlHandler`, an internal class implemented on top of [libcurl](https://curl.haxx.se/libcurl/), on Linux).</span></span>

  > [!NOTE]
  > <span data-ttu-id="57af4-118">Vous pouvez utiliser des API de réseautage de <xref:System.Net.Http.HttpClientHandler> haut niveau au lieu d’instantanéiser directement la classe.</span><span class="sxs-lookup"><span data-stu-id="57af4-118">You may be using high-level networking APIs instead of directly instantiating the <xref:System.Net.Http.HttpClientHandler> class.</span></span> <span data-ttu-id="57af4-119">Ce paramètre affecte également la pile de protocole HTTP <xref:System.Net.Http.HttpClient> est utilisé par les API de réseautage de haut niveau, y compris et [HttpClientFactory](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118)).</span><span class="sxs-lookup"><span data-stu-id="57af4-119">This setting also affects which HTTP protocol stack is used by high-level networking APIs, including <xref:System.Net.Http.HttpClient> and [HttpClientFactory](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118)).</span></span>

- <span data-ttu-id="57af4-120">Défaut : <xref:System.Net.Http.SocketsHttpHandler> `true`Utilisation ( ).</span><span class="sxs-lookup"><span data-stu-id="57af4-120">Default: Use <xref:System.Net.Http.SocketsHttpHandler> (`true`).</span></span>

- <span data-ttu-id="57af4-121">Vous pouvez configurer ce paramètre <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> programmatiquement en appelant la méthode.</span><span class="sxs-lookup"><span data-stu-id="57af4-121">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="57af4-122">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="57af4-122">Setting name</span></span> | <span data-ttu-id="57af4-123">Valeurs</span><span class="sxs-lookup"><span data-stu-id="57af4-123">Values</span></span> |
| - | - | - |
| <span data-ttu-id="57af4-124">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="57af4-124">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="57af4-125">`true`- permet l’utilisation de<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="57af4-125">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="57af4-126">`false`- permet l’utilisation de <xref:System.Net.Http.WinHttpHandler> Windows ou [libcurl](https://curl.haxx.se/libcurl/) sur Linux</span><span class="sxs-lookup"><span data-stu-id="57af4-126">`false` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |
| <span data-ttu-id="57af4-127">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="57af4-127">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="57af4-128">`1`- permet l’utilisation de<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="57af4-128">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="57af4-129">`0`- permet l’utilisation de <xref:System.Net.Http.WinHttpHandler> Windows ou [libcurl](https://curl.haxx.se/libcurl/) sur Linux</span><span class="sxs-lookup"><span data-stu-id="57af4-129">`0` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |

> [!NOTE]
> <span data-ttu-id="57af4-130">À partir de .NET `System.Net.Http.UseSocketsHttpHandler` 5, le réglage n’est plus disponible.</span><span class="sxs-lookup"><span data-stu-id="57af4-130">Starting in .NET 5, the `System.Net.Http.UseSocketsHttpHandler` setting is no longer available.</span></span>
