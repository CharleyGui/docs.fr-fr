---
title: Formulaires et validation
description: Découvrez comment créer des formulaires avec la validation côté client dans éblouissant.
author: danroth27
ms.author: daroth
ms.date: 09/19/2019
ms.openlocfilehash: c30db5e06d36a6d15301835fe782b21058a80592
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088085"
---
# <a name="forms-and-validation"></a><span data-ttu-id="38321-103">Formulaires et validation</span><span class="sxs-lookup"><span data-stu-id="38321-103">Forms and validation</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="38321-104">ASP.NET Web Forms Framework comprend un ensemble de contrôles serveur de validation qui gèrent la validation des entrées utilisateur entrées dans un formulaire (`RequiredFieldValidator`, `CompareValidator`, `RangeValidator`, etc.).</span><span class="sxs-lookup"><span data-stu-id="38321-104">The ASP.NET Web Forms framework includes a set of validation server controls that handle validating user input entered into a form (`RequiredFieldValidator`, `CompareValidator`, `RangeValidator`, and so on).</span></span> <span data-ttu-id="38321-105">ASP.NET Web Forms Framework prend également en charge la liaison de modèle et la validation du modèle en fonction des annotations de données (`[Required]`, `[StringLength]`, `[Range]`, etc.).</span><span class="sxs-lookup"><span data-stu-id="38321-105">The ASP.NET Web Forms framework also supports model binding and validating the model based on data annotations (`[Required]`, `[StringLength]`, `[Range]`, and so on).</span></span> <span data-ttu-id="38321-106">La logique de validation peut être appliquée à la fois sur le serveur et sur le client à l’aide d’une validation JavaScript discrète.</span><span class="sxs-lookup"><span data-stu-id="38321-106">The validation logic can be enforced both on the server and on the client using unobtrusive JavaScript-based validation.</span></span> <span data-ttu-id="38321-107">Le contrôle serveur `ValidationSummary` est utilisé pour afficher un résumé des erreurs de validation à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="38321-107">The `ValidationSummary` server control is used to display a summary of the validation errors to the user.</span></span>

<span data-ttu-id="38321-108">Éblouissant prend en charge le partage de logique de validation entre le client et le serveur.</span><span class="sxs-lookup"><span data-stu-id="38321-108">Blazor supports the sharing of validation logic between both the client and the server.</span></span> <span data-ttu-id="38321-109">ASP.NET fournit des implémentations JavaScript prédéfinies de nombreuses validations de serveur courantes.</span><span class="sxs-lookup"><span data-stu-id="38321-109">ASP.NET provides pre-built JavaScript implementations of many common server validations.</span></span> <span data-ttu-id="38321-110">Dans de nombreux cas, le développeur doit toujours écrire du code JavaScript pour implémenter entièrement sa logique de validation propre à l’application.</span><span class="sxs-lookup"><span data-stu-id="38321-110">In many cases, the developer still has to write JavaScript to fully implement their app-specific validation logic.</span></span> <span data-ttu-id="38321-111">Les mêmes types de modèle, annotations de données et logique de validation peuvent être utilisés sur le serveur et le client.</span><span class="sxs-lookup"><span data-stu-id="38321-111">The same model types, data annotations, and validation logic can be used on both the server and client.</span></span>

<span data-ttu-id="38321-112">Éblouissant fournit un ensemble de composants d’entrée.</span><span class="sxs-lookup"><span data-stu-id="38321-112">Blazor provides a set of input components.</span></span> <span data-ttu-id="38321-113">Les composants d’entrée gèrent les données de champ de liaison à un modèle et valident l’entrée utilisateur lorsque le formulaire est envoyé.</span><span class="sxs-lookup"><span data-stu-id="38321-113">The input components handle binding field data to a model and validating the user input when the form is submitted.</span></span>

|<span data-ttu-id="38321-114">Composant d’entrée</span><span class="sxs-lookup"><span data-stu-id="38321-114">Input component</span></span>|<span data-ttu-id="38321-115">Élément HTML rendu</span><span class="sxs-lookup"><span data-stu-id="38321-115">Rendered HTML element</span></span>    |
|---------------|-------------------------|
|`InputCheckbox`|`<input type="checkbox">`|
|`InputDate`    |`<input type="date">`    |
|`InputNumber`  |`<input type="number">`  |
|`InputSelect`  |`<select>`               |
|`InputText`    |`<input>`                |
|`InputTextArea`|`<textarea>`             |

<span data-ttu-id="38321-116">Le composant `EditForm` encapsule ces composants d’entrée et orchestre le processus de validation par le biais d’une `EditContext`.</span><span class="sxs-lookup"><span data-stu-id="38321-116">The `EditForm` component wraps these input components and orchestrates the validation process through an `EditContext`.</span></span> <span data-ttu-id="38321-117">Lorsque vous créez un `EditForm`, vous spécifiez l’instance de modèle à lier à l’aide du paramètre `Model`.</span><span class="sxs-lookup"><span data-stu-id="38321-117">When creating an `EditForm`, you specify what model instance to bind to using the `Model` parameter.</span></span> <span data-ttu-id="38321-118">La validation s’effectue généralement à l’aide d’annotations de données et est extensible.</span><span class="sxs-lookup"><span data-stu-id="38321-118">Validation is typically done using data annotations, and it's extensible.</span></span> <span data-ttu-id="38321-119">Pour activer la validation basée sur les annotations de données, ajoutez le composant `DataAnnotationsValidator` en tant qu’enfant du `EditForm`.</span><span class="sxs-lookup"><span data-stu-id="38321-119">To enable data annotation-based validation, add the `DataAnnotationsValidator` component as a child of the `EditForm`.</span></span> <span data-ttu-id="38321-120">Le composant `EditForm` fournit un événement pratique pour gérer les envois valides (`OnValidSubmit`) et non valides (`OnInvalidSubmit`).</span><span class="sxs-lookup"><span data-stu-id="38321-120">The `EditForm` component provides a convenient event for handling valid (`OnValidSubmit`) and invalid (`OnInvalidSubmit`) submissions.</span></span> <span data-ttu-id="38321-121">Il y a également un événement `OnSubmit` plus générique qui vous permet de déclencher et de gérer vous-même la validation.</span><span class="sxs-lookup"><span data-stu-id="38321-121">There's also a more generic `OnSubmit` event that lets you trigger and handle the validation yourself.</span></span>

<span data-ttu-id="38321-122">Pour afficher un résumé des erreurs de validation, utilisez le composant `ValidationSummary`.</span><span class="sxs-lookup"><span data-stu-id="38321-122">To display a validation error summary, use the `ValidationSummary` component.</span></span> <span data-ttu-id="38321-123">Pour afficher les messages de validation pour un champ d’entrée spécifique, utilisez le composant `ValidationMessage`, en spécifiant une expression lambda pour le paramètre `For` qui pointe vers le membre de modèle approprié.</span><span class="sxs-lookup"><span data-stu-id="38321-123">To display validation messages for a specific input field, use the `ValidationMessage` component, specifying a lambda expression for the `For` parameter that points to the appropriate model member.</span></span>

<span data-ttu-id="38321-124">Le type de modèle suivant définit plusieurs règles de validation à l’aide d’annotations de données :</span><span class="sxs-lookup"><span data-stu-id="38321-124">The following model type defines several validation rules using data annotations:</span></span>

```csharp
using System;
using System.ComponentModel.DataAnnotations;

public class Starship
{
    [Required]
    [StringLength(16,
        ErrorMessage = "Identifier too long (16 character limit).")]
    public string Identifier { get; set; }

    public string Description { get; set; }

    [Required]
    public string Classification { get; set; }

    [Range(1, 100000,
        ErrorMessage = "Accommodation invalid (1-100000).")]
    public int MaximumAccommodation { get; set; }

    [Required]
    [Range(typeof(bool), "true", "true",
        ErrorMessage = "This form disallows unapproved ships.")]
    public bool IsValidatedDesign { get; set; }

    [Required]
    public DateTime ProductionDate { get; set; }
}
```

<span data-ttu-id="38321-125">Le composant suivant illustre la création d’un formulaire dans éblouissant en fonction du type de modèle `Starship` :</span><span class="sxs-lookup"><span data-stu-id="38321-125">The following component demonstrates building a form in Blazor based on the `Starship` model type:</span></span>

```razor
<h1>New Ship Entry Form</h1>

<EditForm Model="@starship" OnValidSubmit="@HandleValidSubmit">
    <DataAnnotationsValidator />
    <ValidationSummary />

    <p>
        <label for="identifier">Identifier: </label>
        <InputText id="identifier" @bind-Value="starship.Identifier" />
        <ValidationMessage For="() => starship.Identifier" />
    </p>
    <p>
        <label for="description">Description (optional): </label>
        <InputTextArea id="description" @bind-Value="starship.Description" />
    </p>
    <p>
        <label for="classification">Primary Classification: </label>
        <InputSelect id="classification" @bind-Value="starship.Classification">
            <option value="">Select classification ...</option>
            <option value="Exploration">Exploration</option>
            <option value="Diplomacy">Diplomacy</option>
            <option value="Defense">Defense</option>
        </InputSelect>
        <ValidationMessage For="() => starship.Classification" />
    </p>
    <p>
        <label for="accommodation">Maximum Accommodation: </label>
        <InputNumber id="accommodation" @bind-Value="starship.MaximumAccommodation" />
        <ValidationMessage For="() => starship.MaximumAccommodation" />
    </p>
    <p>
        <label for="valid">Engineering Approval: </label>
        <InputCheckbox id="valid" @bind-Value="starship.IsValidatedDesign" />
        <ValidationMessage For="() => starship.IsValidatedDesign" />
    </p>
    <p>
        <label for="productionDate">Production Date: </label>
        <InputDate id="productionDate" @bind-Value="starship.ProductionDate" />
        <ValidationMessage For="() => starship.ProductionDate" />
    </p>

    <button type="submit">Submit</button>
</EditForm>

@code {
    private Starship starship = new Starship();

    private void HandleValidSubmit()
    {
        // Save the data
    }
}
```

<span data-ttu-id="38321-126">Après l’envoi du formulaire, les données liées au modèle n’ont pas été enregistrées dans un magasin de données, comme une base de données.</span><span class="sxs-lookup"><span data-stu-id="38321-126">After the form submission, the model-bound data hasn't been saved to any data store, like a database.</span></span> <span data-ttu-id="38321-127">Dans une application de webassembly éblouissant, les données doivent être envoyées au serveur.</span><span class="sxs-lookup"><span data-stu-id="38321-127">In a Blazor WebAssembly app, the data must be sent to the server.</span></span> <span data-ttu-id="38321-128">Par exemple, à l’aide d’une requête HTTP POSTALe.</span><span class="sxs-lookup"><span data-stu-id="38321-128">For example, using an HTTP POST request.</span></span> <span data-ttu-id="38321-129">Dans une application de serveur éblouissant, les données sont déjà sur le serveur, mais elles doivent être persistantes.</span><span class="sxs-lookup"><span data-stu-id="38321-129">In a Blazor Server app, the data is already on the server, but it must be persisted.</span></span> <span data-ttu-id="38321-130">La gestion de l’accès aux données dans les applications éblouissantes est l’objet de la section relative aux [données](data.md) .</span><span class="sxs-lookup"><span data-stu-id="38321-130">Handling data access in Blazor apps is the subject of the [Dealing with data](data.md) section.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="38321-131">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="38321-131">Additional resources</span></span>

<span data-ttu-id="38321-132">Pour plus d’informations sur les [formulaires et la validation](/aspnet/core/blazor/forms-validation) dans les applications éblouissantes, consultez la documentation de éblouissant.</span><span class="sxs-lookup"><span data-stu-id="38321-132">For more information on [forms and validation](/aspnet/core/blazor/forms-validation) in Blazor apps, see the Blazor documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="38321-133">[Précédent](state-management.md)
>[Suivant](data.md)</span><span class="sxs-lookup"><span data-stu-id="38321-133">[Previous](state-management.md)
[Next](data.md)</span></span>
