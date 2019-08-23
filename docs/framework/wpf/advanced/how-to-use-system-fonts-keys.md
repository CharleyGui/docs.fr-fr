---
title: 'Procédure : Utiliser des clés de polices système'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: 7283e4225b75909322fa312583e9f1a0679762e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918388"
---
# <a name="how-to-use-system-fonts-keys"></a><span data-ttu-id="9ab14-102">Procédure : Utiliser des clés de polices système</span><span class="sxs-lookup"><span data-stu-id="9ab14-102">How to: Use System Fonts Keys</span></span>
<span data-ttu-id="9ab14-103">Les ressources système exposent plusieurs métriques système en tant que ressources pour aider les développeurs à créer des visuels cohérents avec les paramètres système.</span><span class="sxs-lookup"><span data-stu-id="9ab14-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="9ab14-104"><xref:System.Windows.SystemFonts>est une classe qui contient à la fois des valeurs de police système et des ressources de police système qui sont liées <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> aux <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>valeurs, par exemple et.</span><span class="sxs-lookup"><span data-stu-id="9ab14-104"><xref:System.Windows.SystemFonts> is a class that contains both system font values and system font resources that bind to the values—for example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span></span>  
  
 <span data-ttu-id="9ab14-105">Les métriques de police système peuvent être utilisées en tant que ressources statiques ou dynamiques.</span><span class="sxs-lookup"><span data-stu-id="9ab14-105">System font metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="9ab14-106">Utilisez une ressource dynamique si vous souhaitez que les métriques de police soient mises à jour automatiquement pendant que l’application s’exécute ; sinon, utilisez une ressource statique.</span><span class="sxs-lookup"><span data-stu-id="9ab14-106">Use a dynamic resource if you want the font metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ab14-107">Les ressources dynamiques ont une *clé* de mot clé ajoutée au nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="9ab14-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="9ab14-108">L’exemple suivant montre comment accéder à des ressources dynamiques de police système et comment les utiliser pour personnaliser un bouton ou lui appliquer un style.</span><span class="sxs-lookup"><span data-stu-id="9ab14-108">The following example shows how to access and use system font dynamic resources to style or customize a button.</span></span> <span data-ttu-id="9ab14-109">Cet [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemple crée un style de bouton qui <xref:System.Windows.SystemFonts> assigne des valeurs à un bouton.</span><span class="sxs-lookup"><span data-stu-id="9ab14-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example creates a button style that assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ab14-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="9ab14-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#FontDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="9ab14-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ab14-111">See also</span></span>

- [<span data-ttu-id="9ab14-112">Peindre une zone avec un pinceau système</span><span class="sxs-lookup"><span data-stu-id="9ab14-112">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="9ab14-113">Utiliser SystemParameters</span><span class="sxs-lookup"><span data-stu-id="9ab14-113">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
- [<span data-ttu-id="9ab14-114">Utiliser des SystemFonts</span><span class="sxs-lookup"><span data-stu-id="9ab14-114">Use SystemFonts</span></span>](how-to-use-systemfonts.md)
