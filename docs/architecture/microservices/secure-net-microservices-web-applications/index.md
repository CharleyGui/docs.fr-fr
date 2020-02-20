---
title: Sécurisation des microservices .NET et des applications web
description: 'Sécurité dans les microservices .NET et les applications web : Découvrez les options d’authentification dans les applications web ASP.NET Core.'
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: f82212956f5492a51ec99d092e1a5131d1b31313
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77501653"
---
# <a name="make-secure-net-microservices-and-web-applications"></a><span data-ttu-id="41a55-103">Sécuriser les microservices .NET et les applications web</span><span class="sxs-lookup"><span data-stu-id="41a55-103">Make secure .NET Microservices and Web Applications</span></span>

<span data-ttu-id="41a55-104">La sécurité dans les microservices et les applications web est un sujet tellement vaste que la rubrique pourrait facilement remplir plusieurs manuels comme celui-ci. C’est pourquoi nous allons nous concentrer sur l’authentification, l’autorisation et les secrets d’application dans cette section.</span><span class="sxs-lookup"><span data-stu-id="41a55-104">There are so many aspects about security in microservices and web applications that the topic could easy take several books like this one so, in this section, we'll focus on authentication, authorization, and application secrets.</span></span>

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a><span data-ttu-id="41a55-105">Implémenter l’authentification dans les microservices .NET et les applications web</span><span class="sxs-lookup"><span data-stu-id="41a55-105">Implement authentication in .NET microservices and web applications</span></span>

<span data-ttu-id="41a55-106">Il est souvent nécessaire de limiter l’accès aux ressources et aux API publiées par un service à certains utilisateurs ou clients approuvés.</span><span class="sxs-lookup"><span data-stu-id="41a55-106">It's often necessary for resources and APIs published by a service to be limited to certain trusted users or clients.</span></span> <span data-ttu-id="41a55-107">La première étape d’une telle décision d’approbation au niveau des API passe par l’authentification.</span><span class="sxs-lookup"><span data-stu-id="41a55-107">The first step to making these sorts of API-level trust decisions is authentication.</span></span> <span data-ttu-id="41a55-108">L’authentification est le processus qui consiste à vérifier de manière fiable l’identité d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="41a55-108">Authentication is the process of reliably verify a user’s identity.</span></span>

<span data-ttu-id="41a55-109">Dans les scénarios de microservices, l’authentification est généralement gérée de manière centralisée.</span><span class="sxs-lookup"><span data-stu-id="41a55-109">In microservice scenarios, authentication is typically handled centrally.</span></span> <span data-ttu-id="41a55-110">Si vous utilisez une passerelle d’API, celle-ci est parfaitement indiquée pour l’authentification, comme l’illustre la figure 9-1.</span><span class="sxs-lookup"><span data-stu-id="41a55-110">If you're using an API Gateway, the gateway is a good place to authenticate, as shown in Figure 9-1.</span></span> <span data-ttu-id="41a55-111">Si vous utilisez cette approche, vérifiez que les différents microservices ne sont pas directement accessibles (sans la passerelle d’API), à moins qu’un dispositif de sécurité supplémentaire ait été mis en place pour authentifier les messages en provenance ou non de la passerelle.</span><span class="sxs-lookup"><span data-stu-id="41a55-111">If you use this approach, make sure that the individual microservices cannot be reached directly (without the API Gateway) unless additional security is in place to authenticate messages whether they come from the gateway or not.</span></span>

![Diagramme montrant comment l’application mobile cliente interagit avec le serveur principal.](./media/index/api-gateway-centralized-authentication.png)

<span data-ttu-id="41a55-113">**Figure 9-1**.</span><span class="sxs-lookup"><span data-stu-id="41a55-113">**Figure 9-1**.</span></span> <span data-ttu-id="41a55-114">authentification centralisée avec une passerelle d’API</span><span class="sxs-lookup"><span data-stu-id="41a55-114">Centralized authentication with an API Gateway</span></span>

<span data-ttu-id="41a55-115">Lorsque la passerelle d’API centralise l’authentification, elle ajoute des informations utilisateur quand les demandes sont transférées aux microservices.</span><span class="sxs-lookup"><span data-stu-id="41a55-115">When the API Gateway centralizes authentication, it adds user information when forwarding requests to the microservices.</span></span> <span data-ttu-id="41a55-116">Si les services sont accessibles directement, un service d’authentification, comme Azure Active Directory ou un microservice d’authentification dédié faisant office de service d’émission de jeton de sécurité (STS), peut être utilisé pour authentifier les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="41a55-116">If services can be accessed directly, an authentication service like Azure Active Directory or a dedicated authentication microservice acting as a security token service (STS) can be used to authenticate users.</span></span> <span data-ttu-id="41a55-117">Les décisions d’approbation sont partagées entre les services à l’aide de jetons de sécurité ou de cookies.</span><span class="sxs-lookup"><span data-stu-id="41a55-117">Trust decisions are shared between services with security tokens or cookies.</span></span> <span data-ttu-id="41a55-118">(Ces jetons peuvent être partagés entre ASP.NET Core applications, si nécessaire, en implémentant le [partage de cookies](/aspnet/core/security/cookie-sharing).) Ce modèle est illustré dans la figure 9-2.</span><span class="sxs-lookup"><span data-stu-id="41a55-118">(These tokens can be shared between ASP.NET Core applications, if needed, by implementing [cookie sharing](/aspnet/core/security/cookie-sharing).) This pattern is illustrated in Figure 9-2.</span></span>

![Diagramme montrant l’authentification via les microservices backend.](./media/index/identity-microservice-authentication.png)

<span data-ttu-id="41a55-120">**Figure 9-2**.</span><span class="sxs-lookup"><span data-stu-id="41a55-120">**Figure 9-2**.</span></span> <span data-ttu-id="41a55-121">authentification par un microservice d’identité ; l’approbation est partagée à l’aide d’un jeton d’autorisation</span><span class="sxs-lookup"><span data-stu-id="41a55-121">Authentication by identity microservice; trust is shared using an authorization token</span></span>

<span data-ttu-id="41a55-122">Quand les microservices sont accessibles directement, l’approbation, qui comprend l’authentification et l’autorisation, est gérée par un jeton de sécurité émis par un microservice dédié et partagé entre les microservices.</span><span class="sxs-lookup"><span data-stu-id="41a55-122">When microservices are accessed directly, trust, that includes authentication and authorization, is handled by a security token issued by a dedicated microservice, shared between microservices.</span></span>

### <a name="authenticate-with-aspnet-core-identity"></a><span data-ttu-id="41a55-123">S’authentifier avec ASP.NET Core Identity</span><span class="sxs-lookup"><span data-stu-id="41a55-123">Authenticate with ASP.NET Core Identity</span></span>

<span data-ttu-id="41a55-124">Dans ASP.NET Core, le principal mécanisme d’identification des utilisateurs d’une application est le système d’appartenance [ASP.NET Core Identity](/aspnet/core/security/authentication/identity).</span><span class="sxs-lookup"><span data-stu-id="41a55-124">The primary mechanism in ASP.NET Core for identifying an application’s users is the [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) membership system.</span></span> <span data-ttu-id="41a55-125">ASP.NET Core Identity stocke les informations utilisateur (notamment les revendications, les rôles et les informations de connexion) dans un magasin de données configuré par le développeur.</span><span class="sxs-lookup"><span data-stu-id="41a55-125">ASP.NET Core Identity stores user information (including sign-in information, roles, and claims) in a data store configured by the developer.</span></span> <span data-ttu-id="41a55-126">En règle générale, le magasin de données d’ASP.NET Core Identity est un magasin Entity Framework fourni dans le package `Microsoft.AspNetCore.Identity.EntityFrameworkCore`.</span><span class="sxs-lookup"><span data-stu-id="41a55-126">Typically, the ASP.NET Core Identity data store is an Entity Framework store provided in the `Microsoft.AspNetCore.Identity.EntityFrameworkCore` package.</span></span> <span data-ttu-id="41a55-127">Cependant, il est possible d’utiliser des magasins personnalisés ou d’autres packages tiers pour stocker les informations d’identité dans Stockage Table Azure, CosmosDB ou à d’autres emplacements.</span><span class="sxs-lookup"><span data-stu-id="41a55-127">However, custom stores or other third-party packages can be used to store identity information in Azure Table Storage, CosmosDB, or other locations.</span></span>

> [!TIP]
> <span data-ttu-id="41a55-128">ASP.NET Core 2,1 et versions ultérieures fournissent [ASP.net Core identité](/aspnet/core/security/authentication/identity) comme [bibliothèque de classes Razor](/aspnet/core/razor-pages/ui-class). vous ne verrez donc pas la majeure partie du code nécessaire dans votre projet, comme c’était le cas pour les versions précédentes.</span><span class="sxs-lookup"><span data-stu-id="41a55-128">ASP.NET Core 2.1 and later provides [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) as a [Razor Class Library](/aspnet/core/razor-pages/ui-class), so you won't see much of the necessary code in your project, as was the case for previous versions.</span></span> <span data-ttu-id="41a55-129">Pour plus d’informations sur la personnalisation du code d’identité en fonction de vos besoins, consultez l’article [identification de l’échafaudage dans des projets ASP.net Core](/aspnet/core/security/authentication/scaffold-identity).</span><span class="sxs-lookup"><span data-stu-id="41a55-129">For details on how to customize the Identity code to suit your needs, see [Scaffold Identity in ASP.NET Core projects](/aspnet/core/security/authentication/scaffold-identity).</span></span>

<span data-ttu-id="41a55-130">Le code suivant est extrait du modèle de projet ASP.NET Core application Web MVC 3,1 avec l’authentification de compte d’utilisateur individuelle sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="41a55-130">The following code is taken from the ASP.NET Core Web Application MVC 3.1 project template with individual user account authentication selected.</span></span> <span data-ttu-id="41a55-131">Il montre comment configurer ASP.NET Core identité à l’aide de Entity Framework Core dans la méthode `Startup.ConfigureServices`.</span><span class="sxs-lookup"><span data-stu-id="41a55-131">It shows how to configure ASP.NET Core Identity using Entity Framework Core in the `Startup.ConfigureServices` method.</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    //...
    services.AddDbContext<ApplicationDbContext>(options =>
        options.UseSqlServer(
            Configuration.GetConnectionString("DefaultConnection")));

    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddRazorPages();
    //...
}
```

<span data-ttu-id="41a55-132">Une fois ASP.NET Core identité configurée, vous pouvez l’activer en ajoutant le `app.UseAuthentication()` et `endpoints.MapRazorPages()` comme indiqué dans le code suivant dans la méthode `Startup.Configure` du service :</span><span class="sxs-lookup"><span data-stu-id="41a55-132">Once ASP.NET Core Identity is configured, you enable it by adding the `app.UseAuthentication()` and `endpoints.MapRazorPages()` as shown in the following code in the service's `Startup.Configure` method:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    //...
    app.UseRouting();

    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapRazorPages();
    });
    //...
}
```

> [!IMPORTANT]
> <span data-ttu-id="41a55-133">Les lignes du code précédent **doivent être dans l’ordre indiqué** pour que l’identité fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="41a55-133">The lines in the preceeding code **MUST BE IN THE ORDER SHOWN** for Identity to work correctly.</span></span>

<span data-ttu-id="41a55-134">L’utilisation d’ASP.NET Core Identity autorise plusieurs scénarios :</span><span class="sxs-lookup"><span data-stu-id="41a55-134">Using ASP.NET Core Identity enables several scenarios:</span></span>

- <span data-ttu-id="41a55-135">Création d’informations utilisateur à l’aide du type UserManager (userManager.CreateAsync).</span><span class="sxs-lookup"><span data-stu-id="41a55-135">Create new user information using the UserManager type (userManager.CreateAsync).</span></span>

- <span data-ttu-id="41a55-136">Authentification des utilisateurs à l’aide du type SignInManager.</span><span class="sxs-lookup"><span data-stu-id="41a55-136">Authenticate users using the SignInManager type.</span></span> <span data-ttu-id="41a55-137">Vous pouvez utiliser `signInManager.SignInAsync` pour vous connecter directement, ou `signInManager.PasswordSignInAsync` pour confirmer que le mot de passe utilisateur est correct avant de vous connecter.</span><span class="sxs-lookup"><span data-stu-id="41a55-137">You can use `signInManager.SignInAsync` to sign in directly, or `signInManager.PasswordSignInAsync` to confirm the user’s password is correct and then sign them in.</span></span>

- <span data-ttu-id="41a55-138">Identification d’un utilisateur en fonction des informations stockées dans un cookie (qui est lu par l’intergiciel ASP.NET Core Identity) de telle sorte que les requêtes suivantes d’un navigateur incluent l’identité et les revendications de l’utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="41a55-138">Identify a user based on information stored in a cookie (which is read by ASP.NET Core Identity middleware) so that subsequent requests from a browser will include a signed-in user’s identity and claims.</span></span>

<span data-ttu-id="41a55-139">Par ailleurs, ASP.NET Core Identity prend en charge l’[authentification à deux facteurs](/aspnet/core/security/authentication/2fa).</span><span class="sxs-lookup"><span data-stu-id="41a55-139">ASP.NET Core Identity also supports [two-factor authentication](/aspnet/core/security/authentication/2fa).</span></span>

<span data-ttu-id="41a55-140">Pour les scénarios d’authentification qui utilisent un magasin de données utilisateur local et qui conservent l’identité entre les requêtes au moyen de cookies (comme c’est généralement le cas avec les applications web MVC), ASP.NET Core Identity est une solution recommandée.</span><span class="sxs-lookup"><span data-stu-id="41a55-140">For authentication scenarios that make use of a local user data store and that persist identity between requests using cookies (as is typical for MVC web applications), ASP.NET Core Identity is a recommended solution.</span></span>

### <a name="authenticate-with-external-providers"></a><span data-ttu-id="41a55-141">S’authentifier avec des fournisseurs externes</span><span class="sxs-lookup"><span data-stu-id="41a55-141">Authenticate with external providers</span></span>

<span data-ttu-id="41a55-142">ASP.NET Core prend aussi en charge l’utilisation de [fournisseurs d’authentification externes](/aspnet/core/security/authentication/social/) pour permettre aux utilisateurs de se connecter via des flux [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2).</span><span class="sxs-lookup"><span data-stu-id="41a55-142">ASP.NET Core also supports using [external authentication providers](/aspnet/core/security/authentication/social/) to let users sign in via [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) flows.</span></span> <span data-ttu-id="41a55-143">Cela signifie que les utilisateurs peuvent se connecter en utilisant les processus d’authentification existants de certains fournisseurs, tels que Microsoft, Google, Facebook ou Twitter, et associer ces identités à une identité ASP.NET Core dans votre application.</span><span class="sxs-lookup"><span data-stu-id="41a55-143">This means that users can sign in using existing authentication processes from providers like Microsoft, Google, Facebook, or Twitter and associate those identities with an ASP.NET Core identity in your application.</span></span>

<span data-ttu-id="41a55-144">Pour utiliser l’authentification externe, outre l’intégration de l’intergiciel (middleware) d’authentification comme mentionné précédemment, à l’aide de la méthode `app.UseAuthentication()`, vous devez également inscrire le fournisseur externe dans `Startup` comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="41a55-144">To use external authentication, besides including the authentication middleware as mentioned before, using the `app.UseAuthentication()` method, you also have to register the external provider in `Startup` as shown in the following example:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    //...
    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddAuthentication()
        .AddMicrosoftAccount(microsoftOptions =>
        {
            microsoftOptions.ClientId = Configuration["Authentication:Microsoft:ClientId"];
            microsoftOptions.ClientSecret = Configuration["Authentication:Microsoft:ClientSecret"];
        })
        .AddGoogle(googleOptions => { ... })
        .AddTwitter(twitterOptions => { ... })
        .AddFacebook(facebookOptions => { ... });
    //...
}
```

<span data-ttu-id="41a55-145">Les fournisseurs d’authentification externes courants et les packages NuGet qui leur sont associés vous sont présentés dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="41a55-145">Popular external authentication providers and their associated NuGet packages are shown in the following table:</span></span>

| <span data-ttu-id="41a55-146">**Fournisseur**</span><span class="sxs-lookup"><span data-stu-id="41a55-146">**Provider**</span></span>  | <span data-ttu-id="41a55-147">**Package**</span><span class="sxs-lookup"><span data-stu-id="41a55-147">**Package**</span></span>                                          |
| ------------- | ---------------------------------------------------- |
| <span data-ttu-id="41a55-148">**Microsoft**</span><span class="sxs-lookup"><span data-stu-id="41a55-148">**Microsoft**</span></span> | <span data-ttu-id="41a55-149">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span><span class="sxs-lookup"><span data-stu-id="41a55-149">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span></span> |
| <span data-ttu-id="41a55-150">**Google**</span><span class="sxs-lookup"><span data-stu-id="41a55-150">**Google**</span></span>    | <span data-ttu-id="41a55-151">**Microsoft.AspNetCore.Authentication.Google**</span><span class="sxs-lookup"><span data-stu-id="41a55-151">**Microsoft.AspNetCore.Authentication.Google**</span></span>           |
| <span data-ttu-id="41a55-152">**Facebook**</span><span class="sxs-lookup"><span data-stu-id="41a55-152">**Facebook**</span></span>  | <span data-ttu-id="41a55-153">**Microsoft.AspNetCore.Authentication.Facebook**</span><span class="sxs-lookup"><span data-stu-id="41a55-153">**Microsoft.AspNetCore.Authentication.Facebook**</span></span>         |
| <span data-ttu-id="41a55-154">**Twitter**</span><span class="sxs-lookup"><span data-stu-id="41a55-154">**Twitter**</span></span>   | <span data-ttu-id="41a55-155">**Microsoft.AspNetCore.Authentication.Twitter**</span><span class="sxs-lookup"><span data-stu-id="41a55-155">**Microsoft.AspNetCore.Authentication.Twitter**</span></span>          |

<span data-ttu-id="41a55-156">Dans tous les cas, vous devez effectuer une procédure d’inscription d’application qui dépend du fournisseur et qui implique généralement :</span><span class="sxs-lookup"><span data-stu-id="41a55-156">In all cases, you must complete an application registration procedure that is vendor dependent and that usually involves:</span></span>

1. <span data-ttu-id="41a55-157">Obtention d’un ID d’application cliente.</span><span class="sxs-lookup"><span data-stu-id="41a55-157">Getting a Client Application ID.</span></span>
2. <span data-ttu-id="41a55-158">Obtention d’un secret d’application cliente.</span><span class="sxs-lookup"><span data-stu-id="41a55-158">Getting a Client Application Secret.</span></span>
3. <span data-ttu-id="41a55-159">Configuration d’une URL de redirection, gérée par l’intergiciel (middleware) d’autorisation et le fournisseur inscrit</span><span class="sxs-lookup"><span data-stu-id="41a55-159">Configuring an redirection URL, that's handled by the authorization middleware and the registered provider</span></span>
4. <span data-ttu-id="41a55-160">Si vous le souhaitez, vous pouvez configurer une URL de déconnexion pour gérer correctement la déconnexion dans un scénario d’authentification unique (SSO).</span><span class="sxs-lookup"><span data-stu-id="41a55-160">Optionally, configuring a sign-out URL to properly handle sign out in a Single Sign On (SSO) scenario.</span></span>

<span data-ttu-id="41a55-161">Pour plus d’informations sur la configuration de votre application pour un fournisseur externe, voir [authentification du fournisseur externe dans la documentation ASP.net Core](/aspnet/core/security/authentication/social/)).</span><span class="sxs-lookup"><span data-stu-id="41a55-161">For details on configuring your app for an external provider, see the [External provider authentication in the ASP.NET Core documentation](/aspnet/core/security/authentication/social/)).</span></span>

> [!TIP]
<span data-ttu-id="41a55-162">Tous les détails sont traités par l’intergiciel et les services d’autorisation mentionnés précédemment.</span><span class="sxs-lookup"><span data-stu-id="41a55-162">All details are handled by the authorization middleware and services previously mentioned.</span></span> <span data-ttu-id="41a55-163">Par conséquent, il vous suffit de choisir l’option d’authentification du **compte d’utilisateur individuel** lorsque vous créez le projet d’application Web de code ASP.net dans Visual Studio, comme le montre la figure 9-3, en plus de l’inscription des fournisseurs d’authentification mentionnés précédemment.</span><span class="sxs-lookup"><span data-stu-id="41a55-163">So, you just have to choose the **Individual User Account** authentication option when you create the ASP.NET Code web application project in Visual Studio, as shown in Figure 9-3, besides registering the authentication providers previously mentioned.</span></span>

![Capture d’écran de la boîte de dialogue Nouvelle ASP.NET Core application Web.](./media/index/select-individual-user-account-authentication-option.png)

<span data-ttu-id="41a55-165">**Figure 9-3**.</span><span class="sxs-lookup"><span data-stu-id="41a55-165">**Figure 9-3**.</span></span> <span data-ttu-id="41a55-166">Sélection de l’option comptes d’utilisateur individuels, pour l’utilisation de l’authentification externe, lors de la création d’un projet d’application Web dans Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="41a55-166">Selecting the Individual User Accounts option, for using external authentication, when creating a web application project in Visual Studio 2019.</span></span>

<span data-ttu-id="41a55-167">Outre les fournisseurs d’authentification externe mentionnés ci-dessus, il existe des packages tiers qui proposent un intergiciel permettant l’utilisation d’un nombre bien plus important de fournisseurs d’authentification externe.</span><span class="sxs-lookup"><span data-stu-id="41a55-167">In addition to the external authentication providers listed previously, third-party packages are available that provide middleware for using many more external authentication providers.</span></span> <span data-ttu-id="41a55-168">Pour obtenir une liste, consultez le référentiel [Aspnet. Security. OAuth. Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="41a55-168">For a list, see the [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repository on GitHub.</span></span>

<span data-ttu-id="41a55-169">Vous pouvez également créer votre propre middleware d’authentification externe pour répondre à des besoins particuliers.</span><span class="sxs-lookup"><span data-stu-id="41a55-169">You can also create your own external authentication middleware to solve some special need.</span></span>

### <a name="authenticate-with-bearer-tokens"></a><span data-ttu-id="41a55-170">S’authentifier avec des jetons du porteur</span><span class="sxs-lookup"><span data-stu-id="41a55-170">Authenticate with bearer tokens</span></span>

<span data-ttu-id="41a55-171">L’authentification avec ASP.NET Core Identity (ou Identity couplé à des fournisseurs d’authentification externe) est parfaitement adaptée à de nombreux scénarios d’application web dans lesquels il est approprié de stocker les informations utilisateur dans un cookie.</span><span class="sxs-lookup"><span data-stu-id="41a55-171">Authenticating with ASP.NET Core Identity (or Identity plus external authentication providers) works well for many web application scenarios in which storing user information in a cookie is appropriate.</span></span> <span data-ttu-id="41a55-172">En revanche, dans d’autres scénarios, il n’est pas commun de conserver et de transmettre les données au moyen de cookies.</span><span class="sxs-lookup"><span data-stu-id="41a55-172">In other scenarios, though, cookies are not a natural means of persisting and transmitting data.</span></span>

<span data-ttu-id="41a55-173">Par exemple, dans une API web ASP.NET Core qui expose les points de terminaison RESTful potentiellement accessibles par des applications à page unique, des clients natifs, voire d’autres API web, l’authentification par jeton du porteur est généralement privilégiée.</span><span class="sxs-lookup"><span data-stu-id="41a55-173">For example, in an ASP.NET Core Web API that exposes RESTful endpoints that might be accessed by Single Page Applications (SPAs), by native clients, or even by other Web APIs, you typically want to use bearer token authentication instead.</span></span> <span data-ttu-id="41a55-174">Les applications de ce type n’utilisent pas de cookies, mais elles peuvent facilement récupérer un jeton du porteur et l’inclure dans l’en-tête d’autorisation des requêtes suivantes.</span><span class="sxs-lookup"><span data-stu-id="41a55-174">These types of applications do not work with cookies, but can easily retrieve a bearer token and include it in the authorization header of subsequent requests.</span></span> <span data-ttu-id="41a55-175">Pour activer l’authentification par jeton, ASP.NET Core prend en charge plusieurs options en vue d’utiliser [OAuth 2.0](https://oauth.net/2/) et [OpenID Connect](https://openid.net/connect/).</span><span class="sxs-lookup"><span data-stu-id="41a55-175">To enable token authentication, ASP.NET Core supports several options for using [OAuth 2.0](https://oauth.net/2/) and [OpenID Connect](https://openid.net/connect/).</span></span>

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a><span data-ttu-id="41a55-176">S’authentifier avec un fournisseur d’identité OpenID Connect ou OAuth 2.0</span><span class="sxs-lookup"><span data-stu-id="41a55-176">Authenticate with an OpenID Connect or OAuth 2.0 Identity provider</span></span>

<span data-ttu-id="41a55-177">Si les informations utilisateur sont stockées dans Azure Active Directory ou une autre solution d’identité qui prend en charge OpenID Connect ou OAuth 2.0, vous pouvez utiliser le package **Microsoft.AspNetCore.Authentication.OpenIdConnect** pour une authentification via le workflow OpenID Connect.</span><span class="sxs-lookup"><span data-stu-id="41a55-177">If user information is stored in Azure Active Directory or another identity solution that supports OpenID Connect or OAuth 2.0, you can use the **Microsoft.AspNetCore.Authentication.OpenIdConnect** package to authenticate using the OpenID Connect workflow.</span></span> <span data-ttu-id="41a55-178">Par exemple, pour s’authentifier auprès du microservice Identity.Api dans eShopOnContainers, une application web ASP.NET Core peut utiliser le middleware de ce package, comme indiqué dans l’exemple simplifié suivant dans `Startup.cs` :</span><span class="sxs-lookup"><span data-stu-id="41a55-178">For example, to authenticate to the Identity.Api microservice in eShopOnContainers, an ASP.NET Core web application can use middleware from that package as shown in the following simplified example in `Startup.cs`:</span></span>

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseAuthentication();
    //…
    app.UseEndpoints(endpoints =>
    {
        //...
    });
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");
    var callBackUrl = Configuration.GetValue<string>("CallBackUrl");
    var sessionCookieLifetime = configuration.GetValue("SessionCookieLifetimeMinutes", 60);

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;
    })
    .AddCookie(setup => setup.ExpireTimeSpan = TimeSpan.FromMinutes(sessionCookieLifetime))
    .AddOpenIdConnect(options =>
    {
        options.SignInScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.Authority = identityUrl.ToString();
        options.SignedOutRedirectUri = callBackUrl.ToString();
        options.ClientId = useLoadTest ? "mvctest" : "mvc";
        options.ClientSecret = "secret";
        options.ResponseType = useLoadTest ? "code id_token token" : "code id_token";
        options.SaveTokens = true;
        options.GetClaimsFromUserInfoEndpoint = true;
        options.RequireHttpsMetadata = false;
        options.Scope.Add("openid");
        options.Scope.Add("profile");
        options.Scope.Add("orders");
        options.Scope.Add("basket");
        options.Scope.Add("marketing");
        options.Scope.Add("locations");
        options.Scope.Add("webshoppingagg");
        options.Scope.Add("orders.signalrhub");
    });
}
```

<span data-ttu-id="41a55-179">Notez que lorsque vous utilisez ce workflow, le middleware ASP.NET Core Identity n’est pas nécessaire dans la mesure où le stockage des informations utilisateur et l’authentification sont gérés par le service Identity.</span><span class="sxs-lookup"><span data-stu-id="41a55-179">Note that when you use this workflow, the ASP.NET Core Identity middleware is not needed, because all user information storage and authentication is handled by the Identity service.</span></span>

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a><span data-ttu-id="41a55-180">Émettre des jetons de sécurité à partir d’un service ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="41a55-180">Issue security tokens from an ASP.NET Core service</span></span>

<span data-ttu-id="41a55-181">Si vous préférez émettre des jetons de sécurité pour les utilisateurs locaux d’ASP.NET Core Identity plutôt que de faire appel à un fournisseur d’identité externe, vous pouvez profiter de quelques bibliothèques intéressantes.</span><span class="sxs-lookup"><span data-stu-id="41a55-181">If you prefer to issue security tokens for local ASP.NET Core Identity users rather than using an external identity provider, you can take advantage of some good third-party libraries.</span></span>

<span data-ttu-id="41a55-182">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) et [OpenIddict](https://github.com/openiddict/openiddict-core) sont des fournisseurs OpenID Connect qui s’intègrent facilement à ASP.NET Core Identity pour vous permettre d’émettre des jetons de sécurité à partir d’un service ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="41a55-182">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) and [OpenIddict](https://github.com/openiddict/openiddict-core) are OpenID Connect providers that integrate easily with ASP.NET Core Identity to let you issue security tokens from an ASP.NET Core service.</span></span> <span data-ttu-id="41a55-183">La [documentation IdentityServer4](https://identityserver4.readthedocs.io/en/latest/) explique en détail comment utiliser la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="41a55-183">The [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/latest/) has in-depth instructions for using the library.</span></span> <span data-ttu-id="41a55-184">Ceci étant, voici sommairement comment émettre des jetons à l’aide d’IdentityServer4 :</span><span class="sxs-lookup"><span data-stu-id="41a55-184">However, the basic steps to using IdentityServer4 to issue tokens are as follows.</span></span>

1. <span data-ttu-id="41a55-185">Appelez app.UseIdentityServer dans la méthode Startup.Configure pour ajouter IdentityServer4 au pipeline de traitement des requêtes HTTP de l’application.</span><span class="sxs-lookup"><span data-stu-id="41a55-185">You call app.UseIdentityServer in the Startup.Configure method to add IdentityServer4 to the application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="41a55-186">Cela permet à la bibliothèque de remettre les requêtes aux points de terminaison OpenID Connect et OAuth2 comme connect/token.</span><span class="sxs-lookup"><span data-stu-id="41a55-186">This lets the library serve requests to OpenID Connect and OAuth2 endpoints like /connect/token.</span></span>

2. <span data-ttu-id="41a55-187">Configurez IdentityServer4 dans Startup.ConfigureServices en effectuant un appel à services.AddIdentityServer.</span><span class="sxs-lookup"><span data-stu-id="41a55-187">You configure IdentityServer4 in Startup.ConfigureServices by making a call to services.AddIdentityServer.</span></span>

3. <span data-ttu-id="41a55-188">Configurez le serveur d’identité en définissant les données suivantes :</span><span class="sxs-lookup"><span data-stu-id="41a55-188">You configure identity server by setting the following data:</span></span>

   - <span data-ttu-id="41a55-189">Les [informations d’identification](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) à utiliser pour la signature.</span><span class="sxs-lookup"><span data-stu-id="41a55-189">The [credentials](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) to use for signing.</span></span>

   - <span data-ttu-id="41a55-190">Les [ressources d’identité et d’API](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) auxquelles les utilisateurs pourraient demander à accéder :</span><span class="sxs-lookup"><span data-stu-id="41a55-190">The [Identity and API resources](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) that users might request access to:</span></span>

      - <span data-ttu-id="41a55-191">Les ressources d’API représentent les données protégées ou les fonctionnalités auxquelles un utilisateur peut accéder avec un jeton d’accès.</span><span class="sxs-lookup"><span data-stu-id="41a55-191">API resources represent protected data or functionality that a user can access with an access token.</span></span> <span data-ttu-id="41a55-192">Par exemple, il peut s’agit d’une API web (ou un ensemble d’API) qui nécessite une autorisation.</span><span class="sxs-lookup"><span data-stu-id="41a55-192">An example of an API resource would be a web API (or set of APIs) that requires authorization.</span></span>

      - <span data-ttu-id="41a55-193">Les ressources d’identité représentent les informations (revendications) qui sont fournies à un client pour identifier un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="41a55-193">Identity resources represent information (claims) that are given to a client to identify a user.</span></span> <span data-ttu-id="41a55-194">Les revendications peuvent inclure le nom d’utilisateur, l’adresse de messagerie, etc.</span><span class="sxs-lookup"><span data-stu-id="41a55-194">The claims might include the user name, email address, and so on.</span></span>

   - <span data-ttu-id="41a55-195">Les [clients](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) appelés à se connecter pour demander des jetons.</span><span class="sxs-lookup"><span data-stu-id="41a55-195">The [clients](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) that will be connecting in order to request tokens.</span></span>

   - <span data-ttu-id="41a55-196">Le mécanisme de stockage des informations de l’utilisateur, tel que [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) ou une solution équivalente.</span><span class="sxs-lookup"><span data-stu-id="41a55-196">The storage mechanism for user information, such as [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) or an alternative.</span></span>

<span data-ttu-id="41a55-197">Au moment de spécifier les clients et les ressources que doit utiliser IdentityServer4, vous pouvez transmettre une collection <xref:System.Collections.Generic.IEnumerable%601> du type approprié aux méthodes qui acceptent les magasins de clients ou de ressources en mémoire.</span><span class="sxs-lookup"><span data-stu-id="41a55-197">When you specify clients and resources for IdentityServer4 to use, you can pass an <xref:System.Collections.Generic.IEnumerable%601> collection of the appropriate type to methods that take in-memory client or resource stores.</span></span> <span data-ttu-id="41a55-198">Pour les scénarios plus complexes, vous pouvez aussi indiquer des types de fournisseurs de clients ou de ressources via l’injection de dépendances.</span><span class="sxs-lookup"><span data-stu-id="41a55-198">Or for more complex scenarios, you can provide client or resource provider types via Dependency Injection.</span></span>

<span data-ttu-id="41a55-199">Voici un exemple de configuration qui vise à faire utiliser à IdentityServer4 les ressources et les clients en mémoire fournis par un type IClientStore personnalisé :</span><span class="sxs-lookup"><span data-stu-id="41a55-199">A sample configuration for IdentityServer4 to use in-memory resources and clients provided by a custom IClientStore type might look like the following example:</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    //...
    services.AddSingleton<IClientStore, CustomClientStore>();
    services.AddIdentityServer()
        .AddSigningCredential("CN=sts")
        .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
        .AddAspNetIdentity<ApplicationUser>();
    //...
}
```

### <a name="consume-security-tokens"></a><span data-ttu-id="41a55-200">Consommer des jetons de sécurité</span><span class="sxs-lookup"><span data-stu-id="41a55-200">Consume security tokens</span></span>

<span data-ttu-id="41a55-201">L’authentification auprès d’un point de terminaison OpenID Connect ou l’émission de vos propres jetons de sécurité recouvrent certains scénarios.</span><span class="sxs-lookup"><span data-stu-id="41a55-201">Authenticating against an OpenID Connect endpoint or issuing your own security tokens covers some scenarios.</span></span> <span data-ttu-id="41a55-202">Mais qu’en est-il d’un service qui doit simplement limiter l’accès aux utilisateurs disposant de jetons de sécurité valides qui ont été fournis par un autre service ?</span><span class="sxs-lookup"><span data-stu-id="41a55-202">But what about a service that simply needs to limit access to those users who have valid security tokens that were provided by a different service?</span></span>

<span data-ttu-id="41a55-203">Pour ce scénario, le middleware d’authentification qui gère les jetons JWT est disponible dans le package **Microsoft.AspNetCore.Authentication.JwtBearer**.</span><span class="sxs-lookup"><span data-stu-id="41a55-203">For that scenario, authentication middleware that handles JWT tokens is available in the **Microsoft.AspNetCore.Authentication.JwtBearer** package.</span></span> <span data-ttu-id="41a55-204">JWT est l’acronyme de « [JSON Web Token](https://tools.ietf.org/html/rfc7519) » (jeton web JSON). Il s’agit d’un format de jeton de sécurité courant (défini par la norme RFC 7519) destiné à communiquer les revendications de sécurité.</span><span class="sxs-lookup"><span data-stu-id="41a55-204">JWT stands for "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" and is a common security token format (defined by RFC 7519) for communicating security claims.</span></span> <span data-ttu-id="41a55-205">Un exemple simplifié d’utilisation de middlewares pour consommer ces jetons pourrait ressembler à ce fragment de code, pris du microservice Ordering.Api d’eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="41a55-205">A simplified example of how to use middleware to consume such tokens might look like this code fragment, taken from the Ordering.Api microservice of eShopOnContainers.</span></span>

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    // Configure the pipeline to use authentication
    app.UseAuthentication();
    //…
    app.UseEndpoints(endpoints =>
    {
        //...
    });
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultAuthenticateScheme = AspNetCore.Authentication.JwtBearer.JwtBearerDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = AspNetCore.Authentication.JwtBearer.JwtBearerDefaults.AuthenticationScheme;

    }).AddJwtBearer(options =>
    {
        options.Authority = identityUrl;
        options.RequireHttpsMetadata = false;
        options.Audience = "orders";
    });
}
```

<span data-ttu-id="41a55-206">Les paramètres utilisés dans ce cas sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="41a55-206">The parameters in this usage are:</span></span>

- <span data-ttu-id="41a55-207">`Audience` représente le récepteur du jeton entrant ou la ressource à laquelle le jeton accorde l’accès.</span><span class="sxs-lookup"><span data-stu-id="41a55-207">`Audience` represents the receiver of the incoming token or the resource that the token grants access to.</span></span> <span data-ttu-id="41a55-208">Si la valeur spécifiée dans ce paramètre ne correspond pas à celle du paramètre du jeton, celui-ci est rejeté.</span><span class="sxs-lookup"><span data-stu-id="41a55-208">If the value specified in this parameter does not match the parameter in the token, the token will be rejected.</span></span>

- <span data-ttu-id="41a55-209">`Authority` est l’adresse du serveur d’authentification émetteur de jetons.</span><span class="sxs-lookup"><span data-stu-id="41a55-209">`Authority` is the address of the token-issuing authentication server.</span></span> <span data-ttu-id="41a55-210">L’intergiciel d’authentification du porteur de jeton JWT utilise cet URI pour obtenir la clé publique qui permet de valider la signature du jeton.</span><span class="sxs-lookup"><span data-stu-id="41a55-210">The JWT bearer authentication middleware uses this URI to get the public key that can be used to validate the token's signature.</span></span> <span data-ttu-id="41a55-211">Par ailleurs, le middleware vérifie que la valeur du paramètre `iss` du jeton correspond à cet URI.</span><span class="sxs-lookup"><span data-stu-id="41a55-211">The middleware also confirms that the `iss` parameter in the token matches this URI.</span></span>

<span data-ttu-id="41a55-212">Un autre paramètre, `RequireHttpsMetadata`, est utile pour les tests ; vous définissez ce paramètre avec la valeur false pour effectuer des tests dans des environnements où vous n’avez pas de certificats.</span><span class="sxs-lookup"><span data-stu-id="41a55-212">Another parameter, `RequireHttpsMetadata`, is useful for testing purposes; you set this parameter to false so you can test in environments where you don't have certificates.</span></span> <span data-ttu-id="41a55-213">Dans les déploiements réels, les jetons du porteur JWT doivent toujours être transmis uniquement sur HTTPS.</span><span class="sxs-lookup"><span data-stu-id="41a55-213">In real-world deployments, JWT bearer tokens should always be passed only over HTTPS.</span></span>

<span data-ttu-id="41a55-214">Quand cet intergiciel est en place, les jetons JWT sont automatiquement extraits des en-têtes d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="41a55-214">With this middleware in place, JWT tokens are automatically extracted from authorization headers.</span></span> <span data-ttu-id="41a55-215">Ils sont ensuite désérialisés, validés (en utilisant les valeurs des paramètres `Audience` et `Authority`) puis stockés en tant qu’informations utilisateur pour être référencées par la suite par des actions MVC ou des filtres d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="41a55-215">They are then deserialized, validated (using the values in the `Audience` and `Authority` parameters), and stored as user information to be referenced later by MVC actions or authorization filters.</span></span>

<span data-ttu-id="41a55-216">L’intergiciel d’authentification du porteur JWT peut aussi prendre en charge des scénarios plus avancés, tels que l’utilisation d’un certificat local pour valider un jeton si l’autorité n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="41a55-216">The JWT bearer authentication middleware can also support more advanced scenarios, such as using a local certificate to validate a token if the authority is not available.</span></span> <span data-ttu-id="41a55-217">Pour ce scénario, vous pouvez spécifier un objet `TokenValidationParameters` dans l’objet `JwtBearerOptions`.</span><span class="sxs-lookup"><span data-stu-id="41a55-217">For this scenario, you can specify a `TokenValidationParameters` object in the `JwtBearerOptions` object.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="41a55-218">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="41a55-218">Additional resources</span></span>

- <span data-ttu-id="41a55-219">**Partage des cookies entre les applications** </span><span class="sxs-lookup"><span data-stu-id="41a55-219">**Sharing cookies between applications** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/cookie-sharing](/aspnet/core/security/cookie-sharing)

- <span data-ttu-id="41a55-220">**Présentation d’Identity** </span><span class="sxs-lookup"><span data-stu-id="41a55-220">**Introduction to Identity** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- <span data-ttu-id="41a55-221">**Rick Anderson. Authentification à deux facteurs avec SMS** </span><span class="sxs-lookup"><span data-stu-id="41a55-221">**Rick Anderson. Two-factor authentication with SMS** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/2fa](/aspnet/core/security/authentication/2fa)

- <span data-ttu-id="41a55-222">**Activation de l’authentification à l’aide de Facebook, de Google et d’autres fournisseurs externes** </span><span class="sxs-lookup"><span data-stu-id="41a55-222">**Enabling authentication using Facebook, Google and other external providers** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/social/](/aspnet/core/security/authentication/social/)

- <span data-ttu-id="41a55-223">**Michell Anicas. Présentation d’OAuth 2** </span><span class="sxs-lookup"><span data-stu-id="41a55-223">**Michell Anicas. An Introduction to OAuth 2** </span></span>\
  <https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2>

- <span data-ttu-id="41a55-224">**AspNet.Security.OAuth.Providers** (référentiel GitHub pour fournisseurs d’autorisation OAuth ASP.NET) </span><span class="sxs-lookup"><span data-stu-id="41a55-224">**AspNet.Security.OAuth.Providers** (GitHub repo for ASP.NET OAuth providers) </span></span>\
  <https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src>

- <span data-ttu-id="41a55-225">**IdentityServer4. Documentation officielle** </span><span class="sxs-lookup"><span data-stu-id="41a55-225">**IdentityServer4. Official documentation** </span></span>\
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
><span data-ttu-id="41a55-226">[Précédent](../implement-resilient-applications/monitor-app-health.md)
>[Suivant](authorization-net-microservices-web-applications.md)</span><span class="sxs-lookup"><span data-stu-id="41a55-226">[Previous](../implement-resilient-applications/monitor-app-health.md)
[Next](authorization-net-microservices-web-applications.md)</span></span>
