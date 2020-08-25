---
ms.openlocfilehash: f1129500c9b779256b2650fe6fa855152cb3ae80
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811261"
---
### <a name="middleware-database-error-page-marked-as-obsolete"></a><span data-ttu-id="7d437-101">Intergiciel : page d’erreurs de base de données marquée comme obsolète</span><span class="sxs-lookup"><span data-stu-id="7d437-101">Middleware: Database error page marked as obsolete</span></span>

<span data-ttu-id="7d437-102">Les méthodes d’extension [DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) et associées ont été marquées comme obsolètes dans ASP.net Core 5,0.</span><span class="sxs-lookup"><span data-stu-id="7d437-102">The [DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) and its associated extension methods were marked as obsolete in ASP.NET Core 5.0.</span></span> <span data-ttu-id="7d437-103">Les méthodes d’extension et d’intergiciel seront supprimées dans ASP.NET Core 6,0.</span><span class="sxs-lookup"><span data-stu-id="7d437-103">The middleware and extension methods will be removed in ASP.NET Core 6.0.</span></span> <span data-ttu-id="7d437-104">La fonctionnalité sera fournie à la place par `DatabaseDeveloperPageExceptionFilter` et ses méthodes d’extension.</span><span class="sxs-lookup"><span data-stu-id="7d437-104">The functionality will instead be provided by `DatabaseDeveloperPageExceptionFilter` and its extension methods.</span></span>

<span data-ttu-id="7d437-105">Pour plus d’informations, consultez le problème GitHub dans [dotnet/aspnetcore # 24987](https://github.com/dotnet/aspnetcore/issues/24987).</span><span class="sxs-lookup"><span data-stu-id="7d437-105">For discussion, see the GitHub issue at [dotnet/aspnetcore#24987](https://github.com/dotnet/aspnetcore/issues/24987).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7d437-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="7d437-106">Version introduced</span></span>

<span data-ttu-id="7d437-107">5,0 RC 1</span><span class="sxs-lookup"><span data-stu-id="7d437-107">5.0 RC 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="7d437-108">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="7d437-108">Old behavior</span></span>

<span data-ttu-id="7d437-109">`DatabaseErrorPageMiddleware` et les méthodes d’extension associées n’étaient pas obsolètes.</span><span class="sxs-lookup"><span data-stu-id="7d437-109">`DatabaseErrorPageMiddleware` and its associated extension methods weren't obsolete.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="7d437-110">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="7d437-110">New behavior</span></span>

<span data-ttu-id="7d437-111">`DatabaseErrorPageMiddleware` et les méthodes d’extension associées sont obsolètes.</span><span class="sxs-lookup"><span data-stu-id="7d437-111">`DatabaseErrorPageMiddleware` and its associated extension methods are obsolete.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7d437-112">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="7d437-112">Reason for change</span></span>

<span data-ttu-id="7d437-113">`DatabaseErrorPageMiddleware` a été migré vers une API extensible pour la [page d’exception du développeur](/aspnet/core/fundamentals/error-handling#developer-exception-page).</span><span class="sxs-lookup"><span data-stu-id="7d437-113">`DatabaseErrorPageMiddleware` was migrated to an extensible API for the [developer exception page](/aspnet/core/fundamentals/error-handling#developer-exception-page).</span></span> <span data-ttu-id="7d437-114">Pour plus d’informations sur l’API extensible, consultez GitHub issue [dotnet/aspnetcore # 8536](https://github.com/dotnet/aspnetcore/issues/8536).</span><span class="sxs-lookup"><span data-stu-id="7d437-114">For more information on the extensible API, see GitHub issue [dotnet/aspnetcore#8536](https://github.com/dotnet/aspnetcore/issues/8536).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7d437-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="7d437-115">Recommended action</span></span>

<span data-ttu-id="7d437-116">Procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="7d437-116">Complete the following steps:</span></span>

1. <span data-ttu-id="7d437-117">Arrêtez l’utilisation `DatabaseErrorPageMiddleware` de dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="7d437-117">Stop using `DatabaseErrorPageMiddleware` in your project.</span></span> <span data-ttu-id="7d437-118">Par exemple, supprimez l' `UseDatabaseErrorPage` appel de méthode de `Startup.Configure` :</span><span class="sxs-lookup"><span data-stu-id="7d437-118">For example, remove the `UseDatabaseErrorPage` method call from `Startup.Configure`:</span></span>

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDatabaseErrorPage();
        }
    }
    ```

1. <span data-ttu-id="7d437-119">Ajoutez la page exception de développeur à votre projet.</span><span class="sxs-lookup"><span data-stu-id="7d437-119">Add the developer exception page to your project.</span></span> <span data-ttu-id="7d437-120">Par exemple, appelez la <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> méthode dans `Startup.Configure` :</span><span class="sxs-lookup"><span data-stu-id="7d437-120">For example, call the <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> method in `Startup.Configure`:</span></span>

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
    }
    ```

1. <span data-ttu-id="7d437-121">Ajoutez le filtre d’exception de page développeur de bases de données à la collection de services.</span><span class="sxs-lookup"><span data-stu-id="7d437-121">Add the database developer page exception filter to the services collection.</span></span> <span data-ttu-id="7d437-122">Par exemple, appelez la `AddDatabaseDeveloperPageExceptionFilter` méthode dans `Startup.ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="7d437-122">For example, call the `AddDatabaseDeveloperPageExceptionFilter` method in `Startup.ConfigureServices`:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddDatabaseDeveloperPageExceptionFilter();
    }
    ```

#### <a name="category"></a><span data-ttu-id="7d437-123">Category</span><span class="sxs-lookup"><span data-stu-id="7d437-123">Category</span></span>

<span data-ttu-id="7d437-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7d437-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7d437-125">API affectées</span><span class="sxs-lookup"><span data-stu-id="7d437-125">Affected APIs</span></span>

- [<span data-ttu-id="7d437-126">Microsoft. AspNetCore. Builder. DatabaseErrorPageExtensions. UseDatabaseErrorPage</span><span class="sxs-lookup"><span data-stu-id="7d437-126">Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage</span></span>](/dotnet/api/microsoft.aspnetcore.builder.databaseerrorpageextensions.usedatabaseerrorpage?view=aspnetcore-3.0)
- [<span data-ttu-id="7d437-127">Microsoft. AspNetCore. Diagnostics. EntityFrameworkCore. DatabaseErrorPageMiddleware</span><span class="sxs-lookup"><span data-stu-id="7d437-127">Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware</span></span>](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0)

<!-- 

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage`
- `T:Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware`

-->
