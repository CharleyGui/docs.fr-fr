---
title: 'Procédure : afficher les erreurs de validation dans un concepteur réhébergé'
ms.date: 03/30/2017
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
ms.openlocfilehash: ccdb8941f46683dd1fd12387c0c5db2abe1d8dec
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280037"
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a><span data-ttu-id="05c16-102">Procédure : afficher les erreurs de validation dans un concepteur réhébergé</span><span class="sxs-lookup"><span data-stu-id="05c16-102">How to: Display Validation Errors in a Rehosted Designer</span></span>

<span data-ttu-id="05c16-103">Cette rubrique explique comment récupérer et publier des erreurs de validation dans un Concepteur de flux de travail Windows réhébergé.</span><span class="sxs-lookup"><span data-stu-id="05c16-103">This topic describes how to retrieve and publish validation errors in a rehosted Windows Workflow Designer.</span></span> <span data-ttu-id="05c16-104">Cette opération fournit une procédure permettant de confirmer la validité d'un workflow dans un concepteur réhébergé.</span><span class="sxs-lookup"><span data-stu-id="05c16-104">This provides us with a procedure to confirm that a workflow in a rehosted designer is valid.</span></span>  
  
 <span data-ttu-id="05c16-105">Cette tâche comprend deux parties.</span><span class="sxs-lookup"><span data-stu-id="05c16-105">This task has two parts.</span></span> <span data-ttu-id="05c16-106">La première consiste à fournir une implémentation <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span><span class="sxs-lookup"><span data-stu-id="05c16-106">The first is to provide an implementation <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span></span>  <span data-ttu-id="05c16-107">Il existe une méthode critique pour effectuer une implémentation sur cette interface, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> qui vous passera une liste d'objets <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> contenant les informations relatives aux erreurs dans le journal de débogage.</span><span class="sxs-lookup"><span data-stu-id="05c16-107">There is one critical method to implement on this interface, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> which will pass you a list of <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> objects containing information about the errors to the debug log.</span></span>  <span data-ttu-id="05c16-108">Après avoir implémenté l'interface, vous récupérez les informations d'erreur en publiant une instance de cette implémentation dans le contexte d'édition.</span><span class="sxs-lookup"><span data-stu-id="05c16-108">After implementing the interface, you retrieve the error information by publishing an instance of that implementation to the editing context.</span></span>  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a><span data-ttu-id="05c16-109">Implémenter l'interface IValidationErrorService</span><span class="sxs-lookup"><span data-stu-id="05c16-109">Implement the IValidationErrorService Interface</span></span>  
  
1. <span data-ttu-id="05c16-110">Voici un exemple de code pour une implémentation simple qui écrira les erreurs de validation dans le journal de débogage.</span><span class="sxs-lookup"><span data-stu-id="05c16-110">Here is a code sample for a simple implementation that will write out the validation errors to the debug log.</span></span>  
  
    ```csharp  
    using System.Activities.Presentation.Validation;  
    using System.Collections.Generic;  
    using System.Diagnostics;  
    using System.Linq;  
  
    namespace VariableFinderShell  
    {  
        class DebugValidationErrorService : IValidationErrorService  
        {  
            public void ShowValidationErrors(IList<ValidationErrorInfo> errors)  
            {  
                errors.ToList().ForEach(vei => Debug.WriteLine($"Error: {vei.Message}"));  
            }  
        }  
    }  
    ```  
  
### <a name="publishing-to-the-editing-context"></a><span data-ttu-id="05c16-111">Publication dans le contexte d'édition</span><span class="sxs-lookup"><span data-stu-id="05c16-111">Publishing to the Editing Context</span></span>  
  
1. <span data-ttu-id="05c16-112">Voici le code qui publiera cette implémentation dans le contexte d'édition.</span><span class="sxs-lookup"><span data-stu-id="05c16-112">Here is the code that will publish this to the editing context.</span></span>  
  
    ```csharp  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
