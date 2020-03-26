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
# <a name="build-reusable-ui-components-with-blazor"></a><span data-ttu-id="51c88-103">Construire des composants d’interface utilisateur réutilisables avec Blazor</span><span class="sxs-lookup"><span data-stu-id="51c88-103">Build reusable UI components with Blazor</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="51c88-104">Une des belles choses sur ASP.NET Web Forms est de savoir comment il permet l’encapsulation de morceaux réutilisables de code d’interface utilisateur (interface utilisateur) dans les contrôles réutilisables de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="51c88-104">One of the beautiful things about ASP.NET Web Forms is how it enables encapsulation of reusable pieces of user interface (UI) code into reusable UI controls.</span></span> <span data-ttu-id="51c88-105">Les contrôles personnalisés des utilisateurs peuvent être définis dans le balisage à l’aide de fichiers *.ascx.*</span><span class="sxs-lookup"><span data-stu-id="51c88-105">Custom user controls can be defined in markup using *.ascx* files.</span></span> <span data-ttu-id="51c88-106">Vous pouvez également créer des contrôles de serveur élaborés dans le code avec un support complet de concepteur.</span><span class="sxs-lookup"><span data-stu-id="51c88-106">You can also build elaborate server controls in code with full designer support.</span></span>

<span data-ttu-id="51c88-107">Blazor prend également en charge l’encapsulation de l’interface utilisateur à travers *les composants*.</span><span class="sxs-lookup"><span data-stu-id="51c88-107">Blazor also supports UI encapsulation through *components*.</span></span> <span data-ttu-id="51c88-108">Un composant :</span><span class="sxs-lookup"><span data-stu-id="51c88-108">A component:</span></span>

- <span data-ttu-id="51c88-109">Est un morceau autonome de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="51c88-109">Is a self-contained chunk of UI.</span></span>
- <span data-ttu-id="51c88-110">Maintient son propre état et rend la logique.</span><span class="sxs-lookup"><span data-stu-id="51c88-110">Maintains its own state and rendering logic.</span></span>
- <span data-ttu-id="51c88-111">Peut définir les gestionnaires d’événements d’interface utilisateur, se lier aux données d’entrée et gérer son propre cycle de vie.</span><span class="sxs-lookup"><span data-stu-id="51c88-111">Can define UI event handlers, bind to input data, and manage its own lifecycle.</span></span>
- <span data-ttu-id="51c88-112">Est généralement défini dans un fichier *.razor* en utilisant la syntaxe Razor.</span><span class="sxs-lookup"><span data-stu-id="51c88-112">Is typically defined in a *.razor* file using Razor syntax.</span></span>

## <a name="an-introduction-to-razor"></a><span data-ttu-id="51c88-113">Une introduction à Razor</span><span class="sxs-lookup"><span data-stu-id="51c88-113">An introduction to Razor</span></span>

<span data-ttu-id="51c88-114">Razor est un langage de température de balisage léger basé sur HTML et C.</span><span class="sxs-lookup"><span data-stu-id="51c88-114">Razor is a light-weight markup templating language based on HTML and C#.</span></span> <span data-ttu-id="51c88-115">Avec Razor, vous pouvez passer en toute transparence entre le balisage et le code C pour définir votre logique de rendu des composants.</span><span class="sxs-lookup"><span data-stu-id="51c88-115">With Razor, you can seamlessly transition between markup and C# code to define your component rendering logic.</span></span> <span data-ttu-id="51c88-116">Lorsque le fichier *.razor* est compilé, la logique de rendu est capturée d’une manière structurée dans une classe .NET.</span><span class="sxs-lookup"><span data-stu-id="51c88-116">When the *.razor* file is compiled, the rendering logic is captured in a structured way in a .NET class.</span></span> <span data-ttu-id="51c88-117">Le nom de la classe compilée est tiré du nom de fichier *.razor.*</span><span class="sxs-lookup"><span data-stu-id="51c88-117">The name of the compiled class is taken from the *.razor* file name.</span></span> <span data-ttu-id="51c88-118">L’espace de nom est tiré de l’espace nom par défaut pour le projet `@namespace` et le chemin du dossier, ou vous pouvez spécifier explicitement l’espace de nom en utilisant la directive (plus sur les directives Razor ci-dessous).</span><span class="sxs-lookup"><span data-stu-id="51c88-118">The namespace is taken from the default namespace for the project and the folder path, or you can explicitly specify the namespace using the `@namespace` directive (more on Razor directives below).</span></span>

<span data-ttu-id="51c88-119">La logique de rendu d’un composant est rédigée à l’aide d’une balisage HTML normal avec une logique dynamique ajoutée à l’aide de C.</span><span class="sxs-lookup"><span data-stu-id="51c88-119">A component's rendering logic is authored using normal HTML markup with dynamic logic added using C#.</span></span> <span data-ttu-id="51c88-120">Le `@` personnage est utilisé pour passer à C.</span><span class="sxs-lookup"><span data-stu-id="51c88-120">The `@` character is used to transition to C#.</span></span> <span data-ttu-id="51c88-121">Razor est généralement intelligent au sujet de comprendre quand vous avez commuté de nouveau à HTML.</span><span class="sxs-lookup"><span data-stu-id="51c88-121">Razor is typically smart about figuring out when you've switched back to HTML.</span></span> <span data-ttu-id="51c88-122">Par exemple, le composant `<p>` suivant rend une balise avec l’heure actuelle :</span><span class="sxs-lookup"><span data-stu-id="51c88-122">For example, the following component renders a `<p>` tag with the current time:</span></span>

```razor
<p>@DateTime.Now</p>
```

<span data-ttu-id="51c88-123">Pour spécifier explicitement le début et la fin d’une expression C, utilisez des parenthèses :</span><span class="sxs-lookup"><span data-stu-id="51c88-123">To explicitly specify the beginning and ending of a C# expression, use parentheses:</span></span>

```razor
<p>@(DateTime.Now)</p>
```

<span data-ttu-id="51c88-124">Razor facilite également l’utilisation du flux de contrôle C DANS votre logique de rendu.</span><span class="sxs-lookup"><span data-stu-id="51c88-124">Razor also makes it easy to use C# control flow in your rendering logic.</span></span> <span data-ttu-id="51c88-125">Par exemple, vous pouvez rendre sous condition certains HTML comme ceci:</span><span class="sxs-lookup"><span data-stu-id="51c88-125">For example, you can conditionally render some HTML like this:</span></span>

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

<span data-ttu-id="51c88-126">Ou vous pouvez générer une liste d’éléments à l’aide d’une boucle normale de C comme celle-ci `foreach` :</span><span class="sxs-lookup"><span data-stu-id="51c88-126">Or you can generate a list of items using a normal C# `foreach` loop like this:</span></span>

```razor
<ul>
@foreach (var item in items)
{
    <li>@item.Text</li>
}
</ul>
```

<span data-ttu-id="51c88-127">Les directives de rasoir, comme les directives dans ASP.NET formulaires Web, contrôlent de nombreux aspects de la façon dont un composant Razor est compilé.</span><span class="sxs-lookup"><span data-stu-id="51c88-127">Razor directives, like directives in ASP.NET Web Forms, control many aspects of how a Razor component is compiled.</span></span> <span data-ttu-id="51c88-128">Voici quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="51c88-128">Examples include the component's:</span></span>

- <span data-ttu-id="51c88-129">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="51c88-129">Namespace</span></span>
- <span data-ttu-id="51c88-130">Classe de base</span><span class="sxs-lookup"><span data-stu-id="51c88-130">Base class</span></span>
- <span data-ttu-id="51c88-131">Interfaces mises en œuvre</span><span class="sxs-lookup"><span data-stu-id="51c88-131">Implemented interfaces</span></span>
- <span data-ttu-id="51c88-132">Paramètres génériques</span><span class="sxs-lookup"><span data-stu-id="51c88-132">Generic parameters</span></span>
- <span data-ttu-id="51c88-133">Espaces de noms importés</span><span class="sxs-lookup"><span data-stu-id="51c88-133">Imported namespaces</span></span>
- <span data-ttu-id="51c88-134">Itinéraires</span><span class="sxs-lookup"><span data-stu-id="51c88-134">Routes</span></span>

<span data-ttu-id="51c88-135">Les directives de `@` rasoir commencent par le personnage et sont généralement utilisées au début d’une nouvelle ligne au début du fichier.</span><span class="sxs-lookup"><span data-stu-id="51c88-135">Razor directives start with the `@` character and are typically used at the start of a new line at the start of the file.</span></span> <span data-ttu-id="51c88-136">Par exemple, `@namespace` la directive définit l’espace nom du composant :</span><span class="sxs-lookup"><span data-stu-id="51c88-136">For example, the `@namespace` directive defines the component's namespace:</span></span>

```razor
@namespace MyComponentNamespace
```

<span data-ttu-id="51c88-137">Le tableau suivant résume les différentes directives Razor utilisées dans Blazor et leurs équivalents ASP.NET Web Forms, si elles existent.</span><span class="sxs-lookup"><span data-stu-id="51c88-137">The following table summarizes the various Razor directives used in Blazor and their ASP.NET Web Forms equivalents, if they exist.</span></span>

|<span data-ttu-id="51c88-138">Directive</span><span class="sxs-lookup"><span data-stu-id="51c88-138">Directive</span></span>    |<span data-ttu-id="51c88-139">Description</span><span class="sxs-lookup"><span data-stu-id="51c88-139">Description</span></span>|<span data-ttu-id="51c88-140">Exemple</span><span class="sxs-lookup"><span data-stu-id="51c88-140">Example</span></span>|<span data-ttu-id="51c88-141">Formulaires Web équivalents</span><span class="sxs-lookup"><span data-stu-id="51c88-141">Web Forms equivalent</span></span>|
|-------------|-----------|-------|--------------------|
|`@attribute` |<span data-ttu-id="51c88-142">Ajoute un attribut de niveau de classe au composant</span><span class="sxs-lookup"><span data-stu-id="51c88-142">Adds a class-level attribute to the component</span></span>|`@attribute [Authorize]`|<span data-ttu-id="51c88-143">None</span><span class="sxs-lookup"><span data-stu-id="51c88-143">None</span></span>|
|`@code`      |<span data-ttu-id="51c88-144">Ajoute les membres de la classe à la composante</span><span class="sxs-lookup"><span data-stu-id="51c88-144">Adds class members to the component</span></span>|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|<span data-ttu-id="51c88-145">Implémente l’interface spécifiée</span><span class="sxs-lookup"><span data-stu-id="51c88-145">Implements the specified interface</span></span>|`@implements IDisposable`|<span data-ttu-id="51c88-146">Utiliser code-behind</span><span class="sxs-lookup"><span data-stu-id="51c88-146">Use code-behind</span></span>|
|`@inherits`  |<span data-ttu-id="51c88-147">Hérite de la classe de base spécifiée</span><span class="sxs-lookup"><span data-stu-id="51c88-147">Inherits from the specified base class</span></span>|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |<span data-ttu-id="51c88-148">Injecte un service dans le composant</span><span class="sxs-lookup"><span data-stu-id="51c88-148">Injects a service into the component</span></span>|`@inject IJSRuntime JS`|<span data-ttu-id="51c88-149">None</span><span class="sxs-lookup"><span data-stu-id="51c88-149">None</span></span>|
|`@layout`    |<span data-ttu-id="51c88-150">Spécifie un composant de mise en page pour le composant</span><span class="sxs-lookup"><span data-stu-id="51c88-150">Specifies a layout component for the component</span></span>|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |<span data-ttu-id="51c88-151">Définit l’espace de nom pour le composant</span><span class="sxs-lookup"><span data-stu-id="51c88-151">Sets the namespace for the component</span></span>|`@namespace MyNamespace`|<span data-ttu-id="51c88-152">None</span><span class="sxs-lookup"><span data-stu-id="51c88-152">None</span></span>|
|`@page`      |<span data-ttu-id="51c88-153">Spécifie l’itinéraire du composant</span><span class="sxs-lookup"><span data-stu-id="51c88-153">Specifies the route for the component</span></span>|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |<span data-ttu-id="51c88-154">Spécifie un paramètre de type générique pour le composant</span><span class="sxs-lookup"><span data-stu-id="51c88-154">Specifies a generic type parameter for the component</span></span>|`@typeparam TItem`|<span data-ttu-id="51c88-155">Utiliser code-behind</span><span class="sxs-lookup"><span data-stu-id="51c88-155">Use code-behind</span></span>|
|`@using`     |<span data-ttu-id="51c88-156">Spécifie un espace de nom à mettre en portée</span><span class="sxs-lookup"><span data-stu-id="51c88-156">Specifies a namespace to bring into scope</span></span>|`@using MyComponentNamespace`|<span data-ttu-id="51c88-157">Ajouter namespace dans *web.config*</span><span class="sxs-lookup"><span data-stu-id="51c88-157">Add namespace in *web.config*</span></span>|

<span data-ttu-id="51c88-158">Les composants razor utilisent également largement les *attributs des directives* sur les éléments pour contrôler divers aspects de la façon dont les composants sont compilés (traitement des événements, liaison de données, composantes & références d’éléments, et ainsi de suite).</span><span class="sxs-lookup"><span data-stu-id="51c88-158">Razor components also make extensive use of *directive attributes* on elements to control various aspects of how components get compiled (event handling, data binding, component & element references, and so on).</span></span> <span data-ttu-id="51c88-159">Les attributs de directive suivent tous une syntaxe générique commune où les valeurs de la parenthèse sont facultatives :</span><span class="sxs-lookup"><span data-stu-id="51c88-159">Directive attributes all follow a common generic syntax where the values in parenthesis are optional:</span></span>

```razor
@directive(-suffix(:name))(="value")
```

<span data-ttu-id="51c88-160">Le tableau suivant résume les différents attributs des directives Razor utilisées dans Blazor.</span><span class="sxs-lookup"><span data-stu-id="51c88-160">The following table summarizes the various attributes for Razor directives used in Blazor.</span></span>

|<span data-ttu-id="51c88-161">Attribut</span><span class="sxs-lookup"><span data-stu-id="51c88-161">Attribute</span></span>    |<span data-ttu-id="51c88-162">Description</span><span class="sxs-lookup"><span data-stu-id="51c88-162">Description</span></span>|<span data-ttu-id="51c88-163">Exemple</span><span class="sxs-lookup"><span data-stu-id="51c88-163">Example</span></span>|
|-------------|-----------|-------|
|`@attributes`|<span data-ttu-id="51c88-164">Rend un dictionnaire d’attributs</span><span class="sxs-lookup"><span data-stu-id="51c88-164">Renders a dictionary of attributes</span></span>|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |<span data-ttu-id="51c88-165">Crée une liaison de données bidirectionnel</span><span class="sxs-lookup"><span data-stu-id="51c88-165">Creates a two-way data binding</span></span>    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |<span data-ttu-id="51c88-166">Ajoute un gestionnaire d’événements pour l’événement spécifié</span><span class="sxs-lookup"><span data-stu-id="51c88-166">Adds an event handler for the specified event</span></span>|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |<span data-ttu-id="51c88-167">Spécifie une clé à utiliser par l’algorithme de diffing pour préserver les éléments d’une collection</span><span class="sxs-lookup"><span data-stu-id="51c88-167">Specifies a key to be used by the diffing algorithm for preserving elements in a collection</span></span>|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |<span data-ttu-id="51c88-168">Capture une référence au composant ou à l’élément HTML</span><span class="sxs-lookup"><span data-stu-id="51c88-168">Captures a reference to the component or HTML element</span></span>|`<MyDialog @ref="myDialog" />`|

<span data-ttu-id="51c88-169">Les différents attributs de directive`@onclick`utilisés `@bind` `@ref`par Blazor ( , , , , et ainsi de suite) sont couverts dans les sections ci-dessous et les chapitres ultérieurs.</span><span class="sxs-lookup"><span data-stu-id="51c88-169">The various directive attributes used by Blazor (`@onclick`, `@bind`, `@ref`, and so on) are covered in the sections below and later chapters.</span></span>

<span data-ttu-id="51c88-170">Beaucoup de syntaxes utilisées dans les fichiers *.aspx* et *.ascx* ont des syntaxes parallèles dans Razor.</span><span class="sxs-lookup"><span data-stu-id="51c88-170">Many of the syntaxes used in *.aspx* and *.ascx* files have parallel syntaxes in Razor.</span></span> <span data-ttu-id="51c88-171">Voici une simple comparaison des syntaxes pour ASP.NET Web Forms et Razor.</span><span class="sxs-lookup"><span data-stu-id="51c88-171">Below is a simple comparison of the syntaxes for ASP.NET Web Forms and Razor.</span></span>

|<span data-ttu-id="51c88-172">Fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="51c88-172">Feature</span></span>                      |<span data-ttu-id="51c88-173">Web Forms</span><span class="sxs-lookup"><span data-stu-id="51c88-173">Web Forms</span></span>           |<span data-ttu-id="51c88-174">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51c88-174">Syntax</span></span>               |<span data-ttu-id="51c88-175">Razor</span><span class="sxs-lookup"><span data-stu-id="51c88-175">Razor</span></span>         |<span data-ttu-id="51c88-176">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51c88-176">Syntax</span></span> |
|-----------------------------|--------------------|---------------------|--------------|-------|
|<span data-ttu-id="51c88-177">Directives</span><span class="sxs-lookup"><span data-stu-id="51c88-177">Directives</span></span>                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|<span data-ttu-id="51c88-178">Blocs de code</span><span class="sxs-lookup"><span data-stu-id="51c88-178">Code blocks</span></span>                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|<span data-ttu-id="51c88-179">Expressions</span><span class="sxs-lookup"><span data-stu-id="51c88-179">Expressions</span></span><br><span data-ttu-id="51c88-180">(HTML-encodé)</span><span class="sxs-lookup"><span data-stu-id="51c88-180">(HTML-encoded)</span></span>|`<%: %>`            |`<%:DateTime.Now %>` |<span data-ttu-id="51c88-181">Implicite:`@`</span><span class="sxs-lookup"><span data-stu-id="51c88-181">Implicit: `@`</span></span><br><span data-ttu-id="51c88-182">Explicite:`@()`</span><span class="sxs-lookup"><span data-stu-id="51c88-182">Explicit: `@()`</span></span>|`@DateTime.Now`<br>`@(DateTime.Now)`|
|<span data-ttu-id="51c88-183">Commentaires</span><span class="sxs-lookup"><span data-stu-id="51c88-183">Comments</span></span>                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|<span data-ttu-id="51c88-184">Liaison de données</span><span class="sxs-lookup"><span data-stu-id="51c88-184">Data binding</span></span>                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

<span data-ttu-id="51c88-185">Pour ajouter des membres à la `@code` classe de composants Razor, utilisez la directive.</span><span class="sxs-lookup"><span data-stu-id="51c88-185">To add members to the Razor component class, use the `@code` directive.</span></span> <span data-ttu-id="51c88-186">Cette technique est similaire `<script runat="server">...</script>` à l’utilisation d’un bloc dans un ASP.NET Web Forms contrôle utilisateur ou page.</span><span class="sxs-lookup"><span data-stu-id="51c88-186">This technique is similar to using a `<script runat="server">...</script>` block in an ASP.NET Web Forms user control or page.</span></span>

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

<span data-ttu-id="51c88-187">Parce que Razor est basé sur le C, il doit être compilé à partir d’un projet C (*.csproj*).</span><span class="sxs-lookup"><span data-stu-id="51c88-187">Because Razor is based on C#, it must be compiled from within a C# project (*.csproj*).</span></span> <span data-ttu-id="51c88-188">Vous ne pouvez pas compiler des fichiers *.razor* à partir d’un projet Visual Basic (*.vbproj*).</span><span class="sxs-lookup"><span data-stu-id="51c88-188">You can't compile *.razor* files from a Visual Basic project (*.vbproj*).</span></span> <span data-ttu-id="51c88-189">Vous pouvez toujours faire référence aux projets Visual Basic de votre projet Blazor.</span><span class="sxs-lookup"><span data-stu-id="51c88-189">You can still reference Visual Basic projects from your Blazor project.</span></span> <span data-ttu-id="51c88-190">Le contraire est vrai aussi.</span><span class="sxs-lookup"><span data-stu-id="51c88-190">The opposite is true too.</span></span>

<span data-ttu-id="51c88-191">Pour une référence complète de syntaxe Razor, voir [référence de syntaxe Razor pour ASP.NET Core](/aspnet/core/mvc/views/razor).</span><span class="sxs-lookup"><span data-stu-id="51c88-191">For a full Razor syntax reference, see [Razor syntax reference for ASP.NET Core](/aspnet/core/mvc/views/razor).</span></span>

## <a name="use-components"></a><span data-ttu-id="51c88-192">Utiliser des composants</span><span class="sxs-lookup"><span data-stu-id="51c88-192">Use components</span></span>

<span data-ttu-id="51c88-193">Mis à part HTML normal, les composants peuvent également utiliser d’autres composants dans le cadre de leur logique de rendu.</span><span class="sxs-lookup"><span data-stu-id="51c88-193">Aside from normal HTML, components can also use other components as part of their rendering logic.</span></span> <span data-ttu-id="51c88-194">La syntaxe pour l’utilisation d’un composant dans Razor est similaire à l’utilisation d’un contrôle utilisateur dans une application ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="51c88-194">The syntax for using a component in Razor is similar to using a user control in an ASP.NET Web Forms app.</span></span> <span data-ttu-id="51c88-195">Les composants sont spécifiés à l’aide d’une étiquette d’élément qui correspond au nom type du composant.</span><span class="sxs-lookup"><span data-stu-id="51c88-195">Components are specified using an element tag that matches the type name of the component.</span></span> <span data-ttu-id="51c88-196">Par exemple, vous `Counter` pouvez ajouter un composant comme celui-ci :</span><span class="sxs-lookup"><span data-stu-id="51c88-196">For example, you can add a `Counter` component like this:</span></span>

```razor
<Counter />
```

<span data-ttu-id="51c88-197">Contrairement à ASP.NET Web Forms, composants de Blazor :</span><span class="sxs-lookup"><span data-stu-id="51c88-197">Unlike ASP.NET Web Forms, components in Blazor:</span></span>

- <span data-ttu-id="51c88-198">N’utilisez pas de préfixe `asp:`d’élément (par exemple, ).</span><span class="sxs-lookup"><span data-stu-id="51c88-198">Don't use an element prefix (for example, `asp:`).</span></span>
- <span data-ttu-id="51c88-199">N’exigez pas l’enregistrement sur la page ou sur le *web.config*.</span><span class="sxs-lookup"><span data-stu-id="51c88-199">Don't require registration on the page or in the *web.config*.</span></span>

<span data-ttu-id="51c88-200">Pensez à des composants Razor comme vous le feriez .NET types, parce que c’est exactement ce qu’ils sont.</span><span class="sxs-lookup"><span data-stu-id="51c88-200">Think of Razor components like you would .NET types, because that's exactly what they are.</span></span> <span data-ttu-id="51c88-201">Si l’assemblage contenant le composant est référencé, le composant est disponible pour utilisation.</span><span class="sxs-lookup"><span data-stu-id="51c88-201">If the assembly containing the component is referenced, then the component is available for use.</span></span> <span data-ttu-id="51c88-202">Pour mettre en portée l’espace nom `@using` du composant, appliquez la directive :</span><span class="sxs-lookup"><span data-stu-id="51c88-202">To bring the component's namespace into scope, apply the `@using` directive:</span></span>

```razor
@using MyComponentLib

<Counter />
```

<span data-ttu-id="51c88-203">Comme on le voit dans les projets Blazor par défaut, il est courant de mettre `@using` des directives dans un fichier *_Imports.razor* afin qu’ils soient importés dans tous les fichiers *.razor* dans le même répertoire et dans les annuaires pour enfants.</span><span class="sxs-lookup"><span data-stu-id="51c88-203">As seen in the default Blazor projects, it's common to put `@using` directives into a *_Imports.razor* file so that they're imported into all *.razor* files in the same directory and in child directories.</span></span>

<span data-ttu-id="51c88-204">Si l’espace de nom d’un composant n’est pas de portée, vous pouvez spécifier un composant à l’aide de son nom de type complet, comme vous le pouvez dans C :</span><span class="sxs-lookup"><span data-stu-id="51c88-204">If the namespace for a component isn't in scope, you can specify a component using its full type name, as you can in C#:</span></span>

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a><span data-ttu-id="51c88-205">Paramètres de composant</span><span class="sxs-lookup"><span data-stu-id="51c88-205">Component parameters</span></span>

<span data-ttu-id="51c88-206">Dans ASP.NET formulaires Web, vous pouvez faire circuler des paramètres et des données pour contrôler l’utilisation des propriétés publiques.</span><span class="sxs-lookup"><span data-stu-id="51c88-206">In ASP.NET Web Forms, you can flow parameters and data to controls using public properties.</span></span> <span data-ttu-id="51c88-207">Ces propriétés peuvent être définies en balisage à l’aide d’attributs ou définies directement dans le code.</span><span class="sxs-lookup"><span data-stu-id="51c88-207">These properties can be set in markup using attributes or set directly in code.</span></span> <span data-ttu-id="51c88-208">Les composants Blazor fonctionnent de la même manière, bien `[Parameter]` que les propriétés des composants doivent également être marquées par l’attribut pour être considérées comme des paramètres de composant.</span><span class="sxs-lookup"><span data-stu-id="51c88-208">Blazor components work in a similar fashion, although the component properties must also be marked with the `[Parameter]` attribute to be considered component parameters.</span></span>

<span data-ttu-id="51c88-209">Le `Counter` composant suivant définit un `IncrementAmount` paramètre de composant appelé `Counter` qui peut être utilisé pour spécifier la quantité que le devrait être incrémenté chaque fois que le bouton est cliqué.</span><span class="sxs-lookup"><span data-stu-id="51c88-209">The following `Counter` component defines a component parameter called `IncrementAmount` that can be used to specify the amount that the `Counter` should be incremented each time the button is clicked.</span></span>

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

<span data-ttu-id="51c88-210">Pour spécifier un paramètre de composant dans Blazor, utilisez un attribut comme vous le feriez dans ASP.NET formulaires Web :</span><span class="sxs-lookup"><span data-stu-id="51c88-210">To specify a component parameter in Blazor, use an attribute as you would in ASP.NET Web Forms:</span></span>

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a><span data-ttu-id="51c88-211">Gestionnaires d’événements</span><span class="sxs-lookup"><span data-stu-id="51c88-211">Event handlers</span></span>

<span data-ttu-id="51c88-212">ASP.NET Web Forms et Blazor fournissent un modèle de programmation basé sur les événements pour la gestion des événements d’assurance-chômage.</span><span class="sxs-lookup"><span data-stu-id="51c88-212">Both ASP.NET Web Forms and Blazor provide an event-based programming model for handling UI events.</span></span> <span data-ttu-id="51c88-213">Parmi les exemples de tels événements, mentionnons les clics sur les boutons et l’entrée de texte.</span><span class="sxs-lookup"><span data-stu-id="51c88-213">Examples of such events include button clicks and text input.</span></span> <span data-ttu-id="51c88-214">Dans ASP.NET Web Forms, vous utilisez des commandes de serveur HTML pour gérer les événements d’interface utilisateur exposés par le DOM, ou vous pouvez gérer les événements exposés par les contrôles du serveur Web.</span><span class="sxs-lookup"><span data-stu-id="51c88-214">In ASP.NET Web Forms, you use HTML server controls to handle UI events exposed by the DOM, or you can handle events exposed by web server controls.</span></span> <span data-ttu-id="51c88-215">Les événements sont mis en surface sur le serveur par le biais de demandes post-back de formulaire.</span><span class="sxs-lookup"><span data-stu-id="51c88-215">The events are surfaced on the server through form post-back requests.</span></span> <span data-ttu-id="51c88-216">Considérez l’exemple suivant du bouton Web Forms clic:</span><span class="sxs-lookup"><span data-stu-id="51c88-216">Consider the following Web Forms button click example:</span></span>

<span data-ttu-id="51c88-217">*Counter.ascx (en)*</span><span class="sxs-lookup"><span data-stu-id="51c88-217">*Counter.ascx*</span></span>

```aspx-csharp
<asp:Button ID="ClickMeButton" runat="server" Text="Click me!" OnClick="ClickMeButton_Click" />
```

<span data-ttu-id="51c88-218">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="51c88-218">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void ClickMeButton_Click(object sender, EventArgs e)
    {
        Console.WriteLine("The button was clicked!");
    }
}
```

<span data-ttu-id="51c88-219">Dans Blazor, vous pouvez enregistrer les gestionnaires pour les événements `@on{event}`d’interface utilisateur DOM directement en utilisant des attributs de directive du formulaire .</span><span class="sxs-lookup"><span data-stu-id="51c88-219">In Blazor, you can register handlers for DOM UI events directly using directive attributes of the form `@on{event}`.</span></span> <span data-ttu-id="51c88-220">Le `{event}` propriétaire de la place représente le nom de l’événement.</span><span class="sxs-lookup"><span data-stu-id="51c88-220">The `{event}` placeholder represents the name of the event.</span></span> <span data-ttu-id="51c88-221">Par exemple, vous pouvez écouter des clics de boutons comme celui-ci :</span><span class="sxs-lookup"><span data-stu-id="51c88-221">For example, you can listen for button clicks like this:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

<span data-ttu-id="51c88-222">Les gestionnaires d’événements peuvent accepter un argument facultatif et spécifique à un événement pour fournir plus d’information sur l’événement.</span><span class="sxs-lookup"><span data-stu-id="51c88-222">Event handlers can accept an optional, event-specific argument to provide more information about the event.</span></span> <span data-ttu-id="51c88-223">Par exemple, les événements `MouseEventArgs` de souris peuvent prendre un argument, mais il n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="51c88-223">For example, mouse events can take a `MouseEventArgs` argument, but it isn't required.</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e)
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

<span data-ttu-id="51c88-224">Au lieu de se référer à un groupe de méthode pour un gestionnaire d’événements, vous pouvez utiliser une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="51c88-224">Instead of referring to a method group for an event handler, you can use a lambda expression.</span></span> <span data-ttu-id="51c88-225">Une expression lambda vous permet de fermer sur d’autres valeurs de portée.</span><span class="sxs-lookup"><span data-stu-id="51c88-225">A lambda expression allows you to close over other in-scope values.</span></span>

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

<span data-ttu-id="51c88-226">Les gestionnaires d’événements peuvent exécuter de façon synchrone ou asynchrone.</span><span class="sxs-lookup"><span data-stu-id="51c88-226">Event handlers can execute synchronously or asynchronously.</span></span> <span data-ttu-id="51c88-227">Par exemple, `OnClick` le gestionnaire d’événements suivant exécute asynchrone :</span><span class="sxs-lookup"><span data-stu-id="51c88-227">For example, the following `OnClick` event handler executes asynchronously:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

<span data-ttu-id="51c88-228">Une fois qu’un événement est géré, le composant est rendu pour tenir compte de tout changement d’état de composant.</span><span class="sxs-lookup"><span data-stu-id="51c88-228">After an event is handled, the component is rendered to account for any component state changes.</span></span> <span data-ttu-id="51c88-229">Avec des gestionnaires d’événements asynchrones, le composant est rendu immédiatement après la fin de l’exécution du gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="51c88-229">With asynchronous event handlers, the component is rendered immediately after the handler execution completes.</span></span> <span data-ttu-id="51c88-230">Le composant est rendu *à nouveau* après `Task` les compléteurs asynchrones.</span><span class="sxs-lookup"><span data-stu-id="51c88-230">The component is rendered *again* after the asynchronous `Task` completes.</span></span> <span data-ttu-id="51c88-231">Ce mode d’exécution asynchrone offre l’occasion de rendre une `Task` interface utilisateur appropriée alors que l’asynchrone est toujours en cours.</span><span class="sxs-lookup"><span data-stu-id="51c88-231">This asynchronous execution mode provides an opportunity to render some appropriate UI while the asynchronous `Task` is still in progress.</span></span>

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

<span data-ttu-id="51c88-232">Les composants peuvent également définir leurs propres événements `EventCallback<TValue>`en définissant un paramètre de composant de type .</span><span class="sxs-lookup"><span data-stu-id="51c88-232">Components can also define their own events by defining a component parameter of type `EventCallback<TValue>`.</span></span> <span data-ttu-id="51c88-233">Les rappels d’événements prennent en charge toutes les variantes des gestionnaires d’événements d’interface utilisateur de DOM : arguments optionnels, synchrones ou asynchrones, groupes de méthode, ou expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="51c88-233">Event callbacks support all the variations of DOM UI event handlers: optional arguments, synchronous or asynchronous, method groups, or lambda expressions.</span></span>

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a><span data-ttu-id="51c88-234">Liaison de données</span><span class="sxs-lookup"><span data-stu-id="51c88-234">Data binding</span></span>

<span data-ttu-id="51c88-235">Blazor fournit un mécanisme simple pour lier les données d’un composant d’interface utilisateur à l’état du composant.</span><span class="sxs-lookup"><span data-stu-id="51c88-235">Blazor provides a simple mechanism to bind data from a UI component to the component's state.</span></span> <span data-ttu-id="51c88-236">Cette approche diffère des caractéristiques des formulaires Web ASP.NET pour les données contraignantes provenant des sources de données aux contrôles d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="51c88-236">This approach differs from the features in ASP.NET Web Forms for binding data from data sources to UI controls.</span></span> <span data-ttu-id="51c88-237">Nous couvrirons le traitement des données provenant de différentes sources de données dans la section [Traiter les données.](data.md)</span><span class="sxs-lookup"><span data-stu-id="51c88-237">We'll cover handling data from different data sources in the [Dealing with data](data.md) section.</span></span>

<span data-ttu-id="51c88-238">Pour créer une liaison de données bidirectionnelles à partir `@bind` d’un composant d’interface utilisateur à l’état du composant, utilisez l’attribut de directive.</span><span class="sxs-lookup"><span data-stu-id="51c88-238">To create a two-way data binding from a UI component to the component's state, use the `@bind` directive attribute.</span></span> <span data-ttu-id="51c88-239">Dans l’exemple suivant, la valeur de `isChecked` la case à cocher est liée au champ.</span><span class="sxs-lookup"><span data-stu-id="51c88-239">In the following example, the value of the check box is bound to the `isChecked` field.</span></span>

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

<span data-ttu-id="51c88-240">Lorsque le composant est rendu, la valeur de la case `isChecked` à cocher est définie à la valeur du champ.</span><span class="sxs-lookup"><span data-stu-id="51c88-240">When the component is rendered, the value of the checkbox is set to the value of the `isChecked` field.</span></span> <span data-ttu-id="51c88-241">Lorsque l’utilisateur bascule la `onchange` case à cocher, l’événement est déclenché et le `isChecked` champ est réglé à la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="51c88-241">When the user toggles the checkbox, the `onchange` event is fired and the `isChecked` field is set to the new value.</span></span> <span data-ttu-id="51c88-242">La `@bind` syntaxe dans ce cas est équivalente à la majoration suivante :</span><span class="sxs-lookup"><span data-stu-id="51c88-242">The `@bind` syntax in this case is equivalent to the following markup:</span></span>

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

<span data-ttu-id="51c88-243">Pour modifier l’événement utilisé pour `@bind:event` la liaison, utilisez l’attribut.</span><span class="sxs-lookup"><span data-stu-id="51c88-243">To change the event used for the bind, use the `@bind:event` attribute.</span></span>

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

<span data-ttu-id="51c88-244">Les composants peuvent également prendre en charge la liaison des données à leurs paramètres.</span><span class="sxs-lookup"><span data-stu-id="51c88-244">Components can also support data binding to their parameters.</span></span> <span data-ttu-id="51c88-245">Pour lier les données, définissez un paramètre de rappel d’événements du même nom que le paramètre liant.</span><span class="sxs-lookup"><span data-stu-id="51c88-245">To data bind, define an event callback parameter with the same name as the bindable parameter.</span></span> <span data-ttu-id="51c88-246">Le suffixe "Changed" est ajouté au nom.</span><span class="sxs-lookup"><span data-stu-id="51c88-246">The "Changed" suffix is added to the name.</span></span>

<span data-ttu-id="51c88-247">*PasswordBox.razor (en)*</span><span class="sxs-lookup"><span data-stu-id="51c88-247">*PasswordBox.razor*</span></span>

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

<span data-ttu-id="51c88-248">Pour enchaîner une liaison de données à un élément d’interface utilisateur sous-jacent, définissez la valeur et gérez l’événement directement sur l’élément d’interface utilisateur au lieu d’utiliser l’attribut. `@bind`</span><span class="sxs-lookup"><span data-stu-id="51c88-248">To chain a data binding to an underlying UI element, set the value and handle the event directly on the UI element instead of using the `@bind` attribute.</span></span>

<span data-ttu-id="51c88-249">Pour vous lier à `@bind-{Parameter}` un paramètre de composant, utilisez un attribut pour spécifier le paramètre auquel vous souhaitez lier.</span><span class="sxs-lookup"><span data-stu-id="51c88-249">To bind to a component parameter, use a `@bind-{Parameter}` attribute to specify the parameter to which you want to bind.</span></span>

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a><span data-ttu-id="51c88-250">Changements d'état</span><span class="sxs-lookup"><span data-stu-id="51c88-250">State changes</span></span>

<span data-ttu-id="51c88-251">Si l’état du composant a changé en dehors d’un événement normal d’interface utilisateur ou d’un rappel d’événement, alors le composant doit signaler manuellement qu’il doit être rendu à nouveau.</span><span class="sxs-lookup"><span data-stu-id="51c88-251">If the component's state has changed outside of a normal UI event or event callback, then the component must manually signal that it needs to be rendered again.</span></span> <span data-ttu-id="51c88-252">Pour signaler que l’état d’un `StateHasChanged` composant a changé, appelez la méthode sur le composant.</span><span class="sxs-lookup"><span data-stu-id="51c88-252">To signal that a component's state has changed, call the `StateHasChanged` method on the component.</span></span>

<span data-ttu-id="51c88-253">Dans l’exemple ci-dessous, un `AppState` composant affiche un message à partir d’un service qui peut être mis à jour par d’autres parties de l’application.</span><span class="sxs-lookup"><span data-stu-id="51c88-253">In the example below, a component displays a message from an `AppState` service that can be updated by other parts of the app.</span></span> <span data-ttu-id="51c88-254">Le composant enregistre `StateHasChanged` sa `AppState.OnChange` méthode avec l’événement afin que le composant soit rendu chaque fois que le message est mis à jour.</span><span class="sxs-lookup"><span data-stu-id="51c88-254">The component registers its `StateHasChanged` method with the `AppState.OnChange` event so that the component is rendered whenever the message gets updated.</span></span>

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

## <a name="component-lifecycle"></a><span data-ttu-id="51c88-255">Cycle de vie des composants</span><span class="sxs-lookup"><span data-stu-id="51c88-255">Component lifecycle</span></span>

<span data-ttu-id="51c88-256">Le cadre web ASP.NET formes a des méthodes de cycle de vie bien définies pour les modules, les pages et les contrôles.</span><span class="sxs-lookup"><span data-stu-id="51c88-256">The ASP.NET Web Forms framework has well-defined lifecycle methods for modules, pages, and controls.</span></span> <span data-ttu-id="51c88-257">Par exemple, le contrôle suivant met `Init`en `Load`œuvre les gestionnaires d’événements pour les événements , , et `UnLoad` le cycle de vie :</span><span class="sxs-lookup"><span data-stu-id="51c88-257">For example, the following control implements event handlers for the `Init`, `Load`, and `UnLoad` lifecycle events:</span></span>

<span data-ttu-id="51c88-258">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="51c88-258">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

<span data-ttu-id="51c88-259">Les composants Blazor ont également un cycle de vie bien défini.</span><span class="sxs-lookup"><span data-stu-id="51c88-259">Blazor components also have a well-defined lifecycle.</span></span> <span data-ttu-id="51c88-260">Le cycle de vie d’un composant peut être utilisé pour initialiser l’état des composants et mettre en œuvre des comportements de composants avancés.</span><span class="sxs-lookup"><span data-stu-id="51c88-260">A component's lifecycle can be used to initialize component state and implement advanced component behaviors.</span></span>

<span data-ttu-id="51c88-261">Toutes les méthodes du cycle de vie des composants de Blazor ont des versions synchrones et asynchrones.</span><span class="sxs-lookup"><span data-stu-id="51c88-261">All of Blazor's component lifecycle methods have both synchronous and asynchronous versions.</span></span> <span data-ttu-id="51c88-262">Le rendu des composants est synchrone.</span><span class="sxs-lookup"><span data-stu-id="51c88-262">Component rendering is synchronous.</span></span> <span data-ttu-id="51c88-263">Vous ne pouvez pas exécuter la logique asynchrone dans le cadre du rendu composant.</span><span class="sxs-lookup"><span data-stu-id="51c88-263">You can't run asynchronous logic as part of the component rendering.</span></span> <span data-ttu-id="51c88-264">Toute logique asynchrone doit s’exécuter dans le cadre d’une `async` méthode de cycle de vie.</span><span class="sxs-lookup"><span data-stu-id="51c88-264">All asynchronous logic must execute as part of an `async` lifecycle method.</span></span>

### <a name="oninitialized"></a><span data-ttu-id="51c88-265">SurInitialized</span><span class="sxs-lookup"><span data-stu-id="51c88-265">OnInitialized</span></span>

<span data-ttu-id="51c88-266">Les `OnInitialized` `OnInitializedAsync` méthodes et les méthodes sont utilisées pour initialiser le composant.</span><span class="sxs-lookup"><span data-stu-id="51c88-266">The `OnInitialized` and `OnInitializedAsync` methods are used to initialize the component.</span></span> <span data-ttu-id="51c88-267">Un composant est généralement paradés après sa première remise.</span><span class="sxs-lookup"><span data-stu-id="51c88-267">A component is typically initialized after it's first rendered.</span></span> <span data-ttu-id="51c88-268">Une fois qu’un composant est paralé, il peut être rendu plusieurs fois avant qu’il ne soit finalement éliminé.</span><span class="sxs-lookup"><span data-stu-id="51c88-268">After a component is initialized, it may be rendered multiple times before it's eventually disposed.</span></span> <span data-ttu-id="51c88-269">La `OnInitialized` méthode est `Page_Load` similaire à l’événement dans ASP.NET pages et contrôles Web Forms.</span><span class="sxs-lookup"><span data-stu-id="51c88-269">The `OnInitialized` method is similar to the `Page_Load` event in ASP.NET Web Forms pages and controls.</span></span>

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a><span data-ttu-id="51c88-270">OnParametersSet</span><span class="sxs-lookup"><span data-stu-id="51c88-270">OnParametersSet</span></span>

<span data-ttu-id="51c88-271">Les `OnParametersSet` `OnParametersSetAsync` méthodes et les méthodes sont appelées lorsqu’un composant a reçu des paramètres de son parent et que la valeur est attribuée aux propriétés.</span><span class="sxs-lookup"><span data-stu-id="51c88-271">The `OnParametersSet` and `OnParametersSetAsync` methods are called when a component has received parameters from its parent and the value are assigned to properties.</span></span> <span data-ttu-id="51c88-272">Ces méthodes sont exécutées après l’initialisation des composants et *chaque fois que le composant est rendu.*</span><span class="sxs-lookup"><span data-stu-id="51c88-272">These methods are executed after component initialization and *each time the component is rendered*.</span></span>

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a><span data-ttu-id="51c88-273">SurAfterRender</span><span class="sxs-lookup"><span data-stu-id="51c88-273">OnAfterRender</span></span>

<span data-ttu-id="51c88-274">Les `OnAfterRender` `OnAfterRenderAsync` méthodes et les méthodes sont appelées après qu’un composant a terminé le rendu.</span><span class="sxs-lookup"><span data-stu-id="51c88-274">The `OnAfterRender` and `OnAfterRenderAsync` methods are called after a component has finished rendering.</span></span> <span data-ttu-id="51c88-275">Les références d’éléments et de composants sont peuplées à ce stade (plus sur ces concepts ci-dessous).</span><span class="sxs-lookup"><span data-stu-id="51c88-275">Element and component references are populated at this point (more on these concepts below).</span></span> <span data-ttu-id="51c88-276">L’interactivité avec le navigateur est activée à ce stade.</span><span class="sxs-lookup"><span data-stu-id="51c88-276">Interactivity with the browser is enabled at this point.</span></span> <span data-ttu-id="51c88-277">Les interactions avec l’exécution DOM et JavaScript peuvent avoir lieu en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="51c88-277">Interactions with the DOM and JavaScript execution can safely take place.</span></span>

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

<span data-ttu-id="51c88-278">`OnAfterRender`et `OnAfterRenderAsync` *ne sont pas appelés lors du prerendering sur le serveur*.</span><span class="sxs-lookup"><span data-stu-id="51c88-278">`OnAfterRender` and `OnAfterRenderAsync` *aren't called when prerendering on the server*.</span></span>

<span data-ttu-id="51c88-279">Le `firstRender` paramètre est `true` la première fois que le composant est rendu; sinon, sa `false`valeur est .</span><span class="sxs-lookup"><span data-stu-id="51c88-279">The `firstRender` parameter is `true` the first time the component is rendered; otherwise, its value is `false`.</span></span>

### <a name="idisposable"></a><span data-ttu-id="51c88-280">IDisposable</span><span class="sxs-lookup"><span data-stu-id="51c88-280">IDisposable</span></span>

<span data-ttu-id="51c88-281">Les composants Blazor `IDisposable` peuvent implémenter les ressources lorsque le composant est retiré de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="51c88-281">Blazor components can implement `IDisposable` to dispose of resources when the component is removed from the UI.</span></span> <span data-ttu-id="51c88-282">Un composant Razor `IDispose` peut `@implements` être mis en œuvre à l’aide de la directive :</span><span class="sxs-lookup"><span data-stu-id="51c88-282">A Razor component can implement `IDispose` by using the `@implements` directive:</span></span>

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

## <a name="capture-component-references"></a><span data-ttu-id="51c88-283">Capturez les références des composants</span><span class="sxs-lookup"><span data-stu-id="51c88-283">Capture component references</span></span>

<span data-ttu-id="51c88-284">Dans ASP.NET Web Forms, il est courant de manipuler une instance de contrôle directement dans le code en se référant à son ID.</span><span class="sxs-lookup"><span data-stu-id="51c88-284">In ASP.NET Web Forms, it's common to manipulate a control instance directly in code by referring to its ID.</span></span> <span data-ttu-id="51c88-285">Dans Blazor, il est également possible de capturer et de manipuler une référence à un composant, bien qu’il soit beaucoup moins fréquent.</span><span class="sxs-lookup"><span data-stu-id="51c88-285">In Blazor, it's also possible to capture and manipulate a reference to a component, although it's much less common.</span></span>

<span data-ttu-id="51c88-286">Pour saisir une référence de composant `@ref` dans Blazor, utilisez l’attribut de la directive.</span><span class="sxs-lookup"><span data-stu-id="51c88-286">To capture a component reference in Blazor, use the `@ref` directive attribute.</span></span> <span data-ttu-id="51c88-287">La valeur de l’attribut doit correspondre au nom d’un champ défini avec le même type que le composant référencé.</span><span class="sxs-lookup"><span data-stu-id="51c88-287">The value of the attribute should match the name of a settable field with the same type as the referenced component.</span></span>

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

<span data-ttu-id="51c88-288">Lorsque la composante parente est rendue, le champ est peuplé avec l’instance de composant de l’enfant.</span><span class="sxs-lookup"><span data-stu-id="51c88-288">When the parent component is rendered, the field is populated with the child component instance.</span></span> <span data-ttu-id="51c88-289">Vous pouvez ensuite appeler des méthodes sur, ou manipuler autrement, l’instance du composant.</span><span class="sxs-lookup"><span data-stu-id="51c88-289">You can then call methods on, or otherwise manipulate, the component instance.</span></span>

<span data-ttu-id="51c88-290">Il n’est pas recommandé de manipuler directement l’état des composants à l’aide de références de composants.</span><span class="sxs-lookup"><span data-stu-id="51c88-290">Manipulating component state directly using component references isn't recommended.</span></span> <span data-ttu-id="51c88-291">Cela empêche le composant d’être rendu automatiquement aux bons moments.</span><span class="sxs-lookup"><span data-stu-id="51c88-291">Doing so prevents the component from being rendered automatically at the correct times.</span></span>

## <a name="capture-element-references"></a><span data-ttu-id="51c88-292">Références d’élément de capture</span><span class="sxs-lookup"><span data-stu-id="51c88-292">Capture element references</span></span>

<span data-ttu-id="51c88-293">Les composants Blazor peuvent capturer des références à un élément.</span><span class="sxs-lookup"><span data-stu-id="51c88-293">Blazor components can capture references to an element.</span></span> <span data-ttu-id="51c88-294">Contrairement aux commandes de serveur HTML dans ASP.NET formulaires Web, vous ne pouvez pas manipuler directement le DOM à l’aide d’une référence d’élément dans Blazor.</span><span class="sxs-lookup"><span data-stu-id="51c88-294">Unlike HTML server controls in ASP.NET Web Forms, you can't manipulate the DOM directly using an element reference in Blazor.</span></span> <span data-ttu-id="51c88-295">Blazor gère la plupart des interactions DOM pour vous en utilisant son algorithme de diffing DOM.</span><span class="sxs-lookup"><span data-stu-id="51c88-295">Blazor handles most DOM interactions for you using its DOM diffing algorithm.</span></span> <span data-ttu-id="51c88-296">Les références d’éléments capturés dans Blazor sont opaques.</span><span class="sxs-lookup"><span data-stu-id="51c88-296">Captured element references in Blazor are opaque.</span></span> <span data-ttu-id="51c88-297">Cependant, ils sont utilisés pour passer une référence d’élément spécifique dans un appel interop JavaScript.</span><span class="sxs-lookup"><span data-stu-id="51c88-297">However, they're used to pass a specific element reference in a JavaScript interop call.</span></span> <span data-ttu-id="51c88-298">Pour plus d’informations sur JavaScript interop, voir [ASP.NET Core Blazor JavaScript interop](/aspnet/core/blazor/javascript-interop).</span><span class="sxs-lookup"><span data-stu-id="51c88-298">For more information about JavaScript interop, see [ASP.NET Core Blazor JavaScript interop](/aspnet/core/blazor/javascript-interop).</span></span>

## <a name="templated-components"></a><span data-ttu-id="51c88-299">Composants basés sur un modèle</span><span class="sxs-lookup"><span data-stu-id="51c88-299">Templated components</span></span>

<span data-ttu-id="51c88-300">Dans ASP.NET formulaires Web, vous pouvez créer *des contrôles modélistes*.</span><span class="sxs-lookup"><span data-stu-id="51c88-300">In ASP.NET Web Forms, you can create *templated controls*.</span></span> <span data-ttu-id="51c88-301">Les contrôles modélistes permettent au développeur de spécifier une partie du HTML utilisé pour rendre un contrôle des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="51c88-301">Templated controls enable the developer to specify a portion of the HTML used to render a container control.</span></span> <span data-ttu-id="51c88-302">La mécanique de la construction des contrôles de serveur modéliques sont complexes, mais ils permettent des scénarios puissants pour rendre les données d’une manière personnalisable de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="51c88-302">The mechanics of building templated server controls are complex, but they enable powerful scenarios for rendering data in a user customizable way.</span></span> <span data-ttu-id="51c88-303">Des exemples de `Repeater` `DataList`contrôles modélistes incluent et .</span><span class="sxs-lookup"><span data-stu-id="51c88-303">Examples of templated controls include `Repeater` and `DataList`.</span></span>

<span data-ttu-id="51c88-304">Les composants Blazor peuvent également être modélés `RenderFragment` `RenderFragment<T>`en définissant les paramètres des composants de type ou .</span><span class="sxs-lookup"><span data-stu-id="51c88-304">Blazor components can also be templated by defining component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="51c88-305">A `RenderFragment` représente un morceau de marge Razor qui peut ensuite être rendu par le composant.</span><span class="sxs-lookup"><span data-stu-id="51c88-305">A `RenderFragment` represents a chunk of Razor markup that can then be rendered by the component.</span></span> <span data-ttu-id="51c88-306">A `RenderFragment<T>` est un morceau de markup Razor qui prend un paramètre qui peut être spécifié lorsque le fragment de rendu est rendu.</span><span class="sxs-lookup"><span data-stu-id="51c88-306">A `RenderFragment<T>` is a chunk of Razor markup that takes a parameter that can be specified when the render fragment is rendered.</span></span>

### <a name="child-content"></a><span data-ttu-id="51c88-307">Contenu pour enfants</span><span class="sxs-lookup"><span data-stu-id="51c88-307">Child content</span></span>

<span data-ttu-id="51c88-308">Les composants Blazor peuvent capturer `RenderFragment` leur contenu enfant comme un et le rendre dans le cadre du rendu composant.</span><span class="sxs-lookup"><span data-stu-id="51c88-308">Blazor components can capture their child content as a `RenderFragment` and render that content as part of the component rendering.</span></span> <span data-ttu-id="51c88-309">Pour capturer le contenu de l’enfant, définissez un paramètre de composant du type `RenderFragment` et nommez-le `ChildContent`.</span><span class="sxs-lookup"><span data-stu-id="51c88-309">To capture child content, define a component parameter of type `RenderFragment` and name it `ChildContent`.</span></span>

<span data-ttu-id="51c88-310">*ChildContentComponent.razor*</span><span class="sxs-lookup"><span data-stu-id="51c88-310">*ChildContentComponent.razor*</span></span>

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

<span data-ttu-id="51c88-311">Un composant parent peut ensuite fournir du contenu pour enfants à l’aide d’une syntaxe Razor normale.</span><span class="sxs-lookup"><span data-stu-id="51c88-311">A parent component can then supply child content using normal Razor syntax.</span></span>

```razor
<ChildContentComponent>
    <p>The time is @DateTime.Now</p>
</ChildContentComponent>
```

### <a name="template-parameters"></a><span data-ttu-id="51c88-312">Paramètres de modèle</span><span class="sxs-lookup"><span data-stu-id="51c88-312">Template parameters</span></span>

<span data-ttu-id="51c88-313">Un composant Blazor modélisateur peut également `RenderFragment` définir `RenderFragment<T>`plusieurs paramètres de composants de type ou .</span><span class="sxs-lookup"><span data-stu-id="51c88-313">A templated Blazor component can also define multiple component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="51c88-314">Le paramètre `RenderFragment<T>` d’un peut être spécifié lorsqu’il est invoqué.</span><span class="sxs-lookup"><span data-stu-id="51c88-314">The parameter for a `RenderFragment<T>` can be specified when it's invoked.</span></span> <span data-ttu-id="51c88-315">Pour spécifier un paramètre `@typeparam` de type générique pour un composant, utilisez la directive Razor.</span><span class="sxs-lookup"><span data-stu-id="51c88-315">To specify a generic type parameter for a component, use the `@typeparam` Razor directive.</span></span>

<span data-ttu-id="51c88-316">*SimpleListView.razor*</span><span class="sxs-lookup"><span data-stu-id="51c88-316">*SimpleListView.razor*</span></span>

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

<span data-ttu-id="51c88-317">Lors de l’utilisation d’un composant modélé, les paramètres du modèle peuvent être spécifiés à l’aide d’éléments pour enfants qui correspondent aux noms des paramètres.</span><span class="sxs-lookup"><span data-stu-id="51c88-317">When using a templated component, the template parameters can be specified using child elements that match the names of the parameters.</span></span> <span data-ttu-id="51c88-318">Les arguments `RenderFragment<T>` de composants de type `context`adoptés comme éléments ont un paramètre implicite nommé .</span><span class="sxs-lookup"><span data-stu-id="51c88-318">Component arguments of type `RenderFragment<T>` passed as elements have an implicit parameter named `context`.</span></span> <span data-ttu-id="51c88-319">Vous pouvez modifier le nom de `Context` ce paramètre d’implémentaire en utilisant l’attribut sur l’élément enfant.</span><span class="sxs-lookup"><span data-stu-id="51c88-319">You can change the name of this implement parameter using the `Context` attribute on the child element.</span></span> <span data-ttu-id="51c88-320">Tous les paramètres de type générique peuvent être spécifiés à l’aide d’un attribut qui correspond au nom du paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="51c88-320">Any generic type parameters can be specified using an attribute that matches the name of the type parameter.</span></span> <span data-ttu-id="51c88-321">Le paramètre de type sera déduit si possible :</span><span class="sxs-lookup"><span data-stu-id="51c88-321">The type parameter will be inferred if possible:</span></span>

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

<span data-ttu-id="51c88-322">La sortie de ce composant ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="51c88-322">The output of this component looks like this:</span></span>

```html
<h1>My list</h1>
<ul>
    <li>The message is: message1</li>
    <li>The message is: message2</li>
<ul>
```

## <a name="code-behind"></a><span data-ttu-id="51c88-323">Code-behind</span><span class="sxs-lookup"><span data-stu-id="51c88-323">Code-behind</span></span>

<span data-ttu-id="51c88-324">Un composant Blazor est généralement écrit dans un seul fichier *.razor.*</span><span class="sxs-lookup"><span data-stu-id="51c88-324">A Blazor component is typically authored in a single *.razor* file.</span></span> <span data-ttu-id="51c88-325">Cependant, il est également possible de séparer le code et le balisage à l’aide d’un fichier de code.derrière.</span><span class="sxs-lookup"><span data-stu-id="51c88-325">However, it's also possible to separate the code and markup using a code-behind file.</span></span> <span data-ttu-id="51c88-326">Pour utiliser un fichier de composants, ajoutez un fichier CMD qui correspond au nom de fichier du fichier des composants, mais avec une extension *.cs* ajoutée *(Counter.razor.cs*).</span><span class="sxs-lookup"><span data-stu-id="51c88-326">To use a component file, add a C# file that matches the file name of the component file but with a *.cs* extension added (*Counter.razor.cs*).</span></span> <span data-ttu-id="51c88-327">Utilisez le fichier C pour définir une classe de base pour le composant.</span><span class="sxs-lookup"><span data-stu-id="51c88-327">Use the C# file to define a base class for the component.</span></span> <span data-ttu-id="51c88-328">Vous pouvez nommer la classe de base tout ce que vous souhaitez, mais il est `Base` courant de`CounterBase`nommer la classe la même que la classe des composants, mais avec une extension ajoutée ( ).</span><span class="sxs-lookup"><span data-stu-id="51c88-328">You can name the base class anything you'd like, but it's common to name the class the same as the component class, but with a `Base` extension added (`CounterBase`).</span></span> <span data-ttu-id="51c88-329">La classe basée sur les `ComponentBase`composants doit également dériver de .</span><span class="sxs-lookup"><span data-stu-id="51c88-329">The component-based class must also derive from `ComponentBase`.</span></span> <span data-ttu-id="51c88-330">Ensuite, dans le fichier du `@inherits` composant Razor, ajouter la`@inherits CounterBase`directive pour spécifier la classe de base pour le composant ().</span><span class="sxs-lookup"><span data-stu-id="51c88-330">Then, in the Razor component file, add the `@inherits` directive to specify the base class for the component (`@inherits CounterBase`).</span></span>

<span data-ttu-id="51c88-331">*Counter.razor (en)*</span><span class="sxs-lookup"><span data-stu-id="51c88-331">*Counter.razor*</span></span>

```razor
@inherits CounterBase

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>
```

<span data-ttu-id="51c88-332">*Counter.razor.cs*</span><span class="sxs-lookup"><span data-stu-id="51c88-332">*Counter.razor.cs*</span></span>

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

<span data-ttu-id="51c88-333">La visibilité des membres du composant dans `protected` la `public` classe de base doit être ou être visible par la classe des composants.</span><span class="sxs-lookup"><span data-stu-id="51c88-333">The visibility of the component's members in the base class must be `protected` or `public` to be visible to the component class.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="51c88-334">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="51c88-334">Additional resources</span></span>

<span data-ttu-id="51c88-335">Le précédent n’est pas un traitement exhaustif de tous les aspects des composants Blazor.</span><span class="sxs-lookup"><span data-stu-id="51c88-335">The preceding isn't an exhaustive treatment of all aspects of Blazor components.</span></span> <span data-ttu-id="51c88-336">Pour plus d’informations sur la façon de [créer et d’utiliser ASP.NET composants Core Razor](/aspnet/core/blazor/components), voir la documentation Blazor.</span><span class="sxs-lookup"><span data-stu-id="51c88-336">For more information on how to [Create and use ASP.NET Core Razor components](/aspnet/core/blazor/components), see the Blazor documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="51c88-337">[Suivant précédent](app-startup.md)
>[Next](pages-routing-layouts.md)</span><span class="sxs-lookup"><span data-stu-id="51c88-337">[Previous](app-startup.md)
[Next](pages-routing-layouts.md)</span></span>
