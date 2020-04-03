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
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="a6390-103">Options de configuration en temps d’exécution pour le réseautage</span><span class="sxs-lookup"><span data-stu-id="a6390-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="a6390-104">Protocole HTTP/2</span><span class="sxs-lookup"><span data-stu-id="a6390-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="a6390-105">Configure si le support pour le protocole HTTP/2 est activé.</span><span class="sxs-lookup"><span data-stu-id="a6390-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>
- <span data-ttu-id="a6390-106">Défaut: Désactivé`false`( ).</span><span class="sxs-lookup"><span data-stu-id="a6390-106">Default: Disabled (`false`).</span></span>
- <span data-ttu-id="a6390-107">Introduit dans .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="a6390-107">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="a6390-108">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="a6390-108">Setting name</span></span> | <span data-ttu-id="a6390-109">Valeurs</span><span class="sxs-lookup"><span data-stu-id="a6390-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a6390-110">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="a6390-110">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="a6390-111">`false`- désactivé</span><span class="sxs-lookup"><span data-stu-id="a6390-111">`false` - disabled</span></span><br/><span data-ttu-id="a6390-112">`true`- activé</span><span class="sxs-lookup"><span data-stu-id="a6390-112">`true` - enabled</span></span> |
| <span data-ttu-id="a6390-113">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="a6390-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="a6390-114">`0`- désactivé</span><span class="sxs-lookup"><span data-stu-id="a6390-114">`0` - disabled</span></span><br/><span data-ttu-id="a6390-115">`1`- activé</span><span class="sxs-lookup"><span data-stu-id="a6390-115">`1` - enabled</span></span> |

## <a name="usesocketshttphandler"></a><span data-ttu-id="a6390-116">UtilisationSocketsHttpHandler</span><span class="sxs-lookup"><span data-stu-id="a6390-116">UseSocketsHttpHandler</span></span>

- <span data-ttu-id="a6390-117">Configure si les API de réseautage <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> de haut <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> niveau, telles que <xref:System.Net.Http.HttpClient>, l’utilisation ou la mise en œuvre de qui est basée sur [libcurl](https://curl.haxx.se/libcurl/).</span><span class="sxs-lookup"><span data-stu-id="a6390-117">Configures whether high-level networking APIs, such as <xref:System.Net.Http.HttpClient>, use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or the implementation of <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> that's based on [libcurl](https://curl.haxx.se/libcurl/).</span></span>
- <span data-ttu-id="a6390-118">Défaut : <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> `true`Utilisation ( ).</span><span class="sxs-lookup"><span data-stu-id="a6390-118">Default: Use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> (`true`).</span></span>
- <span data-ttu-id="a6390-119">Vous pouvez configurer ce paramètre <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> programmatiquement en appelant la méthode.</span><span class="sxs-lookup"><span data-stu-id="a6390-119">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="a6390-120">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="a6390-120">Setting name</span></span> | <span data-ttu-id="a6390-121">Valeurs</span><span class="sxs-lookup"><span data-stu-id="a6390-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a6390-122">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="a6390-122">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="a6390-123">`true`- permet l’utilisation de<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="a6390-123">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="a6390-124">`false`- permet l’utilisation de<xref:System.Net.Http.HttpClientHandler></span><span class="sxs-lookup"><span data-stu-id="a6390-124">`false` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |
| <span data-ttu-id="a6390-125">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="a6390-125">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="a6390-126">`1`- permet l’utilisation de<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="a6390-126">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="a6390-127">`0`- permet l’utilisation de<xref:System.Net.Http.HttpClientHandler></span><span class="sxs-lookup"><span data-stu-id="a6390-127">`0` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |

> [!NOTE]
> <span data-ttu-id="a6390-128">À partir de .NET `System.Net.Http.UseSocketsHttpHandler` 5, le réglage n’est plus disponible.</span><span class="sxs-lookup"><span data-stu-id="a6390-128">Starting in .NET 5, the `System.Net.Http.UseSocketsHttpHandler` setting is no longer available.</span></span>
