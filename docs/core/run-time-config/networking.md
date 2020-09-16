---
title: Paramètres de configuration de mise en réseau
description: En savoir plus sur les paramètres d’exécution qui configurent la mise en réseau pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: d43b68206cc82f4a41df02bd5998702b4f5d0590
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538131"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="74cfe-103">Options de configuration au moment de l’exécution pour la mise en réseau</span><span class="sxs-lookup"><span data-stu-id="74cfe-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="74cfe-104">Protocole HTTP/2</span><span class="sxs-lookup"><span data-stu-id="74cfe-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="74cfe-105">Configure si la prise en charge du protocole HTTP/2 est activée.</span><span class="sxs-lookup"><span data-stu-id="74cfe-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>

- <span data-ttu-id="74cfe-106">Si vous omettez ce paramètre, la prise en charge du protocole HTTP/2 est désactivée.</span><span class="sxs-lookup"><span data-stu-id="74cfe-106">If you omit this setting, support for the HTTP/2 protocol is disabled.</span></span> <span data-ttu-id="74cfe-107">Cela équivaut à définir la valeur sur `false` .</span><span class="sxs-lookup"><span data-stu-id="74cfe-107">This is equivalent to setting the value to `false`.</span></span>

- <span data-ttu-id="74cfe-108">Introduit dans .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="74cfe-108">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="74cfe-109">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="74cfe-109">Setting name</span></span> | <span data-ttu-id="74cfe-110">Valeurs</span><span class="sxs-lookup"><span data-stu-id="74cfe-110">Values</span></span> |
| - | - | - |
| <span data-ttu-id="74cfe-111">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="74cfe-111">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="74cfe-112">`false` -désactivé</span><span class="sxs-lookup"><span data-stu-id="74cfe-112">`false` - disabled</span></span><br/><span data-ttu-id="74cfe-113">`true` -activé</span><span class="sxs-lookup"><span data-stu-id="74cfe-113">`true` - enabled</span></span> |
| <span data-ttu-id="74cfe-114">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="74cfe-114">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="74cfe-115">`0` -désactivé</span><span class="sxs-lookup"><span data-stu-id="74cfe-115">`0` - disabled</span></span><br/><span data-ttu-id="74cfe-116">`1` -activé</span><span class="sxs-lookup"><span data-stu-id="74cfe-116">`1` - enabled</span></span> |

## <a name="usesocketshttphandler"></a><span data-ttu-id="74cfe-117">UseSocketsHttpHandler</span><span class="sxs-lookup"><span data-stu-id="74cfe-117">UseSocketsHttpHandler</span></span>

- <span data-ttu-id="74cfe-118">Configure si <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> utilise <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> ou des piles de protocole http plus anciennes ( <xref:System.Net.Http.WinHttpHandler> sur Windows et `CurlHandler` , une classe interne implémentée sur [libbouclé](https://curl.haxx.se/libcurl/), sur Linux).</span><span class="sxs-lookup"><span data-stu-id="74cfe-118">Configures whether <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> uses <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or older HTTP protocol stacks (<xref:System.Net.Http.WinHttpHandler> on Windows and `CurlHandler`, an internal class implemented on top of [libcurl](https://curl.haxx.se/libcurl/), on Linux).</span></span>

  > [!NOTE]
  > <span data-ttu-id="74cfe-119">Vous pouvez utiliser des API de mise en réseau de haut niveau au lieu d’instancier directement la <xref:System.Net.Http.HttpClientHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="74cfe-119">You may be using high-level networking APIs instead of directly instantiating the <xref:System.Net.Http.HttpClientHandler> class.</span></span> <span data-ttu-id="74cfe-120">Ce paramètre affecte également la pile de protocole HTTP utilisée par les API de mise en réseau de haut niveau, y compris <xref:System.Net.Http.HttpClient> et [HttpClientFactory](/previous-versions/aspnet/hh995280(v=vs.118)).</span><span class="sxs-lookup"><span data-stu-id="74cfe-120">This setting also affects which HTTP protocol stack is used by high-level networking APIs, including <xref:System.Net.Http.HttpClient> and [HttpClientFactory](/previous-versions/aspnet/hh995280(v=vs.118)).</span></span>

- <span data-ttu-id="74cfe-121">Si vous omettez ce paramètre, <xref:System.Net.Http.HttpClientHandler> utilise <xref:System.Net.Http.SocketsHttpHandler> .</span><span class="sxs-lookup"><span data-stu-id="74cfe-121">If you omit this setting, <xref:System.Net.Http.HttpClientHandler> uses <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="74cfe-122">Cela équivaut à définir la valeur sur `true` .</span><span class="sxs-lookup"><span data-stu-id="74cfe-122">This is equivalent to setting the value to `true`.</span></span>

- <span data-ttu-id="74cfe-123">Vous pouvez configurer ce paramètre par programmation en appelant la <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="74cfe-123">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="74cfe-124">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="74cfe-124">Setting name</span></span> | <span data-ttu-id="74cfe-125">Valeurs</span><span class="sxs-lookup"><span data-stu-id="74cfe-125">Values</span></span> |
| - | - | - |
| <span data-ttu-id="74cfe-126">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="74cfe-126">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="74cfe-127">`true` -active l’utilisation de <xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="74cfe-127">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="74cfe-128">`false` -active l’utilisation de <xref:System.Net.Http.WinHttpHandler> sur Windows ou [libbouclé](https://curl.haxx.se/libcurl/) sur Linux</span><span class="sxs-lookup"><span data-stu-id="74cfe-128">`false` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |
| <span data-ttu-id="74cfe-129">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="74cfe-129">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="74cfe-130">`1` -active l’utilisation de <xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="74cfe-130">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="74cfe-131">`0` -active l’utilisation de <xref:System.Net.Http.WinHttpHandler> sur Windows ou [libbouclé](https://curl.haxx.se/libcurl/) sur Linux</span><span class="sxs-lookup"><span data-stu-id="74cfe-131">`0` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |

> [!NOTE]
> <span data-ttu-id="74cfe-132">À compter de .NET 5, le `System.Net.Http.UseSocketsHttpHandler` paramètre n’est plus disponible.</span><span class="sxs-lookup"><span data-stu-id="74cfe-132">Starting in .NET 5, the `System.Net.Http.UseSocketsHttpHandler` setting is no longer available.</span></span>
