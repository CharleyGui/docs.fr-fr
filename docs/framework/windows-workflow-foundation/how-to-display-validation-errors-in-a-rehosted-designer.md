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
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a>Procédure : afficher les erreurs de validation dans un concepteur réhébergé

Cette rubrique explique comment récupérer et publier des erreurs de validation dans un Concepteur de flux de travail Windows réhébergé. Cette opération fournit une procédure permettant de confirmer la validité d'un workflow dans un concepteur réhébergé.  
  
 Cette tâche comprend deux parties. La première consiste à fournir une implémentation <xref:System.Activities.Presentation.Validation.IValidationErrorService>.  Il existe une méthode critique pour effectuer une implémentation sur cette interface, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> qui vous passera une liste d'objets <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> contenant les informations relatives aux erreurs dans le journal de débogage.  Après avoir implémenté l'interface, vous récupérez les informations d'erreur en publiant une instance de cette implémentation dans le contexte d'édition.  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a>Implémenter l'interface IValidationErrorService  
  
1. Voici un exemple de code pour une implémentation simple qui écrira les erreurs de validation dans le journal de débogage.  
  
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
  
### <a name="publishing-to-the-editing-context"></a>Publication dans le contexte d'édition  
  
1. Voici le code qui publiera cette implémentation dans le contexte d'édition.  
  
    ```csharp  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
