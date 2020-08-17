---
title: 'Sécurité : authentification et autorisation dans ASP.NET Web Forms et Blazor'
description: Découvrez comment gérer l’authentification et l’autorisation dans ASP.NET Web Forms et Blazor .
author: ardalis
ms.author: daroth
no-loc:
- Blazor
ms.date: 09/11/2019
ms.openlocfilehash: 1cc82b14a940465c26377f9181a2e20b46b0783f
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267832"
---
# <a name="security-authentication-and-authorization-in-aspnet-web-forms-and-no-locblazor"></a><span data-ttu-id="a95fd-103">Sécurité : authentification et autorisation dans ASP.NET Web Forms et Blazor</span><span class="sxs-lookup"><span data-stu-id="a95fd-103">Security: Authentication and Authorization in ASP.NET Web Forms and Blazor</span></span>

<span data-ttu-id="a95fd-104">La migration à partir d’une application Web Forms ASP.NET vers Blazor va certainement nécessiter la mise à jour de la manière dont l’authentification et l’autorisation sont effectuées, en supposant que l’authentification a été configurée pour l’application.</span><span class="sxs-lookup"><span data-stu-id="a95fd-104">Migrating from an ASP.NET Web Forms application to Blazor will almost certainly require updating how authentication and authorization is performed, assuming the application had authentication configured.</span></span> <span data-ttu-id="a95fd-105">Ce chapitre explique comment effectuer une migration à partir de ASP.NET Web Forms modèle de fournisseur universel (pour l’appartenance, les rôles et les profils utilisateur) et comment utiliser l’identité ASP.NET Core à partir des Blazor applications.</span><span class="sxs-lookup"><span data-stu-id="a95fd-105">This chapter will cover how to migrate from the ASP.NET Web Forms universal provider model (for membership, roles, and user profiles) and how to work with ASP.NET Core Identity from Blazor apps.</span></span> <span data-ttu-id="a95fd-106">Bien que ce chapitre traite des étapes et des considérations générales, les étapes et scripts détaillés sont disponibles dans la documentation de référence.</span><span class="sxs-lookup"><span data-stu-id="a95fd-106">While this chapter will cover the high level steps and considerations, the detailed steps and scripts may be found in the referenced documentation.</span></span>

## <a name="aspnet-universal-providers"></a><span data-ttu-id="a95fd-107">Fournisseurs universels ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a95fd-107">ASP.NET universal providers</span></span>

<span data-ttu-id="a95fd-108">Depuis ASP.NET 2,0, la plateforme ASP.NET Web Forms a pris en charge un modèle de fournisseur pour diverses fonctionnalités, y compris l’appartenance.</span><span class="sxs-lookup"><span data-stu-id="a95fd-108">Since ASP.NET 2.0, the ASP.NET Web Forms platform has supported a provider model for a variety of features, including membership.</span></span> <span data-ttu-id="a95fd-109">Le fournisseur d’appartenances universel, avec le fournisseur de rôle facultatif, est très couramment déployé avec les applications ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="a95fd-109">The universal membership provider, along with the optional role provider, is very commonly deployed with ASP.NET Web Forms applications.</span></span> <span data-ttu-id="a95fd-110">Il offre une méthode fiable et sécurisée pour gérer l’authentification et l’autorisation qui continuent à fonctionner bien aujourd’hui.</span><span class="sxs-lookup"><span data-stu-id="a95fd-110">It offers a robust and secure way to manage authentication and authorization that continues to work well today.</span></span> <span data-ttu-id="a95fd-111">L’offre la plus récente de ces fournisseurs universels est disponible sous la forme d’un package NuGet, [Microsoft. Aspnet. Providers](https://www.nuget.org/packages/Microsoft.AspNet.Providers).</span><span class="sxs-lookup"><span data-stu-id="a95fd-111">The most recent offering of these universal providers is available as a NuGet package, [Microsoft.AspNet.Providers](https://www.nuget.org/packages/Microsoft.AspNet.Providers).</span></span>

<span data-ttu-id="a95fd-112">L’fournisseurs universels fonctionner avec un schéma de base de données SQL qui comprend des tables telles que `aspnet_Applications` , `aspnet_Membership` , `aspnet_Roles` et `aspnet_Users` .</span><span class="sxs-lookup"><span data-stu-id="a95fd-112">The Universal Providers work with a SQL database schema that includes tables like `aspnet_Applications`, `aspnet_Membership`, `aspnet_Roles`, and `aspnet_Users`.</span></span> <span data-ttu-id="a95fd-113">Lorsqu’ils sont configurés en exécutant la [ commandeaspnet_regsql.exe](https://docs.microsoft.com/previous-versions/ms229862(v=vs.140)), les fournisseurs installent les tables et les procédures stockées qui fournissent toutes les requêtes et commandes nécessaires à l’utilisation des données sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="a95fd-113">When configured by running the [aspnet_regsql.exe command](https://docs.microsoft.com/previous-versions/ms229862(v=vs.140)), the providers install tables and stored procedures that provide all of the necessary queries and commands necessary to work with the underlying data.</span></span> <span data-ttu-id="a95fd-114">Le schéma de base de données et ces procédures stockées ne sont pas compatibles avec les systèmes d’identité ASP.NET Identity et ASP.NET Core plus récents. les données existantes doivent donc être migrées dans le nouveau système.</span><span class="sxs-lookup"><span data-stu-id="a95fd-114">The database schema and these stored procedures are not compatible with newer ASP.NET Identity and ASP.NET Core Identity systems, so existing data must be migrated into the new system.</span></span> <span data-ttu-id="a95fd-115">La figure 1 montre un exemple de schéma de table configuré pour les fournisseurs universels.</span><span class="sxs-lookup"><span data-stu-id="a95fd-115">Figure 1 shows an example table schema configured for universal providers.</span></span>

![schéma des fournisseurs universels](./media/security/membership-tables.png)

<span data-ttu-id="a95fd-117">Le fournisseur universel gère les utilisateurs, l’appartenance, les rôles et les profils.</span><span class="sxs-lookup"><span data-stu-id="a95fd-117">The universal provider handles users, membership, roles, and profiles.</span></span> <span data-ttu-id="a95fd-118">Les utilisateurs reçoivent des identificateurs globaux uniques et des informations très simples (userId, userName) sont stockées dans la `aspnet_Users` table.</span><span class="sxs-lookup"><span data-stu-id="a95fd-118">Users are assigned globally unique identifiers and very basic information (userId, userName) is stored in the `aspnet_Users` table.</span></span> <span data-ttu-id="a95fd-119">Les informations d’authentification, telles que le mot de passe, le format de mot de passe, le Salt de mot de passe, les compteurs de verrouillage et les détails, etc., sont stockées dans la `aspnet_Membership` table.</span><span class="sxs-lookup"><span data-stu-id="a95fd-119">Authentication information, such as password, password format, password salt, lockout counters and details, etc. are stored in the `aspnet_Membership` table.</span></span> <span data-ttu-id="a95fd-120">Les rôles consistent simplement en noms et identificateurs uniques, qui sont attribués aux utilisateurs via la `aspnet_UsersInRoles` table d’association, fournissant ainsi une relation plusieurs-à-plusieurs.</span><span class="sxs-lookup"><span data-stu-id="a95fd-120">Roles consist simply of names and unique identifiers, which are assigned to users via the `aspnet_UsersInRoles` association table, providing a many-to-many relationship.</span></span>

<span data-ttu-id="a95fd-121">Si votre système existant utilise des rôles en plus de l’appartenance, vous devez migrer les comptes d’utilisateur, les mots de passe associés, les rôles et l’appartenance au rôle dans ASP.NET Core identité.</span><span class="sxs-lookup"><span data-stu-id="a95fd-121">If your existing system is using roles in addition to membership, you will need to migrate the user accounts, the associated passwords, the roles, and the role membership into ASP.NET Core Identity.</span></span> <span data-ttu-id="a95fd-122">Vous devrez également mettre à jour votre code là où vous effectuez actuellement des vérifications de rôle à l’aide d’instructions If pour tirer parti des filtres déclaratifs, des attributs et/ou des balises d’aide.</span><span class="sxs-lookup"><span data-stu-id="a95fd-122">You will also most likely need to update your code where you're currently performing role checks using if statements to instead leverage declarative filters, attributes, and/or tag helpers.</span></span> <span data-ttu-id="a95fd-123">Nous examinerons les considérations relatives à la migration plus en détail à la fin de ce chapitre.</span><span class="sxs-lookup"><span data-stu-id="a95fd-123">We will review migration considerations in greater detail at the end of this chapter.</span></span>

### <a name="authorization-configuration-in-web-forms"></a><span data-ttu-id="a95fd-124">Configuration de l’autorisation dans Web Forms</span><span class="sxs-lookup"><span data-stu-id="a95fd-124">Authorization configuration in Web Forms</span></span>

<span data-ttu-id="a95fd-125">Pour configurer l’accès autorisé à certaines pages d’une application ASP.NET Web Forms, vous spécifiez généralement que certaines pages ou dossiers ne sont pas accessibles aux utilisateurs anonymes.</span><span class="sxs-lookup"><span data-stu-id="a95fd-125">To configure authorized access to certain pages in an ASP.NET Web Forms application, typically you specify that certain pages or folders are inaccessible to anonymous users.</span></span> <span data-ttu-id="a95fd-126">Cela s’effectue dans le fichier web.config :</span><span class="sxs-lookup"><span data-stu-id="a95fd-126">This is done in the web.config file:</span></span>

```xml
<?xml version="1.0"?>
<configuration>
    <system.web>
      <authentication mode="Forms">
        <forms defaultUrl="~/home.aspx" loginUrl="~/login.aspx"
          slidingExpiration="true" timeout="2880"></forms>
      </authentication>

      <authorization>
        <deny users="?" />
      </authorization>
    </system.web>
</configuration>
```

<span data-ttu-id="a95fd-127">La `authentication` section de configuration configure l’authentification par formulaire pour l’application.</span><span class="sxs-lookup"><span data-stu-id="a95fd-127">The `authentication` configuration section sets up forms authentication for the application.</span></span> <span data-ttu-id="a95fd-128">La `authorization` section est utilisée pour interdire les utilisateurs anonymes pour l’application entière.</span><span class="sxs-lookup"><span data-stu-id="a95fd-128">The `authorization` section is used to disallow anonymous users for the entire application.</span></span> <span data-ttu-id="a95fd-129">Toutefois, vous pouvez fournir des règles d’autorisation plus granulaires à chaque emplacement, et appliquer des vérifications d’autorisation basées sur les rôles.</span><span class="sxs-lookup"><span data-stu-id="a95fd-129">However, you can provide more granular authorization rules on a per-location basis as well as apply role based authorization checks.</span></span>

```xml
<location path="login.aspx">
  <system.web>
    <authorization>
      <allow users="*" />
    </authorization>
  </system.web>
</location>
```

<span data-ttu-id="a95fd-130">La configuration ci-dessus, lorsqu’elle est combinée avec la première, permet aux utilisateurs anonymes d’accéder à la page de connexion, en remplaçant la restriction à l’ensemble du site sur les utilisateurs non authentifiés.</span><span class="sxs-lookup"><span data-stu-id="a95fd-130">The above configuration, when combined with the first one, would allow anonymous users to access the login page, overriding the site-wide restriction on non-authenticated users.</span></span>

```xml
<location path="/admin">
  <system.web>
    <authorization>
      <allow roles="Administrators" />
      <deny users="*" />
    </authorization>
  </system.web>
</location>
```

<span data-ttu-id="a95fd-131">La configuration ci-dessus, lorsqu’elle est combinée avec les autres, restreint l’accès au `/admin` dossier et à toutes les ressources qu’il contient aux membres du rôle « Administrateurs ».</span><span class="sxs-lookup"><span data-stu-id="a95fd-131">The above configuration, when combined with the others, restricts access to the `/admin` folder and all resources within it to members of the "Administrators" role.</span></span> <span data-ttu-id="a95fd-132">Cela peut également être appliqué en plaçant un `web.config` fichier distinct au sein de la `/admin` racine du dossier.</span><span class="sxs-lookup"><span data-stu-id="a95fd-132">This could also be applied by placing a separate `web.config` file within the `/admin` folder root.</span></span>

### <a name="authorization-code-in-web-forms"></a><span data-ttu-id="a95fd-133">Code d’autorisation dans Web Forms</span><span class="sxs-lookup"><span data-stu-id="a95fd-133">Authorization code in Web Forms</span></span>

<span data-ttu-id="a95fd-134">Outre la configuration de l’accès à l’aide de `web.config` , vous pouvez également configurer par programme l’accès et le comportement dans votre application Web Forms.</span><span class="sxs-lookup"><span data-stu-id="a95fd-134">In addition to configuring access using `web.config`, you can also programmatically configure access and behavior in your Web Forms application.</span></span> <span data-ttu-id="a95fd-135">Par exemple, vous pouvez limiter la possibilité d’effectuer certaines opérations ou d’afficher certaines données en fonction du rôle de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a95fd-135">For instance, you can restrict the ability to perform certain operations or view certain data based on the user's role.</span></span>

<span data-ttu-id="a95fd-136">Ce code peut être utilisé à la fois dans la logique codebehind et dans la page elle-même :</span><span class="sxs-lookup"><span data-stu-id="a95fd-136">This code can be used both in codebehind logic as well as in the page itself:</span></span>

```html
<% if (HttpContext.Current.User.IsInRole("Administrators")) { %>
  <a href="/admin">Go To Admin</a>
<% } %>
```

<span data-ttu-id="a95fd-137">Outre la vérification de l’appartenance à un rôle d’utilisateur, vous pouvez également déterminer s’ils sont authentifiés (bien que cette opération soit souvent mieux effectuée à l’aide de la configuration basée sur l’emplacement décrite ci-dessus).</span><span class="sxs-lookup"><span data-stu-id="a95fd-137">In addition to checking user role membership, you can also determine if they are authenticated (though often this is better done using the location-based configuration covered above).</span></span> <span data-ttu-id="a95fd-138">Vous trouverez ci-dessous un exemple de cette approche.</span><span class="sxs-lookup"><span data-stu-id="a95fd-138">Below is an example of this approach.</span></span>

```csharp
protected void Page_Load(object sender, EventArgs e)
{
    if (!User.Identity.IsAuthenticated)
    {
        FormsAuthentication.RedirectToLoginPage();
    }
    if (!Roles.IsUserInRole(User.Identity.Name, "Administrators"))
    {
        MessageLabel.Text = "Only administrators can view this.";
        SecretPanel.Visible = false;
    }
}
```

<span data-ttu-id="a95fd-139">Dans le code ci-dessus, le contrôle d’accès en fonction du rôle (RBAC) est utilisé pour déterminer si certains éléments de la page, tels qu’un `SecretPanel` , sont visibles en fonction du rôle de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="a95fd-139">In the code above, role-based access control (RBAC) is used to determine whether certain elements of the page, such as a `SecretPanel`, are visible based on the current user's role.</span></span>

<span data-ttu-id="a95fd-140">En règle générale, les applications ASP.NET Web Forms configurent la sécurité dans le `web.config` fichier, puis ajoutent des vérifications supplémentaires si nécessaire dans les `.aspx` pages et leurs `.aspx.cs` fichiers codebehind associés.</span><span class="sxs-lookup"><span data-stu-id="a95fd-140">Typically, ASP.NET Web Forms applications configure security within the `web.config` file and then add additional checks where needed in `.aspx` pages and their related `.aspx.cs` codebehind files.</span></span> <span data-ttu-id="a95fd-141">La plupart des applications exploitent le fournisseur d’appartenances universel, souvent avec le fournisseur de rôles supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="a95fd-141">Most applications leverage the universal membership provider, frequently with the additional role provider.</span></span>

## <a name="aspnet-core-identity"></a><span data-ttu-id="a95fd-142">Identité ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a95fd-142">ASP.NET Core Identity</span></span>

<span data-ttu-id="a95fd-143">Bien qu’elle soit toujours associée à l’authentification et à l’autorisation, ASP.NET Core identité utilise un ensemble différent d’abstractions et d’hypothèses par rapport aux fournisseurs universels.</span><span class="sxs-lookup"><span data-stu-id="a95fd-143">Although still tasked with authentication and authorization, ASP.NET Core Identity uses a different set of abstractions and assumptions when compared to the universal providers.</span></span> <span data-ttu-id="a95fd-144">Par exemple, le nouveau modèle d’identité prend en charge l’authentification tierce, ce qui permet aux utilisateurs de s’authentifier à l’aide d’un compte de média social ou d’un autre fournisseur d’authentification approuvé.</span><span class="sxs-lookup"><span data-stu-id="a95fd-144">For example, the new Identity model supports third party authentication, allowing users to authenticate using a social media account or other trusted authentication provider.</span></span> <span data-ttu-id="a95fd-145">ASP.NET Core identité prend en charge l’interface utilisateur pour les pages couramment utilisées, telles que la connexion, la déconnexion et l’inscription.</span><span class="sxs-lookup"><span data-stu-id="a95fd-145">ASP.NET Core Identity supports UI for commonly needed pages like login, logout, and register.</span></span> <span data-ttu-id="a95fd-146">Il exploite EF Core pour son accès aux données, et utilise EF Core migrations pour générer le schéma nécessaire à la prise en charge de son modèle de données.</span><span class="sxs-lookup"><span data-stu-id="a95fd-146">It leverages EF Core for its data access, and uses EF Core migrations to generate the necessary schema required to supports its data model.</span></span> <span data-ttu-id="a95fd-147">Cette [Présentation de l’identité sur ASP.net Core](https://docs.microsoft.com/aspnet/core/security/authentication/identity) fournit une bonne vue d’ensemble de ce qui est inclus dans ASP.net Core identité et de la façon de commencer à l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="a95fd-147">This [introduction to Identity on ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/identity) provides a good overview of what is included with ASP.NET Core Identity and how to get started working with it.</span></span> <span data-ttu-id="a95fd-148">Si vous n’avez pas déjà configuré ASP.NET Core identité dans votre application et sa base de données, cela vous aidera à commencer.</span><span class="sxs-lookup"><span data-stu-id="a95fd-148">If you haven't already set up ASP.NET Core Identity in your application and its database, it will help you get started.</span></span>

### <a name="roles-claims-and-policies"></a><span data-ttu-id="a95fd-149">Rôles, revendications et stratégies</span><span class="sxs-lookup"><span data-stu-id="a95fd-149">Roles, claims, and policies</span></span>

<span data-ttu-id="a95fd-150">Les fournisseurs universels et l’identité ASP.NET Core prennent en charge le concept de rôles.</span><span class="sxs-lookup"><span data-stu-id="a95fd-150">Both the universal providers and ASP.NET Core Identity support the concept of roles.</span></span> <span data-ttu-id="a95fd-151">Vous pouvez créer des rôles pour les utilisateurs et affecter des utilisateurs à des rôles.</span><span class="sxs-lookup"><span data-stu-id="a95fd-151">You can create roles for users and assign users to roles.</span></span> <span data-ttu-id="a95fd-152">Les utilisateurs peuvent appartenir à n’importe quel nombre de rôles, et vous pouvez vérifier l’appartenance au rôle dans le cadre de votre implémentation d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="a95fd-152">Users can belong to any number of roles, and you can verify role membership as part of your authorization implementation.</span></span>

<span data-ttu-id="a95fd-153">En plus des rôles, ASP.NET Core identité prend en charge les concepts des revendications et des stratégies.</span><span class="sxs-lookup"><span data-stu-id="a95fd-153">In addition to roles, ASP.NET Core identity supports the concepts of claims and policies.</span></span> <span data-ttu-id="a95fd-154">Alors qu’un rôle doit correspondre spécifiquement à un ensemble de ressources, un utilisateur de ce rôle doit pouvoir y accéder, une revendication fait simplement partie de l’identité d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a95fd-154">While a role should specifically correspond to a set of resources a user in that role should be able to access, a claim is simply part of a user's identity.</span></span> <span data-ttu-id="a95fd-155">Une revendication est une paire nom/valeur qui représente l’objet, pas ce que le sujet peut faire.</span><span class="sxs-lookup"><span data-stu-id="a95fd-155">A claim is a name value pair that represents what the subject is, not what the subject can do.</span></span>

<span data-ttu-id="a95fd-156">Il est possible d’inspecter directement les revendications d’un utilisateur et de déterminer si un utilisateur doit se voir accorder l’accès à une ressource.</span><span class="sxs-lookup"><span data-stu-id="a95fd-156">It is possible to directly inspect a user's claims and determine based on these whether a user should be given access to a resource.</span></span> <span data-ttu-id="a95fd-157">Toutefois, ces vérifications sont souvent répétitives et éparpillées dans le système.</span><span class="sxs-lookup"><span data-stu-id="a95fd-157">However, such checks are often repetitive and scattered throughout the system.</span></span> <span data-ttu-id="a95fd-158">Une meilleure approche consiste à définir une *stratégie*.</span><span class="sxs-lookup"><span data-stu-id="a95fd-158">A better approach is to define a *policy*.</span></span>

<span data-ttu-id="a95fd-159">Une stratégie d’autorisation se compose d’une ou de plusieurs exigences.</span><span class="sxs-lookup"><span data-stu-id="a95fd-159">An authorization policy consists of one or more requirements.</span></span> <span data-ttu-id="a95fd-160">Les stratégies sont inscrites dans le cadre de la configuration du service d’autorisation dans la `ConfigureServices` méthode de `Startup.cs` .</span><span class="sxs-lookup"><span data-stu-id="a95fd-160">Policies are registered as part of the authorization service configuration in the `ConfigureServices` method of `Startup.cs`.</span></span> <span data-ttu-id="a95fd-161">Par exemple, l’extrait de code suivant configure une stratégie appelée « CanadiansOnly » qui exige que l’utilisateur dispose de la revendication Country avec la valeur « Canada ».</span><span class="sxs-lookup"><span data-stu-id="a95fd-161">For example, the following code snippet configures a policy called "CanadiansOnly" which has the requirement that the user have the Country claim with the value of "Canada".</span></span>

```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("CanadiansOnly", policy => policy.RequireClaim(ClaimTypes.Country, "Canada"));
});
```

<span data-ttu-id="a95fd-162">Vous pouvez [en savoir plus sur la façon de créer des stratégies personnalisées dans la documentation](https://docs.microsoft.com/aspnet/core/security/authorization/policies).</span><span class="sxs-lookup"><span data-stu-id="a95fd-162">You can [learn more about how to create custom policies in the documentation](https://docs.microsoft.com/aspnet/core/security/authorization/policies).</span></span>

<span data-ttu-id="a95fd-163">Que vous utilisiez des stratégies ou des rôles, vous pouvez spécifier qu’une page particulière de votre Blazor application nécessite ce rôle ou cette stratégie avec l' `[Authorize]` attribut, appliquée à la `@attribute` directive.</span><span class="sxs-lookup"><span data-stu-id="a95fd-163">Whether you're using policies or roles, you can specify that a particular page in your Blazor application require that role or policy with the `[Authorize]` attribute, applied with the `@attribute` directive.</span></span>

<span data-ttu-id="a95fd-164">Exigence d’un rôle :</span><span class="sxs-lookup"><span data-stu-id="a95fd-164">Requiring a role:</span></span>

```csharp
@attribute [Authorize(Roles ="administrators")]
```

<span data-ttu-id="a95fd-165">Exiger la satisfaction d’une stratégie :</span><span class="sxs-lookup"><span data-stu-id="a95fd-165">Requiring a policy be satisfied:</span></span>

```csharp
@attribute [Authorize(Policy ="CanadiansOnly")]
```

<span data-ttu-id="a95fd-166">Si vous avez besoin d’accéder à l’état d’authentification, aux rôles ou aux revendications d’un utilisateur dans votre code, il existe deux méthodes principales pour y parvenir.</span><span class="sxs-lookup"><span data-stu-id="a95fd-166">If you need access to a user's authentication state, roles, or claims in your code, there are two primary ways to achieve this.</span></span> <span data-ttu-id="a95fd-167">La première consiste à recevoir l’état d’authentification en tant que paramètre en cascade.</span><span class="sxs-lookup"><span data-stu-id="a95fd-167">The first is to receive the authentication state as a cascading parameter.</span></span> <span data-ttu-id="a95fd-168">La seconde consiste à accéder à l’État à l’aide d’un injecté `AuthenticationStateProvider` .</span><span class="sxs-lookup"><span data-stu-id="a95fd-168">The second is to access the state using an injected `AuthenticationStateProvider`.</span></span> <span data-ttu-id="a95fd-169">Les détails de chacune de ces approches sont décrits dans la [ Blazor documentation relative](https://docs.microsoft.com/aspnet/core/blazor/security/)à la sécurité.</span><span class="sxs-lookup"><span data-stu-id="a95fd-169">The details of each of these approaches are described in the [Blazor Security documentation](https://docs.microsoft.com/aspnet/core/blazor/security/).</span></span>

<span data-ttu-id="a95fd-170">Le code suivant montre comment recevoir le `AuthenticationState` en tant que paramètre en cascade :</span><span class="sxs-lookup"><span data-stu-id="a95fd-170">The following code shows how to receive the `AuthenticationState` as a cascading parameter:</span></span>

```csharp
[CascadingParameter]
private Task<AuthenticationState> authenticationStateTask { get; set; }
```

<span data-ttu-id="a95fd-171">Une fois ce paramètre en place, vous pouvez faire en sorte que l’utilisateur utilise ce code :</span><span class="sxs-lookup"><span data-stu-id="a95fd-171">With this parameter in place, you can get the user using this code:</span></span>

```csharp
var authState = await authenticationStateTask;
var user = authState.User;
```

<span data-ttu-id="a95fd-172">Le code suivant montre comment injecter les `AuthenticationStateProvider` éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="a95fd-172">The following code shows how to inject the `AuthenticationStateProvider`:</span></span>

```csharp
@using Microsoft.AspNetCore.Components.Authorization
@inject AuthenticationStateProvider AuthenticationStateProvider
```

<span data-ttu-id="a95fd-173">Une fois le fournisseur en place, vous pouvez accéder à l’utilisateur avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="a95fd-173">With the provider in place, you can gain access to the user with the following code:</span></span>

```csharp
AuthenticationState authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
ClaimsPrincipal user = authState.User;

if (user.Identity.IsAuthenticated)
{
  // work with user.Claims and/or user.Roles
}
```

<span data-ttu-id="a95fd-174">**Remarque :** Le `AuthorizeView` composant, abordé plus loin dans ce chapitre, offre un moyen déclaratif de contrôler ce qu’un utilisateur voit sur une page ou un composant.</span><span class="sxs-lookup"><span data-stu-id="a95fd-174">**Note:** The `AuthorizeView` component, covered later in this chapter, provides a declarative way to control what a user sees on a page or component.</span></span>

<span data-ttu-id="a95fd-175">Pour travailler avec les utilisateurs et les revendications (dans les Blazor applications serveur), vous devrez peut-être également injecter une `UserManager<T>` (utiliser `IdentityUser` pour la valeur par défaut) que vous pouvez utiliser pour énumérer et modifier des revendications pour un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a95fd-175">To work with users and claims (in Blazor Server applications) you may also need to inject a `UserManager<T>` (use `IdentityUser` for default) which you can use to enumerate and modify claims for a user.</span></span> <span data-ttu-id="a95fd-176">Injectez d’abord le type et affectez-le à une propriété :</span><span class="sxs-lookup"><span data-stu-id="a95fd-176">First inject the type and assign it to a property:</span></span>

```csharp
@inject UserManager<IdentityUser> MyUserManager
```

<span data-ttu-id="a95fd-177">Utilisez-le ensuite pour travailler avec les revendications de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a95fd-177">Then use it to work with the user's claims.</span></span> <span data-ttu-id="a95fd-178">L’exemple suivant montre comment ajouter une revendication à un utilisateur et la rendre persistante :</span><span class="sxs-lookup"><span data-stu-id="a95fd-178">The following sample shows how to add and persist a claim on a user:</span></span>

```csharp
private async Task AddCountryClaim()
{
    var authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
    var user = authState.User;
    var identityUser = await MyUserManager.FindByNameAsync(user.Identity.Name);

    if (!user.HasClaim(c => c.Type == ClaimTypes.Country))
    {
        // stores the claim in the cookie
        ClaimsIdentity id = new ClaimsIdentity();
        id.AddClaim(new Claim(ClaimTypes.Country, "Canada"));
        user.AddIdentity(id);

        // save the claim in the database
        await MyUserManager.AddClaimAsync(identityUser, new Claim(ClaimTypes.Country, "Canada"));
    }
}
```

<span data-ttu-id="a95fd-179">Si vous devez utiliser des rôles, suivez la même approche.</span><span class="sxs-lookup"><span data-stu-id="a95fd-179">If you need to work with roles, follow the same approach.</span></span> <span data-ttu-id="a95fd-180">Vous devrez peut-être injecter un `RoleManager<T>` (utilisez `IdentityRole` pour le type par défaut) pour répertorier et gérer les rôles eux-mêmes.</span><span class="sxs-lookup"><span data-stu-id="a95fd-180">You may need to inject a `RoleManager<T>` (use `IdentityRole` for default type) to list and manage the roles themselves.</span></span>

<span data-ttu-id="a95fd-181">**Remarque :** Dans Blazor les projets Webassembly, vous devrez fournir des API serveur pour effectuer ces opérations (au lieu d’utiliser `UserManager<T>` ou `RoleManager<T>` directement).</span><span class="sxs-lookup"><span data-stu-id="a95fd-181">**Note:** In Blazor WebAssembly projects, you will need to provide server APIs to perform these operations (instead of using `UserManager<T>` or `RoleManager<T>` directly).</span></span> <span data-ttu-id="a95fd-182">Une Blazor application cliente Webassembly gère les revendications et/ou les rôles en appelant de manière sécurisée les points de terminaison d’API exposés à cet effet.</span><span class="sxs-lookup"><span data-stu-id="a95fd-182">A Blazor WebAssembly client application would manage claims and/or roles by securely calling API endpoints exposed for this purpose.</span></span>

### <a name="migration-guide"></a><span data-ttu-id="a95fd-183">Guide de migration</span><span class="sxs-lookup"><span data-stu-id="a95fd-183">Migration guide</span></span>

<span data-ttu-id="a95fd-184">La migration de ASP.NET Web Forms et des fournisseurs universels vers ASP.NET Core identité nécessite plusieurs étapes :</span><span class="sxs-lookup"><span data-stu-id="a95fd-184">Migrating from ASP.NET Web Forms and universal providers to ASP.NET Core Identity requires several steps:</span></span>

1. <span data-ttu-id="a95fd-185">Créer ASP.NET Core schéma de base de données d’identité dans la base de données de destination</span><span class="sxs-lookup"><span data-stu-id="a95fd-185">Create ASP.NET Core Identity database schema in destination database</span></span>
2. <span data-ttu-id="a95fd-186">Migrer des données à partir du schéma de fournisseur universel vers ASP.NET Core schéma d’identité</span><span class="sxs-lookup"><span data-stu-id="a95fd-186">Migrate data from universal provider schema to ASP.NET Core Identity schema</span></span>
3. <span data-ttu-id="a95fd-187">Migrez la configuration de web.config à des intergiciels et des services, généralement dans `Startup.cs`</span><span class="sxs-lookup"><span data-stu-id="a95fd-187">Migrate configuration from web.config to middleware and services, typically in `Startup.cs`</span></span>
4. <span data-ttu-id="a95fd-188">Mettez à jour des pages individuelles à l’aide de contrôles et de conditionnels pour utiliser des balises tag et de nouvelles API d’identité.</span><span class="sxs-lookup"><span data-stu-id="a95fd-188">Update individual pages using controls and conditionals to use tag helpers and new identity APIs.</span></span>

<span data-ttu-id="a95fd-189">Chacune de ces étapes est décrite en détail dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="a95fd-189">Each of these steps is described in detail in the following sections.</span></span>

### <a name="creating-the-aspnet-core-identity-schema"></a><span data-ttu-id="a95fd-190">Création du schéma d’identité ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a95fd-190">Creating the ASP.NET Core Identity schema</span></span>

<span data-ttu-id="a95fd-191">Il existe plusieurs façons de créer la structure de table nécessaire utilisée pour ASP.NET Core identité.</span><span class="sxs-lookup"><span data-stu-id="a95fd-191">There are several ways to create the necessary table structure used for ASP.NET Core Identity.</span></span> <span data-ttu-id="a95fd-192">La méthode la plus simple consiste à créer une nouvelle ASP.NET Core application Web.</span><span class="sxs-lookup"><span data-stu-id="a95fd-192">The simplest is to create a new ASP.NET Core Web application.</span></span> <span data-ttu-id="a95fd-193">Choisissez application Web, puis modifier l’authentification pour utiliser des comptes d’utilisateur individuels.</span><span class="sxs-lookup"><span data-stu-id="a95fd-193">Choose Web Application and then change Authentication to use Individual User Accounts.</span></span>

![nouveau projet avec des comptes d’utilisateur individuels](./media/security/individual-user-accounts.png)

<span data-ttu-id="a95fd-195">À partir de la ligne de commande, vous pouvez effectuer la même opération en exécutant `dotnet new webapp -au Individual` .</span><span class="sxs-lookup"><span data-stu-id="a95fd-195">From the command line, you can do the same thing by running `dotnet new webapp -au Individual`.</span></span> <span data-ttu-id="a95fd-196">Une fois l’application créée, exécutez-la et inscrivez-vous sur le site.</span><span class="sxs-lookup"><span data-stu-id="a95fd-196">Once the app has been created, run it and register on the site.</span></span> <span data-ttu-id="a95fd-197">Vous devez déclencher une page telle que celle illustrée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="a95fd-197">You should trigger a page like the one shown below:</span></span>

![page appliquer les migrations](./media/security/apply-migrations-page.png)

<span data-ttu-id="a95fd-199">Cliquez sur le bouton « appliquer des migrations » pour créer les tables de base de données nécessaires.</span><span class="sxs-lookup"><span data-stu-id="a95fd-199">Click on the "Apply Migrations" button and the necessary database tables should be created for you.</span></span> <span data-ttu-id="a95fd-200">En outre, les fichiers de migration doivent apparaître dans votre projet, comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="a95fd-200">In addition, the migration files should appear in your project, as shown:</span></span>

![fichiers de migration](./media/security/migration-files.png)

<span data-ttu-id="a95fd-202">Vous pouvez exécuter la migration vous-même, sans exécuter l’application Web, à l’aide de cet outil de ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="a95fd-202">You can run the migration yourself, without running the web application, using this command line tool:</span></span>

```powershell
dotnet ef database update
```

<span data-ttu-id="a95fd-203">Si vous préférez exécuter un script pour appliquer le nouveau schéma à une base de données existante, vous pouvez créer un script pour ces migrations à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a95fd-203">If you would rather run a script to apply the new schema to an existing database, you can script these migrations from the command line.</span></span> <span data-ttu-id="a95fd-204">Exécutez cette commande pour générer le script :</span><span class="sxs-lookup"><span data-stu-id="a95fd-204">Run this command to generate the script:</span></span>

```powershell
dotnet ef migrations script -o auth.sql
```

<span data-ttu-id="a95fd-205">Cela génère un script SQL dans le fichier de sortie `auth.sql` , qui peut ensuite être exécuté sur n’importe quelle base de données de votre choix.</span><span class="sxs-lookup"><span data-stu-id="a95fd-205">This will produce a SQL script in the output file `auth.sql` which can then be run against whatever database you like.</span></span> <span data-ttu-id="a95fd-206">Si vous avez des difficultés à exécuter des `dotnet ef` commandes, assurez [-vous que les outils de EF Core sont installés sur votre système](https://docs.microsoft.com/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="a95fd-206">If you have any trouble running `dotnet ef` commands, [make sure you have the EF Core tools installed on your system](https://docs.microsoft.com/ef/core/miscellaneous/cli/dotnet).</span></span>

<span data-ttu-id="a95fd-207">Dans le cas où vous avez des colonnes supplémentaires sur vos tables sources, vous devez identifier le meilleur emplacement pour ces colonnes dans le nouveau schéma.</span><span class="sxs-lookup"><span data-stu-id="a95fd-207">In the event you have additional columns on your source tables, you will need to identify the best location for these columns in the new schema.</span></span> <span data-ttu-id="a95fd-208">En règle générale, les colonnes trouvées dans la `aspnet_Membership` table doivent être mappées à la `AspNetUsers` table.</span><span class="sxs-lookup"><span data-stu-id="a95fd-208">Generally, columns found on the `aspnet_Membership` table should be mapped to the `AspNetUsers` table.</span></span> <span data-ttu-id="a95fd-209">Les colonnes sur `aspnet_Roles` doivent être mappées à `AspNetRoles` .</span><span class="sxs-lookup"><span data-stu-id="a95fd-209">Columns on `aspnet_Roles` should be mapped to `AspNetRoles`.</span></span> <span data-ttu-id="a95fd-210">Toutes les colonnes supplémentaires de la `aspnet_UsersInRoles` table sont ajoutées à la `AspNetUserRoles` table.</span><span class="sxs-lookup"><span data-stu-id="a95fd-210">Any additional columns on the `aspnet_UsersInRoles` table would be added to the `AspNetUserRoles` table.</span></span>

<span data-ttu-id="a95fd-211">Il est également intéressant de placer des colonnes supplémentaires sur des tables distinctes, afin que les futures migrations n’aient pas besoin de prendre en compte ces personnalisations du schéma d’identité par défaut.</span><span class="sxs-lookup"><span data-stu-id="a95fd-211">It's also worth considering putting any additional columns on separate tables, so that future migrations won't need to take into account such customizations of the default identity schema.</span></span>

### <a name="migrating-data-from-universal-providers-to-aspnet-core-identity"></a><span data-ttu-id="a95fd-212">Migration des données des fournisseurs universels vers ASP.NET Core identité</span><span class="sxs-lookup"><span data-stu-id="a95fd-212">Migrating data from universal providers to ASP.NET Core Identity</span></span>

<span data-ttu-id="a95fd-213">Une fois le schéma de la table de destination en place, l’étape suivante consiste à migrer vos enregistrements d’utilisateur et de rôle vers le nouveau schéma.</span><span class="sxs-lookup"><span data-stu-id="a95fd-213">Once you have the destination table schema in place, the next step is to migrate your user and role records to the new schema.</span></span> <span data-ttu-id="a95fd-214">La liste complète des différences de schéma, y compris les colonnes qui mappent aux nouvelles colonnes, est disponible [ici](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span><span class="sxs-lookup"><span data-stu-id="a95fd-214">A complete list of the schema differences, including which columns map to which new columns, can be found [here](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span></span>

<span data-ttu-id="a95fd-215">Pour migrer vos utilisateurs de l’appartenance vers les nouvelles tables d’identité, vous devez [suivre les étapes décrites dans la documentation](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span><span class="sxs-lookup"><span data-stu-id="a95fd-215">To migrate your users from membership to the new identity tables, you should [follow the steps described in the documentation](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span></span> <span data-ttu-id="a95fd-216">Après avoir effectué ces étapes et le script fourni, vos utilisateurs devront modifier leur mot de passe lors de leur prochaine connexion.</span><span class="sxs-lookup"><span data-stu-id="a95fd-216">After following these steps and the script provided, your users will need to change their password the next time they log in.</span></span>

<span data-ttu-id="a95fd-217">Il est possible de migrer des mots de passe utilisateur, mais le processus est bien plus complexe.</span><span class="sxs-lookup"><span data-stu-id="a95fd-217">It is possible to migrate user passwords but the process is much more involved.</span></span> <span data-ttu-id="a95fd-218">Demander aux utilisateurs de mettre à jour leur mot de passe dans le cadre du processus de migration et les encourager à utiliser de nouveaux mots de passe uniques, est susceptible d’améliorer la sécurité globale de l’application.</span><span class="sxs-lookup"><span data-stu-id="a95fd-218">Requiring users to update their passwords as part of the migration process, and encouraging them to use new, unique passwords, is likely to enhance the overall security of the application.</span></span>

### <a name="migrating-security-settings-from-webconfig-to-startupcs"></a><span data-ttu-id="a95fd-219">Migration des paramètres de sécurité de web.config vers Startup.cs</span><span class="sxs-lookup"><span data-stu-id="a95fd-219">Migrating security settings from web.config to Startup.cs</span></span>

<span data-ttu-id="a95fd-220">Comme indiqué ci-dessus, les fournisseurs de rôles et d’appartenance ASP.NET sont configurés dans le fichier web.config de l’application.</span><span class="sxs-lookup"><span data-stu-id="a95fd-220">As noted above, ASP.NET membership and role providers are configured in the application's web.config file.</span></span> <span data-ttu-id="a95fd-221">Étant donné que les applications ASP.NET Core ne sont pas liées à IIS et utilisent un système distinct pour la configuration, ces paramètres doivent être configurés ailleurs.</span><span class="sxs-lookup"><span data-stu-id="a95fd-221">Since ASP.NET Core apps are not tied to IIS and use a separate system for configuration, these settings must be configured elsewhere.</span></span> <span data-ttu-id="a95fd-222">Pour l’essentiel, ASP.NET Core identité est configurée dans le `Startup.cs` fichier.</span><span class="sxs-lookup"><span data-stu-id="a95fd-222">For the most part, ASP.NET Core Identity is configured in the `Startup.cs` file.</span></span> <span data-ttu-id="a95fd-223">Ouvrez le projet Web créé précédemment (pour générer le schéma de la table d’identité) et examinez son `Startup.cs` fichier.</span><span class="sxs-lookup"><span data-stu-id="a95fd-223">Open the web project that was created earlier (to generate the identity table schema) and review its `Startup.cs` file.</span></span>

<span data-ttu-id="a95fd-224">La méthode ConfigureServices par défaut ajoute la prise en charge de EF Core et de l’identité :</span><span class="sxs-lookup"><span data-stu-id="a95fd-224">The default ConfigureServices method adds support for EF Core and Identity:</span></span>

```csharp
// This method gets called by the runtime. Use this method to add services to the container.
public void ConfigureServices(IServiceCollection services)
{
    services.AddDbContext<ApplicationDbContext>(options =>
        options.UseSqlServer(
            Configuration.GetConnectionString("DefaultConnection")));

    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddRazorPages();
}
```

<span data-ttu-id="a95fd-225">La `AddDefaultIdentity` méthode d’extension est utilisée pour configurer l’identité afin d’utiliser la valeur par défaut `ApplicationDbContext` et le type de l’infrastructure `IdentityUser` .</span><span class="sxs-lookup"><span data-stu-id="a95fd-225">The `AddDefaultIdentity` extension method is used to configure Identity to use the default `ApplicationDbContext` and the framework's `IdentityUser` type.</span></span> <span data-ttu-id="a95fd-226">Si vous utilisez un personnalisé `IdentityUser` , veillez à spécifier son type ici.</span><span class="sxs-lookup"><span data-stu-id="a95fd-226">If you're using a custom `IdentityUser`, be sure to specify its type here.</span></span> <span data-ttu-id="a95fd-227">Si ces méthodes d’extension ne fonctionnent pas dans votre application, vérifiez que vous disposez des instructions using appropriées et que vous disposez des références de package NuGet nécessaires.</span><span class="sxs-lookup"><span data-stu-id="a95fd-227">If these extension methods aren't working in your application, check that you have the appropriate using statements and that you have the necessary NuGet package references.</span></span> <span data-ttu-id="a95fd-228">Par exemple, votre projet doit avoir une version des `Microsoft.AspNetCore.Identity.EntityFrameworkCore` packages et `Microsoft.AspNetCore.Identity.UI` référencée.</span><span class="sxs-lookup"><span data-stu-id="a95fd-228">For example, your project should have some version of the `Microsoft.AspNetCore.Identity.EntityFrameworkCore` and `Microsoft.AspNetCore.Identity.UI` packages referenced.</span></span>

<span data-ttu-id="a95fd-229">Dans, `Startup.cs` vous devez également voir le middleware nécessaire configuré pour le site.</span><span class="sxs-lookup"><span data-stu-id="a95fd-229">Also in `Startup.cs` you should see the necessary middleware configured for the site.</span></span> <span data-ttu-id="a95fd-230">Plus précisément, `UseAuthentication` et `UseAuthorization` doivent être configurés et se trouver à l’emplacement approprié.</span><span class="sxs-lookup"><span data-stu-id="a95fd-230">Specifically, `UseAuthentication` and `UseAuthorization` should be set up, and in the proper location.</span></span>

```csharp

// This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
        app.UseDatabaseErrorPage();
    }
    else
    {
        app.UseExceptionHandler("/Error");
        // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
        app.UseHsts();
    }

    app.UseHttpsRedirection();
    app.UseStaticFiles();

    app.UseRouting();

    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapRazorPages();
    });
}
```

<span data-ttu-id="a95fd-231">ASP.NET Identity ne configure pas l’accès anonyme ou basé sur les rôles à des emplacements à partir de `Startup.cs` .</span><span class="sxs-lookup"><span data-stu-id="a95fd-231">ASP.NET Identity does not configure anonymous or role-based access to locations from `Startup.cs`.</span></span> <span data-ttu-id="a95fd-232">Vous devez migrer toutes les données de configuration d’autorisation spécifiques à l’emplacement vers des filtres dans ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a95fd-232">You will need to migrate any location-specific authorization configuration data to filters in ASP.NET Core.</span></span> <span data-ttu-id="a95fd-233">Prenez note des dossiers et des pages qui nécessitent ces mises à jour.</span><span class="sxs-lookup"><span data-stu-id="a95fd-233">Make note of which folders and pages will require such updates.</span></span> <span data-ttu-id="a95fd-234">Vous allez apporter ces modifications dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="a95fd-234">You will make these changes in the next section.</span></span>

### <a name="updating-individual-pages-to-use-aspnet-core-identity-abstractions"></a><span data-ttu-id="a95fd-235">Mise à jour de pages individuelles à utiliser ASP.NET Core abstractions d’identité</span><span class="sxs-lookup"><span data-stu-id="a95fd-235">Updating individual pages to use ASP.NET Core Identity abstractions</span></span>

<span data-ttu-id="a95fd-236">Dans votre application ASP.NET Web Forms, si vous aviez web.config paramètres pour refuser l’accès à des utilisateurs anonymes à certaines pages ou dossiers, vous devez les migrer en ajoutant simplement l' `[Authorize]` attribut à ces pages :</span><span class="sxs-lookup"><span data-stu-id="a95fd-236">In your ASP.NET Web Forms application, if you had web.config settings to deny access to certain pages or folders to anonymous users, you would migrate these by simply adding the `[Authorize]` attribute to such pages:</span></span>

```razor
@attribute [Authorize]
```

<span data-ttu-id="a95fd-237">Si vous avez encore refusé l’accès, à l’exception des utilisateurs qui appartiennent à un certain rôle, vous pouvez migrer de la même façon en ajoutant un attribut spécifiant un rôle :</span><span class="sxs-lookup"><span data-stu-id="a95fd-237">If you further had denied access except to those users belonging to a certain role, you would likewise migrate this by adding an attribute specifying a role:</span></span>

```razor
@attribute [Authorize(Roles ="administrators")]
```

<span data-ttu-id="a95fd-238">Notez que l' `[Authorize]` attribut ne fonctionne que sur `@page` les composants qui sont atteints via le Blazor routeur.</span><span class="sxs-lookup"><span data-stu-id="a95fd-238">Note that the `[Authorize]` attribute only works on `@page` components that are reached via the Blazor Router.</span></span> <span data-ttu-id="a95fd-239">L’attribut ne fonctionne pas avec les composants enfants, qui doivent utiliser à la place `AuthorizeView` .</span><span class="sxs-lookup"><span data-stu-id="a95fd-239">The attribute does not work with child components, which should instead use `AuthorizeView`.</span></span>

<span data-ttu-id="a95fd-240">Si vous avez une logique dans le balisage de la page pour déterminer s’il faut afficher du code pour un utilisateur donné, vous pouvez remplacer ceci par le `AuthorizeView` composant.</span><span class="sxs-lookup"><span data-stu-id="a95fd-240">If you have logic within page markup for determining whether to display some code to a certain user, you can replace this with the `AuthorizeView` component.</span></span> <span data-ttu-id="a95fd-241">Le [composant AuthorizeView](https://docs.microsoft.com/aspnet/core/blazor/security#authorizeview-component) affiche l’interface utilisateur de manière sélective, selon que l’utilisateur est autorisé ou non à le voir.</span><span class="sxs-lookup"><span data-stu-id="a95fd-241">The [AuthorizeView component](https://docs.microsoft.com/aspnet/core/blazor/security#authorizeview-component) selectively displays UI depending on whether the user is authorized to see it.</span></span> <span data-ttu-id="a95fd-242">Il expose également une `context` variable qui peut être utilisée pour accéder aux informations utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a95fd-242">It also exposes a `context` variable that can be used to access user information.</span></span>

```razor
<AuthorizeView>
    <Authorized>
        <h1>Hello, @context.User.Identity.Name!</h1>
        <p>You can only see this content if you are authenticated.</p>
    </Authorized>
    <NotAuthorized>
        <h1>Authentication Failure!</h1>
        <p>You are not signed in.</p>
    </NotAuthorized>
</AuthorizeView>
```

<span data-ttu-id="a95fd-243">Vous pouvez accéder à l’état d’authentification dans la logique procédurale en accédant à l’utilisateur à partir d’un `Task<AuthenticationState` configuré avec l' `[CascadingParameter]` attribut.</span><span class="sxs-lookup"><span data-stu-id="a95fd-243">You can access authentication state within procedural logic by accessing the user from a `Task<AuthenticationState` configured with the `[CascadingParameter]` attribute.</span></span> <span data-ttu-id="a95fd-244">Cela vous permet d’accéder à l’utilisateur, ce qui vous permet de déterminer s’il est authentifié et s’il appartient à un rôle particulier.</span><span class="sxs-lookup"><span data-stu-id="a95fd-244">This will get you access to the user, which can let you determine if they are authenticated and if they belong to a particular role.</span></span> <span data-ttu-id="a95fd-245">Si vous devez évaluer une stratégie de façon procédurale, vous pouvez injecter une instance du `IAuthorizationService` et appelle la `AuthorizeAsync` méthode sur celle-ci.</span><span class="sxs-lookup"><span data-stu-id="a95fd-245">If you need to evaluate a policy procedurally, you can inject an instance of the `IAuthorizationService` and calls the `AuthorizeAsync` method on it.</span></span> <span data-ttu-id="a95fd-246">L’exemple de code suivant montre comment obtenir des informations utilisateur et autoriser un utilisateur autorisé à effectuer une tâche limitée par la `content-editor` stratégie.</span><span class="sxs-lookup"><span data-stu-id="a95fd-246">The following sample code demonstrates how to get user information and allow an authorized user to perform a task restricted by the `content-editor` policy.</span></span>

```razor
@using Microsoft.AspNetCore.Authorization
@inject IAuthorizationService AuthorizationService

<button @onclick="@DoSomething">Do something important</button>

@code {
    [CascadingParameter]
    private Task<AuthenticationState> authenticationStateTask { get; set; }

    private async Task DoSomething()
    {
        var user = (await authenticationStateTask).User;

        if (user.Identity.IsAuthenticated)
        {
            // Perform an action only available to authenticated (signed-in) users.
        }

        if (user.IsInRole("admin"))
        {
            // Perform an action only available to users in the 'admin' role.
        }

        if ((await AuthorizationService.AuthorizeAsync(user, "content-editor"))
            .Succeeded)
        {
            // Perform an action only available to users satisfying the
            // 'content-editor' policy.
        }
    }
}
```

<span data-ttu-id="a95fd-247">Le `AuthenticationState` doit d’abord être configuré en tant que valeur en cascade pour pouvoir être lié à un paramètre en cascade comme celui-ci.</span><span class="sxs-lookup"><span data-stu-id="a95fd-247">The `AuthenticationState` does first need to be setup as a cascading value before it can be bound to a cascading parameter like this.</span></span> <span data-ttu-id="a95fd-248">Cela s’effectue généralement à l’aide du `CascadingAuthenticationState` composant.</span><span class="sxs-lookup"><span data-stu-id="a95fd-248">That's typically done using the `CascadingAuthenticationState` component.</span></span> <span data-ttu-id="a95fd-249">Cela s’effectue généralement dans `App.razor` :</span><span class="sxs-lookup"><span data-stu-id="a95fd-249">This is typically done in `App.razor`:</span></span>

```razor
<CascadingAuthenticationState>
    <Router AppAssembly="@typeof(Program).Assembly">
        <Found Context="routeData">
            <AuthorizeRouteView RouteData="@routeData"
                DefaultLayout="@typeof(MainLayout)" />
        </Found>
        <NotFound>
            <LayoutView Layout="@typeof(MainLayout)">
                <p>Sorry, there's nothing at this address.</p>
            </LayoutView>
        </NotFound>
    </Router>
</CascadingAuthenticationState>
```

## <a name="summary"></a><span data-ttu-id="a95fd-250">Résumé</span><span class="sxs-lookup"><span data-stu-id="a95fd-250">Summary</span></span>

<span data-ttu-id="a95fd-251">Blazor utilise le même modèle de sécurité que ASP.NET Core, qui est ASP.NET Core identité.</span><span class="sxs-lookup"><span data-stu-id="a95fd-251">Blazor uses the same security model as ASP.NET Core, which is ASP.NET Core Identity.</span></span> <span data-ttu-id="a95fd-252">La migration des fournisseurs universels vers ASP.NET Core identité est relativement simple, en supposant que la personnalisation n’a pas été appliquée au schéma de données d’origine.</span><span class="sxs-lookup"><span data-stu-id="a95fd-252">Migrating from universal providers to ASP.NET Core Identity is relatively straightforward, assuming not too much customization was applied to the original data schema.</span></span> <span data-ttu-id="a95fd-253">Une fois les données migrées, l’utilisation de l’authentification et de l’autorisation dans les Blazor applications est bien documentée, avec une prise en charge configurable et par programmation pour la plupart des exigences de sécurité.</span><span class="sxs-lookup"><span data-stu-id="a95fd-253">Once the data has been migrated, working with authentication and authorization in Blazor apps is well-documented, with configurable as well as programmatic support for most security requirements.</span></span>

## <a name="references"></a><span data-ttu-id="a95fd-254">References</span><span class="sxs-lookup"><span data-stu-id="a95fd-254">References</span></span>

- [<span data-ttu-id="a95fd-255">Présentation de l’identité sur ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a95fd-255">Introduction to Identity on ASP.NET Core</span></span>](https://docs.microsoft.com/aspnet/core/security/authentication/identity)
- [<span data-ttu-id="a95fd-256">Migrer de l’authentification d’appartenance ASP.NET vers l’identité ASP.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="a95fd-256">Migrate from ASP.NET Membership authentication to ASP.NET Core 2.0 Identity</span></span>](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity)
- [<span data-ttu-id="a95fd-257">Migrer l’authentification et l’identité vers ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a95fd-257">Migrate Authentication and Identity to ASP.NET Core</span></span>](https://docs.microsoft.com/aspnet/core/migration/identity)
- [<span data-ttu-id="a95fd-258">BlazorAuthentification et autorisation ASP.net Core</span><span class="sxs-lookup"><span data-stu-id="a95fd-258">ASP.NET Core Blazor authentication and authorization</span></span>](https://docs.microsoft.com/aspnet/core/blazor/security/)

>[!div class="step-by-step"]
><span data-ttu-id="a95fd-259">[Précédent](config.md) 
> [Suivant](migration.md)</span><span class="sxs-lookup"><span data-stu-id="a95fd-259">[Previous](config.md)
[Next](migration.md)</span></span>
