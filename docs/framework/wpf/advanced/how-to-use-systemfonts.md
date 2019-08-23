---
title: 'Procédure : Utiliser SystemFonts'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- system fonts [WPF]
- fonts [WPF], system fonts
- classes [WPF], SystemFonts
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
ms.openlocfilehash: 7438705a82faee464649b5f6f577627a379e9a8c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918362"
---
# <a name="how-to-use-systemfonts"></a>Procédure : Utiliser SystemFonts
Cet exemple montre comment utiliser les ressources statiques de la <xref:System.Windows.SystemFonts> classe pour appliquer un style ou personnaliser un bouton.  
  
## <a name="example"></a>Exemples  
 Les ressources système exposent plusieurs valeurs déterminées par le système en tant que ressources et propriétés pour vous aider à créer des visuels cohérents avec les paramètres système. <xref:System.Windows.SystemFonts>est une classe qui contient à la fois des valeurs de police système comme propriétés statiques, et des propriétés qui référencent des clés de ressource qui peuvent être utilisées pour accéder dynamiquement à ces valeurs au moment de l’exécution. Par exemple, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> est une <xref:System.Windows.SystemFonts> valeur et <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> est une clé de ressource correspondante.  
  
 Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez utiliser les membres de <xref:System.Windows.SystemFonts> comme propriétés statiques ou références de ressources dynamiques (avec la valeur de propriété statique comme clé). Utilisez une référence de ressource dynamique si vous souhaitez que les métriques de police soient mises à jour automatiquement pendant que l’application s’exécute ; sinon, utilisez une référence de valeur statique.  
  
> [!NOTE]
> Les clés de ressources ont le suffixe « Key » ajouté au nom de propriété.  
  
 L’exemple suivant montre comment accéder aux propriétés de <xref:System.Windows.SystemFonts> comme valeurs statiques et les utiliser pour appliquer un style ou personnaliser un bouton. Cet exemple de balisage <xref:System.Windows.SystemFonts> affecte des valeurs à un bouton.  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 Pour utiliser les valeurs de <xref:System.Windows.SystemFonts> dans le code, il n’est pas nécessaire d’utiliser une valeur statique ou une référence de ressource dynamique. Utilisez plutôt les propriétés non-clés de la <xref:System.Windows.SystemFonts> classe. Bien que les propriétés non-clés soient apparemment définies en tant que propriétés statiques, le comportement [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] au moment de l’exécution de comme hébergé par le système réévaluera les propriétés en temps réel et prendra en compte correctement les modifications pilotées par l’utilisateur aux valeurs système. L’exemple suivant montre comment spécifier les paramètres de police d’un bouton.  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.SystemFonts>
- [Peindre une zone avec un pinceau système](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [Utiliser SystemParameters](how-to-use-systemparameters.md)
- [Utiliser des clés de polices système](how-to-use-system-fonts-keys.md)
- [Rubriques de guide pratique](resources-how-to-topics.md)
- [x:Static, extension de balisage](../../xaml-services/x-static-markup-extension.md)
- [Ressources XAML](xaml-resources.md)
- [Extension de balisage DynamicResource](dynamicresource-markup-extension.md)
