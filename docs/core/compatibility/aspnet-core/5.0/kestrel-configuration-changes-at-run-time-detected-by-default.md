---
title: 'Modification avec rupture : Kestrel : modifications de configuration au moment de l’exécution détectées par défaut'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulé Kestrel : modifications de configuration au moment de l’exécution détectées par défaut'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 2e879f020dd108baa14fa8ff67dee7b948209faf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760835"
---
# <a name="kestrel-configuration-changes-at-run-time-detected-by-default"></a>Kestrel : modifications de configuration au moment de l’exécution détectées par défaut

Kestrel réagit maintenant aux modifications apportées à la `Kestrel` section de l' `IConfiguration` instance du projet (par exemple, *appsettings.js*) au moment de l’exécution. Pour en savoir plus sur la configuration de Kestrel à l’aide *deappsettings.jssur*, consultez l’exemple *appsettings.js* dans la [configuration de point de terminaison](/aspnet/core/fundamentals/servers/kestrel#endpoint-configuration).

Kestrel lie, dissocie et relient les points de terminaison nécessaires pour réagir à ces modifications de configuration.

Pour plus d’informations, consultez émettre [dotnet/aspnetcore # 22807](https://github.com/dotnet/aspnetcore/issues/22807).

## <a name="version-introduced"></a>Version introduite

5,0 Preview 7

## <a name="old-behavior"></a>Ancien comportement

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

## <a name="new-behavior"></a>Nouveau comportement

Kestrel réagit aux modifications de configuration au moment de l’exécution par défaut. Pour prendre en charge cette modification, <xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A> appelle par `KestrelServerOptions.Configure(IConfiguration, bool)` `reloadOnChange: true` défaut.

## <a name="reason-for-change"></a>Motif de modification

La modification a été apportée pour prendre en charge la reconfiguration des points de terminaison au moment de l’exécution sans redémarrage complet du serveur. Contrairement à un redémarrage complet du serveur, les points de terminaison non modifiés ne sont pas détachés, même temporairement.

## <a name="recommended-action"></a>Action recommandée

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

## <a name="affected-apis"></a>API affectées

<xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`Overload:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults`

-->
