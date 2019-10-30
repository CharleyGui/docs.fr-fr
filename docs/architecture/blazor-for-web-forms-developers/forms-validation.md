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
# <a name="forms-and-validation"></a>Formulaires et validation

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

ASP.NET Web Forms Framework comprend un ensemble de contrôles serveur de validation qui gèrent la validation des entrées utilisateur entrées dans un formulaire (`RequiredFieldValidator`, `CompareValidator`, `RangeValidator`, etc.). ASP.NET Web Forms Framework prend également en charge la liaison de modèle et la validation du modèle en fonction des annotations de données (`[Required]`, `[StringLength]`, `[Range]`, etc.). La logique de validation peut être appliquée à la fois sur le serveur et sur le client à l’aide d’une validation JavaScript discrète. Le contrôle serveur `ValidationSummary` est utilisé pour afficher un résumé des erreurs de validation à l’utilisateur.

Éblouissant prend en charge le partage de logique de validation entre le client et le serveur. ASP.NET fournit des implémentations JavaScript prédéfinies de nombreuses validations de serveur courantes. Dans de nombreux cas, le développeur doit toujours écrire du code JavaScript pour implémenter entièrement sa logique de validation propre à l’application. Les mêmes types de modèle, annotations de données et logique de validation peuvent être utilisés sur le serveur et le client.

Éblouissant fournit un ensemble de composants d’entrée. Les composants d’entrée gèrent les données de champ de liaison à un modèle et valident l’entrée utilisateur lorsque le formulaire est envoyé.

|Composant d’entrée|Élément HTML rendu    |
|---------------|-------------------------|
|`InputCheckbox`|`<input type="checkbox">`|
|`InputDate`    |`<input type="date">`    |
|`InputNumber`  |`<input type="number">`  |
|`InputSelect`  |`<select>`               |
|`InputText`    |`<input>`                |
|`InputTextArea`|`<textarea>`             |

Le composant `EditForm` encapsule ces composants d’entrée et orchestre le processus de validation par le biais d’une `EditContext`. Lorsque vous créez un `EditForm`, vous spécifiez l’instance de modèle à lier à l’aide du paramètre `Model`. La validation s’effectue généralement à l’aide d’annotations de données et est extensible. Pour activer la validation basée sur les annotations de données, ajoutez le composant `DataAnnotationsValidator` en tant qu’enfant du `EditForm`. Le composant `EditForm` fournit un événement pratique pour gérer les envois valides (`OnValidSubmit`) et non valides (`OnInvalidSubmit`). Il y a également un événement `OnSubmit` plus générique qui vous permet de déclencher et de gérer vous-même la validation.

Pour afficher un résumé des erreurs de validation, utilisez le composant `ValidationSummary`. Pour afficher les messages de validation pour un champ d’entrée spécifique, utilisez le composant `ValidationMessage`, en spécifiant une expression lambda pour le paramètre `For` qui pointe vers le membre de modèle approprié.

Le type de modèle suivant définit plusieurs règles de validation à l’aide d’annotations de données :

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

Le composant suivant illustre la création d’un formulaire dans éblouissant en fonction du type de modèle `Starship` :

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

Après l’envoi du formulaire, les données liées au modèle n’ont pas été enregistrées dans un magasin de données, comme une base de données. Dans une application de webassembly éblouissant, les données doivent être envoyées au serveur. Par exemple, à l’aide d’une requête HTTP POSTALe. Dans une application de serveur éblouissant, les données sont déjà sur le serveur, mais elles doivent être persistantes. La gestion de l’accès aux données dans les applications éblouissantes est l’objet de la section relative aux [données](data.md) .

## <a name="additional-resources"></a>Ressources supplémentaires

Pour plus d’informations sur les [formulaires et la validation](/aspnet/core/blazor/forms-validation) dans les applications éblouissantes, consultez la documentation de éblouissant.

>[!div class="step-by-step"]
>[Précédent](state-management.md)
>[Suivant](data.md)
