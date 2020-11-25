---
title: 'Modification avec rupture : HttpSys : la renégociation de certificat client est désactivée par défaut'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulé HttpSys : renégociation de certificat client désactivée par défaut'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 796989e1a21e3cb206d081e4fe8f79630121dc84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760839"
---
# <a name="httpsys-client-certificate-renegotiation-disabled-by-default"></a><span data-ttu-id="72c8c-103">HttpSys : la renégociation de certificat client est désactivée par défaut</span><span class="sxs-lookup"><span data-stu-id="72c8c-103">HttpSys: Client certificate renegotiation disabled by default</span></span>

<span data-ttu-id="72c8c-104">L’option permettant de renégocier une connexion et de demander un certificat client a été désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="72c8c-104">The option to renegotiate a connection and request a client certificate has been disabled by default.</span></span> <span data-ttu-id="72c8c-105">Pour plus d’informations, consultez émettre [dotnet/aspnetcore # 23181](https://github.com/dotnet/aspnetcore/issues/23181).</span><span class="sxs-lookup"><span data-stu-id="72c8c-105">For discussion, see issue [dotnet/aspnetcore#23181](https://github.com/dotnet/aspnetcore/issues/23181).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="72c8c-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="72c8c-106">Version introduced</span></span>

<span data-ttu-id="72c8c-107">ASP.NET Core 5,0</span><span class="sxs-lookup"><span data-stu-id="72c8c-107">ASP.NET Core 5.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="72c8c-108">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="72c8c-108">Old behavior</span></span>

<span data-ttu-id="72c8c-109">La connexion peut être renégociée pour demander un certificat client.</span><span class="sxs-lookup"><span data-stu-id="72c8c-109">The connection can be renegotiated to request a client certificate.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="72c8c-110">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="72c8c-110">New behavior</span></span>

<span data-ttu-id="72c8c-111">Les certificats clients ne peuvent être demandés que lors de la négociation de connexion initiale.</span><span class="sxs-lookup"><span data-stu-id="72c8c-111">Client certificates can only be requested during the initial connection handshake.</span></span> <span data-ttu-id="72c8c-112">Pour plus d’informations, consultez requête de tirage [dotnet/aspnetcore # 23162](https://github.com/dotnet/aspnetcore/pull/23162).</span><span class="sxs-lookup"><span data-stu-id="72c8c-112">For more information, see pull request [dotnet/aspnetcore#23162](https://github.com/dotnet/aspnetcore/pull/23162).</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="72c8c-113">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="72c8c-113">Reason for change</span></span>

<span data-ttu-id="72c8c-114">La renégociation a entraîné un certain nombre de problèmes de performances et de blocage.</span><span class="sxs-lookup"><span data-stu-id="72c8c-114">Renegotiation caused a number of performance and deadlock issues.</span></span> <span data-ttu-id="72c8c-115">Il n’est pas non plus pris en charge dans HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="72c8c-115">It's also not supported in HTTP/2.</span></span> <span data-ttu-id="72c8c-116">Pour plus de contexte lorsque l’option de contrôle de ce comportement a été introduite dans ASP.NET Core 3,1, consultez émettre [dotnet/aspnetcore # 14806](https://github.com/dotnet/aspnetcore/issues/14806).</span><span class="sxs-lookup"><span data-stu-id="72c8c-116">For additional context from when the option to control this behavior was introduced in ASP.NET Core 3.1, see issue [dotnet/aspnetcore#14806](https://github.com/dotnet/aspnetcore/issues/14806).</span></span>

## <a name="recommended-action"></a><span data-ttu-id="72c8c-117">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="72c8c-117">Recommended action</span></span>

<span data-ttu-id="72c8c-118">Les applications qui requièrent des certificats clients doivent utiliser *netsh.exe* pour affecter la valeur `clientcertnegotiation` à l’option `enabled` .</span><span class="sxs-lookup"><span data-stu-id="72c8c-118">Apps that require client certificates should use *netsh.exe* to set the `clientcertnegotiation` option to `enabled`.</span></span> <span data-ttu-id="72c8c-119">Pour plus d’informations, consultez [commandes netsh http](/windows-server/networking/technologies/netsh/netsh-http).</span><span class="sxs-lookup"><span data-stu-id="72c8c-119">For more information, see [netsh http commands](/windows-server/networking/technologies/netsh/netsh-http).</span></span>

<span data-ttu-id="72c8c-120">Si vous souhaitez que les certificats clients soient activés uniquement pour certaines parties de votre application, consultez les instructions à la page [certificats clients facultatifs](/aspnet/core/security/authentication/certauth?view=aspnetcore-3.1#optional-client-certificates).</span><span class="sxs-lookup"><span data-stu-id="72c8c-120">If you want client certificates enabled for only some parts of your app, see the guidance at [Optional client certificates](/aspnet/core/security/authentication/certauth?view=aspnetcore-3.1#optional-client-certificates).</span></span>

<span data-ttu-id="72c8c-121">Si vous avez besoin de l’ancien comportement de renégociation, définissez `HttpSysOptions.ClientCertificateMethod` sur l’ancienne valeur `ClientCertificateMethod.AllowRenegotiate` .</span><span class="sxs-lookup"><span data-stu-id="72c8c-121">If you need the old renegotiate behavior, set `HttpSysOptions.ClientCertificateMethod` to the old value `ClientCertificateMethod.AllowRenegotiate`.</span></span> <span data-ttu-id="72c8c-122">Cela n’est pas recommandé pour les raisons indiquées ci-dessus et dans le guide lié.</span><span class="sxs-lookup"><span data-stu-id="72c8c-122">This isn't recommended for the reasons outlined above and in the linked guidance.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="72c8c-123">API affectées</span><span class="sxs-lookup"><span data-stu-id="72c8c-123">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.ConnectionInfo.ClientCertificate%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.ConnectionInfo.GetClientCertificateAsync%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Server.HttpSys.HttpSysOptions.ClientCertificateMethod%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.ConnectionInfo.ClientCertificate`
- `Overload:Microsoft.AspNetCore.Http.ConnectionInfo.GetClientCertificateAsync`
- `Overload:Microsoft.AspNetCore.Server.HttpSys.HttpSysOptions.ClientCertificateMethod`

-->
