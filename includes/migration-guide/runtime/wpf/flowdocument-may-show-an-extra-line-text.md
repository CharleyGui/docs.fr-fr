---
ms.openlocfilehash: 0470cefc05fb5da6a6195ee0a96f04feef01fd10
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620431"
---
### <a name="flowdocument-may-show-an-extra-line-of-text"></a><span data-ttu-id="fbbd3-101">FlowDocument peut afficher une ligne de texte supplémentaire</span><span class="sxs-lookup"><span data-stu-id="fbbd3-101">FlowDocument may show an extra line of text</span></span>

#### <a name="details"></a><span data-ttu-id="fbbd3-102">Détails</span><span class="sxs-lookup"><span data-stu-id="fbbd3-102">Details</span></span>

<span data-ttu-id="fbbd3-103">Dans certains cas, un élément <xref:System.Windows.Documents.FlowDocument> affiche une ligne de texte supplémentaire lors de l’exécution sur .NET Framework 4.5 par rapport à la façon dont il s’affichait lors de l’exécution sur .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="fbbd3-103">In some cases, a <xref:System.Windows.Documents.FlowDocument> element will display an extra line of text when running on the .NET Framework 4.5 compared to how it displayed when run on the .NET Framework 4.0.</span></span> <span data-ttu-id="fbbd3-104">Il n’existe aucun cas connu où ce changement provoquerait un affichage incorrect ou illisible du texte, mais il peut avoir comme conséquence que du texte qui était omis dans la vue de <xref:System.Windows.Documents.FlowDocument> désormais apparaisse.</span><span class="sxs-lookup"><span data-stu-id="fbbd3-104">There are no known cases of the change causing any text to be displayed poorly or illegibly, but it could cause text to appear that previously was omitted from a <xref:System.Windows.Documents.FlowDocument>'s view.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fbbd3-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="fbbd3-105">Suggestion</span></span>

<span data-ttu-id="fbbd3-106">Dans certains cas, la diminution d’une unité de la valeur de la propriété PageHeight pour l’élément d’un affichage peut rétablir le nombre précédent de lignes affichées.</span><span class="sxs-lookup"><span data-stu-id="fbbd3-106">In some cases, decreasing the display element's PageHeight property by one can restore the previous number of displayed lines.</span></span>

| <span data-ttu-id="fbbd3-107">Nom</span><span class="sxs-lookup"><span data-stu-id="fbbd3-107">Name</span></span>    | <span data-ttu-id="fbbd3-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="fbbd3-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fbbd3-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="fbbd3-109">Scope</span></span>   |<span data-ttu-id="fbbd3-110">Edge</span><span class="sxs-lookup"><span data-stu-id="fbbd3-110">Edge</span></span>|
|<span data-ttu-id="fbbd3-111">Version</span><span class="sxs-lookup"><span data-stu-id="fbbd3-111">Version</span></span>|<span data-ttu-id="fbbd3-112">4,5</span><span class="sxs-lookup"><span data-stu-id="fbbd3-112">4.5</span></span>|
|<span data-ttu-id="fbbd3-113">Type</span><span class="sxs-lookup"><span data-stu-id="fbbd3-113">Type</span></span>|<span data-ttu-id="fbbd3-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="fbbd3-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fbbd3-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="fbbd3-115">Affected APIs</span></span>

-<xref:System.Windows.Documents.FlowDocument.%23ctor></li><li><xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)></li><li><xref:System.Windows.Controls.FlowDocumentReader.%23ctor></li><li><xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor></li><li><xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor></li></ul>|
