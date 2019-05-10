---
title: 'Procédure : afficher un élément de style visuel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- visual themes [Windows Forms], applying to elements of Windows Forms applications
- professional appearance [Windows Forms], applying to elements of Windows Forms applications
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: a207781b-1baa-4ce9-b788-1e951bd4b5df
ms.openlocfilehash: a2b9524b6a3e3c77d3c68c4d9e138b8c0e2a9373
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662280"
---
# <a name="how-to-render-a-visual-style-element"></a>Procédure : afficher un élément de style visuel
Le <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> expose de l’espace de noms <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> objets qui représentent l’utilisateur Windows de l’interface éléments pris en charge par les styles visuels. Cette rubrique montre comment utiliser le <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> classe pour restituer le <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> qui représente le **fermer la session** et **arrêter** boutons du menu Démarrer.  
  
### <a name="to-render-a-visual-style-element"></a>Pour restituer un élément de style visuel  
  
1. Créer un <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> et définissez-le sur l’élément que vous souhaitez dessiner. Notez l’utilisation de la <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A?displayProperty=nameWithType> propriété et la <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.IsElementDefined%2A?displayProperty=nameWithType> méthode ; le <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor%2A> constructeur lève une exception si les styles visuels sont désactivés ou un élément n’est pas défini.  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#4)]  
  
2. Appelez le <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.DrawBackground%2A> méthode pour restituer l’élément qui le <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> actuellement représente.  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#6)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#6)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- Un contrôle personnalisé dérivé de la <xref:System.Windows.Forms.Control> classe.  
  
- Un <xref:System.Windows.Forms.Form> qui héberge le contrôle personnalisé.  
  
- Fait référence à la <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, et <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> espaces de noms.  
  
## <a name="see-also"></a>Voir aussi

- [Rendu des contrôles avec les styles visuels](rendering-controls-with-visual-styles.md)
