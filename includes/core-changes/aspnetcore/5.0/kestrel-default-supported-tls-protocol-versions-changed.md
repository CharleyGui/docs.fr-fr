---
ms.openlocfilehash: 3244a36808fb687663241e704d08775ea5c96720
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803245"
---
### <a name="kestrel-default-supported-tls-protocol-versions-changed"></a><span data-ttu-id="4328c-101">Kestrel : les versions de protocole TLS prises en charge par défaut ont été modifiées</span><span class="sxs-lookup"><span data-stu-id="4328c-101">Kestrel: Default supported TLS protocol versions changed</span></span>

<span data-ttu-id="4328c-102">Kestrel utilise désormais les versions de protocole TLS par défaut du système au lieu de restreindre les connexions aux protocoles TLS 1,1 et TLS 1,2 comme précédemment.</span><span class="sxs-lookup"><span data-stu-id="4328c-102">Kestrel now uses the system default TLS protocol versions rather than restricting connections to the TLS 1.1 and TLS 1.2 protocols like it did previously.</span></span>

<span data-ttu-id="4328c-103">Cette modification permet :</span><span class="sxs-lookup"><span data-stu-id="4328c-103">This change allows:</span></span>

* <span data-ttu-id="4328c-104">TLS 1,3 à utiliser par défaut dans les environnements qui le prennent en charge.</span><span class="sxs-lookup"><span data-stu-id="4328c-104">TLS 1.3 to be used by default in environments that support it.</span></span>
* <span data-ttu-id="4328c-105">TLS 1,0 à utiliser dans certains environnements (tels que Windows Server 2016 par défaut), ce qui n’est généralement [pas souhaitable](/security/engineering/solving-tls1-problem).</span><span class="sxs-lookup"><span data-stu-id="4328c-105">TLS 1.0 to be used in some environments (such as Windows Server 2016 by default), which is usually [not desirable](/security/engineering/solving-tls1-problem).</span></span>

<span data-ttu-id="4328c-106">Pour plus d’informations, consultez émettre [dotnet/aspnetcore # 22563](https://github.com/dotnet/aspnetcore/issues/22563).</span><span class="sxs-lookup"><span data-stu-id="4328c-106">For discussion, see issue [dotnet/aspnetcore#22563](https://github.com/dotnet/aspnetcore/issues/22563).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4328c-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="4328c-107">Version introduced</span></span>

<span data-ttu-id="4328c-108">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="4328c-108">5.0 Preview 6</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="4328c-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="4328c-109">Old behavior</span></span>

<span data-ttu-id="4328c-110">Kestrel a demandé que les connexions utilisent TLS 1,1 ou TLS 1,2 par défaut.</span><span class="sxs-lookup"><span data-stu-id="4328c-110">Kestrel required that connections use TLS 1.1 or TLS 1.2 by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="4328c-111">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="4328c-111">New behavior</span></span>

<span data-ttu-id="4328c-112">Kestrel permet au système d’exploitation de choisir le meilleur protocole à utiliser et de bloquer les protocoles non sécurisés.</span><span class="sxs-lookup"><span data-stu-id="4328c-112">Kestrel allows the operating system to choose the best protocol to use and to block insecure protocols.</span></span> <span data-ttu-id="4328c-113"><xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType>la valeur par défaut est à la `SslProtocols.None` place de `SslProtocols.Tls12 | SslProtocols.Tls11` .</span><span class="sxs-lookup"><span data-stu-id="4328c-113"><xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType> now defaults to `SslProtocols.None` instead of `SslProtocols.Tls12 | SslProtocols.Tls11`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4328c-114">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="4328c-114">Reason for change</span></span>

<span data-ttu-id="4328c-115">La modification a été apportée pour prendre en charge les versions TLS 1,3 et futures par défaut dès qu’elles sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="4328c-115">The change was made to support TLS 1.3 and future TLS versions by default as they become available.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4328c-116">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="4328c-116">Recommended action</span></span>

<span data-ttu-id="4328c-117">À moins que votre application ait une raison spécifique de ne pas le faire, vous devez utiliser les nouvelles valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="4328c-117">Unless your app has a specific reason not to, you should use the new defaults.</span></span> <span data-ttu-id="4328c-118">Vérifiez que votre système est configuré pour n’autoriser que les protocoles sécurisés.</span><span class="sxs-lookup"><span data-stu-id="4328c-118">Verify your system is configured to allow only secure protocols.</span></span>

<span data-ttu-id="4328c-119">Pour désactiver les anciens protocoles, effectuez l’une des actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="4328c-119">To disable older protocols, take one of the following actions:</span></span>

* <span data-ttu-id="4328c-120">Désactivez les protocoles plus anciens, tels que TLS 1,0, à l’ensemble du système avec les [instructions Windows](/dotnet/framework/network-programming/tls#configuring-schannel-protocols-in-the-windows-registry).</span><span class="sxs-lookup"><span data-stu-id="4328c-120">Disable older protocols, such as TLS 1.0, system-wide with the [Windows instructions](/dotnet/framework/network-programming/tls#configuring-schannel-protocols-in-the-windows-registry).</span></span> <span data-ttu-id="4328c-121">Elle est actuellement activée par défaut sur toutes les versions de Windows.</span><span class="sxs-lookup"><span data-stu-id="4328c-121">It's currently enabled by default on all Windows versions.</span></span>
* <span data-ttu-id="4328c-122">Sélectionnez manuellement les protocoles que vous souhaitez prendre en charge dans le code comme suit :</span><span class="sxs-lookup"><span data-stu-id="4328c-122">Manually select which protocols you want to support in code as follows:</span></span>

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

<span data-ttu-id="4328c-123">Malheureusement, il n’existe aucune API pour exclure des protocoles spécifiques.</span><span class="sxs-lookup"><span data-stu-id="4328c-123">Unfortunately, there's no API to exclude specific protocols.</span></span>

#### <a name="category"></a><span data-ttu-id="4328c-124">Category</span><span class="sxs-lookup"><span data-stu-id="4328c-124">Category</span></span>

<span data-ttu-id="4328c-125">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4328c-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4328c-126">API affectées</span><span class="sxs-lookup"><span data-stu-id="4328c-126">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`P:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols`

-->
