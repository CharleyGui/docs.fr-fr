---
ms.openlocfilehash: 19c613bf48479cb1e52531a4d6594db8ad89b8f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804642"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a>WorkflowDesigner.Load ne supprime pas la propriété de symbole

|   |   |
|---|---|
|Détails|Quand vous ciblez .NET Framework 4.5 dans le Concepteur de flux de travail et que vous chargez un flux de travail 3.5 réhébergé avec la méthode <xref:System.Activities.Presentation.WorkflowDesigner.Load>, une exception <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> est levée quand vous enregistrez le flux de travail.|
|Suggestion|Ce bogue se produit uniquement quand vous reciblez .NET Framework 4.5 dans le Concepteur de flux de travail. Vous pouvez donc contourner ce problème en définissant <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> sur .NET Framework 4.0. Vous pouvez également éviter le problème en utilisant la méthode <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> au lieu de <xref:System.Activities.Presentation.WorkflowDesigner.Load> pour charger le flux de travail.|
|Étendue|Majeure|
|Version|4.5|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|
