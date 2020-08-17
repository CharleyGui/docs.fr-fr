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
# <a name="security-authentication-and-authorization-in-aspnet-web-forms-and-no-locblazor"></a>Sécurité : authentification et autorisation dans ASP.NET Web Forms et Blazor

La migration à partir d’une application Web Forms ASP.NET vers Blazor va certainement nécessiter la mise à jour de la manière dont l’authentification et l’autorisation sont effectuées, en supposant que l’authentification a été configurée pour l’application. Ce chapitre explique comment effectuer une migration à partir de ASP.NET Web Forms modèle de fournisseur universel (pour l’appartenance, les rôles et les profils utilisateur) et comment utiliser l’identité ASP.NET Core à partir des Blazor applications. Bien que ce chapitre traite des étapes et des considérations générales, les étapes et scripts détaillés sont disponibles dans la documentation de référence.

## <a name="aspnet-universal-providers"></a>Fournisseurs universels ASP.NET

Depuis ASP.NET 2,0, la plateforme ASP.NET Web Forms a pris en charge un modèle de fournisseur pour diverses fonctionnalités, y compris l’appartenance. Le fournisseur d’appartenances universel, avec le fournisseur de rôle facultatif, est très couramment déployé avec les applications ASP.NET Web Forms. Il offre une méthode fiable et sécurisée pour gérer l’authentification et l’autorisation qui continuent à fonctionner bien aujourd’hui. L’offre la plus récente de ces fournisseurs universels est disponible sous la forme d’un package NuGet, [Microsoft. Aspnet. Providers](https://www.nuget.org/packages/Microsoft.AspNet.Providers).

L’fournisseurs universels fonctionner avec un schéma de base de données SQL qui comprend des tables telles que `aspnet_Applications` , `aspnet_Membership` , `aspnet_Roles` et `aspnet_Users` . Lorsqu’ils sont configurés en exécutant la [ commandeaspnet_regsql.exe](https://docs.microsoft.com/previous-versions/ms229862(v=vs.140)), les fournisseurs installent les tables et les procédures stockées qui fournissent toutes les requêtes et commandes nécessaires à l’utilisation des données sous-jacentes. Le schéma de base de données et ces procédures stockées ne sont pas compatibles avec les systèmes d’identité ASP.NET Identity et ASP.NET Core plus récents. les données existantes doivent donc être migrées dans le nouveau système. La figure 1 montre un exemple de schéma de table configuré pour les fournisseurs universels.

![schéma des fournisseurs universels](./media/security/membership-tables.png)

Le fournisseur universel gère les utilisateurs, l’appartenance, les rôles et les profils. Les utilisateurs reçoivent des identificateurs globaux uniques et des informations très simples (userId, userName) sont stockées dans la `aspnet_Users` table. Les informations d’authentification, telles que le mot de passe, le format de mot de passe, le Salt de mot de passe, les compteurs de verrouillage et les détails, etc., sont stockées dans la `aspnet_Membership` table. Les rôles consistent simplement en noms et identificateurs uniques, qui sont attribués aux utilisateurs via la `aspnet_UsersInRoles` table d’association, fournissant ainsi une relation plusieurs-à-plusieurs.

Si votre système existant utilise des rôles en plus de l’appartenance, vous devez migrer les comptes d’utilisateur, les mots de passe associés, les rôles et l’appartenance au rôle dans ASP.NET Core identité. Vous devrez également mettre à jour votre code là où vous effectuez actuellement des vérifications de rôle à l’aide d’instructions If pour tirer parti des filtres déclaratifs, des attributs et/ou des balises d’aide. Nous examinerons les considérations relatives à la migration plus en détail à la fin de ce chapitre.

### <a name="authorization-configuration-in-web-forms"></a>Configuration de l’autorisation dans Web Forms

Pour configurer l’accès autorisé à certaines pages d’une application ASP.NET Web Forms, vous spécifiez généralement que certaines pages ou dossiers ne sont pas accessibles aux utilisateurs anonymes. Cela s’effectue dans le fichier web.config :

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

La `authentication` section de configuration configure l’authentification par formulaire pour l’application. La `authorization` section est utilisée pour interdire les utilisateurs anonymes pour l’application entière. Toutefois, vous pouvez fournir des règles d’autorisation plus granulaires à chaque emplacement, et appliquer des vérifications d’autorisation basées sur les rôles.

```xml
<location path="login.aspx">
  <system.web>
    <authorization>
      <allow users="*" />
    </authorization>
  </system.web>
</location>
```

La configuration ci-dessus, lorsqu’elle est combinée avec la première, permet aux utilisateurs anonymes d’accéder à la page de connexion, en remplaçant la restriction à l’ensemble du site sur les utilisateurs non authentifiés.

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

La configuration ci-dessus, lorsqu’elle est combinée avec les autres, restreint l’accès au `/admin` dossier et à toutes les ressources qu’il contient aux membres du rôle « Administrateurs ». Cela peut également être appliqué en plaçant un `web.config` fichier distinct au sein de la `/admin` racine du dossier.

### <a name="authorization-code-in-web-forms"></a>Code d’autorisation dans Web Forms

Outre la configuration de l’accès à l’aide de `web.config` , vous pouvez également configurer par programme l’accès et le comportement dans votre application Web Forms. Par exemple, vous pouvez limiter la possibilité d’effectuer certaines opérations ou d’afficher certaines données en fonction du rôle de l’utilisateur.

Ce code peut être utilisé à la fois dans la logique codebehind et dans la page elle-même :

```html
<% if (HttpContext.Current.User.IsInRole("Administrators")) { %>
  <a href="/admin">Go To Admin</a>
<% } %>
```

Outre la vérification de l’appartenance à un rôle d’utilisateur, vous pouvez également déterminer s’ils sont authentifiés (bien que cette opération soit souvent mieux effectuée à l’aide de la configuration basée sur l’emplacement décrite ci-dessus). Vous trouverez ci-dessous un exemple de cette approche.

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

Dans le code ci-dessus, le contrôle d’accès en fonction du rôle (RBAC) est utilisé pour déterminer si certains éléments de la page, tels qu’un `SecretPanel` , sont visibles en fonction du rôle de l’utilisateur actuel.

En règle générale, les applications ASP.NET Web Forms configurent la sécurité dans le `web.config` fichier, puis ajoutent des vérifications supplémentaires si nécessaire dans les `.aspx` pages et leurs `.aspx.cs` fichiers codebehind associés. La plupart des applications exploitent le fournisseur d’appartenances universel, souvent avec le fournisseur de rôles supplémentaire.

## <a name="aspnet-core-identity"></a>Identité ASP.NET Core

Bien qu’elle soit toujours associée à l’authentification et à l’autorisation, ASP.NET Core identité utilise un ensemble différent d’abstractions et d’hypothèses par rapport aux fournisseurs universels. Par exemple, le nouveau modèle d’identité prend en charge l’authentification tierce, ce qui permet aux utilisateurs de s’authentifier à l’aide d’un compte de média social ou d’un autre fournisseur d’authentification approuvé. ASP.NET Core identité prend en charge l’interface utilisateur pour les pages couramment utilisées, telles que la connexion, la déconnexion et l’inscription. Il exploite EF Core pour son accès aux données, et utilise EF Core migrations pour générer le schéma nécessaire à la prise en charge de son modèle de données. Cette [Présentation de l’identité sur ASP.net Core](https://docs.microsoft.com/aspnet/core/security/authentication/identity) fournit une bonne vue d’ensemble de ce qui est inclus dans ASP.net Core identité et de la façon de commencer à l’utiliser. Si vous n’avez pas déjà configuré ASP.NET Core identité dans votre application et sa base de données, cela vous aidera à commencer.

### <a name="roles-claims-and-policies"></a>Rôles, revendications et stratégies

Les fournisseurs universels et l’identité ASP.NET Core prennent en charge le concept de rôles. Vous pouvez créer des rôles pour les utilisateurs et affecter des utilisateurs à des rôles. Les utilisateurs peuvent appartenir à n’importe quel nombre de rôles, et vous pouvez vérifier l’appartenance au rôle dans le cadre de votre implémentation d’autorisation.

En plus des rôles, ASP.NET Core identité prend en charge les concepts des revendications et des stratégies. Alors qu’un rôle doit correspondre spécifiquement à un ensemble de ressources, un utilisateur de ce rôle doit pouvoir y accéder, une revendication fait simplement partie de l’identité d’un utilisateur. Une revendication est une paire nom/valeur qui représente l’objet, pas ce que le sujet peut faire.

Il est possible d’inspecter directement les revendications d’un utilisateur et de déterminer si un utilisateur doit se voir accorder l’accès à une ressource. Toutefois, ces vérifications sont souvent répétitives et éparpillées dans le système. Une meilleure approche consiste à définir une *stratégie*.

Une stratégie d’autorisation se compose d’une ou de plusieurs exigences. Les stratégies sont inscrites dans le cadre de la configuration du service d’autorisation dans la `ConfigureServices` méthode de `Startup.cs` . Par exemple, l’extrait de code suivant configure une stratégie appelée « CanadiansOnly » qui exige que l’utilisateur dispose de la revendication Country avec la valeur « Canada ».

```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("CanadiansOnly", policy => policy.RequireClaim(ClaimTypes.Country, "Canada"));
});
```

Vous pouvez [en savoir plus sur la façon de créer des stratégies personnalisées dans la documentation](https://docs.microsoft.com/aspnet/core/security/authorization/policies).

Que vous utilisiez des stratégies ou des rôles, vous pouvez spécifier qu’une page particulière de votre Blazor application nécessite ce rôle ou cette stratégie avec l' `[Authorize]` attribut, appliquée à la `@attribute` directive.

Exigence d’un rôle :

```csharp
@attribute [Authorize(Roles ="administrators")]
```

Exiger la satisfaction d’une stratégie :

```csharp
@attribute [Authorize(Policy ="CanadiansOnly")]
```

Si vous avez besoin d’accéder à l’état d’authentification, aux rôles ou aux revendications d’un utilisateur dans votre code, il existe deux méthodes principales pour y parvenir. La première consiste à recevoir l’état d’authentification en tant que paramètre en cascade. La seconde consiste à accéder à l’État à l’aide d’un injecté `AuthenticationStateProvider` . Les détails de chacune de ces approches sont décrits dans la [ Blazor documentation relative](https://docs.microsoft.com/aspnet/core/blazor/security/)à la sécurité.

Le code suivant montre comment recevoir le `AuthenticationState` en tant que paramètre en cascade :

```csharp
[CascadingParameter]
private Task<AuthenticationState> authenticationStateTask { get; set; }
```

Une fois ce paramètre en place, vous pouvez faire en sorte que l’utilisateur utilise ce code :

```csharp
var authState = await authenticationStateTask;
var user = authState.User;
```

Le code suivant montre comment injecter les `AuthenticationStateProvider` éléments suivants :

```csharp
@using Microsoft.AspNetCore.Components.Authorization
@inject AuthenticationStateProvider AuthenticationStateProvider
```

Une fois le fournisseur en place, vous pouvez accéder à l’utilisateur avec le code suivant :

```csharp
AuthenticationState authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
ClaimsPrincipal user = authState.User;

if (user.Identity.IsAuthenticated)
{
  // work with user.Claims and/or user.Roles
}
```

**Remarque :** Le `AuthorizeView` composant, abordé plus loin dans ce chapitre, offre un moyen déclaratif de contrôler ce qu’un utilisateur voit sur une page ou un composant.

Pour travailler avec les utilisateurs et les revendications (dans les Blazor applications serveur), vous devrez peut-être également injecter une `UserManager<T>` (utiliser `IdentityUser` pour la valeur par défaut) que vous pouvez utiliser pour énumérer et modifier des revendications pour un utilisateur. Injectez d’abord le type et affectez-le à une propriété :

```csharp
@inject UserManager<IdentityUser> MyUserManager
```

Utilisez-le ensuite pour travailler avec les revendications de l’utilisateur. L’exemple suivant montre comment ajouter une revendication à un utilisateur et la rendre persistante :

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

Si vous devez utiliser des rôles, suivez la même approche. Vous devrez peut-être injecter un `RoleManager<T>` (utilisez `IdentityRole` pour le type par défaut) pour répertorier et gérer les rôles eux-mêmes.

**Remarque :** Dans Blazor les projets Webassembly, vous devrez fournir des API serveur pour effectuer ces opérations (au lieu d’utiliser `UserManager<T>` ou `RoleManager<T>` directement). Une Blazor application cliente Webassembly gère les revendications et/ou les rôles en appelant de manière sécurisée les points de terminaison d’API exposés à cet effet.

### <a name="migration-guide"></a>Guide de migration

La migration de ASP.NET Web Forms et des fournisseurs universels vers ASP.NET Core identité nécessite plusieurs étapes :

1. Créer ASP.NET Core schéma de base de données d’identité dans la base de données de destination
2. Migrer des données à partir du schéma de fournisseur universel vers ASP.NET Core schéma d’identité
3. Migrez la configuration de web.config à des intergiciels et des services, généralement dans `Startup.cs`
4. Mettez à jour des pages individuelles à l’aide de contrôles et de conditionnels pour utiliser des balises tag et de nouvelles API d’identité.

Chacune de ces étapes est décrite en détail dans les sections suivantes.

### <a name="creating-the-aspnet-core-identity-schema"></a>Création du schéma d’identité ASP.NET Core

Il existe plusieurs façons de créer la structure de table nécessaire utilisée pour ASP.NET Core identité. La méthode la plus simple consiste à créer une nouvelle ASP.NET Core application Web. Choisissez application Web, puis modifier l’authentification pour utiliser des comptes d’utilisateur individuels.

![nouveau projet avec des comptes d’utilisateur individuels](./media/security/individual-user-accounts.png)

À partir de la ligne de commande, vous pouvez effectuer la même opération en exécutant `dotnet new webapp -au Individual` . Une fois l’application créée, exécutez-la et inscrivez-vous sur le site. Vous devez déclencher une page telle que celle illustrée ci-dessous :

![page appliquer les migrations](./media/security/apply-migrations-page.png)

Cliquez sur le bouton « appliquer des migrations » pour créer les tables de base de données nécessaires. En outre, les fichiers de migration doivent apparaître dans votre projet, comme indiqué ci-dessous :

![fichiers de migration](./media/security/migration-files.png)

Vous pouvez exécuter la migration vous-même, sans exécuter l’application Web, à l’aide de cet outil de ligne de commande :

```powershell
dotnet ef database update
```

Si vous préférez exécuter un script pour appliquer le nouveau schéma à une base de données existante, vous pouvez créer un script pour ces migrations à partir de la ligne de commande. Exécutez cette commande pour générer le script :

```powershell
dotnet ef migrations script -o auth.sql
```

Cela génère un script SQL dans le fichier de sortie `auth.sql` , qui peut ensuite être exécuté sur n’importe quelle base de données de votre choix. Si vous avez des difficultés à exécuter des `dotnet ef` commandes, assurez [-vous que les outils de EF Core sont installés sur votre système](https://docs.microsoft.com/ef/core/miscellaneous/cli/dotnet).

Dans le cas où vous avez des colonnes supplémentaires sur vos tables sources, vous devez identifier le meilleur emplacement pour ces colonnes dans le nouveau schéma. En règle générale, les colonnes trouvées dans la `aspnet_Membership` table doivent être mappées à la `AspNetUsers` table. Les colonnes sur `aspnet_Roles` doivent être mappées à `AspNetRoles` . Toutes les colonnes supplémentaires de la `aspnet_UsersInRoles` table sont ajoutées à la `AspNetUserRoles` table.

Il est également intéressant de placer des colonnes supplémentaires sur des tables distinctes, afin que les futures migrations n’aient pas besoin de prendre en compte ces personnalisations du schéma d’identité par défaut.

### <a name="migrating-data-from-universal-providers-to-aspnet-core-identity"></a>Migration des données des fournisseurs universels vers ASP.NET Core identité

Une fois le schéma de la table de destination en place, l’étape suivante consiste à migrer vos enregistrements d’utilisateur et de rôle vers le nouveau schéma. La liste complète des différences de schéma, y compris les colonnes qui mappent aux nouvelles colonnes, est disponible [ici](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity).

Pour migrer vos utilisateurs de l’appartenance vers les nouvelles tables d’identité, vous devez [suivre les étapes décrites dans la documentation](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity). Après avoir effectué ces étapes et le script fourni, vos utilisateurs devront modifier leur mot de passe lors de leur prochaine connexion.

Il est possible de migrer des mots de passe utilisateur, mais le processus est bien plus complexe. Demander aux utilisateurs de mettre à jour leur mot de passe dans le cadre du processus de migration et les encourager à utiliser de nouveaux mots de passe uniques, est susceptible d’améliorer la sécurité globale de l’application.

### <a name="migrating-security-settings-from-webconfig-to-startupcs"></a>Migration des paramètres de sécurité de web.config vers Startup.cs

Comme indiqué ci-dessus, les fournisseurs de rôles et d’appartenance ASP.NET sont configurés dans le fichier web.config de l’application. Étant donné que les applications ASP.NET Core ne sont pas liées à IIS et utilisent un système distinct pour la configuration, ces paramètres doivent être configurés ailleurs. Pour l’essentiel, ASP.NET Core identité est configurée dans le `Startup.cs` fichier. Ouvrez le projet Web créé précédemment (pour générer le schéma de la table d’identité) et examinez son `Startup.cs` fichier.

La méthode ConfigureServices par défaut ajoute la prise en charge de EF Core et de l’identité :

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

La `AddDefaultIdentity` méthode d’extension est utilisée pour configurer l’identité afin d’utiliser la valeur par défaut `ApplicationDbContext` et le type de l’infrastructure `IdentityUser` . Si vous utilisez un personnalisé `IdentityUser` , veillez à spécifier son type ici. Si ces méthodes d’extension ne fonctionnent pas dans votre application, vérifiez que vous disposez des instructions using appropriées et que vous disposez des références de package NuGet nécessaires. Par exemple, votre projet doit avoir une version des `Microsoft.AspNetCore.Identity.EntityFrameworkCore` packages et `Microsoft.AspNetCore.Identity.UI` référencée.

Dans, `Startup.cs` vous devez également voir le middleware nécessaire configuré pour le site. Plus précisément, `UseAuthentication` et `UseAuthorization` doivent être configurés et se trouver à l’emplacement approprié.

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

ASP.NET Identity ne configure pas l’accès anonyme ou basé sur les rôles à des emplacements à partir de `Startup.cs` . Vous devez migrer toutes les données de configuration d’autorisation spécifiques à l’emplacement vers des filtres dans ASP.NET Core. Prenez note des dossiers et des pages qui nécessitent ces mises à jour. Vous allez apporter ces modifications dans la section suivante.

### <a name="updating-individual-pages-to-use-aspnet-core-identity-abstractions"></a>Mise à jour de pages individuelles à utiliser ASP.NET Core abstractions d’identité

Dans votre application ASP.NET Web Forms, si vous aviez web.config paramètres pour refuser l’accès à des utilisateurs anonymes à certaines pages ou dossiers, vous devez les migrer en ajoutant simplement l' `[Authorize]` attribut à ces pages :

```razor
@attribute [Authorize]
```

Si vous avez encore refusé l’accès, à l’exception des utilisateurs qui appartiennent à un certain rôle, vous pouvez migrer de la même façon en ajoutant un attribut spécifiant un rôle :

```razor
@attribute [Authorize(Roles ="administrators")]
```

Notez que l' `[Authorize]` attribut ne fonctionne que sur `@page` les composants qui sont atteints via le Blazor routeur. L’attribut ne fonctionne pas avec les composants enfants, qui doivent utiliser à la place `AuthorizeView` .

Si vous avez une logique dans le balisage de la page pour déterminer s’il faut afficher du code pour un utilisateur donné, vous pouvez remplacer ceci par le `AuthorizeView` composant. Le [composant AuthorizeView](https://docs.microsoft.com/aspnet/core/blazor/security#authorizeview-component) affiche l’interface utilisateur de manière sélective, selon que l’utilisateur est autorisé ou non à le voir. Il expose également une `context` variable qui peut être utilisée pour accéder aux informations utilisateur.

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

Vous pouvez accéder à l’état d’authentification dans la logique procédurale en accédant à l’utilisateur à partir d’un `Task<AuthenticationState` configuré avec l' `[CascadingParameter]` attribut. Cela vous permet d’accéder à l’utilisateur, ce qui vous permet de déterminer s’il est authentifié et s’il appartient à un rôle particulier. Si vous devez évaluer une stratégie de façon procédurale, vous pouvez injecter une instance du `IAuthorizationService` et appelle la `AuthorizeAsync` méthode sur celle-ci. L’exemple de code suivant montre comment obtenir des informations utilisateur et autoriser un utilisateur autorisé à effectuer une tâche limitée par la `content-editor` stratégie.

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

Le `AuthenticationState` doit d’abord être configuré en tant que valeur en cascade pour pouvoir être lié à un paramètre en cascade comme celui-ci. Cela s’effectue généralement à l’aide du `CascadingAuthenticationState` composant. Cela s’effectue généralement dans `App.razor` :

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

## <a name="summary"></a>Résumé

Blazor utilise le même modèle de sécurité que ASP.NET Core, qui est ASP.NET Core identité. La migration des fournisseurs universels vers ASP.NET Core identité est relativement simple, en supposant que la personnalisation n’a pas été appliquée au schéma de données d’origine. Une fois les données migrées, l’utilisation de l’authentification et de l’autorisation dans les Blazor applications est bien documentée, avec une prise en charge configurable et par programmation pour la plupart des exigences de sécurité.

## <a name="references"></a>References

- [Présentation de l’identité sur ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/identity)
- [Migrer de l’authentification d’appartenance ASP.NET vers l’identité ASP.NET Core 2,0](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity)
- [Migrer l’authentification et l’identité vers ASP.NET Core](https://docs.microsoft.com/aspnet/core/migration/identity)
- [BlazorAuthentification et autorisation ASP.net Core](https://docs.microsoft.com/aspnet/core/blazor/security/)

>[!div class="step-by-step"]
>[Précédent](config.md) 
> [Suivant](migration.md)
