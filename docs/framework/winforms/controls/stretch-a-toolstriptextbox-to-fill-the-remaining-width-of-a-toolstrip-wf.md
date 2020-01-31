---
title: "Comment : étirer un ToolStripTextBox pour remplir la largeur restante d'un ToolStrip"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
ms.openlocfilehash: c60cc2a377f08a73159f25b2ab5f2812d41f0c10
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742842"
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a>Comment : étirer un ToolStripTextBox pour remplir la largeur restante d'un ToolStrip (Windows Forms)
Lorsque vous affectez à la propriété <xref:System.Windows.Forms.ToolStrip.Stretch%2A> d’un contrôle <xref:System.Windows.Forms.ToolStrip> la valeur `true`, le contrôle remplit son conteneur de bout en bout, puis se redimensionne quand son conteneur est redimensionné. Dans cette configuration, il peut s’avérer utile d’étirer un élément dans le contrôle, tel qu’un <xref:System.Windows.Forms.ToolStripTextBox>, de remplir l’espace disponible et de le redimensionner lorsque le contrôle est redimensionné. Cet étirement est utile, par exemple, si vous souhaitez obtenir une apparence et un comportement similaires à la barre d’adresses dans Microsoft® Internet Explorer.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant fournit une classe dérivée de <xref:System.Windows.Forms.ToolStripTextBox> appelée `ToolStripSpringTextBox`. Cette classe substitue la méthode <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> pour calculer la largeur disponible du contrôle <xref:System.Windows.Forms.ToolStrip> parent après la soustraction de la largeur combinée de tous les autres éléments. Cet exemple de code fournit également une classe <xref:System.Windows.Forms.Form> et une classe `Program` pour illustrer le nouveau comportement.  
  
 [!code-csharp[ToolStripSpringTextBox#00](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- Références aux assemblys System, System.Drawing et System.Windows.Forms.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripTextBox>
- <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>
- [Architecture du contrôle ToolStrip](toolstrip-control-architecture.md)
- [Guide pratique pour utiliser la propriété Spring dans un StatusStrip de manière interactive](how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
