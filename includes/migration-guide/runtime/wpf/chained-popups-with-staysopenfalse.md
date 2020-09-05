---
ms.openlocfilehash: 7bf5f7e8a49acc2918dd0d68a1c54a5c277091b0
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496574"
---
### <a name="chained-popups-with-staysopenfalse"></a><span data-ttu-id="85099-101">Fenêtres contextuelles chaînées avec StaysOpen=False</span><span class="sxs-lookup"><span data-stu-id="85099-101">Chained Popups with StaysOpen=False</span></span>

#### <a name="details"></a><span data-ttu-id="85099-102">Détails</span><span class="sxs-lookup"><span data-stu-id="85099-102">Details</span></span>

<span data-ttu-id="85099-103">Une fenêtre contextuelle avec StaysOpen=False est supposée se fermer quand vous cliquez en dehors de la fenêtre contextuelle.</span><span class="sxs-lookup"><span data-stu-id="85099-103">A Popup with StaysOpen=False is supposed to close when you click outside the Popup.</span></span> <span data-ttu-id="85099-104">Quand plusieurs de ces fenêtres contextuelles sont chaînées (c’est-à-dire quand une fenêtre en contient une autre), de nombreux problèmes apparaissaient, notamment :</span><span class="sxs-lookup"><span data-stu-id="85099-104">When two or more such Popups are chained (i.e. one contains another), there were many problems, including:</span></span><ul><li><span data-ttu-id="85099-105">Ouvrez deux niveaux, cliquez en dehors de P2 mais à l’intérieur de P1.</span><span class="sxs-lookup"><span data-stu-id="85099-105">Open two levels, click outside P2 but inside P1.</span></span>  <span data-ttu-id="85099-106">Il ne se passe rien.</span><span class="sxs-lookup"><span data-stu-id="85099-106">Nothing happens.</span></span></li><li><span data-ttu-id="85099-107">Ouvrez deux niveaux, cliquez en dehors de P1.</span><span class="sxs-lookup"><span data-stu-id="85099-107">Open two levels, click outside P1.</span></span>  <span data-ttu-id="85099-108">Les deux fenêtres contextuelles se ferment.</span><span class="sxs-lookup"><span data-stu-id="85099-108">Both popups close.</span></span></li><li><span data-ttu-id="85099-109">Ouvrez et fermez les deux niveaux.</span><span class="sxs-lookup"><span data-stu-id="85099-109">Open and close two levels.</span></span>  <span data-ttu-id="85099-110">Essayez à nouveau d’ouvrir P2.</span><span class="sxs-lookup"><span data-stu-id="85099-110">Then try to open P2 again.</span></span>  <span data-ttu-id="85099-111">Il ne se passe rien.</span><span class="sxs-lookup"><span data-stu-id="85099-111">Nothing happens.</span></span></li><li><span data-ttu-id="85099-112">Essayez d’ouvrir trois niveaux.</span><span class="sxs-lookup"><span data-stu-id="85099-112">Try to open three levels.</span></span>  <span data-ttu-id="85099-113">Vous ne le pouvez pas.</span><span class="sxs-lookup"><span data-stu-id="85099-113">You can't.</span></span>  <span data-ttu-id="85099-114">(Rien ne se passe ou les deux premiers niveaux se ferment, en fonction de l’endroit où vous cliquez.) Ces cas (et autres variantes) fonctionnent à présent comme prévu.</span><span class="sxs-lookup"><span data-stu-id="85099-114">(Either nothing happens or the first two levels close, depending on where you click.) These cases (and other variants) now work as expected.</span></span></li></ul>

| <span data-ttu-id="85099-115">Name</span><span class="sxs-lookup"><span data-stu-id="85099-115">Name</span></span>    | <span data-ttu-id="85099-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="85099-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="85099-117">Étendue</span><span class="sxs-lookup"><span data-stu-id="85099-117">Scope</span></span>   |<span data-ttu-id="85099-118">Edge</span><span class="sxs-lookup"><span data-stu-id="85099-118">Edge</span></span>|
|<span data-ttu-id="85099-119">Version</span><span class="sxs-lookup"><span data-stu-id="85099-119">Version</span></span>|<span data-ttu-id="85099-120">4.7.1</span><span class="sxs-lookup"><span data-stu-id="85099-120">4.7.1</span></span>|
|<span data-ttu-id="85099-121">Type</span><span class="sxs-lookup"><span data-stu-id="85099-121">Type</span></span>|<span data-ttu-id="85099-122">Runtime</span><span class="sxs-lookup"><span data-stu-id="85099-122">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="85099-123">API affectées</span><span class="sxs-lookup"><span data-stu-id="85099-123">Affected APIs</span></span>

- <xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Windows.Controls.Primitives.Popup.StaysOpen`

-->
