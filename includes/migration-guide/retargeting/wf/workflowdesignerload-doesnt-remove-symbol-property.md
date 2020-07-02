---
ms.openlocfilehash: ddc98448101c65003001ad05e67f29d75d99ad44
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616052"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a><span data-ttu-id="2beb7-101">WorkflowDesigner.Load ne supprime pas la propriété de symbole</span><span class="sxs-lookup"><span data-stu-id="2beb7-101">WorkflowDesigner.Load doesn't remove symbol property</span></span>

#### <a name="details"></a><span data-ttu-id="2beb7-102">Détails</span><span class="sxs-lookup"><span data-stu-id="2beb7-102">Details</span></span>

<span data-ttu-id="2beb7-103">Quand vous ciblez .NET Framework 4.5 dans le Concepteur de flux de travail et que vous chargez un flux de travail 3.5 réhébergé avec la méthode <xref:System.Activities.Presentation.WorkflowDesigner.Load>, une exception <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=fullName> est levée quand vous enregistrez le flux de travail.</span><span class="sxs-lookup"><span data-stu-id="2beb7-103">When targeting the .NET Framework 4.5 in the workflow designer, and loading a re-hosted 3.5 workflow with the <xref:System.Activities.Presentation.WorkflowDesigner.Load> method, a <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=fullName> is thrown while saving the workflow.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2beb7-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="2beb7-104">Suggestion</span></span>

<span data-ttu-id="2beb7-105">Ce bogue se produit uniquement quand vous reciblez .NET Framework 4.5 dans le Concepteur de flux de travail. Vous pouvez donc contourner ce problème en définissant `WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName` sur .NET Framework 4.0. Vous pouvez également éviter le problème en utilisant la méthode <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> au lieu de <xref:System.Activities.Presentation.WorkflowDesigner.Load> pour charger le flux de travail.</span><span class="sxs-lookup"><span data-stu-id="2beb7-105">This bug only manifests when targeting .NET Framework 4.5 in the workflow designer, so it can be worked around by setting the `WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName` to the 4.0 .NET Framework.Alternatively, the issue may be avoided by using the <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> method to load the workflow, instead of <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span></span>

| <span data-ttu-id="2beb7-106">Nom</span><span class="sxs-lookup"><span data-stu-id="2beb7-106">Name</span></span>    | <span data-ttu-id="2beb7-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="2beb7-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2beb7-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="2beb7-108">Scope</span></span>   | <span data-ttu-id="2beb7-109">Majeure</span><span class="sxs-lookup"><span data-stu-id="2beb7-109">Major</span></span>       |
| <span data-ttu-id="2beb7-110">Version</span><span class="sxs-lookup"><span data-stu-id="2beb7-110">Version</span></span> | <span data-ttu-id="2beb7-111">4,5</span><span class="sxs-lookup"><span data-stu-id="2beb7-111">4.5</span></span>         |
| <span data-ttu-id="2beb7-112">Type</span><span class="sxs-lookup"><span data-stu-id="2beb7-112">Type</span></span>    | <span data-ttu-id="2beb7-113">Reciblage</span><span class="sxs-lookup"><span data-stu-id="2beb7-113">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="2beb7-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="2beb7-114">Affected APIs</span></span>

- <xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType>
