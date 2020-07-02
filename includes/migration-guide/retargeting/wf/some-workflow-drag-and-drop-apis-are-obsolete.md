---
ms.openlocfilehash: b6cb7edcd6bed50efdf59f3321320ac8cd1b1ab8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617228"
---
### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a>Certaines API WorkFlow de glisser-déplacer sont obsolètes

#### <a name="details"></a>Détails

Cette API WorkFlow de glisser-déplacer est obsolète et génère des avertissements du compilateur si l’application est régénérée avec la version 4.5.

#### <a name="suggestion"></a>Suggestion

Utilisez à la place les nouvelles API <xref:System.Activities.Presentation.DragDropHelper?displayProperty=fullName> qui prennent en charge les opérations avec plusieurs objets. Vous pouvez également supprimer les avertissements de génération ou les éviter en utilisant un compilateur plus ancien. Ces API sont toujours prises en charge.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4,5         |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType>
