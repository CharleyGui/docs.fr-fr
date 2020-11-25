---
title: 'Modification avec rupture : intergiciel : page d’erreurs de base de données marquée comme obsolète'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulé intergiciel (middleware) : page d’erreurs de base de données marquée comme obsolète'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: f828b5e20c2a9a709d675e435caa99727aebd5b6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761135"
---
# <a name="middleware-database-error-page-marked-as-obsolete"></a>Intergiciel : page d’erreurs de base de données marquée comme obsolète

Les méthodes d’extension [DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) et associées ont été marquées comme obsolètes dans ASP.net Core 5,0. Les méthodes d’extension et d’intergiciel seront supprimées dans ASP.NET Core 6,0. La fonctionnalité sera fournie à la place par `DatabaseDeveloperPageExceptionFilter` et ses méthodes d’extension.

Pour plus d’informations, consultez le problème GitHub dans [dotnet/aspnetcore # 24987](https://github.com/dotnet/aspnetcore/issues/24987).

## <a name="version-introduced"></a>Version introduite

5,0 RC 1

## <a name="old-behavior"></a>Ancien comportement

`DatabaseErrorPageMiddleware` et les méthodes d’extension associées n’étaient pas obsolètes.

## <a name="new-behavior"></a>Nouveau comportement

`DatabaseErrorPageMiddleware` et les méthodes d’extension associées sont obsolètes.

## <a name="reason-for-change"></a>Motif de modification

`DatabaseErrorPageMiddleware` a été migré vers une API extensible pour la [page d’exception du développeur](/aspnet/core/fundamentals/error-handling#developer-exception-page). Pour plus d’informations sur l’API extensible, consultez GitHub issue [dotnet/aspnetcore # 8536](https://github.com/dotnet/aspnetcore/issues/8536).

## <a name="recommended-action"></a>Action recommandée

Suivez les étapes ci-dessous :

1. Arrêtez l’utilisation `DatabaseErrorPageMiddleware` de dans votre projet. Par exemple, supprimez l' `UseDatabaseErrorPage` appel de méthode de `Startup.Configure` :

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDatabaseErrorPage();
        }
    }
    ```

1. Ajoutez la page exception de développeur à votre projet. Par exemple, appelez la <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> méthode dans `Startup.Configure` :

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
    }
    ```

1. Ajoutez le package NuGet [Microsoft. AspNetCore. Diagnostics. EntityFrameworkCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore) au fichier projet.

1. Ajoutez le filtre d’exception de page développeur de bases de données à la collection de services. Par exemple, appelez la `AddDatabaseDeveloperPageExceptionFilter` méthode dans `Startup.ConfigureServices` :

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddDatabaseDeveloperPageExceptionFilter();
    }
    ```

## <a name="affected-apis"></a>API affectées

- [Microsoft. AspNetCore. Builder. DatabaseErrorPageExtensions. UseDatabaseErrorPage](/dotnet/api/microsoft.aspnetcore.builder.databaseerrorpageextensions.usedatabaseerrorpage?view=aspnetcore-3.0)
- [Microsoft. AspNetCore. Diagnostics. EntityFrameworkCore. DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0)

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage`
- `T:Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware`

-->
