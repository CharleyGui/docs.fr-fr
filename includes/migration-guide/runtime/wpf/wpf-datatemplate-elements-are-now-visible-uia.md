---
ms.openlocfilehash: 06c699281c8890ac65be1d282b72b54774acc280
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620476"
---
### <a name="wpf-datatemplate-elements-are-now-visible-to-uia"></a><span data-ttu-id="58e63-101">Les éléments DataTemplate WPF sont désormais détectés par UI Automation</span><span class="sxs-lookup"><span data-stu-id="58e63-101">WPF DataTemplate elements are now visible to UIA</span></span>

#### <a name="details"></a><span data-ttu-id="58e63-102">Détails</span><span class="sxs-lookup"><span data-stu-id="58e63-102">Details</span></span>

<span data-ttu-id="58e63-103">Avant, les éléments <xref:System.Windows.DataTemplate?displayProperty=fullName> étaient invisibles pour UI Automation.</span><span class="sxs-lookup"><span data-stu-id="58e63-103">Previously, <xref:System.Windows.DataTemplate?displayProperty=fullName> elements were invisible to UI Automation.</span></span> <span data-ttu-id="58e63-104">À compter de la version 4.5, UI Automation détecte ces éléments.</span><span class="sxs-lookup"><span data-stu-id="58e63-104">Beginning in 4.5, UI Automation will detect these elements.</span></span> <span data-ttu-id="58e63-105">C’est pratique dans de nombreux cas, mais peut compromettre les tests qui dépendent des arborescences UI Automation qui ne contiennent pas d’éléments <xref:System.Windows.DataTemplate?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="58e63-105">This is useful in many cases, but can break tests that depend on UIA trees not containing <xref:System.Windows.DataTemplate?displayProperty=fullName> elements.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="58e63-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="58e63-106">Suggestion</span></span>

<span data-ttu-id="58e63-107">Les tests UI Automation pour cette application peuvent nécessiter des modifications pour prendre en compte l’arborescence UI Automation qui contient maintenant des éléments <xref:System.Windows.DataTemplate?displayProperty=fullName> qui étaient invisibles.</span><span class="sxs-lookup"><span data-stu-id="58e63-107">UI Automation tests for this app may need updated to account for the UIA tree now including previously invisible <xref:System.Windows.DataTemplate?displayProperty=fullName> elements.</span></span> <span data-ttu-id="58e63-108">Par exemple, les tests qui attendent des éléments contigus doivent maintenant s’attendre à ce que des éléments UIA, autrefois indétectables, se trouvent entre ces éléments.</span><span class="sxs-lookup"><span data-stu-id="58e63-108">For example, tests that expect some elements to be next to each other may now need to expect previously invisible UIA elements in between.</span></span> <span data-ttu-id="58e63-109">Autre exemple : Les tests qui reposent sur certains nombres ou index pour les éléments UIA peuvent nécessiter la modification de leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="58e63-109">Or tests that rely on certain counts or indexes for UIA elements may need updated with new values.</span></span>

| <span data-ttu-id="58e63-110">Nom</span><span class="sxs-lookup"><span data-stu-id="58e63-110">Name</span></span>    | <span data-ttu-id="58e63-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="58e63-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="58e63-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="58e63-112">Scope</span></span>   |<span data-ttu-id="58e63-113">Edge</span><span class="sxs-lookup"><span data-stu-id="58e63-113">Edge</span></span>|
|<span data-ttu-id="58e63-114">Version</span><span class="sxs-lookup"><span data-stu-id="58e63-114">Version</span></span>|<span data-ttu-id="58e63-115">4,5</span><span class="sxs-lookup"><span data-stu-id="58e63-115">4.5</span></span>|
|<span data-ttu-id="58e63-116">Type</span><span class="sxs-lookup"><span data-stu-id="58e63-116">Type</span></span>|<span data-ttu-id="58e63-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="58e63-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="58e63-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="58e63-118">Affected APIs</span></span>

-<xref:System.Windows.DataTemplate.%23ctor></li><li><xref:System.Windows.DataTemplate.%23ctor(System.Object)></li></ul>|
