---
title: 'Procédure : Utiliser des clés de paramètres système'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
ms.openlocfilehash: edacb4b98ab01f081f668dc3374f6588492210d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918369"
---
# <a name="how-to-use-system-parameters-keys"></a><span data-ttu-id="e1f98-102">Procédure : Utiliser des clés de paramètres système</span><span class="sxs-lookup"><span data-stu-id="e1f98-102">How to: Use System Parameters Keys</span></span>
<span data-ttu-id="e1f98-103">Les ressources système exposent plusieurs métriques système en tant que ressources pour aider les développeurs à créer des visuels cohérents avec les paramètres système.</span><span class="sxs-lookup"><span data-stu-id="e1f98-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="e1f98-104"><xref:System.Windows.SystemParameters>est une classe qui contient à la fois des valeurs de paramètre système et des clés de ressource qui sont liées <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> aux <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>valeurs, par exemple et.</span><span class="sxs-lookup"><span data-stu-id="e1f98-104"><xref:System.Windows.SystemParameters> is a class that contains both system parameter values and resource keys that bind to the values—for example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span></span> <span data-ttu-id="e1f98-105">Les métriques de paramètres système peuvent être utilisées en tant que ressources statiques ou dynamiques.</span><span class="sxs-lookup"><span data-stu-id="e1f98-105">System parameter metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="e1f98-106">Utilisez une ressource dynamique si vous souhaitez que les métriques de paramètres soient mises à jour automatiquement pendant que l’application s’exécute ; sinon, utilisez une ressource statique.</span><span class="sxs-lookup"><span data-stu-id="e1f98-106">Use a dynamic resource if you want the parameter metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1f98-107">Les ressources dynamiques ont une *clé* de mot clé ajoutée au nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="e1f98-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="e1f98-108">L’exemple suivant montre comment accéder à des ressources dynamiques de paramètres système et comment les utiliser pour personnaliser un bouton ou lui appliquer un style.</span><span class="sxs-lookup"><span data-stu-id="e1f98-108">The following example shows how to access and use system parameter dynamic resources to style or customize a button.</span></span> <span data-ttu-id="e1f98-109">Cet [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemple dimensionne un bouton en <xref:System.Windows.SystemParameters> affectant des valeurs à la largeur et à la hauteur du bouton.</span><span class="sxs-lookup"><span data-stu-id="e1f98-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example sizes a button by assigning <xref:System.Windows.SystemParameters> values to the button's width and height.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1f98-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="e1f98-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="e1f98-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1f98-111">See also</span></span>

- [<span data-ttu-id="e1f98-112">Peindre une zone avec un pinceau système</span><span class="sxs-lookup"><span data-stu-id="e1f98-112">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="e1f98-113">Utiliser des SystemFonts</span><span class="sxs-lookup"><span data-stu-id="e1f98-113">Use SystemFonts</span></span>](how-to-use-systemfonts.md)
- [<span data-ttu-id="e1f98-114">Utiliser SystemParameters</span><span class="sxs-lookup"><span data-stu-id="e1f98-114">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
