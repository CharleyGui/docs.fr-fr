---
ms.openlocfilehash: 921baed7381fad363cc832c6b6af69068c2c8f43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802443"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a><span data-ttu-id="ba1e4-101">L’arrière-plan de RibbonGroup est défini sur Transparent dans les versions localisées</span><span class="sxs-lookup"><span data-stu-id="ba1e4-101">RibbonGroup background is set to transparent in localized builds</span></span>

|   |   |
|---|---|
|<span data-ttu-id="ba1e4-102">Détails</span><span class="sxs-lookup"><span data-stu-id="ba1e4-102">Details</span></span>|<span data-ttu-id="ba1e4-103">L’arrière-plan de <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> sur les versions localisées était toujours dessiné avec le pinceau Transparent, ce qui offrait une expérience assez pauvre de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ba1e4-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> background on localized builds was always painted with Transparent brush, resulting in poor UI experience.</span></span> <span data-ttu-id="ba1e4-104">Ce point est résolu dans le correctif de .NET Framework 4.7 WPF par le biais d’une mise à jour des ressources localisées pour <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, qui à son tour garantit que le bon pinceau est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="ba1e4-104">This is fixed in .NET Framework 4.7 WPF fix by updating the localized resources for <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, which in turn ensures that the correct brush is selected.</span></span>|
|<span data-ttu-id="ba1e4-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="ba1e4-105">Suggestion</span></span>|<span data-ttu-id="ba1e4-106">Mettre à niveau vers .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="ba1e4-106">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="ba1e4-107">Étendue</span><span class="sxs-lookup"><span data-stu-id="ba1e4-107">Scope</span></span>|<span data-ttu-id="ba1e4-108">Edge</span><span class="sxs-lookup"><span data-stu-id="ba1e4-108">Edge</span></span>|
|<span data-ttu-id="ba1e4-109">Version</span><span class="sxs-lookup"><span data-stu-id="ba1e4-109">Version</span></span>|<span data-ttu-id="ba1e4-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="ba1e4-110">4.6.2</span></span>|
|<span data-ttu-id="ba1e4-111">Type</span><span class="sxs-lookup"><span data-stu-id="ba1e4-111">Type</span></span>|<span data-ttu-id="ba1e4-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="ba1e4-112">Runtime</span></span>|
