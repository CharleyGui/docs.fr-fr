---
ms.openlocfilehash: d6405573e476ce18513938b500041adefbeeef1b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497881"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a><span data-ttu-id="74be7-101">L’arrière-plan de RibbonGroup est défini sur Transparent dans les versions localisées</span><span class="sxs-lookup"><span data-stu-id="74be7-101">RibbonGroup background is set to transparent in localized builds</span></span>

#### <a name="details"></a><span data-ttu-id="74be7-102">Détails</span><span class="sxs-lookup"><span data-stu-id="74be7-102">Details</span></span>

<span data-ttu-id="74be7-103">L’arrière-plan de <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> sur les versions localisées était toujours dessiné avec le pinceau Transparent, ce qui offrait une expérience assez pauvre de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="74be7-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> background on localized builds was always painted with Transparent brush, resulting in poor UI experience.</span></span> <span data-ttu-id="74be7-104">Ce point est résolu dans le correctif de .NET Framework 4.7 WPF par le biais d’une mise à jour des ressources localisées pour <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName>, qui à son tour garantit que le bon pinceau est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="74be7-104">This is fixed in .NET Framework 4.7 WPF fix by updating the localized resources for <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName>, which in turn ensures that the correct brush is selected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="74be7-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="74be7-105">Suggestion</span></span>

<span data-ttu-id="74be7-106">Mettre à niveau vers .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="74be7-106">Upgrade to .NET Framework 4.7</span></span>

| <span data-ttu-id="74be7-107">Name</span><span class="sxs-lookup"><span data-stu-id="74be7-107">Name</span></span>    | <span data-ttu-id="74be7-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="74be7-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="74be7-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="74be7-109">Scope</span></span>   |<span data-ttu-id="74be7-110">Edge</span><span class="sxs-lookup"><span data-stu-id="74be7-110">Edge</span></span>|
|<span data-ttu-id="74be7-111">Version</span><span class="sxs-lookup"><span data-stu-id="74be7-111">Version</span></span>|<span data-ttu-id="74be7-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="74be7-112">4.6.2</span></span>|
|<span data-ttu-id="74be7-113">Type</span><span class="sxs-lookup"><span data-stu-id="74be7-113">Type</span></span>|<span data-ttu-id="74be7-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="74be7-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="74be7-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="74be7-115">Affected APIs</span></span>

<span data-ttu-id="74be7-116">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="74be7-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
