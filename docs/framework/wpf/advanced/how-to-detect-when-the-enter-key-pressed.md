---
title: "Comment : effectuer une détection en cas d'appui sur la touche Entrée"
description: Détectez quand la touche entrée est sélectionnée sur le clavier dans Windows Presentation Foundation. Cet exemple se compose de XAML et d’un fichier code-behind.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: a955f52ec7bf93b32c70259b27fb51747664ac2e
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163186"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a><span data-ttu-id="0efd2-104">Comment : effectuer une détection en cas d'appui sur la touche Entrée</span><span class="sxs-lookup"><span data-stu-id="0efd2-104">How to: Detect When the Enter Key Pressed</span></span>
<span data-ttu-id="0efd2-105">Cet exemple montre comment détecter le moment où la <xref:System.Windows.Input.Key.Enter> touche est enfoncée sur le clavier.</span><span class="sxs-lookup"><span data-stu-id="0efd2-105">This example shows how to detect when the <xref:System.Windows.Input.Key.Enter> key is pressed on the keyboard.</span></span>  
  
 <span data-ttu-id="0efd2-106">Cet exemple se compose d’un [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] fichier et d’un fichier code-behind.</span><span class="sxs-lookup"><span data-stu-id="0efd2-106">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0efd2-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="0efd2-107">Example</span></span>  
 <span data-ttu-id="0efd2-108">Quand l’utilisateur appuie sur la <xref:System.Windows.Input.Key.Enter> touche dans le <xref:System.Windows.Controls.TextBox> , l’entrée dans la zone de texte apparaît dans une autre zone du [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0efd2-108">When the user presses the <xref:System.Windows.Input.Key.Enter> key in the <xref:System.Windows.Controls.TextBox>, the input in the text box appears in another area of the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="0efd2-109">Le code XAML suivant crée l’interface utilisateur, qui se compose d’un, d’un <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.TextBlock> et d’un <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="0efd2-109">The following XAML creates the user interface, which consists of a <xref:System.Windows.Controls.StackPanel>, a <xref:System.Windows.Controls.TextBlock>, and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 <span data-ttu-id="0efd2-110">Le code-behind suivant crée le <xref:System.Windows.UIElement.KeyDown> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="0efd2-110">The following code behind creates the <xref:System.Windows.UIElement.KeyDown> event handler.</span></span>  <span data-ttu-id="0efd2-111">Si la touche enfoncée est la <xref:System.Windows.Input.Key.Enter> clé, un message s’affiche dans la <xref:System.Windows.Controls.TextBlock> .</span><span class="sxs-lookup"><span data-stu-id="0efd2-111">If the key that is pressed is the <xref:System.Windows.Input.Key.Enter> key, a message is displayed in the <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a><span data-ttu-id="0efd2-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0efd2-112">See also</span></span>

- [<span data-ttu-id="0efd2-113">Vue d'ensemble des entrées</span><span class="sxs-lookup"><span data-stu-id="0efd2-113">Input Overview</span></span>](input-overview.md)
- [<span data-ttu-id="0efd2-114">Vue d'ensemble des événements routés</span><span class="sxs-lookup"><span data-stu-id="0efd2-114">Routed Events Overview</span></span>](routed-events-overview.md)
