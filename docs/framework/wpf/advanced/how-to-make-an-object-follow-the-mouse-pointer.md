---
title: "Procédure : Faire en sorte qu'un objet suive le pointeur de la souris"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- following the mouse pointer (cursor)
- mouse pointer (cursor), making objects follow
- cursor (mouse pointer), making objects follow
ms.assetid: 50b20415-14bc-405c-baf3-2fb254fffde3
ms.openlocfilehash: 4ef3028b6c71b94a593d168ad6570c4aec12b86b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005067"
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a>Procédure : Faire en sorte qu'un objet suive le pointeur de la souris
Cet exemple montre comment modifier les dimensions d’un objet lorsque le pointeur de la souris se déplace sur l’écran.  
  
 L’exemple comprend un fichier [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] qui crée le [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] et un fichier code-behind qui crée le gestionnaire d’événements.  
  
## <a name="example"></a>Exemple  
 Le code XAML suivant crée le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], qui se compose d’une <xref:System.Windows.Shapes.Ellipse> à l’intérieur d’un <xref:System.Windows.Controls.StackPanel>, et attache le gestionnaire d’événements pour l’événement <xref:System.Windows.UIElement.MouseMove>.  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 Le code-behind suivant crée le <xref:System.Windows.UIElement.MouseMove> Gestionnaire d’événements.  Lorsque le pointeur de la souris se déplace, la hauteur et la largeur du <xref:System.Windows.Shapes.Ellipse> sont augmentées et réduites.  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des entrées](input-overview.md)
