---
ms.openlocfilehash: d00b8ecaa61b358e062d85a2b68ca8a95cada442
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803262"
---
### <a name="kestrel-configuration-changes-at-run-time-detected-by-default"></a>Kestrel : modifications de configuration au moment de l’exécution détectées par défaut

Kestrel réagit maintenant aux modifications apportées à la `Kestrel` section de l' `IConfiguration` instance du projet (par exemple, *appsettings.js*) au moment de l’exécution. Pour en savoir plus sur la configuration de Kestrel à l’aide *deappsettings.jssur*, consultez l’exemple *appsettings.js* dans la [configuration de point de terminaison](/aspnet/core/fundamentals/servers/kestrel#endpoint-configuration).

Kestrel lie, dissocie et relient les points de terminaison nécessaires pour réagir à ces modifications de configuration.

Pour plus d’informations, consultez émettre [dotnet/aspnetcore # 22807](https://github.com/dotnet/aspnetcore/issues/22807).

#### <a name="version-introduced"></a>Version introduite

5,0 Preview 7

#### <a name="old-behavior"></a>Ancien comportement

Avant ASP.NET Core 5,0 Preview 6, Kestrel ne prenait pas en charge la modification de la configuration au moment de l’exécution.

Dans ASP.NET Core 5,0 Preview 6, vous pouvez choisir le comportement à présent par défaut qui consiste à réagir aux modifications de configuration au moment de l’exécution. L’activation manuelle de la configuration requise de la liaison Kestrel :

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

#### <a name="new-behavior"></a>Nouveau comportement

Kestrel réagit aux modifications de configuration au moment de l’exécution par défaut. Pour prendre en charge cette modification, <xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A> appelle par `KestrelServerOptions.Configure(IConfiguration, bool)` `reloadOnChange: true` défaut.

#### <a name="reason-for-change"></a>Motif de modification

La modification a été apportée pour prendre en charge la reconfiguration des points de terminaison au moment de l’exécution sans redémarrage complet du serveur. Contrairement à un redémarrage complet du serveur, les points de terminaison non modifiés ne sont pas détachés, même temporairement.

#### <a name="recommended-action"></a>Action recommandée

* Pour la plupart des scénarios dans lesquels la section de configuration par défaut de Kestrel ne change pas au moment de l’exécution, cette modification n’a aucun impact et aucune action n’est nécessaire.
* Pour les scénarios dans lesquels la section de configuration par défaut de Kestrel change au moment de l’exécution et Kestrel doit réagir, c’est désormais le comportement par défaut.
* Pour les scénarios dans lesquels la section de configuration par défaut de Kestrel change au moment de l’exécution et Kestrel ne doit pas réagir, vous pouvez vous désabonner comme suit :

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

**Remarques :**

Cette modification ne modifie pas le comportement de la `KestrelServerOptions.Configure(IConfiguration)` surcharge, qui est toujours le comportement par défaut `reloadOnChange: false` .

Il est également important de s’assurer que la source de configuration prend en charge le rechargement. Pour les sources JSON, le rechargement est configuré en appelant `AddJsonFile(path, reloadOnChange: true)` . Le rechargement est déjà configuré par défaut pour *appsettings.jssur* et *appSettings. { Environnement}. JSON*.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`Overload:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults`

-->
