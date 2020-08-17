---
title: Pages, routage et dispositions
description: Apprenez à créer des pages dans Blazor , à travailler avec le routage côté client et à gérer les mises en page.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 09/19/2019
ms.openlocfilehash: 714ba0be7c2014895a75250a47e6ce448863eb6c
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267787"
---
# <a name="pages-routing-and-layouts"></a><span data-ttu-id="ba3a9-103">Pages, routage et dispositions</span><span class="sxs-lookup"><span data-stu-id="ba3a9-103">Pages, routing, and layouts</span></span>

<span data-ttu-id="ba3a9-104">ASP.NET Web Forms applications sont composées de pages définies dans des fichiers *. aspx* .</span><span class="sxs-lookup"><span data-stu-id="ba3a9-104">ASP.NET Web Forms apps are composed of pages defined in *.aspx* files.</span></span> <span data-ttu-id="ba3a9-105">L’adresse de chaque page est basée sur son chemin d’accès physique au projet.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-105">Each page's address is based on its physical file path in the project.</span></span> <span data-ttu-id="ba3a9-106">Quand un navigateur envoie une requête à la page, le contenu de la page est rendu dynamiquement sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-106">When a browser makes a request to the page, the contents of the page are dynamically rendered on the server.</span></span> <span data-ttu-id="ba3a9-107">Les comptes de rendu pour le balisage HTML de la page et ses contrôles serveur.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-107">The rendering accounts for both the page's HTML markup and its server controls.</span></span>

<span data-ttu-id="ba3a9-108">Dans Blazor , chaque page de l’application est un composant, généralement défini dans un fichier *. Razor* , avec un ou plusieurs itinéraires spécifiés.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-108">In Blazor, each page in the app is a component, typically defined in a *.razor* file, with one or more specified routes.</span></span> <span data-ttu-id="ba3a9-109">Le routage s’effectue principalement côté client sans impliquer de demande de serveur spécifique.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-109">Routing mostly happens client-side without involving a specific server request.</span></span> <span data-ttu-id="ba3a9-110">Le navigateur effectue d’abord une demande à l’adresse racine de l’application.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-110">The browser first makes a request to the root address of the app.</span></span> <span data-ttu-id="ba3a9-111">Un `Router` composant racine de l' Blazor application gère alors l’interception des demandes de navigation et les requêtes de navigation vers le composant approprié.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-111">A root `Router` component in the Blazor app then handles intercepting navigation requests and them to the correct component.</span></span>

<span data-ttu-id="ba3a9-112">Blazor prend également en charge la *liaison profonde*.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-112">Blazor also supports *deep linking*.</span></span> <span data-ttu-id="ba3a9-113">La liaison profonde se produit lorsque le navigateur envoie une requête à un itinéraire spécifique autre que la racine de l’application.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-113">Deep linking occurs when the browser makes a request to a specific route other than the root of the app.</span></span> <span data-ttu-id="ba3a9-114">Les demandes de liens ciblés envoyées au serveur sont routées vers l' Blazor application, qui achemine ensuite la demande côté client vers le composant approprié.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-114">Requests for deep links sent to the server are routed to the Blazor app, which then routes the request client-side to the correct component.</span></span>

<span data-ttu-id="ba3a9-115">Une page simple dans ASP.NET Web Forms peut contenir le balisage suivant :</span><span class="sxs-lookup"><span data-stu-id="ba3a9-115">A simple page in ASP.NET Web Forms might contain the following markup:</span></span>

<span data-ttu-id="ba3a9-116">*Nom. aspx*</span><span class="sxs-lookup"><span data-stu-id="ba3a9-116">*Name.aspx*</span></span>

```aspx-csharp
<%@ Page Title="Name" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Name.aspx.cs" Inherits="WebApplication1.Name" %>

<asp:Content ID="BodyContent" ContentPlaceHolderID="MainContent" runat="server">
    <div>
        What is your name?<br />
        <asp:TextBox ID="TextBox1" runat="server"></asp:TextBox>
        <asp:Button ID="Button1" runat="server" Text="Submit" OnClick="Button1_Click" />
    </div>
    <div>
        <asp:Literal ID="Literal1" runat="server" />
    </div>
</asp:Content>
```

<span data-ttu-id="ba3a9-117">*Name.aspx.cs*</span><span class="sxs-lookup"><span data-stu-id="ba3a9-117">*Name.aspx.cs*</span></span>

```csharp
public partial class Name : System.Web.UI.Page
{
    protected void Button1_Click1(object sender, EventArgs e)
    {
        Literal1.Text = "Hello " + TextBox1.Text;
    }
}
```

<span data-ttu-id="ba3a9-118">La page équivalente dans une application ressemble à Blazor ceci :</span><span class="sxs-lookup"><span data-stu-id="ba3a9-118">The equivalent page in a Blazor app would look like this:</span></span>

<span data-ttu-id="ba3a9-119">*Name. Razor*</span><span class="sxs-lookup"><span data-stu-id="ba3a9-119">*Name.razor*</span></span>

```razor
@page "/Name"
@layout MainLayout

<div>
    What is your name?<br />
    <input @bind="text" />
    <button @onclick="OnClick">Submit</button>
</div>
<div>
    @if (name != null)
    {
        @:Hello @name
    }
</div>

@code {
    string text;
    string name;

    void OnClick() {
        name = text;
    }
}
```

## <a name="create-pages"></a><span data-ttu-id="ba3a9-120">Créer des pages</span><span class="sxs-lookup"><span data-stu-id="ba3a9-120">Create pages</span></span>

<span data-ttu-id="ba3a9-121">Pour créer une page dans Blazor , créez un composant et ajoutez la `@page` directive Razor pour spécifier l’itinéraire du composant.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-121">To create a page in Blazor, create a component and add the `@page` Razor directive to specify the route for the component.</span></span> <span data-ttu-id="ba3a9-122">La `@page` directive prend un seul paramètre, qui est le modèle de routage à ajouter à ce composant.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-122">The `@page` directive takes a single parameter, which is the route template to add to that component.</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="ba3a9-123">Le paramètre de modèle de routage est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-123">The route template parameter is required.</span></span> <span data-ttu-id="ba3a9-124">Contrairement à ASP.NET Web Forms, l’itinéraire vers un Blazor composant *n’est pas* déduit de son emplacement de fichier (bien que cela puisse être une fonctionnalité ajoutée à l’avenir).</span><span class="sxs-lookup"><span data-stu-id="ba3a9-124">Unlike ASP.NET Web Forms, the route to a Blazor component *isn't* inferred from its file location (although that may be a feature added in the future).</span></span>

<span data-ttu-id="ba3a9-125">La syntaxe de modèle de routage est identique à la syntaxe de base utilisée pour le routage dans ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-125">The route template syntax is the same basic syntax used for routing in ASP.NET Web Forms.</span></span> <span data-ttu-id="ba3a9-126">Les paramètres de routage sont spécifiés dans le modèle à l’aide d’accolades.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-126">Route parameters are specified in the template using braces.</span></span> <span data-ttu-id="ba3a9-127">Blazor lie les valeurs d’itinéraire aux paramètres de composant portant le même nom (non-respect de la casse).</span><span class="sxs-lookup"><span data-stu-id="ba3a9-127">Blazor will bind route values to component parameters with the same name (case-insensitive).</span></span>

```razor
@page "/product/{id}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public string Id { get; set; }
}
```

<span data-ttu-id="ba3a9-128">Vous pouvez également spécifier des contraintes sur la valeur du paramètre d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-128">You can also specify constraints on the value of the route parameter.</span></span> <span data-ttu-id="ba3a9-129">Par exemple, pour contraindre l’ID de produit en tant que `int` :</span><span class="sxs-lookup"><span data-stu-id="ba3a9-129">For example, to constrain the product ID to be an `int`:</span></span>

```razor
@page "/product/{id:int}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public int Id { get; set; }
}
```

<span data-ttu-id="ba3a9-130">Pour obtenir la liste complète des contraintes d’itinéraire prises en charge par Blazor , consultez [contraintes de routage](/aspnet/core/blazor/routing#route-constraints).</span><span class="sxs-lookup"><span data-stu-id="ba3a9-130">For a full list of the route constraints supported by Blazor, see [Route constraints](/aspnet/core/blazor/routing#route-constraints).</span></span>

## <a name="router-component"></a><span data-ttu-id="ba3a9-131">Composant routeur</span><span class="sxs-lookup"><span data-stu-id="ba3a9-131">Router component</span></span>

<span data-ttu-id="ba3a9-132">Le routage dans Blazor est géré par le `Router` composant.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-132">Routing in Blazor is handled by the `Router` component.</span></span> <span data-ttu-id="ba3a9-133">Le `Router` composant est généralement utilisé dans le composant racine de l’application (*app. Razor*).</span><span class="sxs-lookup"><span data-stu-id="ba3a9-133">The `Router` component is typically used in the app's root component (*App.razor*).</span></span>

```razor
<Router AppAssembly="@typeof(Program).Assembly">
    <Found Context="routeData">
        <RouteView RouteData="@routeData" DefaultLayout="@typeof(MainLayout)" />
    </Found>
    <NotFound>
        <LayoutView Layout="@typeof(MainLayout)">
            <p>Sorry, there's nothing at this address.</p>
        </LayoutView>
    </NotFound>
</Router>
```

<span data-ttu-id="ba3a9-134">Le `Router` composant Découvre les composants routables dans le spécifié `AppAssembly` et dans le spécifié, éventuellement `AdditionalAssemblies` .</span><span class="sxs-lookup"><span data-stu-id="ba3a9-134">The `Router` component discovers the routable components in the specified `AppAssembly` and in the optionally specified `AdditionalAssemblies`.</span></span> <span data-ttu-id="ba3a9-135">Lorsque le navigateur navigue, le `Router` intercepte la navigation et restitue le contenu de son `Found` paramètre avec l’extrait `RouteData` si un itinéraire correspond à l’adresse ; sinon, le `Router` restitue son `NotFound` paramètre.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-135">When the browser navigates, the `Router` intercepts the navigation and renders the contents of its `Found` parameter with the extracted `RouteData` if a route matches the address, otherwise the `Router` renders its `NotFound` parameter.</span></span>

<span data-ttu-id="ba3a9-136">Le `RouteView` composant gère le rendu du composant correspondant spécifié par `RouteData` avec sa disposition, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-136">The `RouteView` component handles rendering the matched component specified by the `RouteData` with its layout if it has one.</span></span> <span data-ttu-id="ba3a9-137">Si le composant correspondant n’a pas de disposition, le cas échéant, l’option spécifiée `DefaultLayout` est utilisée.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-137">If the matched component doesn't have a layout, then the optionally specified `DefaultLayout` is used.</span></span>

<span data-ttu-id="ba3a9-138">Le `LayoutView` composant affiche son contenu enfant dans la disposition spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-138">The `LayoutView` component renders its child content within the specified layout.</span></span> <span data-ttu-id="ba3a9-139">Nous étudierons plus en détail les dispositions plus loin dans ce chapitre.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-139">We'll look at layouts more in detail later in this chapter.</span></span>

## <a name="navigation"></a><span data-ttu-id="ba3a9-140">Navigation</span><span class="sxs-lookup"><span data-stu-id="ba3a9-140">Navigation</span></span>

<span data-ttu-id="ba3a9-141">Dans ASP.NET Web Forms, vous déclenchez la navigation vers une page différente en renvoyant une réponse de redirection au navigateur.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-141">In ASP.NET Web Forms, you trigger navigation to a different page by returning a redirect response to the browser.</span></span> <span data-ttu-id="ba3a9-142">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="ba3a9-142">For example:</span></span>

```csharp
protected void NavigateButton_Click(object sender, EventArgs e)
{
    Response.Redirect("Counter");
}
```

<span data-ttu-id="ba3a9-143">Le retour d’une réponse de redirection n’est généralement pas possible dans Blazor .</span><span class="sxs-lookup"><span data-stu-id="ba3a9-143">Returning a redirect response isn't typically possible in Blazor.</span></span> <span data-ttu-id="ba3a9-144">Blazor n’utilise pas de modèle de demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-144">Blazor doesn't use a request-reply model.</span></span> <span data-ttu-id="ba3a9-145">Toutefois, vous pouvez déclencher des navigations de navigateur directement, comme vous pouvez le faire avec JavaScript.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-145">You can, however, trigger browser navigations directly, as you can with JavaScript.</span></span>

<span data-ttu-id="ba3a9-146">Blazor fournit un `NavigationManager` service qui peut être utilisé pour :</span><span class="sxs-lookup"><span data-stu-id="ba3a9-146">Blazor provides a `NavigationManager` service that can be used to:</span></span>

- <span data-ttu-id="ba3a9-147">Récupérer l’adresse actuelle du navigateur</span><span class="sxs-lookup"><span data-stu-id="ba3a9-147">Get the current browser address</span></span>
- <span data-ttu-id="ba3a9-148">Obtient l’adresse de base</span><span class="sxs-lookup"><span data-stu-id="ba3a9-148">Get the base address</span></span>
- <span data-ttu-id="ba3a9-149">Navigations de déclencheur</span><span class="sxs-lookup"><span data-stu-id="ba3a9-149">Trigger navigations</span></span>
- <span data-ttu-id="ba3a9-150">Recevoir une notification lorsque l’adresse change</span><span class="sxs-lookup"><span data-stu-id="ba3a9-150">Get notified when the address changes</span></span>

<span data-ttu-id="ba3a9-151">Pour accéder à une autre adresse, utilisez la `NavigateTo` méthode :</span><span class="sxs-lookup"><span data-stu-id="ba3a9-151">To navigate to a different address, use the `NavigateTo` method:</span></span>

```razor
@page "/"
@inject NavigationManager NavigationManager

<button @onclick="Navigate">Navigate</button>

@code {
    void Navigate() {
        NavigationManager.NavigateTo("counter");
    }
}
```

<span data-ttu-id="ba3a9-152">Pour obtenir une description de tous les `NavigationManager` membres, consultez [URI et assistance de l’état de navigation](/aspnet/core/blazor/routing#uri-and-navigation-state-helpers).</span><span class="sxs-lookup"><span data-stu-id="ba3a9-152">For a description of all `NavigationManager` members, see [URI and navigation state helpers](/aspnet/core/blazor/routing#uri-and-navigation-state-helpers).</span></span>

## <a name="base-urls"></a><span data-ttu-id="ba3a9-153">URL de base</span><span class="sxs-lookup"><span data-stu-id="ba3a9-153">Base URLs</span></span>

<span data-ttu-id="ba3a9-154">Si votre Blazor application est déployée sous un chemin d’accès de base, vous devez spécifier l’URL de base dans les métadonnées de la page à l’aide de la `<base>` balise pour le routage vers la propriété de travail.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-154">If your Blazor app is deployed under a base path, then you need to specify the base URL in the page metadata using the `<base>` tag for routing to work property.</span></span> <span data-ttu-id="ba3a9-155">Si la page hôte de l’application est affichée par le serveur à l’aide de Razor, vous pouvez utiliser la `~/` syntaxe pour spécifier l’adresse de base de l’application.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-155">If the host page for the app is server-rendered using Razor, then you can use the `~/` syntax to specify the app's base address.</span></span> <span data-ttu-id="ba3a9-156">Si la page hôte est du code HTML statique, vous devez spécifier l’URL de base explicitement.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-156">If the host page is static HTML, then you need to specify the base URL explicitly.</span></span>

```html
<base href="~/" />
```

## <a name="page-layout"></a><span data-ttu-id="ba3a9-157">Mise en page</span><span class="sxs-lookup"><span data-stu-id="ba3a9-157">Page layout</span></span>

<span data-ttu-id="ba3a9-158">La mise en page dans ASP.NET Web Forms est gérée par les pages maîtres.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-158">Page layout in ASP.NET Web Forms is handled by Master Pages.</span></span> <span data-ttu-id="ba3a9-159">Les pages maîtres définissent un modèle avec un ou plusieurs espaces réservés de contenu qui peuvent ensuite être fournis par des pages individuelles.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-159">Master Pages define a template with one or more content placeholders that can then be supplied by individual pages.</span></span> <span data-ttu-id="ba3a9-160">Les pages maîtres sont définies dans les fichiers *. Master* et commencent par la `<%@ Master %>` directive.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-160">Master Pages are defined in *.master* files and start with the `<%@ Master %>` directive.</span></span> <span data-ttu-id="ba3a9-161">Le contenu des fichiers *. Master* est codé comme s’il s’agissait d’une page *. aspx* , mais avec l’ajout de `<asp:ContentPlaceHolder>` contrôles pour marquer l’emplacement où les pages peuvent fournir du contenu.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-161">The content of the *.master* files is coded as you would an *.aspx* page, but with the addition of `<asp:ContentPlaceHolder>` controls to mark where pages can supply content.</span></span>

<span data-ttu-id="ba3a9-162">*Site.master*</span><span class="sxs-lookup"><span data-stu-id="ba3a9-162">*Site.master*</span></span>

```aspx-csharp
<%@ Master Language="C#" AutoEventWireup="true" CodeBehind="Site.master.cs" Inherits="WebApplication1.SiteMaster" %>

<!DOCTYPE html>
<html lang="en">
<head runat="server">
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title><%: Page.Title %> - My ASP.NET Application</title>
    <link href="~/favicon.ico" rel="shortcut icon" type="image/x-icon" />
</head>
<body>
    <form runat="server">
        <div class="container body-content">
            <asp:ContentPlaceHolder ID="MainContent" runat="server">
            </asp:ContentPlaceHolder>
            <hr />
            <footer>
                <p>&copy; <%: DateTime.Now.Year %> - My ASP.NET Application</p>
            </footer>
        </div>
    </form>
</body>
</html>
```

<span data-ttu-id="ba3a9-163">Dans Blazor , vous gérez la mise en page à l’aide de composants de disposition.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-163">In Blazor, you handle page layout using layout components.</span></span> <span data-ttu-id="ba3a9-164">Les composants de disposition héritent de `LayoutComponentBase` , qui définit une seule `Body` propriété de type `RenderFragment` , qui peut être utilisée pour afficher le contenu de la page.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-164">Layout components inherit from `LayoutComponentBase`, which defines a single `Body` property of type `RenderFragment`, which can be used to render the contents of the page.</span></span>

<span data-ttu-id="ba3a9-165">*MainLayout. Razor*</span><span class="sxs-lookup"><span data-stu-id="ba3a9-165">*MainLayout.razor*</span></span>

```razor
@inherits LayoutComponentBase
<h1>Main layout</h1>
<div>
    @Body
</div>
```

<span data-ttu-id="ba3a9-166">Lors du rendu de la page avec une disposition, la page est rendue dans le contenu de la disposition spécifiée à l’emplacement où la disposition affiche sa `Body` propriété.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-166">When the page with a layout is rendered, the page is rendered within the contents of the specified layout at the location where the layout renders its `Body` property.</span></span>

<span data-ttu-id="ba3a9-167">Pour appliquer une disposition à une page, utilisez la `@layout` directive :</span><span class="sxs-lookup"><span data-stu-id="ba3a9-167">To apply a layout to a page, use the `@layout` directive:</span></span>

```razor
@layout MainLayout
```

<span data-ttu-id="ba3a9-168">Vous pouvez spécifier la disposition de tous les composants d’un dossier et de ses sous-dossiers à l’aide d’un fichier *_Imports. Razor* .</span><span class="sxs-lookup"><span data-stu-id="ba3a9-168">You can specify the layout for all components in a folder and subfolders using an *_Imports.razor* file.</span></span> <span data-ttu-id="ba3a9-169">Vous pouvez également spécifier une disposition par défaut pour toutes vos pages à l’aide du [composant routeur](#router-component).</span><span class="sxs-lookup"><span data-stu-id="ba3a9-169">You can also specify a default layout for all your pages using the [Router component](#router-component).</span></span>

<span data-ttu-id="ba3a9-170">Les pages maîtres peuvent définir plusieurs espaces réservés de contenu, mais les dispositions de Blazor ne possèdent qu’une seule `Body` propriété.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-170">Master Pages can define multiple content placeholders, but layouts in Blazor only have a single `Body` property.</span></span> <span data-ttu-id="ba3a9-171">Cette limitation des Blazor composants de la disposition sera prévue dans une prochaine version.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-171">This limitation of Blazor layout components will hopefully be addressed in a future release.</span></span>

<span data-ttu-id="ba3a9-172">Les pages maîtres dans ASP.NET Web Forms peuvent être imbriquées.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-172">Master Pages in ASP.NET Web Forms can be nested.</span></span> <span data-ttu-id="ba3a9-173">Autrement dit, une page maître peut également utiliser une page maître.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-173">That is, a Master Page may also use a Master Page.</span></span> <span data-ttu-id="ba3a9-174">Les composants de disposition dans Blazor peuvent également être imbriqués.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-174">Layout components in Blazor may be nested too.</span></span> <span data-ttu-id="ba3a9-175">Vous pouvez appliquer un composant de disposition à un composant de disposition.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-175">You can apply a layout component to a layout component.</span></span> <span data-ttu-id="ba3a9-176">Le contenu de la disposition interne sera rendu dans la disposition externe.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-176">The contents of the inner layout will be rendered within the outer layout.</span></span>

<span data-ttu-id="ba3a9-177">*ChildLayout. Razor*</span><span class="sxs-lookup"><span data-stu-id="ba3a9-177">*ChildLayout.razor*</span></span>

```razor
@layout MainLayout
<h2>Child layout</h2>
<div>
    @Body
</div>
```

<span data-ttu-id="ba3a9-178">*Index. Razor*</span><span class="sxs-lookup"><span data-stu-id="ba3a9-178">*Index.razor*</span></span>

```razor
@page "/"
@layout ChildLayout
<p>I'm in a nested layout!</p>
```

<span data-ttu-id="ba3a9-179">La sortie rendue pour la page serait alors :</span><span class="sxs-lookup"><span data-stu-id="ba3a9-179">The rendered output for the page would then be:</span></span>

```html
<h1>Main layout</h1>
<div>
    <h2>Child layout</h2>
    <div>
        <p>I'm in a nested layout!</p>
    </div>
</div>
```

<span data-ttu-id="ba3a9-180">Les dispositions de Blazor ne définissent généralement pas les éléments HTML racine d’une page ( `<html>` , `<body>` , `<head>` , etc.).</span><span class="sxs-lookup"><span data-stu-id="ba3a9-180">Layouts in Blazor don't typically define the root HTML elements for a page (`<html>`, `<body>`, `<head>`, and so on).</span></span> <span data-ttu-id="ba3a9-181">Les éléments HTML racine sont définis à la place dans la Blazor page hôte d’une application, qui est utilisée pour afficher le contenu HTML initial de l’application (consultez [bootstrap Blazor ](project-structure.md#bootstrap-blazor)).</span><span class="sxs-lookup"><span data-stu-id="ba3a9-181">The root HTML elements are instead defined in a Blazor app's host page, which is used to render the initial HTML content for the app (see [Bootstrap Blazor](project-structure.md#bootstrap-blazor)).</span></span> <span data-ttu-id="ba3a9-182">La page hôte peut afficher plusieurs composants racine pour l’application avec le balisage environnant.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-182">The host page can render multiple root components for the app with surrounding markup.</span></span>

<span data-ttu-id="ba3a9-183">Les composants dans Blazor , y compris les pages, ne peuvent pas restituer de `<script>` balises.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-183">Components in Blazor, including pages, can't render `<script>` tags.</span></span> <span data-ttu-id="ba3a9-184">Cette restriction de rendu existe, car `<script>` les balises sont chargées une seule fois et ne peuvent pas être modifiées.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-184">This rendering restriction exists because `<script>` tags get loaded once and then can't be changed.</span></span> <span data-ttu-id="ba3a9-185">Un comportement inattendu peut se produire si vous essayez d’afficher dynamiquement les balises à l’aide de syntaxe Razor.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-185">Unexpected behavior may occur if you try to render the tags dynamically using Razor syntax.</span></span> <span data-ttu-id="ba3a9-186">Au lieu de cela, toutes les `<script>` balises doivent être ajoutées à la page hôte de l’application.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-186">Instead, all `<script>` tags should be added to the app's host page.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ba3a9-187">[Précédent](components.md) 
> [Suivant](state-management.md)</span><span class="sxs-lookup"><span data-stu-id="ba3a9-187">[Previous](components.md)
[Next](state-management.md)</span></span>
