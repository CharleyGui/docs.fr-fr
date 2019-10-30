---
title: Créer des composants d’interface utilisateur réutilisables avec éblouissant
description: Découvrez comment créer des composants d’interface utilisateur réutilisables avec éblouissant et comment ils sont comparés aux contrôles ASP.NET Web Forms.
author: danroth27
ms.author: daroth
ms.date: 09/18/2019
ms.openlocfilehash: 79919b183a4eb759f0b27c97500ee71c9378770b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088101"
---
# <a name="build-reusable-ui-components-with-blazor"></a>Créer des composants d’interface utilisateur réutilisables avec éblouissant

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

L’une des merveilles de ASP.NET Web Forms est la façon dont il permet l’encapsulation de parties réutilisables de code d’interface utilisateur dans des contrôles d’interface utilisateur réutilisables. Les contrôles utilisateur personnalisés peuvent être définis dans le balisage à l’aide de fichiers *. ascx* . Vous pouvez également créer des contrôles serveur élaborés dans du code avec une prise en charge de concepteur complète.

Éblouissant prend également en charge l’encapsulation de l’interface utilisateur par le biais de *composants*. Un composant :

- Est un bloc d’interface utilisateur autonome.
- Conserve son propre État et sa logique de rendu.
- Peut définir des gestionnaires d’événements d’interface utilisateur, les lier aux données d’entrée et gérer leur propre cycle de vie.
- Est généralement défini dans un fichier *. Razor* à l’aide de syntaxe Razor.

## <a name="an-introduction-to-razor"></a>Présentation de Razor

Razor est un langage de création de balises léger basé sur HTML C#et. Avec Razor, vous pouvez effectuer une transition transparente entre le C# balisage et le code pour définir la logique de rendu de votre composant. Quand le fichier *. Razor* est compilé, la logique de rendu est capturée de manière structurée dans une classe .net. Le nom de la classe compilée est extrait du nom de fichier *. Razor* . L’espace de noms est extrait de l’espace de noms par défaut du projet et du chemin d’accès au dossier, ou vous pouvez spécifier explicitement l’espace de noms à l’aide de la directive `@namespace` (plus d’informations sur les directives Razor ci-dessous).

La logique de rendu d’un composant est créée à l’aide d’un balisage HTML C#normal avec la logique dynamique ajoutée à l’aide de. Le caractère `@` est utilisé pour effectuer la C#transition vers. Razor est en général intelligent de déterminer quand vous avez rétabli en HTML. Par exemple, le composant suivant effectue le rendu d’une balise `<p>` avec l’heure actuelle :

```razor
<p>@DateTime.Now</p>
```

Pour spécifier explicitement le début et la fin d' C# une expression, utilisez des parenthèses :

```razor
<p>@(DateTime.Now)</p>
```

Razor facilite également l’utilisation C# du workflow de contrôle dans votre logique de rendu. Par exemple, vous pouvez restituer de façon conditionnelle du code HTML comme suit :

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

Ou vous pouvez générer une liste d’éléments à l’aide C# d’une boucle de `foreach` normale comme suit :

```razor
<ul>
@foreach (var item in items)
{
    <li>item.Text</li>
}
</ul>
```

Les directives Razor, comme les directives dans ASP.NET Web Forms, contrôlent de nombreux aspects de la compilation d’un composant Razor. Voici quelques exemples :

- Espace de noms
- Classe de base
- Interfaces implémentées
- Paramètres génériques
- Espaces de noms importés
- Routes

Les directives Razor commencent par le caractère `@` et sont généralement utilisées au début d’une nouvelle ligne au début du fichier. Par exemple, la directive `@namespace` définit l’espace de noms du composant :

```razor
@namespace MyComponentNamespace
```

Le tableau suivant récapitule les différentes directives Razor utilisées dans éblouissant et leurs ASP.NET Web Forms équivalents, s’ils existent.

|Directive    |Description|Exemple|Équivalent Web Forms|
|-------------|-----------|-------|--------------------|
|`@attribute` |Ajoute un attribut de niveau classe au composant.|`@attribute [Authorize]`|aucune.|
|`@code`      |Ajoute des membres de classe au composant|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|Implémente l’interface spécifiée|`@implements IDisposable`|Utiliser du code-behind|
|`@inherits`  |Hérite de la classe de base spécifiée|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |Injecte un service dans le composant.|`@inject IJSRuntime JS`|aucune.|
|`@layout`    |Spécifie un composant de disposition pour le composant|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |Définit l’espace de noms pour le composant|`@namespace MyNamespace`|aucune.|
|`@page`      |Spécifie l’itinéraire pour le composant|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |Spécifie un paramètre de type générique pour le composant|`@typeparam TItem`|Utiliser du code-behind|
|`@using`     |Spécifie un espace de noms à placer dans la portée|`@using MyComponentNamespace`|Ajouter un espace de noms dans *Web. config*|

Les composants Razor utilisent également de manière intensive les *attributs de directive* sur les éléments pour contrôler différents aspects de la compilation des composants (gestion des événements, liaison de données, composants & références d’éléments, etc.). Les attributs de directive suivent une syntaxe générique commune dans laquelle les valeurs entre parenthèses sont facultatives :

```razor
@directive(-suffix(:name))(="value")
```

Le tableau suivant résume les différents attributs des directives Razor utilisées dans éblouissant.

|Attribut    |Description|Exemple|
|-------------|-----------|-------|
|`@attributes`|Génère le rendu d’un dictionnaire d’attributs|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |Crée une liaison de données bidirectionnelle    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |Ajoute un gestionnaire d’événements pour l’événement spécifié.|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |Spécifie une clé à utiliser par l’algorithme de comparaison pour conserver les éléments d’une collection|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |Capture une référence au composant ou à l’élément HTML|`<MyDialog @ref="myDialog" />`|

Les différents attributs de directive utilisés par éblouissant (`@onclick`, `@bind`, `@ref`, etc.) sont traités dans les sections ci-dessous et les chapitres ultérieurs.

La plupart des syntaxes utilisées dans les fichiers *. aspx* et *. ascx* ont des syntaxes parallèles dans Razor. Vous trouverez ci-dessous une comparaison simple des syntaxes pour ASP.NET Web Forms et Razor.

|Fonction                      |Web Forms           |Syntaxe               |Razor         |Syntaxe |
|-----------------------------|--------------------|---------------------|--------------|-------|
|Directives                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|Blocs de code                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|Expressions<br>(Encodé en HTML)|`<%: %>`            |`<%:DateTime.Now %>` |Implicite : `@`<br>Explicite : `@()`|`@DateTime.Now`<br>`@(DateTime.Now)`|
|Comments                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|Liaison de données                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

Pour ajouter des membres à la classe de composant Razor, utilisez la directive `@code`. Cette technique est similaire à l’utilisation d’un bloc `<script runat="server">...</script>` dans un contrôle utilisateur ou une page ASP.NET Web Forms.

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

Comme Razor est basé sur C#, il doit être compilé à partir d' C# un projet ( *. csproj*). Vous ne pouvez pas compiler de fichiers *. Razor* à partir d’un projet VB ( *. vbproj*). Vous pouvez toujours référencer des projets VB à partir de votre projet éblouissant. L’inverse est également vrai.

Pour obtenir une référence complète syntaxe Razor, consultez [syntaxe Razor référence pour ASP.net Core](/aspnet/core/mvc/views/razor).

## <a name="use-components"></a>Utiliser des composants

Hormis le code HTML normal, les composants peuvent également utiliser d’autres composants dans le cadre de leur logique de rendu. La syntaxe d’utilisation d’un composant dans Razor est semblable à l’utilisation d’un contrôle utilisateur dans une application ASP.NET Web Forms. Les composants sont spécifiés à l’aide d’une balise d’élément qui correspond au nom de type du composant. Par exemple, vous pouvez ajouter un composant `Counter` comme suit :

```razor
<Counter />
```

Contrairement à ASP.NET Web Forms, les composants de éblouissant :

- N’utilisez pas de préfixe d’élément (par exemple, `asp:`).
- Ne nécessite pas d’inscription sur la page ou dans le *fichier Web. config*.

Considérez les composants Razor comme des types .NET, car c’est exactement ce qu’ils sont. Si l’assembly contenant le composant est référencé, le composant peut être utilisé. Pour mettre l’espace de noms du composant dans la portée, appliquez la directive `@using` :

```razor
@using MyComponentLib

<Counter />
```

Comme indiqué dans les projets éblouissants par défaut, il est courant de placer les directives `@using` dans un fichier *_Imports. Razor* afin qu’elles soient importées dans tous les fichiers *. Razor* dans le même répertoire et dans les répertoires enfants.

Si l’espace de noms d’un composant n’est pas dans l’étendue, vous pouvez spécifier un composant à l’aide de son C#nom de type complet, comme vous pouvez le faire dans :

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a>Paramètres de composant

Dans ASP.NET Web Forms, vous pouvez transmettre des paramètres et des données à des contrôles à l’aide de propriétés publiques. Ces propriétés peuvent être définies dans le balisage à l’aide d’attributs ou d’une valeur directement dans le code. Les composants éblouissant fonctionnent de manière similaire, bien que les propriétés des composants doivent également être marquées avec l’attribut `[Parameter]` pour être considérées comme des paramètres de composant.

Le composant `Counter` suivant définit un paramètre de composant appelé `IncrementAmount` qui peut être utilisé pour spécifier la quantité d’incrémentation de la `Counter` à chaque clic sur le bouton.

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

Pour spécifier un paramètre de composant dans éblouissant, utilisez un attribut comme vous le feriez dans ASP.NET Web Forms :

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a>Gestionnaires d’événements

ASP.NET Web Forms et éblouissant fournissent un modèle de programmation basé sur les événements pour gérer les événements d’interface utilisateur. Les clics de bouton et l’entrée de texte sont des exemples de tels événements. Dans ASP.NET Web Forms, vous utilisez des contrôles serveur HTML pour gérer les événements d’interface utilisateur exposés par le DOM ou vous pouvez gérer les événements exposés par les contrôles serveur Web. Les événements sont exposés sur le serveur via des demandes de publication de formulaire. Prenons l’exemple de clic de bouton Web Forms suivant :

*Counter. ascx*

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

Dans éblouissant, vous pouvez inscrire des gestionnaires pour les événements de l’interface utilisateur DOM directement à l’aide des attributs de directive de la forme `@on{event}`. L’espace réservé `{event}` représente le nom de l’événement. Par exemple, vous pouvez écouter les clics de bouton comme suit :

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

Les gestionnaires d’événements peuvent accepter un argument facultatif spécifique à l’événement pour fournir plus d’informations sur l’événement. Par exemple, les événements de souris peuvent prendre un argument `MouseEventArgs`, mais ce n’est pas obligatoire.

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e)
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

Au lieu de faire référence à un groupe de méthodes pour un gestionnaire d’événements, vous pouvez utiliser une expression lambda. Une expression lambda vous permet de fermer d’autres valeurs dans la portée.

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

Les gestionnaires d’événements peuvent s’exécuter de façon synchrone ou asynchrone. Par exemple, le gestionnaire d’événements `OnClick` suivant s’exécute de façon asynchrone :

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

Une fois qu’un événement est géré, le composant est rendu pour tenir compte des modifications d’état des composants. Avec les gestionnaires d’événements asynchrones, le composant est rendu immédiatement après la fin de l’exécution du gestionnaire. Le composant est *à nouveau* rendu une fois l' `Task` asynchrone terminée. Ce mode d’exécution asynchrone offre la possibilité d’afficher une interface utilisateur appropriée pendant que l' `Task` asynchrone est toujours en cours.

```razor
<button @onclick="Get message">Get message</button>

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

Les composants peuvent également définir leurs propres événements en définissant un paramètre de composant de type `EventCallback<TValue>`. Les rappels d’événements prennent en charge toutes les variations des gestionnaires d’événements de l’interface utilisateur DOM : des arguments facultatifs, synchrones ou asynchrones, des groupes de méthodes ou des expressions lambda.

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a>Liaison de données

Éblouissant fournit un mécanisme simple pour lier les données d’un composant de l’interface utilisateur à l’état du composant. Cette approche diffère des fonctionnalités de ASP.NET Web Forms pour la liaison de données de sources de données à des contrôles d’interface utilisateur. Nous traiterons de la gestion des données de différentes sources de données dans la section relative [aux données](data.md) .

Pour créer une liaison de données bidirectionnelle entre un composant de l’interface utilisateur et l’état du composant, utilisez l’attribut `@bind` directive. Dans l’exemple suivant, la valeur de la case à cocher est liée au champ `isChecked`.

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

Lorsque le composant est rendu, la valeur de la case à cocher est définie sur la valeur du champ `isChecked`. Lorsque l’utilisateur active ou désactive la case à cocher, l’événement `onchange` est déclenché et le champ `isChecked` est défini sur la nouvelle valeur. Dans ce cas, la syntaxe de `@bind` est équivalente à la balise suivante :

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

Pour modifier l’événement utilisé pour la liaison, utilisez l’attribut `@bind:event`.

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

Les composants peuvent également prendre en charge la liaison de données à leurs paramètres. Pour la liaison de données, définissez un paramètre de rappel d’événement portant le même nom que le paramètre pouvant être lié. Le suffixe « modifié » est ajouté au nom.

*PasswordBox. Razor*

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

Pour chaîner une liaison de données à un élément d’interface utilisateur sous-jacent, définissez la valeur et gérez l’événement directement sur l’élément d’interface utilisateur au lieu d’utiliser l’attribut `@bind`.

Pour établir une liaison avec un paramètre de composant, utilisez un attribut `@bind-{Parameter}` pour spécifier le paramètre à lier.

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a>Modification de l'état

Si l’état du composant a été modifié en dehors d’un événement d’interface utilisateur normal ou d’un rappel d’événement, le composant doit indiquer manuellement qu’il doit être de nouveau restitué. Pour signaler que l’état d’un composant a changé, appelez la méthode `StateHasChanged` sur le composant.

Dans l’exemple ci-dessous, un composant affiche un message d’un service `AppState` qui peut être mis à jour par d’autres parties de l’application. Le composant inscrit sa méthode `StateHasChanged` avec l’événement `AppState.OnChange` afin que le composant soit rendu chaque fois que le message est mis à jour.

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

ASP.NET Web Forms Framework a des méthodes de cycle de vie bien définies pour les modules, les pages et les contrôles. Par exemple, le contrôle suivant implémente des gestionnaires d’événements pour les événements de cycle de vie `Init`, `Load` et `UnLoad` :

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

Les composants éblouissants disposent également d’un cycle de vie bien défini. Le cycle de vie d’un composant peut être utilisé pour initialiser l’état d’un composant et implémenter des comportements de composant avancés.

Toutes les méthodes de cycle de vie des composants de éblouissant ont des versions synchrones et asynchrones. Le rendu des composants est synchrone. Vous ne pouvez pas exécuter une logique asynchrone dans le cadre du rendu des composants. Toute la logique asynchrone doit s’exécuter dans le cadre d’une méthode de cycle de vie `async`.

### <a name="oninitialized"></a>OnInitialized

Les méthodes `OnInitialized` et `OnInitializedAsync` sont utilisées pour initialiser le composant. Un composant est généralement initialisé après son premier rendu. Une fois qu’un composant a été initialisé, il peut être restitué plusieurs fois avant d’être supprimé. La méthode `OnInitialized` est semblable à l’événement `Page_Load` dans ASP.NET Web Forms pages et les contrôles.

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a>OnParametersSet

Les méthodes `OnParametersSet` et `OnParametersSetAsync` sont appelées lorsqu’un composant a reçu des paramètres de son parent et que la valeur est assignée aux propriétés. Ces méthodes sont exécutées après l’initialisation du composant et *chaque fois que le composant est rendu*.

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a>OnAfterRender

Les méthodes `OnAfterRender` et `OnAfterRenderAsync` sont appelées après la fin du rendu d’un composant. Les références à un élément et à un composant sont remplies à ce stade (en savoir plus sur ces concepts ci-dessous). L’interactivité avec le navigateur est activée à ce stade. Les interactions avec l’exécution DOM et JavaScript peuvent être effectuées en toute sécurité.

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

`OnAfterRender` et `OnAfterRenderAsync` *ne sont pas appelées lors du prérendu sur le serveur*.

Le paramètre `firstRender` est `true` la première fois que le composant est restitué. dans le cas contraire, sa valeur est `false`.

### <a name="idisposable"></a>IDisposable

Les composants éblouissants peuvent implémenter `IDisposable` pour supprimer des ressources lorsque le composant est supprimé de l’interface utilisateur. Un composant Razor peut implémenter `IDispose` à l’aide de la directive `@implements` :

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

## <a name="capture-component-references"></a>Références du composant de capture

Dans ASP.NET Web Forms, il est courant de manipuler une instance de contrôle directement dans le code en faisant référence à son ID. Dans éblouissant, il est également possible de capturer et manipuler une référence à un composant, bien qu’il soit bien moins courant.

Pour capturer une référence de composant dans éblouissant, utilisez l’attribut de directive `@ref`. La valeur de l’attribut doit correspondre au nom d’un champ définissable avec le même type que le composant référencé.

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

Lors du rendu du composant parent, le champ est rempli avec l’instance du composant enfant. Vous pouvez ensuite appeler des méthodes sur l’instance de composant ou la manipuler.

La manipulation directe de l’état d’un composant à l’aide de références de composant n’est pas recommandée. Ce faisant, vous empêchez le rendu automatique du composant aux moments appropriés.

## <a name="capture-element-references"></a>Références des éléments de capture

Les composants éblouissant peuvent capturer des références à un élément. Contrairement aux contrôles serveur HTML dans ASP.NET Web Forms, vous ne pouvez pas manipuler le DOM directement à l’aide d’une référence d’élément dans éblouissant. Éblouissant gère la plupart des interactions DOM pour vous à l’aide de son algorithme de comparaison DOM. Les références d’élément capturées dans éblouissant sont opaques. Toutefois, elles sont utilisées pour passer une référence d’élément spécifique dans un appel d’interopérabilité JavaScript. Pour plus d’informations sur l’interopérabilité JavaScript, consultez [ASP.net Core l’interopérabilité avec éblouissant](/aspnet/core/blazor/javascript-interop).

## <a name="templated-components"></a>Composants basés sur un modèle

Dans ASP.NET Web Forms, vous pouvez créer des *contrôles basés*sur un modèle. Les contrôles basés sur un modèle permettent au développeur de spécifier une partie du code HTML utilisé pour restituer un contrôle conteneur. La mécanique de la création de contrôles serveur basés sur des modèles est complexe, mais elle permet de puissants scénarios de rendu des données de manière personnalisable par l’utilisateur. `Repeater` et `DataList`sont des exemples de contrôles basés sur un modèle.

Les composants éblouissants peuvent également être basés sur un modèle en définissant des paramètres de composant de type `RenderFragment` ou `RenderFragment<T>`. Un `RenderFragment` représente un segment de balisage Razor qui peut ensuite être rendu par le composant. Un `RenderFragment<T>` est un segment de balisage Razor qui prend un paramètre qui peut être spécifié lors du rendu du fragment de rendu.

### <a name="child-content"></a>Contenu enfant

Les composants éblouissant peuvent capturer leur contenu enfant sous forme de `RenderFragment` et afficher ce contenu dans le cadre du rendu des composants. Pour capturer le contenu enfant, définissez un paramètre de composant de type `RenderFragment` et nommez-le `ChildContent`.

*ChildContentComponent. Razor*

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

Un composant parent peut ensuite fournir le contenu enfant à l’aide d’un syntaxe Razor normal.

```razor
<ChildContentComponent>
    <p>The time is @DateTime.Now</p>
</ChildContentComponent>
```

### <a name="template-parameters"></a>Paramètres de modèle

Un composant éblouissant basé sur des modèles peut également définir plusieurs paramètres de composant de type `RenderFragment` ou `RenderFragment<T>`. Le paramètre d’un `RenderFragment<T>` peut être spécifié lorsqu’il est appelé. Pour spécifier un paramètre de type générique pour un composant, utilisez la directive Razor `@typeparam`.

*SimpleListView. Razor*

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

Lorsque vous utilisez un composant basé sur un modèle, les paramètres de modèle peuvent être spécifiés à l’aide d’éléments enfants qui correspondent aux noms des paramètres. Les arguments de composant de type `RenderFragment<T>` passés en tant qu’éléments ont un paramètre implicite nommé `context`. Vous pouvez modifier le nom de ce paramètre d’implémentation à l’aide de l’attribut `Context` sur l’élément enfant. Tous les paramètres de type générique peuvent être spécifiés à l’aide d’un attribut qui correspond au nom du paramètre de type. Le paramètre de type sera déduit si possible :

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

La sortie de ce composant ressemble à ceci :

```html
<h1>My list</h1>
<ul>
    <li>The message is: message1</li>
    <li>The message is: message2</li>
<ul>
```

## <a name="code-behind"></a>Code-behind

Un composant éblouissant est généralement créé dans un seul fichier *. Razor* . Toutefois, il est également possible de séparer le code et le balisage à l’aide d’un fichier code-behind. Pour utiliser un fichier de composant, ajoutez C# un fichier qui correspond au nom du fichier du composant, mais avec une extension *. cs* ajoutée (*Counter.Razor.cs*). Utilisez le C# fichier pour définir une classe de base pour le composant. Vous pouvez nommer la classe de base tout ce que vous souhaitez, mais il est courant de nommer la classe comme la classe du composant, mais avec une extension de `Base` ajoutée (`CounterBase`). La classe basée sur les composants doit également dériver de `ComponentBase`. Ensuite, dans le fichier du composant Razor, ajoutez la directive `@inherits` pour spécifier la classe de base pour le composant (`@inherits CounterBase`).

*Counter. Razor*

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

La visibilité des membres du composant dans la classe de base doit être `protected` ou `public` pour être visible pour la classe de composant.

## <a name="additional-resources"></a>Ressources supplémentaires

Ce qui précède n’est pas un traitement exhaustif de tous les aspects des composants de éblouissant. Pour plus d’informations sur la [création et l’utilisation de ASP.net Core les composants Razor](/aspnet/core/blazor/components), consultez la documentation de l’éblouissant.

>[!div class="step-by-step"]
>[Précédent](app-startup.md)
>[Suivant](pages-routing-layouts.md)
