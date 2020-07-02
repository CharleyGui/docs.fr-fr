---
ms.openlocfilehash: b6cb7edcd6bed50efdf59f3321320ac8cd1b1ab8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617228"
---
### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a><span data-ttu-id="cc279-101">Certaines API WorkFlow de glisser-déplacer sont obsolètes</span><span class="sxs-lookup"><span data-stu-id="cc279-101">Some WorkFlow drag-and-drop APIs are obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="cc279-102">Détails</span><span class="sxs-lookup"><span data-stu-id="cc279-102">Details</span></span>

<span data-ttu-id="cc279-103">Cette API WorkFlow de glisser-déplacer est obsolète et génère des avertissements du compilateur si l’application est régénérée avec la version 4.5.</span><span class="sxs-lookup"><span data-stu-id="cc279-103">This WorkFlow drag-and-drop API is obsolete and will cause compiler warnings if the app is rebuilt against 4.5.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="cc279-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="cc279-104">Suggestion</span></span>

<span data-ttu-id="cc279-105">Utilisez à la place les nouvelles API <xref:System.Activities.Presentation.DragDropHelper?displayProperty=fullName> qui prennent en charge les opérations avec plusieurs objets.</span><span class="sxs-lookup"><span data-stu-id="cc279-105">New <xref:System.Activities.Presentation.DragDropHelper?displayProperty=fullName> APIs that support operations with multiple objects should be used instead.</span></span> <span data-ttu-id="cc279-106">Vous pouvez également supprimer les avertissements de génération ou les éviter en utilisant un compilateur plus ancien.</span><span class="sxs-lookup"><span data-stu-id="cc279-106">Alternatively, the build warnings can be suppressed or they can be avoided by using an older compiler.</span></span> <span data-ttu-id="cc279-107">Ces API sont toujours prises en charge.</span><span class="sxs-lookup"><span data-stu-id="cc279-107">The APIs are still supported.</span></span>

| <span data-ttu-id="cc279-108">Nom</span><span class="sxs-lookup"><span data-stu-id="cc279-108">Name</span></span>    | <span data-ttu-id="cc279-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="cc279-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cc279-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="cc279-110">Scope</span></span>   | <span data-ttu-id="cc279-111">Secondaire</span><span class="sxs-lookup"><span data-stu-id="cc279-111">Minor</span></span>       |
| <span data-ttu-id="cc279-112">Version</span><span class="sxs-lookup"><span data-stu-id="cc279-112">Version</span></span> | <span data-ttu-id="cc279-113">4,5</span><span class="sxs-lookup"><span data-stu-id="cc279-113">4.5</span></span>         |
| <span data-ttu-id="cc279-114">Type</span><span class="sxs-lookup"><span data-stu-id="cc279-114">Type</span></span>    | <span data-ttu-id="cc279-115">Reciblage</span><span class="sxs-lookup"><span data-stu-id="cc279-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="cc279-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="cc279-116">Affected APIs</span></span>

- <xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType>
