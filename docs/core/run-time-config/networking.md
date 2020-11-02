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
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="091a9-103">Options de configuration au moment de l’exécution pour la mise en réseau</span><span class="sxs-lookup"><span data-stu-id="091a9-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="091a9-104">Protocole HTTP/2</span><span class="sxs-lookup"><span data-stu-id="091a9-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="091a9-105">Configure si la prise en charge du protocole HTTP/2 est activée.</span><span class="sxs-lookup"><span data-stu-id="091a9-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>

- <span data-ttu-id="091a9-106">Introduit dans .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="091a9-106">Introduced in .NET Core 3.0.</span></span>

- <span data-ttu-id="091a9-107">.NET Core 3,0 uniquement : Si vous omettez ce paramètre, la prise en charge du protocole HTTP/2 est désactivée.</span><span class="sxs-lookup"><span data-stu-id="091a9-107">.NET Core 3.0 only: If you omit this setting, support for the HTTP/2 protocol is disabled.</span></span> <span data-ttu-id="091a9-108">Cela équivaut à définir la valeur sur `false` .</span><span class="sxs-lookup"><span data-stu-id="091a9-108">This is equivalent to setting the value to `false`.</span></span>

- <span data-ttu-id="091a9-109">.NET Core 3,1 et .NET 5 + : Si vous omettez ce paramètre, la prise en charge du protocole HTTP/2 est activée.</span><span class="sxs-lookup"><span data-stu-id="091a9-109">.NET Core 3.1 and .NET 5+: If you omit this setting, support for the HTTP/2 protocol is enabled.</span></span> <span data-ttu-id="091a9-110">Cela équivaut à définir la valeur sur `true` .</span><span class="sxs-lookup"><span data-stu-id="091a9-110">This is equivalent to setting the value to `true`.</span></span>

| | <span data-ttu-id="091a9-111">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="091a9-111">Setting name</span></span> | <span data-ttu-id="091a9-112">Valeurs</span><span class="sxs-lookup"><span data-stu-id="091a9-112">Values</span></span> |
| - | - | - |
| <span data-ttu-id="091a9-113">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="091a9-113">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="091a9-114">`false` -désactivé</span><span class="sxs-lookup"><span data-stu-id="091a9-114">`false` - disabled</span></span><br/><span data-ttu-id="091a9-115">`true` -activé</span><span class="sxs-lookup"><span data-stu-id="091a9-115">`true` - enabled</span></span> |
| <span data-ttu-id="091a9-116">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="091a9-116">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="091a9-117">`0` -désactivé</span><span class="sxs-lookup"><span data-stu-id="091a9-117">`0` - disabled</span></span><br/><span data-ttu-id="091a9-118">`1` -activé</span><span class="sxs-lookup"><span data-stu-id="091a9-118">`1` - enabled</span></span> |

## <a name="usesocketshttphandler"></a><span data-ttu-id="091a9-119">UseSocketsHttpHandler</span><span class="sxs-lookup"><span data-stu-id="091a9-119">UseSocketsHttpHandler</span></span>

- <span data-ttu-id="091a9-120">Configure si <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> utilise <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> ou des piles de protocole http plus anciennes ( <xref:System.Net.Http.WinHttpHandler> sur Windows et `CurlHandler` , une classe interne implémentée sur [libbouclé](https://curl.haxx.se/libcurl/), sur Linux).</span><span class="sxs-lookup"><span data-stu-id="091a9-120">Configures whether <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> uses <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or older HTTP protocol stacks (<xref:System.Net.Http.WinHttpHandler> on Windows and `CurlHandler`, an internal class implemented on top of [libcurl](https://curl.haxx.se/libcurl/), on Linux).</span></span>

  > [!NOTE]
  > <span data-ttu-id="091a9-121">Vous pouvez utiliser des API de mise en réseau de haut niveau au lieu d’instancier directement la <xref:System.Net.Http.HttpClientHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="091a9-121">You may be using high-level networking APIs instead of directly instantiating the <xref:System.Net.Http.HttpClientHandler> class.</span></span> <span data-ttu-id="091a9-122">Ce paramètre affecte également la pile de protocole HTTP utilisée par les API de mise en réseau de haut niveau, y compris <xref:System.Net.Http.HttpClient> et [HttpClientFactory](/previous-versions/aspnet/hh995280(v=vs.118)).</span><span class="sxs-lookup"><span data-stu-id="091a9-122">This setting also affects which HTTP protocol stack is used by high-level networking APIs, including <xref:System.Net.Http.HttpClient> and [HttpClientFactory](/previous-versions/aspnet/hh995280(v=vs.118)).</span></span>

- <span data-ttu-id="091a9-123">Si vous omettez ce paramètre, <xref:System.Net.Http.HttpClientHandler> utilise <xref:System.Net.Http.SocketsHttpHandler> .</span><span class="sxs-lookup"><span data-stu-id="091a9-123">If you omit this setting, <xref:System.Net.Http.HttpClientHandler> uses <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="091a9-124">Cela équivaut à définir la valeur sur `true` .</span><span class="sxs-lookup"><span data-stu-id="091a9-124">This is equivalent to setting the value to `true`.</span></span>

- <span data-ttu-id="091a9-125">Vous pouvez configurer ce paramètre par programmation en appelant la <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="091a9-125">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="091a9-126">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="091a9-126">Setting name</span></span> | <span data-ttu-id="091a9-127">Valeurs</span><span class="sxs-lookup"><span data-stu-id="091a9-127">Values</span></span> |
| - | - | - |
| <span data-ttu-id="091a9-128">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="091a9-128">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="091a9-129">`true` -active l’utilisation de <xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="091a9-129">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="091a9-130">`false` -active l’utilisation de <xref:System.Net.Http.WinHttpHandler> sur Windows ou [libbouclé](https://curl.haxx.se/libcurl/) sur Linux</span><span class="sxs-lookup"><span data-stu-id="091a9-130">`false` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |
| <span data-ttu-id="091a9-131">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="091a9-131">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="091a9-132">`1` -active l’utilisation de <xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="091a9-132">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="091a9-133">`0` -active l’utilisation de <xref:System.Net.Http.WinHttpHandler> sur Windows ou [libbouclé](https://curl.haxx.se/libcurl/) sur Linux</span><span class="sxs-lookup"><span data-stu-id="091a9-133">`0` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |

> [!NOTE]
> <span data-ttu-id="091a9-134">À compter de .NET 5, le `System.Net.Http.UseSocketsHttpHandler` paramètre n’est plus disponible.</span><span class="sxs-lookup"><span data-stu-id="091a9-134">Starting in .NET 5, the `System.Net.Http.UseSocketsHttpHandler` setting is no longer available.</span></span>

## <a name="latin1-headers-net-core-31-only"></a><span data-ttu-id="091a9-135">En-têtes latin1 (.NET Core 3,1 uniquement)</span><span class="sxs-lookup"><span data-stu-id="091a9-135">Latin1 headers (.NET Core 3.1 only)</span></span>

- <span data-ttu-id="091a9-136">Ce commutateur permet de détendre la validation de l’en-tête HTTP, ce qui permet <xref:System.Net.Http.SocketsHttpHandler> à d’envoyer des caractères encodés ISO-8859-1 (latin-1) dans les en-têtes.</span><span class="sxs-lookup"><span data-stu-id="091a9-136">This switch allows relaxing the HTTP header validation, enabling <xref:System.Net.Http.SocketsHttpHandler> to send ISO-8859-1 (Latin-1) encoded characters in headers.</span></span>

- <span data-ttu-id="091a9-137">Si vous omettez ce paramètre, une tentative d’envoi d’un caractère non-ASCII se traduira par <xref:System.Net.Http.HttpRequestException> .</span><span class="sxs-lookup"><span data-stu-id="091a9-137">If you omit this setting, an attempt to send a non-ASCII character will result in <xref:System.Net.Http.HttpRequestException>.</span></span> <span data-ttu-id="091a9-138">Cela équivaut à définir la valeur sur `false` .</span><span class="sxs-lookup"><span data-stu-id="091a9-138">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="091a9-139">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="091a9-139">Setting name</span></span> | <span data-ttu-id="091a9-140">Valeurs</span><span class="sxs-lookup"><span data-stu-id="091a9-140">Values</span></span> |
| - | - | - |
| <span data-ttu-id="091a9-141">**runtimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="091a9-141">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.AllowLatin1Headers` | <span data-ttu-id="091a9-142">`false` -désactivé</span><span class="sxs-lookup"><span data-stu-id="091a9-142">`false` - disabled</span></span><br/><span data-ttu-id="091a9-143">`true` -activé</span><span class="sxs-lookup"><span data-stu-id="091a9-143">`true` - enabled</span></span> |
| <span data-ttu-id="091a9-144">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="091a9-144">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_ALLOWLATIN1HEADERS` | <span data-ttu-id="091a9-145">`0` -désactivé</span><span class="sxs-lookup"><span data-stu-id="091a9-145">`0` - disabled</span></span><br/><span data-ttu-id="091a9-146">`1` -activé</span><span class="sxs-lookup"><span data-stu-id="091a9-146">`1` - enabled</span></span> |

> [!NOTE]
> <span data-ttu-id="091a9-147">Cette option est disponible uniquement dans .NET Core 3,1 depuis la version 3.1.9, et non dans les versions antérieures ou ultérieures.</span><span class="sxs-lookup"><span data-stu-id="091a9-147">This option is only available in .NET Core 3.1 since version 3.1.9, and not in previous or later versions.</span></span> <span data-ttu-id="091a9-148">Dans .NET 5, nous vous recommandons d’utiliser <xref:System.Net.Http.SocketsHttpHandler.RequestHeaderEncodingSelector> .</span><span class="sxs-lookup"><span data-stu-id="091a9-148">In .NET 5 we recommend using <xref:System.Net.Http.SocketsHttpHandler.RequestHeaderEncodingSelector>.</span></span>
