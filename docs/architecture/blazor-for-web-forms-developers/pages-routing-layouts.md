---
title: Pages, routage et dispositions
description: Apprenez à créer des pages dans éblouissant, à travailler avec le routage côté client et à gérer les mises en page.
author: danroth27
ms.author: daroth
ms.date: 09/19/2019
ms.openlocfilehash: 693eee270a46ccb56ed5fef8fced1d4a1cf1974f
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72520232"
---
# <a name="pages-routing-and-layouts"></a>Pages, routage et dispositions

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

ASP.NET Web Forms applications sont composées de pages définies dans des fichiers *. aspx* . L’adresse de chaque page est basée sur son chemin d’accès physique au projet. Quand un navigateur envoie une requête à la page, le contenu de la page est rendu dynamiquement sur le serveur. Les comptes de rendu pour le balisage HTML de la page et ses contrôles serveur.

Dans éblouissant, chaque page de l’application est un composant, généralement défini dans un fichier *. Razor* , avec un ou plusieurs itinéraires spécifiés. Le routage s’effectue principalement côté client sans impliquer de demande de serveur spécifique. Le navigateur effectue d’abord une demande à l’adresse racine de l’application. Un composant `Router` racine de l’application éblouissant gère alors l’interception des requêtes de navigation et les demandes de navigation vers le composant approprié.

Éblouissant prend également en charge la *liaison profonde*. La liaison profonde se produit lorsque le navigateur envoie une requête à un itinéraire spécifique autre que la racine de l’application. Les demandes de liens ciblés envoyés vers le serveur sont acheminées vers l’application éblouissante, qui achemine ensuite la demande côté client vers le composant approprié.

Une page simple dans ASP.NET Web Forms peut contenir le balisage suivant :

*Nom. aspx*

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

*Name.aspx.cs*

```csharp
public partial class Name : System.Web.UI.Page
{
    protected void Button1_Click1(object sender, EventArgs e)
    {
        Literal1.Text = "Hello " + TextBox1.Text;
    }
}
```

La page équivalente dans une application éblouissante ressemble à ceci :

*Name. Razor*

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

## <a name="create-pages"></a>Créer des pages

Pour créer une page dans éblouissant, créez un composant et ajoutez la `@page` directive Razor pour spécifier l’itinéraire du composant. La directive `@page` accepte un seul paramètre, qui est le modèle de routage à ajouter à ce composant.

```razor
@page "/counter"
```

Le paramètre de modèle de routage est obligatoire. Contrairement à ASP.NET Web Forms, l’itinéraire vers un composant éblouissant *n’est pas* déduit de son emplacement de fichier (bien que cela puisse être une fonctionnalité ajoutée à l’avenir).

La syntaxe de modèle de routage est identique à la syntaxe de base utilisée pour le routage dans ASP.NET Web Forms. Les paramètres de routage sont spécifiés dans le modèle à l’aide d’accolades. Éblouissant lie les valeurs de l’itinéraire aux paramètres du composant portant le même nom (non-respect de la casse).

```razor
@page "/product/{id}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public string Id { get; set; }
}
```

Vous pouvez également spécifier des contraintes sur la valeur du paramètre d’itinéraire. Par exemple, pour contraindre l’ID de produit en tant que `int`:

```razor
@page "/product/{id:int}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public int Id { get; set; }
}
```

Pour obtenir la liste complète des contraintes d’itinéraire prises en charge par éblouissant, consultez [contraintes de routage](/aspnet/core/blazor/routing#route-constraints).

## <a name="router-component"></a>Composant routeur

Le routage dans éblouissant est géré par le composant `Router`. Le composant `Router` est généralement utilisé dans le composant racine de l’application (*app. Razor*).

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

Le composant `Router` Découvre les composants routables dans le `AppAssembly` spécifié et dans la `AdditionalAssemblies`éventuellement spécifiée. Lorsque le navigateur navigue, le `Router` intercepte la navigation et restitue le contenu de son paramètre `Found` avec le `RouteData` extrait si un itinéraire correspond à l’adresse, sinon le `Router` restitue son paramètre `NotFound`.

Le composant `RouteView` gère le rendu du composant correspondant spécifié par la `RouteData` avec sa disposition, le cas échéant. Si le composant correspondant n’a pas de disposition, la `DefaultLayout` éventuellement spécifiée est utilisée.

Le composant `LayoutView` restitue son contenu enfant dans la disposition spécifiée. Nous étudierons plus en détail les dispositions plus loin dans ce chapitre.

## <a name="navigation"></a>Navigation

Dans ASP.NET Web Forms, vous déclenchez la navigation vers une page différente en renvoyant une réponse de redirection au navigateur. Par exemple :

```csharp
protected void NavigateButton_Click(object sender, EventArgs e)
{
    Response.Redirect("Counter");
}
```

Le retour d’une réponse de redirection n’est généralement pas possible dans éblouissant. Éblouissant n’utilise pas de modèle de demande-réponse. Toutefois, vous pouvez déclencher des navigations de navigateur directement, comme vous pouvez le faire avec JavaScript.

Éblouissant fournit un service `NavigationManager` qui peut être utilisé pour :

- Récupérer l’adresse actuelle du navigateur
- Obtient l’adresse de base
- Navigations de déclencheur
- Recevoir une notification lorsque l’adresse change

Pour accéder à une autre adresse, utilisez la méthode `NavigateTo` :

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

Pour obtenir une description de tous les membres de `NavigationManager`, consultez [URI et assistance de l’état de navigation](/aspnet/core/blazor/routing#uri-and-navigation-state-helpers).

## <a name="base-urls"></a>URL de base

Si votre application éblouissant est déployée sous un chemin d’accès de base, vous devez spécifier l’URL de base dans les métadonnées de la page à l’aide de la balise `<base>` pour le routage vers la propriété de travail. Si la page hôte de l’application est affichée par le serveur à l’aide de Razor, vous pouvez utiliser la syntaxe `~/` pour spécifier l’adresse de base de l’application. Si la page hôte est du code HTML statique, vous devez spécifier l’URL de base explicitement.

```html
<base href="~/" />
```

## <a name="page-layout"></a>Mise en page

La mise en page dans ASP.NET Web Forms est gérée par les pages maîtres. Les pages maîtres définissent un modèle avec un ou plusieurs espaces réservés de contenu qui peuvent ensuite être fournis par des pages individuelles. Les pages maîtres sont définies dans les fichiers *. Master* et commencent avec la directive `<%@ Master %>`. Le contenu des fichiers *. Master* est codé comme s’il s’agissait d’une page *. aspx* , mais avec l’ajout de `<asp:ContentPlaceHolder>` contrôles pour marquer l’emplacement où les pages peuvent fournir du contenu.

*Site. Master*

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

Dans éblouissant, vous gérez la mise en page à l’aide de composants de disposition. Les composants de disposition héritent de `LayoutComponentBase`, qui définit une seule `Body` propriété de type `RenderFragment`, qui peut être utilisée pour afficher le contenu de la page.

*MainLayout. Razor*

```razor
@inherits LayoutComponentBase
<h1>Main layout</h1>
<div>
    @Body
</div>
```

Lors du rendu de la page avec une disposition, la page est rendue dans le contenu de la disposition spécifiée à l’emplacement où la disposition affiche sa propriété `Body`.

Pour appliquer une disposition à une page, utilisez la directive `@layout` :

```razor
@layout MainLayout
```

Vous pouvez spécifier la disposition de tous les composants d’un dossier et de ses sous-dossiers à l’aide d’un fichier *_Imports. Razor* . Vous pouvez également spécifier une disposition par défaut pour toutes vos pages à l’aide du [composant routeur](#router-component).

Les pages maîtres peuvent définir plusieurs espaces réservés de contenu, mais les dispositions dans éblouissantes n’ont qu’une seule `Body` propriété. Cette limitation des composants de la disposition éblouissante sera prévue dans une prochaine version.

Les pages maîtres dans ASP.NET Web Forms peuvent être imbriquées. Autrement dit, une page maître peut également utiliser une page maître. Les composants de disposition dans éblouissant peuvent également être imbriqués. Vous pouvez appliquer un composant de disposition à un composant de disposition. Le contenu de la disposition interne sera rendu dans la disposition externe.

*ChildLayout. Razor*

```razor
@layout MainLayout
<h2>Child layout</h2>
<div>
    @Body
</div>
```

*Index. Razor*

```razor
@page "/"
@layout ChildLayout
<p>I'm in a nested layout!</p>
```

La sortie rendue pour la page serait alors :

```html
<h1>Main layout</h1>
<div>
    <h2>Child layout</h2>
    <div>
        <p>I'm in a nested layout!</p>
    </div>
</div>
```

Dans éblouissant, les dispositions ne définissent généralement pas les éléments HTML racine d’une page (`<html>`, `<body>`, `<head>`, etc.). Les éléments HTML racine sont définis à la place dans la page hôte d’une application éblouissante, qui est utilisée pour afficher le contenu HTML initial de l’application (consultez [amorçage éblouissant](project-structure.md#bootstrap-blazor)). La page hôte peut afficher plusieurs composants racine pour l’application avec le balisage environnant.

Les composants de éblouissant, y compris les pages, ne peuvent pas restituer les balises `<script>`. Cette restriction de rendu existe, car les balises `<script>` sont chargées une seule fois et ne peuvent pas être modifiées. Un comportement inattendu peut se produire si vous essayez d’afficher dynamiquement les balises à l’aide de syntaxe Razor. Au lieu de cela, toutes les balises `<script>` doivent être ajoutées à la page hôte de l’application.

>[!div class="step-by-step"]
>[Précédent](components.md)
>[Suivant](state-management.md)
