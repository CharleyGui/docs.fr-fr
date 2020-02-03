---
title: IdentityServer pour les applications Cloud natives
description: Architecture des applications .NET natives Cloud pour Azure | IdentityServer
ms.date: 06/30/2019
ms.openlocfilehash: 48d0b95a40682f3127127851781b4d0e26e44630
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728579"
---
# <a name="identityserver-for-cloud-native-applications"></a><span data-ttu-id="d4528-103">IdentityServer pour les applications Cloud natives</span><span class="sxs-lookup"><span data-stu-id="d4528-103">IdentityServer for cloud-native applications</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="d4528-104">IdentityServer est un serveur d’authentification open source qui implémente les normes OpenID Connect (OIDC) et OAuth 2,0 pour ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d4528-104">IdentityServer is an open-source authentication server that implements OpenID Connect (OIDC) and OAuth 2.0 standards for ASP.NET Core.</span></span> <span data-ttu-id="d4528-105">Il est conçu pour fournir un moyen courant d’authentifier les demandes à toutes vos applications, qu’il s’agisse de points de terminaison Web, natifs, mobiles ou d’API.</span><span class="sxs-lookup"><span data-stu-id="d4528-105">It's designed to provide a common way to authenticate requests to all of your applications, whether they're web, native, mobile, or API endpoints.</span></span> <span data-ttu-id="d4528-106">IdentityServer peut être utilisé pour implémenter l’authentification unique (SSO) pour plusieurs applications et types d’applications.</span><span class="sxs-lookup"><span data-stu-id="d4528-106">IdentityServer can be used to implement Single Sign-On (SSO) for multiple applications and application types.</span></span> <span data-ttu-id="d4528-107">Il peut être utilisé pour authentifier les utilisateurs réels via des formulaires de connexion et des interfaces utilisateur similaires, ainsi que l’authentification basée sur les services qui implique généralement l’émission, la vérification et le renouvellement de jetons sans aucune interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d4528-107">It can be used to authenticate actual users via sign-in forms and similar user interfaces as well as service-based authentication that typically involves token issuance, verification, and renewal without any user interface.</span></span> <span data-ttu-id="d4528-108">IdentityServer est conçu pour être une solution personnalisable.</span><span class="sxs-lookup"><span data-stu-id="d4528-108">IdentityServer is designed to be a customizable solution.</span></span> <span data-ttu-id="d4528-109">Chaque instance est généralement personnalisée pour s’adapter aux besoins d’une organisation et/ou d’un ensemble d’applications.</span><span class="sxs-lookup"><span data-stu-id="d4528-109">Each instance is typically customized to suit an individual organization and/or set of applications' needs.</span></span>

## <a name="common-web-app-scenarios"></a><span data-ttu-id="d4528-110">Scénarios courants pour les applications Web</span><span class="sxs-lookup"><span data-stu-id="d4528-110">Common web app scenarios</span></span>

<span data-ttu-id="d4528-111">En règle générale, les applications doivent prendre en charge tout ou partie des scénarios suivants :</span><span class="sxs-lookup"><span data-stu-id="d4528-111">Typically, applications need to support some or all of the following scenarios:</span></span>

- <span data-ttu-id="d4528-112">Utilisateurs humains accédant aux applications Web à l’aide d’un navigateur.</span><span class="sxs-lookup"><span data-stu-id="d4528-112">Human users accessing web applications with a browser.</span></span>
- <span data-ttu-id="d4528-113">Utilisateurs humains accédant aux API Web principales à partir d’applications basées sur un navigateur.</span><span class="sxs-lookup"><span data-stu-id="d4528-113">Human users accessing back-end Web APIs from browser-based apps.</span></span>
- <span data-ttu-id="d4528-114">Utilisateurs humains sur des clients mobiles/natifs accédant aux API Web principales.</span><span class="sxs-lookup"><span data-stu-id="d4528-114">Human users on mobile/native clients accessing back-end Web APIs.</span></span>
- <span data-ttu-id="d4528-115">Autres applications qui accèdent aux API Web principales (sans utilisateur ou interface utilisateur actif).</span><span class="sxs-lookup"><span data-stu-id="d4528-115">Other applications accessing back-end Web APIs (without an active user or user interface).</span></span>
- <span data-ttu-id="d4528-116">Toute application peut avoir besoin d’interagir avec d’autres API Web, à l’aide de sa propre identité ou en déléguant l’identité de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d4528-116">Any application may need to interact with other Web APIs, using its own identity or delegating to the user's identity.</span></span>

<span data-ttu-id="d4528-117">![les types d’applications et les scénarios](./media/application-types.png)
**Figure 8-1**.</span><span class="sxs-lookup"><span data-stu-id="d4528-117">![Application types and scenarios](./media/application-types.png)
**Figure 8-1**.</span></span> <span data-ttu-id="d4528-118">Types d’applications et scénarios.</span><span class="sxs-lookup"><span data-stu-id="d4528-118">Application types and scenarios.</span></span>

<span data-ttu-id="d4528-119">Dans chacun de ces scénarios, la fonctionnalité exposée doit être sécurisée contre toute utilisation non autorisée.</span><span class="sxs-lookup"><span data-stu-id="d4528-119">In each of these scenarios, the exposed functionality needs to be secured against unauthorized use.</span></span> <span data-ttu-id="d4528-120">Au minimum, cela nécessite généralement l’authentification de l’utilisateur ou du principal qui effectue une demande de ressource.</span><span class="sxs-lookup"><span data-stu-id="d4528-120">At a minimum, this typically requires authenticating the user or principal making a request for a resource.</span></span> <span data-ttu-id="d4528-121">Cette authentification peut utiliser l’un des protocoles courants tels que SAML2p, WS-FED ou OpenID Connect.</span><span class="sxs-lookup"><span data-stu-id="d4528-121">This authentication may use one of several common protocols such as SAML2p, WS-Fed, or OpenID Connect.</span></span> <span data-ttu-id="d4528-122">La communication avec les API utilise généralement le protocole OAuth2 et sa prise en charge des jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="d4528-122">Communicating with APIs typically uses the OAuth2 protocol and its support for security tokens.</span></span> <span data-ttu-id="d4528-123">La séparation de ces problèmes critiques de sécurité transversale et de leurs détails d’implémentation à partir des applications elles-mêmes garantit la cohérence et améliore la sécurité et la maintenabilité.</span><span class="sxs-lookup"><span data-stu-id="d4528-123">Separating these critical cross-cutting security concerns and their implementation details from the applications themselves ensures consistency and improves security and maintainability.</span></span> <span data-ttu-id="d4528-124">L’externalisation de ces préoccupations à un produit dédié comme IdentityServer permet à chaque application de résoudre ces problèmes eux-mêmes.</span><span class="sxs-lookup"><span data-stu-id="d4528-124">Outsourcing these concerns to a dedicated product like IdentityServer helps the requirement for every application to solve these problems itself.</span></span>

<span data-ttu-id="d4528-125">IdentityServer fournit un intergiciel (middleware) qui s’exécute dans une application ASP.NET Coree et ajoute la prise en charge de OpenID Connect et OAuth2 (voir [spécifications prises en charge](http://docs.identityserver.io/en/latest/intro/specs.html)).</span><span class="sxs-lookup"><span data-stu-id="d4528-125">IdentityServer provides middleware that runs within an ASP.NET Core application and adds support for OpenID Connect and OAuth2 (see [supported specifications](http://docs.identityserver.io/en/latest/intro/specs.html)).</span></span> <span data-ttu-id="d4528-126">Les organisations créent leur propre ASP.NET Core application à l’aide de l’intergiciel (middleware) IdentityServer pour agir en tant que STS pour tous les protocoles de sécurité basés sur les jetons.</span><span class="sxs-lookup"><span data-stu-id="d4528-126">Organizations would create their own ASP.NET Core app using IdentityServer middleware to act as the STS for all of their token-based security protocols.</span></span> <span data-ttu-id="d4528-127">L’intergiciel IdentityServer expose des points de terminaison pour prendre en charge les fonctionnalités standard, notamment :</span><span class="sxs-lookup"><span data-stu-id="d4528-127">The IdentityServer middleware exposes endpoints to support standard functionality, including:</span></span>

- <span data-ttu-id="d4528-128">Autoriser (authentifier l’utilisateur final)</span><span class="sxs-lookup"><span data-stu-id="d4528-128">Authorize (authenticate the end user)</span></span>
- <span data-ttu-id="d4528-129">Jeton (demander un jeton par programmation)</span><span class="sxs-lookup"><span data-stu-id="d4528-129">Token (request a token programmatically)</span></span>
- <span data-ttu-id="d4528-130">Découverte (métadonnées relatives au serveur)</span><span class="sxs-lookup"><span data-stu-id="d4528-130">Discovery (metadata about the server)</span></span>
- <span data-ttu-id="d4528-131">Informations utilisateur (obtenir les informations utilisateur avec un jeton d’accès valide)</span><span class="sxs-lookup"><span data-stu-id="d4528-131">User Info (get user information with a valid access token)</span></span>
- <span data-ttu-id="d4528-132">Autorisation de l’appareil (utilisée pour démarrer l’autorisation du workflow de l’appareil)</span><span class="sxs-lookup"><span data-stu-id="d4528-132">Device Authorization (used to start device flow authorization)</span></span>
- <span data-ttu-id="d4528-133">Inretrospect (validation de jeton)</span><span class="sxs-lookup"><span data-stu-id="d4528-133">Introspection (token validation)</span></span>
- <span data-ttu-id="d4528-134">Révocation (révocation de jeton)</span><span class="sxs-lookup"><span data-stu-id="d4528-134">Revocation (token revocation)</span></span>
- <span data-ttu-id="d4528-135">Terminer la session (déclencher la déconnexion unique pour toutes les applications)</span><span class="sxs-lookup"><span data-stu-id="d4528-135">End Session (trigger single sign-out across all apps)</span></span>

## <a name="getting-started"></a><span data-ttu-id="d4528-136">Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="d4528-136">Getting started</span></span>

<span data-ttu-id="d4528-137">IdentityServer4 est open source et gratuit à utiliser.</span><span class="sxs-lookup"><span data-stu-id="d4528-137">IdentityServer4 is open-source and free to use.</span></span> <span data-ttu-id="d4528-138">Vous pouvez l’ajouter à vos applications à l’aide de ses packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="d4528-138">You can add it to your applications using its NuGet packages.</span></span> <span data-ttu-id="d4528-139">Le package principal est [IdentityServer4](https://www.nuget.org/packages/IdentityServer4/) qui a été téléchargé plus de 4 millions fois.</span><span class="sxs-lookup"><span data-stu-id="d4528-139">The main package is [IdentityServer4](https://www.nuget.org/packages/IdentityServer4/) that has been downloaded over four million times.</span></span> <span data-ttu-id="d4528-140">Le package de base n’inclut pas de code d’interface utilisateur et ne prend en charge que dans la configuration de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="d4528-140">The base package doesn't include any user interface code and only supports in memory configuration.</span></span> <span data-ttu-id="d4528-141">Pour l’utiliser avec une base de données, vous devez également disposer d’un fournisseur de données comme [IdentityServer4. EntityFramework](https://www.nuget.org/packages/IdentityServer4.EntityFramework) qui utilise Entity Framework Core pour stocker les données de configuration et opérationnelles pour IdentityServer.</span><span class="sxs-lookup"><span data-stu-id="d4528-141">To use it with a database, you'll also want a data provider like [IdentityServer4.EntityFramework](https://www.nuget.org/packages/IdentityServer4.EntityFramework) that uses Entity Framework Core to store configuration and operational data for IdentityServer.</span></span> <span data-ttu-id="d4528-142">Pour l’interface utilisateur, vous pouvez copier des fichiers à partir du référentiel de l' [interface utilisateur de démarrage rapide](https://github.com/IdentityServer/IdentityServer4.Quickstart.UI) dans votre application ASP.net Core MVC pour ajouter la prise en charge de la connexion et de la déconnexion à l’aide de l’intergiciel IdentityServer.</span><span class="sxs-lookup"><span data-stu-id="d4528-142">For user interface, you can copy files from the [Quickstart UI repository](https://github.com/IdentityServer/IdentityServer4.Quickstart.UI) into your ASP.NET Core MVC application to add support for sign in and sign out using IdentityServer middleware.</span></span>

## <a name="configuration"></a><span data-ttu-id="d4528-143">Configuration</span><span class="sxs-lookup"><span data-stu-id="d4528-143">Configuration</span></span>

<span data-ttu-id="d4528-144">IdentityServer prend en charge différents types de protocoles et de fournisseurs d’authentification sociale qui peuvent être configurés dans le cadre de chaque installation personnalisée.</span><span class="sxs-lookup"><span data-stu-id="d4528-144">IdentityServer supports different kinds of protocols and social authentication providers that can be configured as part of each custom installation.</span></span> <span data-ttu-id="d4528-145">Cette opération est généralement effectuée dans la classe `Startup` de l’application ASP.NET Core dans la méthode `ConfigureServices`.</span><span class="sxs-lookup"><span data-stu-id="d4528-145">This is typically done in the ASP.NET Core application's `Startup` class in the `ConfigureServices` method.</span></span> <span data-ttu-id="d4528-146">La configuration implique la spécification des protocoles pris en charge et des chemins d’accès aux serveurs et points de terminaison qui seront utilisés.</span><span class="sxs-lookup"><span data-stu-id="d4528-146">The configuration involves specifying the supported protocols and the paths to the servers and endpoints that will be used.</span></span> <span data-ttu-id="d4528-147">La figure 8-2 montre un exemple de configuration issu du projet d’interface utilisateur de démarrage rapide IdentityServer4 :</span><span class="sxs-lookup"><span data-stu-id="d4528-147">Figure 8-2 shows an example configuration taken from the IdentityServer4 Quickstart UI project:</span></span>

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();

        // some details omitted
        services.AddIdentityServer();

          services.AddAuthentication()
            .AddGoogle("Google", options =>
            {
                options.SignInScheme = IdentityServerConstants.ExternalCookieAuthenticationScheme;

                options.ClientId = "<insert here>";
                options.ClientSecret = "<insert here>";
            })
            .AddOpenIdConnect("demoidsrv", "IdentityServer", options =>
            {
                options.SignInScheme = IdentityServerConstants.ExternalCookieAuthenticationScheme;
                options.SignOutScheme = IdentityServerConstants.SignoutScheme;

                options.Authority = "https://demo.identityserver.io/";
                options.ClientId = "implicit";
                options.ResponseType = "id_token";
                options.SaveTokens = true;
                options.CallbackPath = new PathString("/signin-idsrv");
                options.SignedOutCallbackPath = new PathString("/signout-callback-idsrv");
                options.RemoteSignOutPath = new PathString("/signout-idsrv");

                options.TokenValidationParameters = new TokenValidationParameters
                {
                    NameClaimType = "name",
                    RoleClaimType = "role"
                };
            });
    }
}
```

<span data-ttu-id="d4528-148">**Figure 8-2** :</span><span class="sxs-lookup"><span data-stu-id="d4528-148">**Figure 8-2**.</span></span> <span data-ttu-id="d4528-149">Configuration de IdentityServer.</span><span class="sxs-lookup"><span data-stu-id="d4528-149">Configuring IdentityServer.</span></span>

<span data-ttu-id="d4528-150">IdentityServer héberge également un site de démonstration public qui peut être utilisé pour tester différents protocoles et configurations.</span><span class="sxs-lookup"><span data-stu-id="d4528-150">IdentityServer also hosts a public demo site that can be used to test various protocols and configurations.</span></span> <span data-ttu-id="d4528-151">Il se trouve dans [https://demo.identityserver.io/](https://demo.identityserver.io/) et contient des informations sur la façon de configurer son comportement en fonction du `client_id` qui lui est fourni.</span><span class="sxs-lookup"><span data-stu-id="d4528-151">It's located at [https://demo.identityserver.io/](https://demo.identityserver.io/) and includes information on how to configure its behavior based on the `client_id` provided to it.</span></span>

## <a name="javascript-clients"></a><span data-ttu-id="d4528-152">Clients JavaScript</span><span class="sxs-lookup"><span data-stu-id="d4528-152">JavaScript clients</span></span>

<span data-ttu-id="d4528-153">De nombreuses applications Cloud natives exploitent les API côté serveur et les applications à page unique clientes riches sur le serveur frontal.</span><span class="sxs-lookup"><span data-stu-id="d4528-153">Many cloud-native applications leverage server-side APIs and rich client single page applications (SPAs) on the front end.</span></span> <span data-ttu-id="d4528-154">IdentityServer fournit un [client JavaScript](http://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html) (`oidc-client.js`) via NPM qui peut être ajouté à spas pour lui permettre d’utiliser IdentityServer pour la connexion, la déconnexion et l’authentification basée sur les jetons des API Web.</span><span class="sxs-lookup"><span data-stu-id="d4528-154">IdentityServer ships a [JavaScript client](http://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html) (`oidc-client.js`) via NPM that can be added to SPAs to enable them to use IdentityServer for sign in, sign out, and token-based authentication of web APIs.</span></span>

## <a name="references"></a><span data-ttu-id="d4528-155">Références</span><span class="sxs-lookup"><span data-stu-id="d4528-155">References</span></span>

- [<span data-ttu-id="d4528-156">Documentation IdentityServer</span><span class="sxs-lookup"><span data-stu-id="d4528-156">IdentityServer documentation</span></span>](http://docs.identityserver.io/en/latest/)
- [<span data-ttu-id="d4528-157">Types d’applications</span><span class="sxs-lookup"><span data-stu-id="d4528-157">Application types</span></span>](https://docs.microsoft.com/azure/active-directory/develop/app-types)
- [<span data-ttu-id="d4528-158">Client JavaScript OIDC</span><span class="sxs-lookup"><span data-stu-id="d4528-158">JavaScript OIDC client</span></span>](http://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html)

>[!div class="step-by-step"]
><span data-ttu-id="d4528-159">[Précédent](azure-active-directory.md)
>[Suivant](security.md)</span><span class="sxs-lookup"><span data-stu-id="d4528-159">[Previous](azure-active-directory.md)
[Next](security.md)</span></span>
