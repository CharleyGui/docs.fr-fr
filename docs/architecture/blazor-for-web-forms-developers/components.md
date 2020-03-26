---
title: Construire des composants d’interface utilisateur réutilisables avec Blazor
description: Découvrez comment créer des composants d’interface utilisateur réutilisables avec Blazor et comment ils se comparent aux contrôles ASP.NET Web Forms.
author: danroth27
ms.author: daroth
ms.date: 09/18/2019
ms.openlocfilehash: 228f7aec4c7b87cb6d4127b55745f7a5ed90aaf9
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80228627"
---
# <a name="build-reusable-ui-components-with-blazor"></a>Construire des composants d’interface utilisateur réutilisables avec Blazor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Une des belles choses sur ASP.NET Web Forms est de savoir comment il permet l’encapsulation de morceaux réutilisables de code d’interface utilisateur (interface utilisateur) dans les contrôles réutilisables de l’interface utilisateur. Les contrôles personnalisés des utilisateurs peuvent être définis dans le balisage à l’aide de fichiers *.ascx.* Vous pouvez également créer des contrôles de serveur élaborés dans le code avec un support complet de concepteur.

Blazor prend également en charge l’encapsulation de l’interface utilisateur à travers *les composants*. Un composant :

- Est un morceau autonome de l’interface utilisateur.
- Maintient son propre état et rend la logique.
- Peut définir les gestionnaires d’événements d’interface utilisateur, se lier aux données d’entrée et gérer son propre cycle de vie.
- Est généralement défini dans un fichier *.razor* en utilisant la syntaxe Razor.

## <a name="an-introduction-to-razor"></a>Une introduction à Razor

Razor est un langage de température de balisage léger basé sur HTML et C. Avec Razor, vous pouvez passer en toute transparence entre le balisage et le code C pour définir votre logique de rendu des composants. Lorsque le fichier *.razor* est compilé, la logique de rendu est capturée d’une manière structurée dans une classe .NET. Le nom de la classe compilée est tiré du nom de fichier *.razor.* L’espace de nom est tiré de l’espace nom par défaut pour le projet `@namespace` et le chemin du dossier, ou vous pouvez spécifier explicitement l’espace de nom en utilisant la directive (plus sur les directives Razor ci-dessous).

La logique de rendu d’un composant est rédigée à l’aide d’une balisage HTML normal avec une logique dynamique ajoutée à l’aide de C. Le `@` personnage est utilisé pour passer à C. Razor est généralement intelligent au sujet de comprendre quand vous avez commuté de nouveau à HTML. Par exemple, le composant `<p>` suivant rend une balise avec l’heure actuelle :

```razor
<p>@DateTime.Now</p>
```

Pour spécifier explicitement le début et la fin d’une expression C, utilisez des parenthèses :

```razor
<p>@(DateTime.Now)</p>
```

Razor facilite également l’utilisation du flux de contrôle C DANS votre logique de rendu. Par exemple, vous pouvez rendre sous condition certains HTML comme ceci:

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

Ou vous pouvez générer une liste d’éléments à l’aide d’une boucle normale de C comme celle-ci `foreach` :

```razor
<ul>
@foreach (var item in items)
{
    <li>@item.Text</li>
}
</ul>
```

Les directives de rasoir, comme les directives dans ASP.NET formulaires Web, contrôlent de nombreux aspects de la façon dont un composant Razor est compilé. Voici quelques exemples :

- Espace de noms
- Classe de base
- Interfaces mises en œuvre
- Paramètres génériques
- Espaces de noms importés
- Itinéraires

Les directives de `@` rasoir commencent par le personnage et sont généralement utilisées au début d’une nouvelle ligne au début du fichier. Par exemple, `@namespace` la directive définit l’espace nom du composant :

```razor
@namespace MyComponentNamespace
```

Le tableau suivant résume les différentes directives Razor utilisées dans Blazor et leurs équivalents ASP.NET Web Forms, si elles existent.

|Directive    |Description|Exemple|Formulaires Web équivalents|
|-------------|-----------|-------|--------------------|
|`@attribute` |Ajoute un attribut de niveau de classe au composant|`@attribute [Authorize]`|None|
|`@code`      |Ajoute les membres de la classe à la composante|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|Implémente l’interface spécifiée|`@implements IDisposable`|Utiliser code-behind|
|`@inherits`  |Hérite de la classe de base spécifiée|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |Injecte un service dans le composant|`@inject IJSRuntime JS`|None|
|`@layout`    |Spécifie un composant de mise en page pour le composant|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |Définit l’espace de nom pour le composant|`@namespace MyNamespace`|None|
|`@page`      |Spécifie l’itinéraire du composant|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |Spécifie un paramètre de type générique pour le composant|`@typeparam TItem`|Utiliser code-behind|
|`@using`     |Spécifie un espace de nom à mettre en portée|`@using MyComponentNamespace`|Ajouter namespace dans *web.config*|

Les composants razor utilisent également largement les *attributs des directives* sur les éléments pour contrôler divers aspects de la façon dont les composants sont compilés (traitement des événements, liaison de données, composantes & références d’éléments, et ainsi de suite). Les attributs de directive suivent tous une syntaxe générique commune où les valeurs de la parenthèse sont facultatives :

```razor
@directive(-suffix(:name))(="value")
```

Le tableau suivant résume les différents attributs des directives Razor utilisées dans Blazor.

|Attribut    |Description|Exemple|
|-------------|-----------|-------|
|`@attributes`|Rend un dictionnaire d’attributs|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |Crée une liaison de données bidirectionnel    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |Ajoute un gestionnaire d’événements pour l’événement spécifié|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |Spécifie une clé à utiliser par l’algorithme de diffing pour préserver les éléments d’une collection|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |Capture une référence au composant ou à l’élément HTML|`<MyDialog @ref="myDialog" />`|

Les différents attributs de directive`@onclick`utilisés `@bind` `@ref`par Blazor ( , , , , et ainsi de suite) sont couverts dans les sections ci-dessous et les chapitres ultérieurs.

Beaucoup de syntaxes utilisées dans les fichiers *.aspx* et *.ascx* ont des syntaxes parallèles dans Razor. Voici une simple comparaison des syntaxes pour ASP.NET Web Forms et Razor.

|Fonctionnalité                      |Web Forms           |Syntaxe               |Razor         |Syntaxe |
|-----------------------------|--------------------|---------------------|--------------|-------|
|Directives                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|Blocs de code                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|Expressions<br>(HTML-encodé)|`<%: %>`            |`<%:DateTime.Now %>` |Implicite:`@`<br>Explicite:`@()`|`@DateTime.Now`<br>`@(DateTime.Now)`|
|Commentaires                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|Liaison de données                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

Pour ajouter des membres à la `@code` classe de composants Razor, utilisez la directive. Cette technique est similaire `<script runat="server">...</script>` à l’utilisation d’un bloc dans un ASP.NET Web Forms contrôle utilisateur ou page.

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

Parce que Razor est basé sur le C, il doit être compilé à partir d’un projet C (*.csproj*). Vous ne pouvez pas compiler des fichiers *.razor* à partir d’un projet Visual Basic (*.vbproj*). Vous pouvez toujours faire référence aux projets Visual Basic de votre projet Blazor. Le contraire est vrai aussi.

Pour une référence complète de syntaxe Razor, voir [référence de syntaxe Razor pour ASP.NET Core](/aspnet/core/mvc/views/razor).

## <a name="use-components"></a>Utiliser des composants

Mis à part HTML normal, les composants peuvent également utiliser d’autres composants dans le cadre de leur logique de rendu. La syntaxe pour l’utilisation d’un composant dans Razor est similaire à l’utilisation d’un contrôle utilisateur dans une application ASP.NET Web Forms. Les composants sont spécifiés à l’aide d’une étiquette d’élément qui correspond au nom type du composant. Par exemple, vous `Counter` pouvez ajouter un composant comme celui-ci :

```razor
<Counter />
```

Contrairement à ASP.NET Web Forms, composants de Blazor :

- N’utilisez pas de préfixe `asp:`d’élément (par exemple, ).
- N’exigez pas l’enregistrement sur la page ou sur le *web.config*.

Pensez à des composants Razor comme vous le feriez .NET types, parce que c’est exactement ce qu’ils sont. Si l’assemblage contenant le composant est référencé, le composant est disponible pour utilisation. Pour mettre en portée l’espace nom `@using` du composant, appliquez la directive :

```razor
@using MyComponentLib

<Counter />
```

Comme on le voit dans les projets Blazor par défaut, il est courant de mettre `@using` des directives dans un fichier *_Imports.razor* afin qu’ils soient importés dans tous les fichiers *.razor* dans le même répertoire et dans les annuaires pour enfants.

Si l’espace de nom d’un composant n’est pas de portée, vous pouvez spécifier un composant à l’aide de son nom de type complet, comme vous le pouvez dans C :

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a>Paramètres de composant

Dans ASP.NET formulaires Web, vous pouvez faire circuler des paramètres et des données pour contrôler l’utilisation des propriétés publiques. Ces propriétés peuvent être définies en balisage à l’aide d’attributs ou définies directement dans le code. Les composants Blazor fonctionnent de la même manière, bien `[Parameter]` que les propriétés des composants doivent également être marquées par l’attribut pour être considérées comme des paramètres de composant.

Le `Counter` composant suivant définit un `IncrementAmount` paramètre de composant appelé `Counter` qui peut être utilisé pour spécifier la quantité que le devrait être incrémenté chaque fois que le bouton est cliqué.

```razor
<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>

@code {
    int currentCount = 0;

    [Parameter]
    public int IncrementAmount { get; set; } = 1;

    void IncrementCount()
    {
        currentCount+=IncrementAmount;
    }
}
```

Pour spécifier un paramètre de composant dans Blazor, utilisez un attribut comme vous le feriez dans ASP.NET formulaires Web :

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a>Gestionnaires d’événements

ASP.NET Web Forms et Blazor fournissent un modèle de programmation basé sur les événements pour la gestion des événements d’assurance-chômage. Parmi les exemples de tels événements, mentionnons les clics sur les boutons et l’entrée de texte. Dans ASP.NET Web Forms, vous utilisez des commandes de serveur HTML pour gérer les événements d’interface utilisateur exposés par le DOM, ou vous pouvez gérer les événements exposés par les contrôles du serveur Web. Les événements sont mis en surface sur le serveur par le biais de demandes post-back de formulaire. Considérez l’exemple suivant du bouton Web Forms clic:

*Counter.ascx (en)*

```aspx-csharp
<asp:Button ID="ClickMeButton" runat="server" Text="Click me!" OnClick="ClickMeButton_Click" />
```

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void ClickMeButton_Click(object sender, EventArgs e)
    {
        Console.WriteLine("The button was clicked!");
    }
}
```

Dans Blazor, vous pouvez enregistrer les gestionnaires pour les événements `@on{event}`d’interface utilisateur DOM directement en utilisant des attributs de directive du formulaire . Le `{event}` propriétaire de la place représente le nom de l’événement. Par exemple, vous pouvez écouter des clics de boutons comme celui-ci :

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

Les gestionnaires d’événements peuvent accepter un argument facultatif et spécifique à un événement pour fournir plus d’information sur l’événement. Par exemple, les événements `MouseEventArgs` de souris peuvent prendre un argument, mais il n’est pas nécessaire.

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e)
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

Au lieu de se référer à un groupe de méthode pour un gestionnaire d’événements, vous pouvez utiliser une expression lambda. Une expression lambda vous permet de fermer sur d’autres valeurs de portée.

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

Les gestionnaires d’événements peuvent exécuter de façon synchrone ou asynchrone. Par exemple, `OnClick` le gestionnaire d’événements suivant exécute asynchrone :

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

Une fois qu’un événement est géré, le composant est rendu pour tenir compte de tout changement d’état de composant. Avec des gestionnaires d’événements asynchrones, le composant est rendu immédiatement après la fin de l’exécution du gestionnaire. Le composant est rendu *à nouveau* après `Task` les compléteurs asynchrones. Ce mode d’exécution asynchrone offre l’occasion de rendre une `Task` interface utilisateur appropriée alors que l’asynchrone est toujours en cours.

```razor
<button @onclick="ShowMessage">Get message</button>

@if (showMessage)
{
    @if (message == null)
    {
        <p><em>Loading...</em></p>
    }
    else
    {
        <p>The message is: @message</p>
    }
}

@code
{
    bool showMessage = false;
    string message;

    public async Task ShowMessage()
    {
        showMessage = true;
        message = await MessageService.GetMessageAsync();
    }
}
```

Les composants peuvent également définir leurs propres événements `EventCallback<TValue>`en définissant un paramètre de composant de type . Les rappels d’événements prennent en charge toutes les variantes des gestionnaires d’événements d’interface utilisateur de DOM : arguments optionnels, synchrones ou asynchrones, groupes de méthode, ou expressions lambda.

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a>Liaison de données

Blazor fournit un mécanisme simple pour lier les données d’un composant d’interface utilisateur à l’état du composant. Cette approche diffère des caractéristiques des formulaires Web ASP.NET pour les données contraignantes provenant des sources de données aux contrôles d’interface utilisateur. Nous couvrirons le traitement des données provenant de différentes sources de données dans la section [Traiter les données.](data.md)

Pour créer une liaison de données bidirectionnelles à partir `@bind` d’un composant d’interface utilisateur à l’état du composant, utilisez l’attribut de directive. Dans l’exemple suivant, la valeur de `isChecked` la case à cocher est liée au champ.

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

Lorsque le composant est rendu, la valeur de la case `isChecked` à cocher est définie à la valeur du champ. Lorsque l’utilisateur bascule la `onchange` case à cocher, l’événement est déclenché et le `isChecked` champ est réglé à la nouvelle valeur. La `@bind` syntaxe dans ce cas est équivalente à la majoration suivante :

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

Pour modifier l’événement utilisé pour `@bind:event` la liaison, utilisez l’attribut.

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

Les composants peuvent également prendre en charge la liaison des données à leurs paramètres. Pour lier les données, définissez un paramètre de rappel d’événements du même nom que le paramètre liant. Le suffixe "Changed" est ajouté au nom.

*PasswordBox.razor (en)*

```razor
Password: <input
    value="@Password"
    @oninput="OnPasswordChanged"
    type="@(showPassword ? "text" : "password")" />

<label><input type="checkbox" @bind="showPassword" />Show password</label>

@code {
    private bool showPassword;

    [Parameter]
    public string Password { get; set; }

    [Parameter]
    public EventCallback<string> PasswordChanged { get; set; }

    private Task OnPasswordChanged(ChangeEventArgs e)
    {
        Password = e.Value.ToString();
        return PasswordChanged.InvokeAsync(Password);
    }
}
```

Pour enchaîner une liaison de données à un élément d’interface utilisateur sous-jacent, définissez la valeur et gérez l’événement directement sur l’élément d’interface utilisateur au lieu d’utiliser l’attribut. `@bind`

Pour vous lier à `@bind-{Parameter}` un paramètre de composant, utilisez un attribut pour spécifier le paramètre auquel vous souhaitez lier.

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a>Changements d'état

Si l’état du composant a changé en dehors d’un événement normal d’interface utilisateur ou d’un rappel d’événement, alors le composant doit signaler manuellement qu’il doit être rendu à nouveau. Pour signaler que l’état d’un `StateHasChanged` composant a changé, appelez la méthode sur le composant.

Dans l’exemple ci-dessous, un `AppState` composant affiche un message à partir d’un service qui peut être mis à jour par d’autres parties de l’application. Le composant enregistre `StateHasChanged` sa `AppState.OnChange` méthode avec l’événement afin que le composant soit rendu chaque fois que le message est mis à jour.

```csharp
public class AppState
{
    public string Message { get; }

    // Lets components receive change notifications
    public event Action OnChange;

    public void UpdateMessage(string message)
    {
        shortlist.Add(itinerary);
        NotifyStateChanged();
    }

    private void NotifyStateChanged() => OnChange?.Invoke();
}
```

```razor
@inject AppState AppState

<p>App message: @AppState.Message</p>

@code {
    protected override void OnInitialized()
    {
        AppState.OnChange += StateHasChanged
    }
}
```

## <a name="component-lifecycle"></a>Cycle de vie des composants

Le cadre web ASP.NET formes a des méthodes de cycle de vie bien définies pour les modules, les pages et les contrôles. Par exemple, le contrôle suivant met `Init`en `Load`œuvre les gestionnaires d’événements pour les événements , , et `UnLoad` le cycle de vie :

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

Les composants Blazor ont également un cycle de vie bien défini. Le cycle de vie d’un composant peut être utilisé pour initialiser l’état des composants et mettre en œuvre des comportements de composants avancés.

Toutes les méthodes du cycle de vie des composants de Blazor ont des versions synchrones et asynchrones. Le rendu des composants est synchrone. Vous ne pouvez pas exécuter la logique asynchrone dans le cadre du rendu composant. Toute logique asynchrone doit s’exécuter dans le cadre d’une `async` méthode de cycle de vie.

### <a name="oninitialized"></a>SurInitialized

Les `OnInitialized` `OnInitializedAsync` méthodes et les méthodes sont utilisées pour initialiser le composant. Un composant est généralement paradés après sa première remise. Une fois qu’un composant est paralé, il peut être rendu plusieurs fois avant qu’il ne soit finalement éliminé. La `OnInitialized` méthode est `Page_Load` similaire à l’événement dans ASP.NET pages et contrôles Web Forms.

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a>OnParametersSet

Les `OnParametersSet` `OnParametersSetAsync` méthodes et les méthodes sont appelées lorsqu’un composant a reçu des paramètres de son parent et que la valeur est attribuée aux propriétés. Ces méthodes sont exécutées après l’initialisation des composants et *chaque fois que le composant est rendu.*

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a>SurAfterRender

Les `OnAfterRender` `OnAfterRenderAsync` méthodes et les méthodes sont appelées après qu’un composant a terminé le rendu. Les références d’éléments et de composants sont peuplées à ce stade (plus sur ces concepts ci-dessous). L’interactivité avec le navigateur est activée à ce stade. Les interactions avec l’exécution DOM et JavaScript peuvent avoir lieu en toute sécurité.

```csharp
protected override void OnAfterRender(bool firstRender)
{
    if (firstRender)
    {
        ...
    }
}
protected override async Task OnAfterRenderAsync(bool firstRender)
{
    if (firstRender)
    {
        await ...
    }
}
```

`OnAfterRender`et `OnAfterRenderAsync` *ne sont pas appelés lors du prerendering sur le serveur*.

Le `firstRender` paramètre est `true` la première fois que le composant est rendu; sinon, sa `false`valeur est .

### <a name="idisposable"></a>IDisposable

Les composants Blazor `IDisposable` peuvent implémenter les ressources lorsque le composant est retiré de l’interface utilisateur. Un composant Razor `IDispose` peut `@implements` être mis en œuvre à l’aide de la directive :

```razor
@using System
@implements IDisposable

...

@code {
    public void Dispose()
    {
        ...
    }
}
```

## <a name="capture-component-references"></a>Capturez les références des composants

Dans ASP.NET Web Forms, il est courant de manipuler une instance de contrôle directement dans le code en se référant à son ID. Dans Blazor, il est également possible de capturer et de manipuler une référence à un composant, bien qu’il soit beaucoup moins fréquent.

Pour saisir une référence de composant `@ref` dans Blazor, utilisez l’attribut de la directive. La valeur de l’attribut doit correspondre au nom d’un champ défini avec le même type que le composant référencé.

```razor
<MyLoginDialog @ref="loginDialog" ... />

@code {
    MyLoginDialog loginDialog;

    void OnSomething()
    {
        loginDialog.Show();
    }
}
```

Lorsque la composante parente est rendue, le champ est peuplé avec l’instance de composant de l’enfant. Vous pouvez ensuite appeler des méthodes sur, ou manipuler autrement, l’instance du composant.

Il n’est pas recommandé de manipuler directement l’état des composants à l’aide de références de composants. Cela empêche le composant d’être rendu automatiquement aux bons moments.

## <a name="capture-element-references"></a>Références d’élément de capture

Les composants Blazor peuvent capturer des références à un élément. Contrairement aux commandes de serveur HTML dans ASP.NET formulaires Web, vous ne pouvez pas manipuler directement le DOM à l’aide d’une référence d’élément dans Blazor. Blazor gère la plupart des interactions DOM pour vous en utilisant son algorithme de diffing DOM. Les références d’éléments capturés dans Blazor sont opaques. Cependant, ils sont utilisés pour passer une référence d’élément spécifique dans un appel interop JavaScript. Pour plus d’informations sur JavaScript interop, voir [ASP.NET Core Blazor JavaScript interop](/aspnet/core/blazor/javascript-interop).

## <a name="templated-components"></a>Composants basés sur un modèle

Dans ASP.NET formulaires Web, vous pouvez créer *des contrôles modélistes*. Les contrôles modélistes permettent au développeur de spécifier une partie du HTML utilisé pour rendre un contrôle des conteneurs. La mécanique de la construction des contrôles de serveur modéliques sont complexes, mais ils permettent des scénarios puissants pour rendre les données d’une manière personnalisable de l’utilisateur. Des exemples de `Repeater` `DataList`contrôles modélistes incluent et .

Les composants Blazor peuvent également être modélés `RenderFragment` `RenderFragment<T>`en définissant les paramètres des composants de type ou . A `RenderFragment` représente un morceau de marge Razor qui peut ensuite être rendu par le composant. A `RenderFragment<T>` est un morceau de markup Razor qui prend un paramètre qui peut être spécifié lorsque le fragment de rendu est rendu.

### <a name="child-content"></a>Contenu pour enfants

Les composants Blazor peuvent capturer `RenderFragment` leur contenu enfant comme un et le rendre dans le cadre du rendu composant. Pour capturer le contenu de l’enfant, définissez un paramètre de composant du type `RenderFragment` et nommez-le `ChildContent`.

*ChildContentComponent.razor*

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

Un composant parent peut ensuite fournir du contenu pour enfants à l’aide d’une syntaxe Razor normale.

```razor
<ChildContentComponent>
    <p>The time is @DateTime.Now</p>
</ChildContentComponent>
```

### <a name="template-parameters"></a>Paramètres de modèle

Un composant Blazor modélisateur peut également `RenderFragment` définir `RenderFragment<T>`plusieurs paramètres de composants de type ou . Le paramètre `RenderFragment<T>` d’un peut être spécifié lorsqu’il est invoqué. Pour spécifier un paramètre `@typeparam` de type générique pour un composant, utilisez la directive Razor.

*SimpleListView.razor*

```razor
@typeparam TItem

@Heading

<ul>
@foreach (var item in Items)
{
    <li>@ItemTemplate(item)</li>
}
</ul>

@code {
    [Parameter]
    public RenderFragment Heading { get; set; }

    [Parameter]
    public RenderFragment<TItem> ItemTemplate { get; set; }

    [Parameter]
    public IEnumerable<TItem> Items { get; set; }
}
```

Lors de l’utilisation d’un composant modélé, les paramètres du modèle peuvent être spécifiés à l’aide d’éléments pour enfants qui correspondent aux noms des paramètres. Les arguments `RenderFragment<T>` de composants de type `context`adoptés comme éléments ont un paramètre implicite nommé . Vous pouvez modifier le nom de `Context` ce paramètre d’implémentaire en utilisant l’attribut sur l’élément enfant. Tous les paramètres de type générique peuvent être spécifiés à l’aide d’un attribut qui correspond au nom du paramètre de type. Le paramètre de type sera déduit si possible :

```razor
<SimpleListView Items="messages" TItem="string">
    <Heading>
        <h1>My list</h1>
    </Heading>
    <ItemTemplate Content="message">
        <p>The message is: @message</p>
    </ItemTemplate>
</SimpleListView>
```

La sortie de ce composant ressemble à ceci :

```html
<h1>My list</h1>
<ul>
    <li>The message is: message1</li>
    <li>The message is: message2</li>
<ul>
```

## <a name="code-behind"></a>Code-behind

Un composant Blazor est généralement écrit dans un seul fichier *.razor.* Cependant, il est également possible de séparer le code et le balisage à l’aide d’un fichier de code.derrière. Pour utiliser un fichier de composants, ajoutez un fichier CMD qui correspond au nom de fichier du fichier des composants, mais avec une extension *.cs* ajoutée *(Counter.razor.cs*). Utilisez le fichier C pour définir une classe de base pour le composant. Vous pouvez nommer la classe de base tout ce que vous souhaitez, mais il est `Base` courant de`CounterBase`nommer la classe la même que la classe des composants, mais avec une extension ajoutée ( ). La classe basée sur les `ComponentBase`composants doit également dériver de . Ensuite, dans le fichier du `@inherits` composant Razor, ajouter la`@inherits CounterBase`directive pour spécifier la classe de base pour le composant ().

*Counter.razor (en)*

```razor
@inherits CounterBase

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>
```

*Counter.razor.cs*

```csharp
public class CounterBase : ComponentBase
{
    protected int currentCount = 0;

    protected void IncrementCount()
    {
        currentCount++;
    }
}
```

La visibilité des membres du composant dans `protected` la `public` classe de base doit être ou être visible par la classe des composants.

## <a name="additional-resources"></a>Ressources supplémentaires

Le précédent n’est pas un traitement exhaustif de tous les aspects des composants Blazor. Pour plus d’informations sur la façon de [créer et d’utiliser ASP.NET composants Core Razor](/aspnet/core/blazor/components), voir la documentation Blazor.

>[!div class="step-by-step"]
>[Suivant précédent](app-startup.md)
>[Next](pages-routing-layouts.md)
