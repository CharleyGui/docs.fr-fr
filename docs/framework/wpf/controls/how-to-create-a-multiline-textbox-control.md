---
title: 'Comment : créer un contrôle TextBox multiligne'
description: Découvrez comment utiliser XAML pour définir un contrôle TextBox qui se développe pour s’adapter à plusieurs lignes de texte dans une application Windows Presentation Foundation.
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
ms.openlocfilehash: 0a88d4d768884df135afddb491431650b9ba2d24
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166253"
---
# <a name="how-to-create-a-multiline-textbox-control"></a>Comment : créer un contrôle TextBox multiligne
Cet exemple montre comment utiliser [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pour définir un <xref:System.Windows.Controls.TextBox> contrôle qui se développe automatiquement pour s’adapter à plusieurs lignes de texte.  
  
## <a name="example"></a>Exemple  
 Si vous affectez à l’attribut la valeur <xref:System.Windows.Controls.TextBox.TextWrapping%2A> **Wrap** , le texte entré est renvoyé à la ligne lorsque le bord du <xref:System.Windows.Controls.TextBox> contrôle est atteint, ce qui étend automatiquement le <xref:System.Windows.Controls.TextBox> contrôle pour inclure de la place pour une nouvelle ligne, si nécessaire.  
  
 Si vous affectez la <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> **valeur true** à l’attribut, une nouvelle ligne est insérée quand la touche retour est enfoncée, puis le développement automatique de <xref:System.Windows.Controls.TextBox> pour inclure de l’espace pour une nouvelle ligne, si nécessaire.  
  
 L' <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> attribut ajoute une barre de défilement au <xref:System.Windows.Controls.TextBox> , afin que le contenu du <xref:System.Windows.Controls.TextBox> puisse être défilé si le se <xref:System.Windows.Controls.TextBox> développe au-delà de la taille du frame ou de la fenêtre qui l’englobe.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.TextWrapping>
- [Vue d'ensemble de TextBox](textbox-overview.md)
- [Vue d'ensemble de RichTextBox](richtextbox-overview.md)
