---
ms.openlocfilehash: 0470cefc05fb5da6a6195ee0a96f04feef01fd10
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620431"
---
### <a name="flowdocument-may-show-an-extra-line-of-text"></a>FlowDocument peut afficher une ligne de texte supplémentaire

#### <a name="details"></a>Détails

Dans certains cas, un élément <xref:System.Windows.Documents.FlowDocument> affiche une ligne de texte supplémentaire lors de l’exécution sur .NET Framework 4.5 par rapport à la façon dont il s’affichait lors de l’exécution sur .NET Framework 4.0. Il n’existe aucun cas connu où ce changement provoquerait un affichage incorrect ou illisible du texte, mais il peut avoir comme conséquence que du texte qui était omis dans la vue de <xref:System.Windows.Documents.FlowDocument> désormais apparaisse.

#### <a name="suggestion"></a>Suggestion

Dans certains cas, la diminution d’une unité de la valeur de la propriété PageHeight pour l’élément d’un affichage peut rétablir le nombre précédent de lignes affichées.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Windows.Documents.FlowDocument.%23ctor></li><li><xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)></li><li><xref:System.Windows.Controls.FlowDocumentReader.%23ctor></li><li><xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor></li><li><xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor></li></ul>|
