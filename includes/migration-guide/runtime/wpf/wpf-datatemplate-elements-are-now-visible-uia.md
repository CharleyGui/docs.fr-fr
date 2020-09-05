---
ms.openlocfilehash: 4394e69dafeb6cce2d7719a67bbce396d3bc1086
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497254"
---
### <a name="wpf-datatemplate-elements-are-now-visible-to-uia"></a><span data-ttu-id="821bb-101">Les éléments DataTemplate WPF sont désormais détectés par UI Automation</span><span class="sxs-lookup"><span data-stu-id="821bb-101">WPF DataTemplate elements are now visible to UIA</span></span>

#### <a name="details"></a><span data-ttu-id="821bb-102">Détails</span><span class="sxs-lookup"><span data-stu-id="821bb-102">Details</span></span>

<span data-ttu-id="821bb-103">Avant, les éléments <xref:System.Windows.DataTemplate?displayProperty=fullName> étaient invisibles pour UI Automation.</span><span class="sxs-lookup"><span data-stu-id="821bb-103">Previously, <xref:System.Windows.DataTemplate?displayProperty=fullName> elements were invisible to UI Automation.</span></span> <span data-ttu-id="821bb-104">À compter de la version 4.5, UI Automation détecte ces éléments.</span><span class="sxs-lookup"><span data-stu-id="821bb-104">Beginning in 4.5, UI Automation will detect these elements.</span></span> <span data-ttu-id="821bb-105">C’est pratique dans de nombreux cas, mais peut compromettre les tests qui dépendent des arborescences UI Automation qui ne contiennent pas d’éléments <xref:System.Windows.DataTemplate?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="821bb-105">This is useful in many cases, but can break tests that depend on UIA trees not containing <xref:System.Windows.DataTemplate?displayProperty=fullName> elements.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="821bb-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="821bb-106">Suggestion</span></span>

<span data-ttu-id="821bb-107">Les tests UI Automation pour cette application peuvent nécessiter des modifications pour prendre en compte l’arborescence UI Automation qui contient maintenant des éléments <xref:System.Windows.DataTemplate?displayProperty=fullName> qui étaient invisibles.</span><span class="sxs-lookup"><span data-stu-id="821bb-107">UI Automation tests for this app may need updated to account for the UIA tree now including previously invisible <xref:System.Windows.DataTemplate?displayProperty=fullName> elements.</span></span> <span data-ttu-id="821bb-108">Par exemple, les tests qui attendent des éléments contigus doivent maintenant s’attendre à ce que des éléments UIA, autrefois indétectables, se trouvent entre ces éléments.</span><span class="sxs-lookup"><span data-stu-id="821bb-108">For example, tests that expect some elements to be next to each other may now need to expect previously invisible UIA elements in between.</span></span> <span data-ttu-id="821bb-109">Autre exemple : Les tests qui reposent sur certains nombres ou index pour les éléments UIA peuvent nécessiter la modification de leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="821bb-109">Or tests that rely on certain counts or indexes for UIA elements may need updated with new values.</span></span>

| <span data-ttu-id="821bb-110">Name</span><span class="sxs-lookup"><span data-stu-id="821bb-110">Name</span></span>    | <span data-ttu-id="821bb-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="821bb-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="821bb-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="821bb-112">Scope</span></span>   |<span data-ttu-id="821bb-113">Edge</span><span class="sxs-lookup"><span data-stu-id="821bb-113">Edge</span></span>|
|<span data-ttu-id="821bb-114">Version</span><span class="sxs-lookup"><span data-stu-id="821bb-114">Version</span></span>|<span data-ttu-id="821bb-115">4,5</span><span class="sxs-lookup"><span data-stu-id="821bb-115">4.5</span></span>|
|<span data-ttu-id="821bb-116">Type</span><span class="sxs-lookup"><span data-stu-id="821bb-116">Type</span></span>|<span data-ttu-id="821bb-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="821bb-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="821bb-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="821bb-118">Affected APIs</span></span>

- <xref:System.Windows.DataTemplate.%23ctor>
- <xref:System.Windows.DataTemplate.%23ctor(System.Object)>

<!--

#### Affected APIs

- `M:System.Windows.DataTemplate.#ctor`
- `M:System.Windows.DataTemplate.#ctor(System.Object)`

-->
