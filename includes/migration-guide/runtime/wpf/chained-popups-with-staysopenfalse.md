---
ms.openlocfilehash: 171b7a3a962f8259e64b88f1ae893e649b5f24bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621105"
---
### <a name="chained-popups-with-staysopenfalse"></a><span data-ttu-id="296c6-101">Fenêtres contextuelles chaînées avec StaysOpen=False</span><span class="sxs-lookup"><span data-stu-id="296c6-101">Chained Popups with StaysOpen=False</span></span>

#### <a name="details"></a><span data-ttu-id="296c6-102">Détails</span><span class="sxs-lookup"><span data-stu-id="296c6-102">Details</span></span>

<span data-ttu-id="296c6-103">Une fenêtre contextuelle avec StaysOpen=False est supposée se fermer quand vous cliquez en dehors de la fenêtre contextuelle.</span><span class="sxs-lookup"><span data-stu-id="296c6-103">A Popup with StaysOpen=False is supposed to close when you click outside the Popup.</span></span> <span data-ttu-id="296c6-104">Quand plusieurs de ces fenêtres contextuelles sont chaînées (c’est-à-dire quand une fenêtre en contient une autre), de nombreux problèmes apparaissaient, notamment :</span><span class="sxs-lookup"><span data-stu-id="296c6-104">When two or more such Popups are chained (i.e. one contains another), there were many problems, including:</span></span><ul><li><span data-ttu-id="296c6-105">Ouvrez deux niveaux, cliquez en dehors de P2 mais à l’intérieur de P1.</span><span class="sxs-lookup"><span data-stu-id="296c6-105">Open two levels, click outside P2 but inside P1.</span></span>  <span data-ttu-id="296c6-106">Rien ne se produit.</span><span class="sxs-lookup"><span data-stu-id="296c6-106">Nothing happens.</span></span></li><li><span data-ttu-id="296c6-107">Ouvrez deux niveaux, cliquez en dehors de P1.</span><span class="sxs-lookup"><span data-stu-id="296c6-107">Open two levels, click outside P1.</span></span>  <span data-ttu-id="296c6-108">Les deux fenêtres contextuelles se ferment.</span><span class="sxs-lookup"><span data-stu-id="296c6-108">Both popups close.</span></span></li><li><span data-ttu-id="296c6-109">Ouvrez et fermez les deux niveaux.</span><span class="sxs-lookup"><span data-stu-id="296c6-109">Open and close two levels.</span></span>  <span data-ttu-id="296c6-110">Essayez à nouveau d’ouvrir P2.</span><span class="sxs-lookup"><span data-stu-id="296c6-110">Then try to open P2 again.</span></span>  <span data-ttu-id="296c6-111">Rien ne se produit.</span><span class="sxs-lookup"><span data-stu-id="296c6-111">Nothing happens.</span></span></li><li><span data-ttu-id="296c6-112">Essayez d’ouvrir trois niveaux.</span><span class="sxs-lookup"><span data-stu-id="296c6-112">Try to open three levels.</span></span>  <span data-ttu-id="296c6-113">Désolé... Cette migration est impossible.</span><span class="sxs-lookup"><span data-stu-id="296c6-113">You can't.</span></span>  <span data-ttu-id="296c6-114">(Rien ne se passe ou les deux premiers niveaux se ferment, en fonction de l’endroit où vous cliquez.) Ces cas (et autres variantes) fonctionnent à présent comme prévu.</span><span class="sxs-lookup"><span data-stu-id="296c6-114">(Either nothing happens or the first two levels close, depending on where you click.) These cases (and other variants) now work as expected.</span></span></li></ul>

| <span data-ttu-id="296c6-115">Nom</span><span class="sxs-lookup"><span data-stu-id="296c6-115">Name</span></span>    | <span data-ttu-id="296c6-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="296c6-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="296c6-117">Étendue</span><span class="sxs-lookup"><span data-stu-id="296c6-117">Scope</span></span>   |<span data-ttu-id="296c6-118">Edge</span><span class="sxs-lookup"><span data-stu-id="296c6-118">Edge</span></span>|
|<span data-ttu-id="296c6-119">Version</span><span class="sxs-lookup"><span data-stu-id="296c6-119">Version</span></span>|<span data-ttu-id="296c6-120">4.7.1</span><span class="sxs-lookup"><span data-stu-id="296c6-120">4.7.1</span></span>|
|<span data-ttu-id="296c6-121">Type</span><span class="sxs-lookup"><span data-stu-id="296c6-121">Type</span></span>|<span data-ttu-id="296c6-122">Runtime</span><span class="sxs-lookup"><span data-stu-id="296c6-122">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="296c6-123">API affectées</span><span class="sxs-lookup"><span data-stu-id="296c6-123">Affected APIs</span></span>

-<xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|
