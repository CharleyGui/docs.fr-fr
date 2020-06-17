---
ms.openlocfilehash: d00b8ecaa61b358e062d85a2b68ca8a95cada442
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803262"
---
### <a name="kestrel-configuration-changes-at-run-time-detected-by-default"></a><span data-ttu-id="6b2c4-101">Kestrel : modifications de configuration au moment de l’exécution détectées par défaut</span><span class="sxs-lookup"><span data-stu-id="6b2c4-101">Kestrel: Configuration changes at run time detected by default</span></span>

<span data-ttu-id="6b2c4-102">Kestrel réagit maintenant aux modifications apportées à la `Kestrel` section de l' `IConfiguration` instance du projet (par exemple, *appsettings.js*) au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="6b2c4-102">Kestrel now reacts to changes made to the `Kestrel` section of the project's `IConfiguration` instance (for example, *appsettings.json*) at run time.</span></span> <span data-ttu-id="6b2c4-103">Pour en savoir plus sur la configuration de Kestrel à l’aide *deappsettings.jssur*, consultez l’exemple *appsettings.js* dans la [configuration de point de terminaison](/aspnet/core/fundamentals/servers/kestrel#endpoint-configuration).</span><span class="sxs-lookup"><span data-stu-id="6b2c4-103">To learn more about how to configure Kestrel using *appsettings.json*, see the *appsettings.json* example in [Endpoint configuration](/aspnet/core/fundamentals/servers/kestrel#endpoint-configuration).</span></span>

<span data-ttu-id="6b2c4-104">Kestrel lie, dissocie et relient les points de terminaison nécessaires pour réagir à ces modifications de configuration.</span><span class="sxs-lookup"><span data-stu-id="6b2c4-104">Kestrel will bind, unbind, and rebind endpoints as necessary to react to these configuration changes.</span></span>

<span data-ttu-id="6b2c4-105">Pour plus d’informations, consultez émettre [dotnet/aspnetcore # 22807](https://github.com/dotnet/aspnetcore/issues/22807).</span><span class="sxs-lookup"><span data-stu-id="6b2c4-105">For discussion, see issue [dotnet/aspnetcore#22807](https://github.com/dotnet/aspnetcore/issues/22807).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6b2c4-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="6b2c4-106">Version introduced</span></span>

<span data-ttu-id="6b2c4-107">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="6b2c4-107">5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6b2c4-108">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="6b2c4-108">Old behavior</span></span>

<span data-ttu-id="6b2c4-109">Avant ASP.NET Core 5,0 Preview 6, Kestrel ne prenait pas en charge la modification de la configuration au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="6b2c4-109">Before ASP.NET Core 5.0 Preview 6, Kestrel didn't support changing configuration at run time.</span></span>

<span data-ttu-id="6b2c4-110">Dans ASP.NET Core 5,0 Preview 6, vous pouvez choisir le comportement à présent par défaut qui consiste à réagir aux modifications de configuration au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="6b2c4-110">In ASP.NET Core 5.0 Preview 6, you could opt into the now-default behavior of reacting to configuration changes at run time.</span></span> <span data-ttu-id="6b2c4-111">L’activation manuelle de la configuration requise de la liaison Kestrel :</span><span class="sxs-lookup"><span data-stu-id="6b2c4-111">Opting in required binding Kestrel's configuration manually:</span></span>

```csharp
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
                webBuilder.UseKestrel((builderContext, kestrelOptions) =>
                {
                    kestrelOptions.Configure(
                        builderContext.Configuration.GetSection("Kestrel"), reloadOnChange: true);
                });

                webBuilder.UseStartup<Startup>();
            });
}
```

#### <a name="new-behavior"></a><span data-ttu-id="6b2c4-112">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="6b2c4-112">New behavior</span></span>

<span data-ttu-id="6b2c4-113">Kestrel réagit aux modifications de configuration au moment de l’exécution par défaut.</span><span class="sxs-lookup"><span data-stu-id="6b2c4-113">Kestrel reacts to configuration changes at run time by default.</span></span> <span data-ttu-id="6b2c4-114">Pour prendre en charge cette modification, <xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A> appelle par `KestrelServerOptions.Configure(IConfiguration, bool)` `reloadOnChange: true` défaut.</span><span class="sxs-lookup"><span data-stu-id="6b2c4-114">To support that change, <xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A> calls `KestrelServerOptions.Configure(IConfiguration, bool)` with `reloadOnChange: true` by default.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6b2c4-115">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="6b2c4-115">Reason for change</span></span>

<span data-ttu-id="6b2c4-116">La modification a été apportée pour prendre en charge la reconfiguration des points de terminaison au moment de l’exécution sans redémarrage complet du serveur.</span><span class="sxs-lookup"><span data-stu-id="6b2c4-116">The change was made to support endpoint reconfiguration at run time without completely restarting the server.</span></span> <span data-ttu-id="6b2c4-117">Contrairement à un redémarrage complet du serveur, les points de terminaison non modifiés ne sont pas détachés, même temporairement.</span><span class="sxs-lookup"><span data-stu-id="6b2c4-117">Unlike with a full server restart, unchanged endpoints aren't unbound even temporarily.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6b2c4-118">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="6b2c4-118">Recommended action</span></span>

* <span data-ttu-id="6b2c4-119">Pour la plupart des scénarios dans lesquels la section de configuration par défaut de Kestrel ne change pas au moment de l’exécution, cette modification n’a aucun impact et aucune action n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="6b2c4-119">For most scenarios in which Kestrel's default configuration section doesn't change at run time, this change has no impact and no action is needed.</span></span>
* <span data-ttu-id="6b2c4-120">Pour les scénarios dans lesquels la section de configuration par défaut de Kestrel change au moment de l’exécution et Kestrel doit réagir, c’est désormais le comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="6b2c4-120">For scenarios in which Kestrel's default configuration section does change at run time and Kestrel should react to it, this is now the default behavior.</span></span>
* <span data-ttu-id="6b2c4-121">Pour les scénarios dans lesquels la section de configuration par défaut de Kestrel change au moment de l’exécution et Kestrel ne doit pas réagir, vous pouvez vous désabonner comme suit :</span><span class="sxs-lookup"><span data-stu-id="6b2c4-121">For scenarios in which Kestrel's default configuration section changes at run time and Kestrel shouldn't react to it, you can opt out as follows:</span></span>

    ```csharp
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
                    webBuilder.UseKestrel((builderContext, kestrelOptions) =>
                    {
                        kestrelOptions.Configure(
                            builderContext.Configuration.GetSection("Kestrel"), reloadOnChange: false);
                    });

                    webBuilder.UseStartup<Startup>();
                });
    }
    ```

<span data-ttu-id="6b2c4-122">**Remarques :**</span><span class="sxs-lookup"><span data-stu-id="6b2c4-122">**Notes:**</span></span>

<span data-ttu-id="6b2c4-123">Cette modification ne modifie pas le comportement de la `KestrelServerOptions.Configure(IConfiguration)` surcharge, qui est toujours le comportement par défaut `reloadOnChange: false` .</span><span class="sxs-lookup"><span data-stu-id="6b2c4-123">This change doesn't modify the behavior of the `KestrelServerOptions.Configure(IConfiguration)` overload, which still defaults to the `reloadOnChange: false` behavior.</span></span>

<span data-ttu-id="6b2c4-124">Il est également important de s’assurer que la source de configuration prend en charge le rechargement.</span><span class="sxs-lookup"><span data-stu-id="6b2c4-124">It's also important to make sure the configuration source supports reloading.</span></span> <span data-ttu-id="6b2c4-125">Pour les sources JSON, le rechargement est configuré en appelant `AddJsonFile(path, reloadOnChange: true)` .</span><span class="sxs-lookup"><span data-stu-id="6b2c4-125">For JSON sources, reloading is configured by calling `AddJsonFile(path, reloadOnChange: true)`.</span></span> <span data-ttu-id="6b2c4-126">Le rechargement est déjà configuré par défaut pour *appsettings.jssur* et *appSettings. { Environnement}. JSON*.</span><span class="sxs-lookup"><span data-stu-id="6b2c4-126">Reloading is already configured by default for *appsettings.json* and *appsettings.{Environment}.json*.</span></span>

#### <a name="category"></a><span data-ttu-id="6b2c4-127">Category</span><span class="sxs-lookup"><span data-stu-id="6b2c4-127">Category</span></span>

<span data-ttu-id="6b2c4-128">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6b2c4-128">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6b2c4-129">API affectées</span><span class="sxs-lookup"><span data-stu-id="6b2c4-129">Affected APIs</span></span>

<xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`Overload:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults`

-->
