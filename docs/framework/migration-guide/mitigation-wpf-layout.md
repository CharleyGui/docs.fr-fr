---
title: 'Atténuation : disposition WPF'
description: Découvrez comment atténuer les problèmes qui résultent d’une modification de la disposition des contrôles WPF, comme le positionnement d’un objet se déplaçant d’un pixel.
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: caed758f6e86a1e2bee255c2f29ca3160b327e17
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244078"
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="2acb2-103">Atténuation : disposition WPF</span><span class="sxs-lookup"><span data-stu-id="2acb2-103">Mitigation: WPF Layout</span></span>

<span data-ttu-id="2acb2-104">La disposition des contrôles WPF peut varier légèrement.</span><span class="sxs-lookup"><span data-stu-id="2acb2-104">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="2acb2-105">Impact</span><span class="sxs-lookup"><span data-stu-id="2acb2-105">Impact</span></span>  

 <span data-ttu-id="2acb2-106">Résultat de cette modification :</span><span class="sxs-lookup"><span data-stu-id="2acb2-106">As a result of this change:</span></span>  
  
- <span data-ttu-id="2acb2-107">La largeur ou la hauteur d'éléments peut croître ou diminuer d'un pixel au plus.</span><span class="sxs-lookup"><span data-stu-id="2acb2-107">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
- <span data-ttu-id="2acb2-108">La position d'un objet peut se déplacer d'un pixel au plus.</span><span class="sxs-lookup"><span data-stu-id="2acb2-108">The placement of an object can move by at most one pixel.</span></span>  
  
- <span data-ttu-id="2acb2-109">Les éléments centrés peuvent être décalés verticalement ou horizontalement d'un pixel au plus.</span><span class="sxs-lookup"><span data-stu-id="2acb2-109">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="2acb2-110">Par défaut, cette nouvelle disposition est activée uniquement pour les applications qui ciblent le .NET. Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="2acb2-110">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="2acb2-111">Limitation des risques</span><span class="sxs-lookup"><span data-stu-id="2acb2-111">Mitigation</span></span>  

 <span data-ttu-id="2acb2-112">Dans la mesure où cette modification tend à éliminer le découpage droit ou inférieur des contrôles WPF dont le PPP est élevé, les applications qui ciblent les versions antérieures du .NET Framework, mais qui s'exécutent sur le .NET Framework 4.6, peuvent choisir ce nouveau comportement en ajoutant la ligne suivante à la section `<runtime>` du fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="2acb2-112">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="2acb2-113">Les applications qui ciblent le .NET Framework 4.6, mais veulent que les contrôles WPF soient rendus à l'aide de l'algorithme de disposition précédent peuvent y parvenir en ajoutant la ligne suivante à la section `<runtime>` du fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="2acb2-113">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="2acb2-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2acb2-114">See also</span></span>

- [<span data-ttu-id="2acb2-115">Compatibilité des applications</span><span class="sxs-lookup"><span data-stu-id="2acb2-115">Application compatibility</span></span>](application-compatibility.md)
