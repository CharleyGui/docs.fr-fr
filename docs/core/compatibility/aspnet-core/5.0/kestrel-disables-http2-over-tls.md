---
title: 'Modification avec rupture : Kestrel : HTTP/2 désactivé sur TLS sur des versions de Windows incompatibles'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulé Kestrel : HTTP/2 désactivé sur TLS sur des versions de Windows incompatibles'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: befd393795f3e1859d391bca513dd9856101d295
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761118"
---
# <a name="kestrel-http2-disabled-over-tls-on-incompatible-windows-versions"></a><span data-ttu-id="a5f71-103">Kestrel : HTTP/2 désactivé sur TLS sur des versions de Windows incompatibles</span><span class="sxs-lookup"><span data-stu-id="a5f71-103">Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions</span></span>

<span data-ttu-id="a5f71-104">Pour activer HTTP/2 sur le protocole TLS (Transport Layer Security) sur Windows, deux conditions doivent être remplies :</span><span class="sxs-lookup"><span data-stu-id="a5f71-104">To enable HTTP/2 over Transport Layer Security (TLS) on Windows, two requirements need to be met:</span></span>

- <span data-ttu-id="a5f71-105">La prise en charge de la négociation de protocole Application-Layer (ALPN), disponible à partir de Windows 8.1 et de Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="a5f71-105">Application-Layer Protocol Negotiation (ALPN) support, which is available starting with Windows 8.1 and Windows Server 2012 R2.</span></span>
- <span data-ttu-id="a5f71-106">Un ensemble de chiffrements compatibles avec HTTP/2, disponible à partir de Windows 10 et Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="a5f71-106">A set of ciphers compatible with HTTP/2, which is available starting with Windows 10 and Windows Server 2016.</span></span>

<span data-ttu-id="a5f71-107">Par conséquent, le comportement de Kestrel lorsque HTTP/2 sur TLS est configuré est devenu :</span><span class="sxs-lookup"><span data-stu-id="a5f71-107">As such, Kestrel's behavior when HTTP/2 over TLS is configured has changed to:</span></span>

- <span data-ttu-id="a5f71-108">Rétrograder à `Http1` et enregistrer un message au `Information` niveau lorsque [ListenOptions. HttpProtocols](/dotnet/api/microsoft.aspnetcore.server.kestrel.core.httpprotocols) a la valeur `Http1AndHttp2` .</span><span class="sxs-lookup"><span data-stu-id="a5f71-108">Downgrade to `Http1` and log a message at the `Information` level when [ListenOptions.HttpProtocols](/dotnet/api/microsoft.aspnetcore.server.kestrel.core.httpprotocols) is set to `Http1AndHttp2`.</span></span> <span data-ttu-id="a5f71-109">`Http1AndHttp2` est la valeur par défaut de `ListenOptions.HttpProtocols`.</span><span class="sxs-lookup"><span data-stu-id="a5f71-109">`Http1AndHttp2` is the default value for `ListenOptions.HttpProtocols`.</span></span>
- <span data-ttu-id="a5f71-110">Lève une `NotSupportedException` lorsque `ListenOptions.HttpProtocols` a la valeur `Http2` .</span><span class="sxs-lookup"><span data-stu-id="a5f71-110">Throw a `NotSupportedException` when `ListenOptions.HttpProtocols` is set to `Http2`.</span></span>

<span data-ttu-id="a5f71-111">Pour plus d’informations, consultez émettre [dotnet/aspnetcore # 23068](https://github.com/dotnet/aspnetcore/issues/23068).</span><span class="sxs-lookup"><span data-stu-id="a5f71-111">For discussion, see issue [dotnet/aspnetcore#23068](https://github.com/dotnet/aspnetcore/issues/23068).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="a5f71-112">Version introduite</span><span class="sxs-lookup"><span data-stu-id="a5f71-112">Version introduced</span></span>

<span data-ttu-id="a5f71-113">ASP.NET Core 5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="a5f71-113">ASP.NET Core 5.0 Preview 7</span></span>

## <a name="old-behavior"></a><span data-ttu-id="a5f71-114">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="a5f71-114">Old behavior</span></span>

<span data-ttu-id="a5f71-115">Le tableau suivant décrit le comportement lorsque le protocole HTTP/2 sur TLS est configuré.</span><span class="sxs-lookup"><span data-stu-id="a5f71-115">The following table outlines the behavior when HTTP/2 over TLS is configured.</span></span>

| <span data-ttu-id="a5f71-116">Protocoles</span><span class="sxs-lookup"><span data-stu-id="a5f71-116">Protocols</span></span> | <span data-ttu-id="a5f71-117">Windows 7,</span><span class="sxs-lookup"><span data-stu-id="a5f71-117">Windows 7,</span></span><br /><span data-ttu-id="a5f71-118">Windows Server 2008 R2,</span><span class="sxs-lookup"><span data-stu-id="a5f71-118">Windows Server 2008 R2,</span></span><br /><span data-ttu-id="a5f71-119">ou version antérieure</span><span class="sxs-lookup"><span data-stu-id="a5f71-119">or earlier</span></span> | <span data-ttu-id="a5f71-120">Windows 8,</span><span class="sxs-lookup"><span data-stu-id="a5f71-120">Windows 8,</span></span><br /><span data-ttu-id="a5f71-121">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="a5f71-121">Windows Server 2012</span></span> | <span data-ttu-id="a5f71-122">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="a5f71-122">Windows 8.1,</span></span><br /><span data-ttu-id="a5f71-123">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="a5f71-123">Windows Server 2012 R2</span></span> | <span data-ttu-id="a5f71-124">Windows 10,</span><span class="sxs-lookup"><span data-stu-id="a5f71-124">Windows 10,</span></span><br /><span data-ttu-id="a5f71-125">Windows Server 2016,</span><span class="sxs-lookup"><span data-stu-id="a5f71-125">Windows Server 2016,</span></span><br /><span data-ttu-id="a5f71-126"> ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="a5f71-126">or newer</span></span> |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | <span data-ttu-id="a5f71-127">Lever `NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="a5f71-127">Throw `NotSupportedException`</span></span>                   | <span data-ttu-id="a5f71-128">Erreur lors de la négociation TLS</span><span class="sxs-lookup"><span data-stu-id="a5f71-128">Error during TLS handshake</span></span>     | <span data-ttu-id="a5f71-129">Erreur lors de la négociation TLS &ast;</span><span class="sxs-lookup"><span data-stu-id="a5f71-129">Error during TLS handshake &ast;</span></span>     | <span data-ttu-id="a5f71-130">Aucune erreur</span><span class="sxs-lookup"><span data-stu-id="a5f71-130">No error</span></span> |
| `Http1AndHttp2` | <span data-ttu-id="a5f71-131">Rétrograder à `Http1`</span><span class="sxs-lookup"><span data-stu-id="a5f71-131">Downgrade to `Http1`</span></span>                    | <span data-ttu-id="a5f71-132">Rétrograder à `Http1`</span><span class="sxs-lookup"><span data-stu-id="a5f71-132">Downgrade to `Http1`</span></span>     | <span data-ttu-id="a5f71-133">Erreur lors de la négociation TLS &ast;</span><span class="sxs-lookup"><span data-stu-id="a5f71-133">Error during TLS handshake &ast;</span></span>     | <span data-ttu-id="a5f71-134">Aucune erreur</span><span class="sxs-lookup"><span data-stu-id="a5f71-134">No error</span></span> |

<span data-ttu-id="a5f71-135">&ast; Configurez des suites de chiffrement compatibles pour activer ces scénarios.</span><span class="sxs-lookup"><span data-stu-id="a5f71-135">&ast; Configure compatible cipher suites to enable these scenarios.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="a5f71-136">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="a5f71-136">New behavior</span></span>

<span data-ttu-id="a5f71-137">Le tableau suivant décrit le comportement lorsque le protocole HTTP/2 sur TLS est configuré.</span><span class="sxs-lookup"><span data-stu-id="a5f71-137">The following table outlines the behavior when HTTP/2 over TLS is configured.</span></span>

| <span data-ttu-id="a5f71-138">Protocoles</span><span class="sxs-lookup"><span data-stu-id="a5f71-138">Protocols</span></span> | <span data-ttu-id="a5f71-139">Windows 7,</span><span class="sxs-lookup"><span data-stu-id="a5f71-139">Windows 7,</span></span><br /><span data-ttu-id="a5f71-140">Windows Server 2008 R2,</span><span class="sxs-lookup"><span data-stu-id="a5f71-140">Windows Server 2008 R2,</span></span><br /><span data-ttu-id="a5f71-141">ou version antérieure</span><span class="sxs-lookup"><span data-stu-id="a5f71-141">or earlier</span></span> | <span data-ttu-id="a5f71-142">Windows 8,</span><span class="sxs-lookup"><span data-stu-id="a5f71-142">Windows 8,</span></span><br /><span data-ttu-id="a5f71-143">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="a5f71-143">Windows Server 2012</span></span> | <span data-ttu-id="a5f71-144">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="a5f71-144">Windows 8.1,</span></span><br /><span data-ttu-id="a5f71-145">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="a5f71-145">Windows Server 2012 R2</span></span> | <span data-ttu-id="a5f71-146">Windows 10,</span><span class="sxs-lookup"><span data-stu-id="a5f71-146">Windows 10,</span></span><br /><span data-ttu-id="a5f71-147">Windows Server 2016,</span><span class="sxs-lookup"><span data-stu-id="a5f71-147">Windows Server 2016,</span></span><br /><span data-ttu-id="a5f71-148"> ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="a5f71-148">or newer</span></span> |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | <span data-ttu-id="a5f71-149">Lever `NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="a5f71-149">Throw `NotSupportedException`</span></span>                   | <span data-ttu-id="a5f71-150">Lever `NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="a5f71-150">Throw `NotSupportedException`</span></span>     | <span data-ttu-id="a5f71-151">Lever `NotSupportedException`&ast;&ast;</span><span class="sxs-lookup"><span data-stu-id="a5f71-151">Throw `NotSupportedException` &ast;&ast;</span></span>     | <span data-ttu-id="a5f71-152">Aucune erreur</span><span class="sxs-lookup"><span data-stu-id="a5f71-152">No error</span></span> |
| `Http1AndHttp2` | <span data-ttu-id="a5f71-153">Rétrograder à `Http1`</span><span class="sxs-lookup"><span data-stu-id="a5f71-153">Downgrade to `Http1`</span></span>                    | <span data-ttu-id="a5f71-154">Rétrograder à `Http1`</span><span class="sxs-lookup"><span data-stu-id="a5f71-154">Downgrade to `Http1`</span></span>     | <span data-ttu-id="a5f71-155">Rétrograder à `Http1`&ast;&ast;</span><span class="sxs-lookup"><span data-stu-id="a5f71-155">Downgrade to `Http1` &ast;&ast;</span></span>     | <span data-ttu-id="a5f71-156">Aucune erreur</span><span class="sxs-lookup"><span data-stu-id="a5f71-156">No error</span></span> |

<span data-ttu-id="a5f71-157">&ast;&ast; Configurez les suites de chiffrement compatibles et définissez le commutateur de contexte d’application `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` sur `true` pour activer ces scénarios.</span><span class="sxs-lookup"><span data-stu-id="a5f71-157">&ast;&ast; Configure compatible cipher suites and set the app context switch `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` to `true` to enable these scenarios.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="a5f71-158">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="a5f71-158">Reason for change</span></span>

<span data-ttu-id="a5f71-159">Cette modification garantit que les erreurs de compatibilité pour HTTP/2 sur TLS sur des versions plus anciennes de Windows sont exposées le plus tôt et le plus clairement possible.</span><span class="sxs-lookup"><span data-stu-id="a5f71-159">This change ensures compatibility errors for HTTP/2 over TLS on older Windows versions are surfaced as early and as clearly as possible.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a5f71-160">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="a5f71-160">Recommended action</span></span>

<span data-ttu-id="a5f71-161">Assurez-vous que HTTP/2 sur TLS est désactivé sur les versions de Windows incompatibles.</span><span class="sxs-lookup"><span data-stu-id="a5f71-161">Ensure HTTP/2 over TLS is disabled on incompatible Windows versions.</span></span> <span data-ttu-id="a5f71-162">Windows 8.1 et Windows Server 2012 R2 ne sont pas compatibles, car ils n’ont pas les chiffrements nécessaires par défaut.</span><span class="sxs-lookup"><span data-stu-id="a5f71-162">Windows 8.1 and Windows Server 2012 R2 are incompatible since they lack the necessary ciphers by default.</span></span> <span data-ttu-id="a5f71-163">Toutefois, il est possible de mettre à jour les paramètres de configuration de l’ordinateur pour utiliser les chiffrements compatibles HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="a5f71-163">However, it's possible to update the Computer Configuration settings to use HTTP/2 compatible ciphers.</span></span> <span data-ttu-id="a5f71-164">Pour plus d’informations, voir [suites de chiffrement TLS dans Windows 8.1](/windows/win32/secauthn/tls-cipher-suites-in-windows-8-1).</span><span class="sxs-lookup"><span data-stu-id="a5f71-164">For more information, see [TLS cipher suites in Windows 8.1](/windows/win32/secauthn/tls-cipher-suites-in-windows-8-1).</span></span> <span data-ttu-id="a5f71-165">Une fois configuré, vous devez activer HTTP/2 sur TLS sur Kestrel en définissant le commutateur de contexte d’application `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` .</span><span class="sxs-lookup"><span data-stu-id="a5f71-165">Once configured, HTTP/2 over TLS on Kestrel must be enabled by setting the app context switch `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2`.</span></span> <span data-ttu-id="a5f71-166">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="a5f71-166">For example:</span></span>

```csharp
AppContext.SetSwitch("Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2", true);
```

<span data-ttu-id="a5f71-167">Aucune prise en charge sous-jacente n’a changé.</span><span class="sxs-lookup"><span data-stu-id="a5f71-167">No underlying support has changed.</span></span> <span data-ttu-id="a5f71-168">Par exemple, HTTP/2 sur TLS n’a jamais fonctionné sur Windows 8 ou Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="a5f71-168">For example, HTTP/2 over TLS has never worked on Windows 8 or Windows Server 2012.</span></span> <span data-ttu-id="a5f71-169">Cette modification modifie le mode de présentation des erreurs dans ces scénarios non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="a5f71-169">This change modifies how errors in these unsupported scenarios are presented.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="a5f71-170">API affectées</span><span class="sxs-lookup"><span data-stu-id="a5f71-170">Affected APIs</span></span>

<span data-ttu-id="a5f71-171">None</span><span class="sxs-lookup"><span data-stu-id="a5f71-171">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
