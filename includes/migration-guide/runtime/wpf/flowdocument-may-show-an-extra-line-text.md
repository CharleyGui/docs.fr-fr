---
ms.openlocfilehash: a61005e317020c47a283dae292236624ec6057ce
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497781"
---
### <a name="flowdocument-may-show-an-extra-line-of-text"></a><span data-ttu-id="62c4f-101">FlowDocument peut afficher une ligne de texte supplémentaire</span><span class="sxs-lookup"><span data-stu-id="62c4f-101">FlowDocument may show an extra line of text</span></span>

#### <a name="details"></a><span data-ttu-id="62c4f-102">Détails</span><span class="sxs-lookup"><span data-stu-id="62c4f-102">Details</span></span>

<span data-ttu-id="62c4f-103">Dans certains cas, un élément <xref:System.Windows.Documents.FlowDocument> affiche une ligne de texte supplémentaire lors de l’exécution sur .NET Framework 4.5 par rapport à la façon dont il s’affichait lors de l’exécution sur .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="62c4f-103">In some cases, a <xref:System.Windows.Documents.FlowDocument> element will display an extra line of text when running on the .NET Framework 4.5 compared to how it displayed when run on the .NET Framework 4.0.</span></span> <span data-ttu-id="62c4f-104">Il n’existe aucun cas connu où ce changement provoquerait un affichage incorrect ou illisible du texte, mais il peut avoir comme conséquence que du texte qui était omis dans la vue de <xref:System.Windows.Documents.FlowDocument> désormais apparaisse.</span><span class="sxs-lookup"><span data-stu-id="62c4f-104">There are no known cases of the change causing any text to be displayed poorly or illegibly, but it could cause text to appear that previously was omitted from a <xref:System.Windows.Documents.FlowDocument>'s view.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="62c4f-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="62c4f-105">Suggestion</span></span>

<span data-ttu-id="62c4f-106">Dans certains cas, la diminution d’une unité de la valeur de la propriété PageHeight pour l’élément d’un affichage peut rétablir le nombre précédent de lignes affichées.</span><span class="sxs-lookup"><span data-stu-id="62c4f-106">In some cases, decreasing the display element's PageHeight property by one can restore the previous number of displayed lines.</span></span>

| <span data-ttu-id="62c4f-107">Name</span><span class="sxs-lookup"><span data-stu-id="62c4f-107">Name</span></span>    | <span data-ttu-id="62c4f-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="62c4f-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="62c4f-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="62c4f-109">Scope</span></span>   |<span data-ttu-id="62c4f-110">Edge</span><span class="sxs-lookup"><span data-stu-id="62c4f-110">Edge</span></span>|
|<span data-ttu-id="62c4f-111">Version</span><span class="sxs-lookup"><span data-stu-id="62c4f-111">Version</span></span>|<span data-ttu-id="62c4f-112">4,5</span><span class="sxs-lookup"><span data-stu-id="62c4f-112">4.5</span></span>|
|<span data-ttu-id="62c4f-113">Type</span><span class="sxs-lookup"><span data-stu-id="62c4f-113">Type</span></span>|<span data-ttu-id="62c4f-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="62c4f-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="62c4f-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="62c4f-115">Affected APIs</span></span>

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
