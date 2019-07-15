---
ms.openlocfilehash: 97a92c6bce80b93e9a8bdd863bf881631eaffb27
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804642"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a><span data-ttu-id="4421e-101">WorkflowDesigner.Load ne supprime pas la propriété de symbole</span><span class="sxs-lookup"><span data-stu-id="4421e-101">WorkflowDesigner.Load doesn't remove symbol property</span></span>

|   |   |
|---|---|
|<span data-ttu-id="4421e-102">Détails</span><span class="sxs-lookup"><span data-stu-id="4421e-102">Details</span></span>|<span data-ttu-id="4421e-103">Quand vous ciblez .NET Framework 4.5 dans le Concepteur de flux de travail et que vous chargez un flux de travail 3.5 réhébergé avec la méthode <xref:System.Activities.Presentation.WorkflowDesigner.Load>, une exception <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> est levée quand vous enregistrez le flux de travail.</span><span class="sxs-lookup"><span data-stu-id="4421e-103">When targeting the .NET Framework 4.5 in the workflow designer, and loading a re-hosted 3.5 workflow with the <xref:System.Activities.Presentation.WorkflowDesigner.Load> method, a <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> is thrown while saving the workflow.</span></span>|
|<span data-ttu-id="4421e-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="4421e-104">Suggestion</span></span>|<span data-ttu-id="4421e-105">Ce bogue se produit uniquement quand vous reciblez .NET Framework 4.5 dans le Concepteur de flux de travail. Vous pouvez donc contourner ce problème en définissant <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> sur .NET Framework 4.0. Vous pouvez également éviter le problème en utilisant la méthode <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> au lieu de <xref:System.Activities.Presentation.WorkflowDesigner.Load> pour charger le flux de travail.</span><span class="sxs-lookup"><span data-stu-id="4421e-105">This bug only manifests when targeting .NET Framework 4.5 in the workflow designer, so it can be worked around by setting the <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> to the 4.0 .NET Framework.Alternatively, the issue may be avoided by using the <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> method to load the workflow, instead of <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span></span>|
|<span data-ttu-id="4421e-106">Portée</span><span class="sxs-lookup"><span data-stu-id="4421e-106">Scope</span></span>|<span data-ttu-id="4421e-107">Majeur</span><span class="sxs-lookup"><span data-stu-id="4421e-107">Major</span></span>|
|<span data-ttu-id="4421e-108">Version</span><span class="sxs-lookup"><span data-stu-id="4421e-108">Version</span></span>|<span data-ttu-id="4421e-109">4.5</span><span class="sxs-lookup"><span data-stu-id="4421e-109">4.5</span></span>|
|<span data-ttu-id="4421e-110">Type</span><span class="sxs-lookup"><span data-stu-id="4421e-110">Type</span></span>|<span data-ttu-id="4421e-111">Reciblage</span><span class="sxs-lookup"><span data-stu-id="4421e-111">Retargeting</span></span>|
|<span data-ttu-id="4421e-112">API affectées</span><span class="sxs-lookup"><span data-stu-id="4421e-112">Affected APIs</span></span>|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|

