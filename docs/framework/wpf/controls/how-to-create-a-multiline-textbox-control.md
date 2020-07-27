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
# <a name="how-to-create-a-multiline-textbox-control"></a><span data-ttu-id="22511-103">Comment : créer un contrôle TextBox multiligne</span><span class="sxs-lookup"><span data-stu-id="22511-103">How to: Create a Multiline TextBox Control</span></span>
<span data-ttu-id="22511-104">Cet exemple montre comment utiliser [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pour définir un <xref:System.Windows.Controls.TextBox> contrôle qui se développe automatiquement pour s’adapter à plusieurs lignes de texte.</span><span class="sxs-lookup"><span data-stu-id="22511-104">This example shows how to use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to define a <xref:System.Windows.Controls.TextBox> control that will automatically expand to accommodate multiple lines of text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22511-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="22511-105">Example</span></span>  
 <span data-ttu-id="22511-106">Si vous affectez à l’attribut la valeur <xref:System.Windows.Controls.TextBox.TextWrapping%2A> **Wrap** , le texte entré est renvoyé à la ligne lorsque le bord du <xref:System.Windows.Controls.TextBox> contrôle est atteint, ce qui étend automatiquement le <xref:System.Windows.Controls.TextBox> contrôle pour inclure de la place pour une nouvelle ligne, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="22511-106">Setting the <xref:System.Windows.Controls.TextBox.TextWrapping%2A> attribute to **Wrap** will cause entered text to wrap to a new line when the edge of the <xref:System.Windows.Controls.TextBox> control is reached, automatically expanding the <xref:System.Windows.Controls.TextBox> control to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="22511-107">Si vous affectez la <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> **valeur true** à l’attribut, une nouvelle ligne est insérée quand la touche retour est enfoncée, puis le développement automatique de <xref:System.Windows.Controls.TextBox> pour inclure de l’espace pour une nouvelle ligne, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="22511-107">Setting the <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> attribute to **true** causes a new line to be inserted when the RETURN key is pressed, once again automatically expanding the <xref:System.Windows.Controls.TextBox> to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="22511-108">L' <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> attribut ajoute une barre de défilement au <xref:System.Windows.Controls.TextBox> , afin que le contenu du <xref:System.Windows.Controls.TextBox> puisse être défilé si le se <xref:System.Windows.Controls.TextBox> développe au-delà de la taille du frame ou de la fenêtre qui l’englobe.</span><span class="sxs-lookup"><span data-stu-id="22511-108">The <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> attribute adds a scroll bar to the <xref:System.Windows.Controls.TextBox>, so that the contents of the <xref:System.Windows.Controls.TextBox> can be scrolled through if the <xref:System.Windows.Controls.TextBox> expands beyond the size of the frame or window that encloses it.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="22511-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22511-109">See also</span></span>

- <xref:System.Windows.TextWrapping>
- [<span data-ttu-id="22511-110">Vue d'ensemble de TextBox</span><span class="sxs-lookup"><span data-stu-id="22511-110">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="22511-111">Vue d'ensemble de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="22511-111">RichTextBox Overview</span></span>](richtextbox-overview.md)
