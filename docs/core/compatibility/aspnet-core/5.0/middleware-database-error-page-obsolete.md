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
# <a name="middleware-database-error-page-marked-as-obsolete"></a><span data-ttu-id="2df0c-103">Intergiciel : page d’erreurs de base de données marquée comme obsolète</span><span class="sxs-lookup"><span data-stu-id="2df0c-103">Middleware: Database error page marked as obsolete</span></span>

<span data-ttu-id="2df0c-104">Les méthodes d’extension [DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) et associées ont été marquées comme obsolètes dans ASP.net Core 5,0.</span><span class="sxs-lookup"><span data-stu-id="2df0c-104">The [DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) and its associated extension methods were marked as obsolete in ASP.NET Core 5.0.</span></span> <span data-ttu-id="2df0c-105">Les méthodes d’extension et d’intergiciel seront supprimées dans ASP.NET Core 6,0.</span><span class="sxs-lookup"><span data-stu-id="2df0c-105">The middleware and extension methods will be removed in ASP.NET Core 6.0.</span></span> <span data-ttu-id="2df0c-106">La fonctionnalité sera fournie à la place par `DatabaseDeveloperPageExceptionFilter` et ses méthodes d’extension.</span><span class="sxs-lookup"><span data-stu-id="2df0c-106">The functionality will instead be provided by `DatabaseDeveloperPageExceptionFilter` and its extension methods.</span></span>

<span data-ttu-id="2df0c-107">Pour plus d’informations, consultez le problème GitHub dans [dotnet/aspnetcore # 24987](https://github.com/dotnet/aspnetcore/issues/24987).</span><span class="sxs-lookup"><span data-stu-id="2df0c-107">For discussion, see the GitHub issue at [dotnet/aspnetcore#24987](https://github.com/dotnet/aspnetcore/issues/24987).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="2df0c-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="2df0c-108">Version introduced</span></span>

<span data-ttu-id="2df0c-109">5,0 RC 1</span><span class="sxs-lookup"><span data-stu-id="2df0c-109">5.0 RC 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="2df0c-110">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="2df0c-110">Old behavior</span></span>

<span data-ttu-id="2df0c-111">`DatabaseErrorPageMiddleware` et les méthodes d’extension associées n’étaient pas obsolètes.</span><span class="sxs-lookup"><span data-stu-id="2df0c-111">`DatabaseErrorPageMiddleware` and its associated extension methods weren't obsolete.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="2df0c-112">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="2df0c-112">New behavior</span></span>

<span data-ttu-id="2df0c-113">`DatabaseErrorPageMiddleware` et les méthodes d’extension associées sont obsolètes.</span><span class="sxs-lookup"><span data-stu-id="2df0c-113">`DatabaseErrorPageMiddleware` and its associated extension methods are obsolete.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="2df0c-114">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="2df0c-114">Reason for change</span></span>

<span data-ttu-id="2df0c-115">`DatabaseErrorPageMiddleware` a été migré vers une API extensible pour la [page d’exception du développeur](/aspnet/core/fundamentals/error-handling#developer-exception-page).</span><span class="sxs-lookup"><span data-stu-id="2df0c-115">`DatabaseErrorPageMiddleware` was migrated to an extensible API for the [developer exception page](/aspnet/core/fundamentals/error-handling#developer-exception-page).</span></span> <span data-ttu-id="2df0c-116">Pour plus d’informations sur l’API extensible, consultez GitHub issue [dotnet/aspnetcore # 8536](https://github.com/dotnet/aspnetcore/issues/8536).</span><span class="sxs-lookup"><span data-stu-id="2df0c-116">For more information on the extensible API, see GitHub issue [dotnet/aspnetcore#8536](https://github.com/dotnet/aspnetcore/issues/8536).</span></span>

## <a name="recommended-action"></a><span data-ttu-id="2df0c-117">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="2df0c-117">Recommended action</span></span>

<span data-ttu-id="2df0c-118">Suivez les étapes ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="2df0c-118">Complete the following steps:</span></span>

1. <span data-ttu-id="2df0c-119">Arrêtez l’utilisation `DatabaseErrorPageMiddleware` de dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="2df0c-119">Stop using `DatabaseErrorPageMiddleware` in your project.</span></span> <span data-ttu-id="2df0c-120">Par exemple, supprimez l' `UseDatabaseErrorPage` appel de méthode de `Startup.Configure` :</span><span class="sxs-lookup"><span data-stu-id="2df0c-120">For example, remove the `UseDatabaseErrorPage` method call from `Startup.Configure`:</span></span>

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDatabaseErrorPage();
        }
    }
    ```

1. <span data-ttu-id="2df0c-121">Ajoutez la page exception de développeur à votre projet.</span><span class="sxs-lookup"><span data-stu-id="2df0c-121">Add the developer exception page to your project.</span></span> <span data-ttu-id="2df0c-122">Par exemple, appelez la <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> méthode dans `Startup.Configure` :</span><span class="sxs-lookup"><span data-stu-id="2df0c-122">For example, call the <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> method in `Startup.Configure`:</span></span>

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
    }
    ```

1. <span data-ttu-id="2df0c-123">Ajoutez le package NuGet [Microsoft. AspNetCore. Diagnostics. EntityFrameworkCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore) au fichier projet.</span><span class="sxs-lookup"><span data-stu-id="2df0c-123">Add the [Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore) NuGet package to the project file.</span></span>

1. <span data-ttu-id="2df0c-124">Ajoutez le filtre d’exception de page développeur de bases de données à la collection de services.</span><span class="sxs-lookup"><span data-stu-id="2df0c-124">Add the database developer page exception filter to the services collection.</span></span> <span data-ttu-id="2df0c-125">Par exemple, appelez la `AddDatabaseDeveloperPageExceptionFilter` méthode dans `Startup.ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="2df0c-125">For example, call the `AddDatabaseDeveloperPageExceptionFilter` method in `Startup.ConfigureServices`:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddDatabaseDeveloperPageExceptionFilter();
    }
    ```

## <a name="affected-apis"></a><span data-ttu-id="2df0c-126">API affectées</span><span class="sxs-lookup"><span data-stu-id="2df0c-126">Affected APIs</span></span>

- [<span data-ttu-id="2df0c-127">Microsoft. AspNetCore. Builder. DatabaseErrorPageExtensions. UseDatabaseErrorPage</span><span class="sxs-lookup"><span data-stu-id="2df0c-127">Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage</span></span>](/dotnet/api/microsoft.aspnetcore.builder.databaseerrorpageextensions.usedatabaseerrorpage?view=aspnetcore-3.0)
- [<span data-ttu-id="2df0c-128">Microsoft. AspNetCore. Diagnostics. EntityFrameworkCore. DatabaseErrorPageMiddleware</span><span class="sxs-lookup"><span data-stu-id="2df0c-128">Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware</span></span>](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0)

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage`
- `T:Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware`

-->
