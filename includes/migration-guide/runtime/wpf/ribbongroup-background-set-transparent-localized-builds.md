---
ms.openlocfilehash: 9500907c6a1ba5b27008dcad4c9b47aef9092106
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802443"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a><span data-ttu-id="d752f-101">L’arrière-plan de RibbonGroup est défini sur Transparent dans les versions localisées</span><span class="sxs-lookup"><span data-stu-id="d752f-101">RibbonGroup background is set to transparent in localized builds</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d752f-102">Détails</span><span class="sxs-lookup"><span data-stu-id="d752f-102">Details</span></span>|<span data-ttu-id="d752f-103">L’arrière-plan de <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> sur les versions localisées était toujours dessiné avec le pinceau Transparent, ce qui offrait une expérience assez pauvre de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d752f-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> background on localized builds was always painted with Transparent brush, resulting in poor UI experience.</span></span> <span data-ttu-id="d752f-104">Ce point est résolu dans le correctif de .NET Framework 4.7 WPF par le biais d’une mise à jour des ressources localisées pour <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, qui à son tour garantit que le bon pinceau est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="d752f-104">This is fixed in .NET Framework 4.7 WPF fix by updating the localized resources for <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, which in turn ensures that the correct brush is selected.</span></span>|
|<span data-ttu-id="d752f-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="d752f-105">Suggestion</span></span>|<span data-ttu-id="d752f-106">Mettre à niveau vers .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="d752f-106">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="d752f-107">Portée</span><span class="sxs-lookup"><span data-stu-id="d752f-107">Scope</span></span>|<span data-ttu-id="d752f-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="d752f-108">Edge</span></span>|
|<span data-ttu-id="d752f-109">Version</span><span class="sxs-lookup"><span data-stu-id="d752f-109">Version</span></span>|<span data-ttu-id="d752f-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="d752f-110">4.6.2</span></span>|
|<span data-ttu-id="d752f-111">Type</span><span class="sxs-lookup"><span data-stu-id="d752f-111">Type</span></span>|<span data-ttu-id="d752f-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="d752f-112">Runtime</span></span>|

