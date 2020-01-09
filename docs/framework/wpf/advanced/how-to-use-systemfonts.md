---
title: Guide pratique pour utiliser des SystemFonts
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- system fonts [WPF]
- fonts [WPF], system fonts
- classes [WPF], SystemFonts
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
ms.openlocfilehash: 157565ceb9057049aef8b2bf274847d58c6b8dc8
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559961"
---
# <a name="how-to-use-systemfonts"></a><span data-ttu-id="2f531-102">Guide pratique pour utiliser des SystemFonts</span><span class="sxs-lookup"><span data-stu-id="2f531-102">How to: Use SystemFonts</span></span>
<span data-ttu-id="2f531-103">Cet exemple montre comment utiliser les ressources statiques de la classe <xref:System.Windows.SystemFonts> pour appliquer un style ou personnaliser un bouton.</span><span class="sxs-lookup"><span data-stu-id="2f531-103">This example shows how to use the static resources of the <xref:System.Windows.SystemFonts> class in order to style or customize a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f531-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="2f531-104">Example</span></span>  
 <span data-ttu-id="2f531-105">Les ressources système exposent plusieurs valeurs déterminées par le système en tant que ressources et propriétés pour vous aider à créer des visuels cohérents avec les paramètres système.</span><span class="sxs-lookup"><span data-stu-id="2f531-105">System resources expose several system-determined values as both resources and properties in order to help you create visuals that are consistent with system settings.</span></span> <span data-ttu-id="2f531-106"><xref:System.Windows.SystemFonts> est une classe qui contient à la fois des valeurs de police système comme propriétés statiques et des propriétés qui font référence à des clés de ressource qui peuvent être utilisées pour accéder dynamiquement à ces valeurs au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2f531-106"><xref:System.Windows.SystemFonts> is a class that contains both system font values as static properties, and properties that reference resource keys that can be used to access those values dynamically at run time.</span></span> <span data-ttu-id="2f531-107">Par exemple, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> est une valeur de <xref:System.Windows.SystemFonts> et <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> est une clé de ressource correspondante.</span><span class="sxs-lookup"><span data-stu-id="2f531-107">For example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> is a <xref:System.Windows.SystemFonts> value, and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> is a corresponding resource key.</span></span>  
  
 <span data-ttu-id="2f531-108">Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez utiliser les membres de <xref:System.Windows.SystemFonts> en tant que propriétés statiques ou références de ressources dynamiques (avec la valeur de propriété statique comme clé).</span><span class="sxs-lookup"><span data-stu-id="2f531-108">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can use the members of <xref:System.Windows.SystemFonts> as either static properties or dynamic resource references (with the static property value as the key).</span></span> <span data-ttu-id="2f531-109">Utilisez une référence de ressource dynamique si vous souhaitez que les métriques de police soient mises à jour automatiquement pendant que l’application s’exécute ; sinon, utilisez une référence de valeur statique.</span><span class="sxs-lookup"><span data-stu-id="2f531-109">Use a dynamic resource reference if you want the font metric to automatically update while the application runs; otherwise, use a static value reference.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f531-110">Les clés de ressources ont le suffixe « Key » ajouté au nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="2f531-110">The resource keys have the suffix "Key" appended to the property name.</span></span>  
  
 <span data-ttu-id="2f531-111">L’exemple suivant montre comment accéder aux propriétés de <xref:System.Windows.SystemFonts> et les utiliser comme valeurs statiques afin de Styler ou de personnaliser un bouton.</span><span class="sxs-lookup"><span data-stu-id="2f531-111">The following example shows how to access and use the properties of <xref:System.Windows.SystemFonts> as static values in order to style or customize a button.</span></span> <span data-ttu-id="2f531-112">Cet exemple de balisage affecte des valeurs <xref:System.Windows.SystemFonts> à un bouton.</span><span class="sxs-lookup"><span data-stu-id="2f531-112">This markup example assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 <span data-ttu-id="2f531-113">Pour utiliser les valeurs de <xref:System.Windows.SystemFonts> dans le code, il n’est pas nécessaire d’utiliser une valeur statique ou une référence de ressource dynamique.</span><span class="sxs-lookup"><span data-stu-id="2f531-113">To use the values of <xref:System.Windows.SystemFonts> in code, you do not have to use either a static value or a dynamic resource reference.</span></span> <span data-ttu-id="2f531-114">Utilisez plutôt les propriétés non-clés de la classe <xref:System.Windows.SystemFonts>.</span><span class="sxs-lookup"><span data-stu-id="2f531-114">Instead, use the non-key properties of the <xref:System.Windows.SystemFonts> class.</span></span> <span data-ttu-id="2f531-115">Bien que les propriétés non-clé soient apparemment définies en tant que propriétés statiques, le comportement au moment de l’exécution de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tel qu’il est hébergé par le système réévaluera les propriétés en temps réel et tiendra compte des modifications pilotées par l’utilisateur pour les valeurs système.</span><span class="sxs-lookup"><span data-stu-id="2f531-115">Although the non-key properties are apparently defined as static properties, the run-time behavior of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as hosted by the system will reevaluate the properties in real time and will properly account for user-driven changes to system values.</span></span> <span data-ttu-id="2f531-116">L’exemple suivant montre comment spécifier les paramètres de police d’un bouton.</span><span class="sxs-lookup"><span data-stu-id="2f531-116">The following example shows how to specify the font settings of a button.</span></span>  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a><span data-ttu-id="2f531-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f531-117">See also</span></span>

- <xref:System.Windows.SystemFonts>
- [<span data-ttu-id="2f531-118">Peindre une zone avec un pinceau système</span><span class="sxs-lookup"><span data-stu-id="2f531-118">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="2f531-119">Utiliser SystemParameters</span><span class="sxs-lookup"><span data-stu-id="2f531-119">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
- [<span data-ttu-id="2f531-120">Utiliser des clés de polices système</span><span class="sxs-lookup"><span data-stu-id="2f531-120">Use System Fonts Keys</span></span>](how-to-use-system-fonts-keys.md)
- [<span data-ttu-id="2f531-121">Guides pratiques</span><span class="sxs-lookup"><span data-stu-id="2f531-121">How-to Topics</span></span>](resources-how-to-topics.md)
- [<span data-ttu-id="2f531-122">x:Static, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="2f531-122">x:Static Markup Extension</span></span>](../../../desktop-wpf/xaml-services/xstatic-markup-extension.md)
- [<span data-ttu-id="2f531-123">Ressources XAML</span><span class="sxs-lookup"><span data-stu-id="2f531-123">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="2f531-124">Extension de balisage DynamicResource</span><span class="sxs-lookup"><span data-stu-id="2f531-124">DynamicResource Markup Extension</span></span>](dynamicresource-markup-extension.md)
