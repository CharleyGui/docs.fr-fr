---
ms.openlocfilehash: a61005e317020c47a283dae292236624ec6057ce
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497781"
---
### <a name="flowdocument-may-show-an-extra-line-of-text"></a>FlowDocument peut afficher une ligne de texte supplémentaire

#### <a name="details"></a>Détails

Dans certains cas, un élément <xref:System.Windows.Documents.FlowDocument> affiche une ligne de texte supplémentaire lors de l’exécution sur .NET Framework 4.5 par rapport à la façon dont il s’affichait lors de l’exécution sur .NET Framework 4.0. Il n’existe aucun cas connu où ce changement provoquerait un affichage incorrect ou illisible du texte, mais il peut avoir comme conséquence que du texte qui était omis dans la vue de <xref:System.Windows.Documents.FlowDocument> désormais apparaisse.

#### <a name="suggestion"></a>Suggestion

Dans certains cas, la diminution d’une unité de la valeur de la propriété PageHeight pour l’élément d’un affichage peut rétablir le nombre précédent de lignes affichées.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Documents.FlowDocument.%23ctor>
- <xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)>
- <xref:System.Windows.Controls.FlowDocumentReader.%23ctor>
- <xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor>
- <xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor>

<!--

#### Affected APIs

- `M:System.Windows.Documents.FlowDocument.#ctor`
- `M:System.Windows.Documents.FlowDocument.#ctor(System.Windows.Documents.Block)`
- `M:System.Windows.Controls.FlowDocumentReader.#ctor`
- `M:System.Windows.Controls.FlowDocumentPageViewer.#ctor`
- `M:System.Windows.Controls.Primitives.DocumentPageView.#ctor`

-->
