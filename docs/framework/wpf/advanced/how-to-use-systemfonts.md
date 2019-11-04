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
ms.openlocfilehash: 63ba7a6fb1c8776cc35c0e6f07a6b78f5b3d93d0
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459510"
---
# <a name="how-to-use-systemfonts"></a>Guide pratique pour utiliser des SystemFonts
Cet exemple montre comment utiliser les ressources statiques de la classe <xref:System.Windows.SystemFonts> pour appliquer un style ou personnaliser un bouton.  
  
## <a name="example"></a>Exemple  
 Les ressources système exposent plusieurs valeurs déterminées par le système en tant que ressources et propriétés pour vous aider à créer des visuels cohérents avec les paramètres système. <xref:System.Windows.SystemFonts> est une classe qui contient à la fois des valeurs de police système comme propriétés statiques et des propriétés qui font référence à des clés de ressource qui peuvent être utilisées pour accéder dynamiquement à ces valeurs au moment de l’exécution. Par exemple, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> est une valeur de <xref:System.Windows.SystemFonts> et <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> est une clé de ressource correspondante.  
  
 Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez utiliser les membres de <xref:System.Windows.SystemFonts> en tant que propriétés statiques ou références de ressources dynamiques (avec la valeur de propriété statique comme clé). Utilisez une référence de ressource dynamique si vous souhaitez que les métriques de police soient mises à jour automatiquement pendant que l’application s’exécute ; sinon, utilisez une référence de valeur statique.  
  
> [!NOTE]
> Les clés de ressources ont le suffixe « Key » ajouté au nom de propriété.  
  
 L’exemple suivant montre comment accéder aux propriétés de <xref:System.Windows.SystemFonts> et les utiliser comme valeurs statiques afin de Styler ou de personnaliser un bouton. Cet exemple de balisage affecte des valeurs <xref:System.Windows.SystemFonts> à un bouton.  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 Pour utiliser les valeurs de <xref:System.Windows.SystemFonts> dans le code, il n’est pas nécessaire d’utiliser une valeur statique ou une référence de ressource dynamique. Utilisez plutôt les propriétés non-clés de la classe <xref:System.Windows.SystemFonts>. Bien que les propriétés non-clé soient apparemment définies en tant que propriétés statiques, le comportement au moment de l’exécution de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tel qu’il est hébergé par le système réévaluera les propriétés en temps réel et tiendra compte des modifications pilotées par l’utilisateur pour les valeurs système. L’exemple suivant montre comment spécifier les paramètres de police d’un bouton.  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.SystemFonts>
- [Peindre une zone avec un pinceau système](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [Utiliser SystemParameters](how-to-use-systemparameters.md)
- [Utiliser des clés de polices système](how-to-use-system-fonts-keys.md)
- [Rubriques de guide pratique](resources-how-to-topics.md)
- [x:Static, extension de balisage](../../xaml-services/x-static-markup-extension.md)
- [Ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Extension de balisage DynamicResource](dynamicresource-markup-extension.md)
