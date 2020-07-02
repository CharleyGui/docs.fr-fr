---
ms.openlocfilehash: ddc98448101c65003001ad05e67f29d75d99ad44
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616052"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a>WorkflowDesigner.Load ne supprime pas la propriété de symbole

#### <a name="details"></a>Détails

Quand vous ciblez .NET Framework 4.5 dans le Concepteur de flux de travail et que vous chargez un flux de travail 3.5 réhébergé avec la méthode <xref:System.Activities.Presentation.WorkflowDesigner.Load>, une exception <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=fullName> est levée quand vous enregistrez le flux de travail.

#### <a name="suggestion"></a>Suggestion

Ce bogue se produit uniquement quand vous reciblez .NET Framework 4.5 dans le Concepteur de flux de travail. Vous pouvez donc contourner ce problème en définissant `WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName` sur .NET Framework 4.0. Vous pouvez également éviter le problème en utilisant la méthode <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> au lieu de <xref:System.Activities.Presentation.WorkflowDesigner.Load> pour charger le flux de travail.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Majeure       |
| Version | 4,5         |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType>
