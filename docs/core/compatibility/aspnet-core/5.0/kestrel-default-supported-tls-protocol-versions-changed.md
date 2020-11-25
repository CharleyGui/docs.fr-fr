---
title: 'Modification avec rupture : Kestrel : les versions de protocole TLS prises en charge par défaut ont été modifiées'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulé Kestrel : versions de protocole TLS prises en charge par défaut modifiées'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: d7018be7cc778560b7b9c65472d42d7e0fbf623d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760828"
---
# <a name="kestrel-default-supported-tls-protocol-versions-changed"></a><span data-ttu-id="3137c-103">Kestrel : les versions de protocole TLS prises en charge par défaut ont été modifiées</span><span class="sxs-lookup"><span data-stu-id="3137c-103">Kestrel: Default supported TLS protocol versions changed</span></span>

<span data-ttu-id="3137c-104">Kestrel utilise désormais les versions de protocole TLS par défaut du système au lieu de restreindre les connexions aux protocoles TLS 1,1 et TLS 1,2 comme précédemment.</span><span class="sxs-lookup"><span data-stu-id="3137c-104">Kestrel now uses the system default TLS protocol versions rather than restricting connections to the TLS 1.1 and TLS 1.2 protocols like it did previously.</span></span>

<span data-ttu-id="3137c-105">Cette modification permet :</span><span class="sxs-lookup"><span data-stu-id="3137c-105">This change allows:</span></span>

* <span data-ttu-id="3137c-106">TLS 1,3 à utiliser par défaut dans les environnements qui le prennent en charge.</span><span class="sxs-lookup"><span data-stu-id="3137c-106">TLS 1.3 to be used by default in environments that support it.</span></span>
* <span data-ttu-id="3137c-107">TLS 1,0 à utiliser dans certains environnements (tels que Windows Server 2016 par défaut), ce qui n’est généralement [pas souhaitable](/security/engineering/solving-tls1-problem).</span><span class="sxs-lookup"><span data-stu-id="3137c-107">TLS 1.0 to be used in some environments (such as Windows Server 2016 by default), which is usually [not desirable](/security/engineering/solving-tls1-problem).</span></span>

<span data-ttu-id="3137c-108">Pour plus d’informations, consultez émettre [dotnet/aspnetcore # 22563](https://github.com/dotnet/aspnetcore/issues/22563).</span><span class="sxs-lookup"><span data-stu-id="3137c-108">For discussion, see issue [dotnet/aspnetcore#22563](https://github.com/dotnet/aspnetcore/issues/22563).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="3137c-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="3137c-109">Version introduced</span></span>

<span data-ttu-id="3137c-110">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="3137c-110">5.0 Preview 6</span></span>

## <a name="old-behavior"></a><span data-ttu-id="3137c-111">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="3137c-111">Old behavior</span></span>

<span data-ttu-id="3137c-112">Kestrel a demandé que les connexions utilisent TLS 1,1 ou TLS 1,2 par défaut.</span><span class="sxs-lookup"><span data-stu-id="3137c-112">Kestrel required that connections use TLS 1.1 or TLS 1.2 by default.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="3137c-113">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="3137c-113">New behavior</span></span>

<span data-ttu-id="3137c-114">Kestrel permet au système d’exploitation de choisir le meilleur protocole à utiliser et de bloquer les protocoles non sécurisés.</span><span class="sxs-lookup"><span data-stu-id="3137c-114">Kestrel allows the operating system to choose the best protocol to use and to block insecure protocols.</span></span> <span data-ttu-id="3137c-115"><xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType> la valeur par défaut est à la `SslProtocols.None` place de `SslProtocols.Tls12 | SslProtocols.Tls11` .</span><span class="sxs-lookup"><span data-stu-id="3137c-115"><xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType> now defaults to `SslProtocols.None` instead of `SslProtocols.Tls12 | SslProtocols.Tls11`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="3137c-116">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="3137c-116">Reason for change</span></span>

<span data-ttu-id="3137c-117">La modification a été apportée pour prendre en charge les versions TLS 1,3 et futures par défaut dès qu’elles sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="3137c-117">The change was made to support TLS 1.3 and future TLS versions by default as they become available.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="3137c-118">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="3137c-118">Recommended action</span></span>

<span data-ttu-id="3137c-119">À moins que votre application ait une raison spécifique de ne pas le faire, vous devez utiliser les nouvelles valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="3137c-119">Unless your app has a specific reason not to, you should use the new defaults.</span></span> <span data-ttu-id="3137c-120">Vérifiez que votre système est configuré pour n’autoriser que les protocoles sécurisés.</span><span class="sxs-lookup"><span data-stu-id="3137c-120">Verify your system is configured to allow only secure protocols.</span></span>

<span data-ttu-id="3137c-121">Pour désactiver les anciens protocoles, effectuez l’une des actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="3137c-121">To disable older protocols, take one of the following actions:</span></span>

* <span data-ttu-id="3137c-122">Désactivez les protocoles plus anciens, tels que TLS 1,0, à l’ensemble du système avec les [instructions Windows](../../../../framework/network-programming/tls.md#configuring-schannel-protocols-in-the-windows-registry).</span><span class="sxs-lookup"><span data-stu-id="3137c-122">Disable older protocols, such as TLS 1.0, system-wide with the [Windows instructions](../../../../framework/network-programming/tls.md#configuring-schannel-protocols-in-the-windows-registry).</span></span> <span data-ttu-id="3137c-123">Elle est actuellement activée par défaut sur toutes les versions de Windows.</span><span class="sxs-lookup"><span data-stu-id="3137c-123">It's currently enabled by default on all Windows versions.</span></span>
* <span data-ttu-id="3137c-124">Sélectionnez manuellement les protocoles que vous souhaitez prendre en charge dans le code comme suit :</span><span class="sxs-lookup"><span data-stu-id="3137c-124">Manually select which protocols you want to support in code as follows:</span></span>

    ```csharp
    using System.Security.Authentication;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Extensions.Hosting;

    public class Program
    {
        public static void Main(string[] args) =>
            CreateHostBuilder(args).Build().Run();

        public static IHostBuilder CreateHostBuilder(string[] args) =>
            Host.CreateDefaultBuilder(args)
                .ConfigureWebHostDefaults(webBuilder =>
                {
                    webBuilder.UseKestrel(kestrelOptions =>
                    {
                        kestrelOptions.ConfigureHttpsDefaults(httpsOptions =>
                        {
                            httpsOptions.SslProtocols = SslProtocols.Tls12 | SslProtocols.Tls13;
                        });
                    });

                    webBuilder.UseStartup<Startup>();
                });
    }
    ```

<span data-ttu-id="3137c-125">Malheureusement, il n’existe aucune API pour exclure des protocoles spécifiques.</span><span class="sxs-lookup"><span data-stu-id="3137c-125">Unfortunately, there's no API to exclude specific protocols.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="3137c-126">API affectées</span><span class="sxs-lookup"><span data-stu-id="3137c-126">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`P:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols`

-->
