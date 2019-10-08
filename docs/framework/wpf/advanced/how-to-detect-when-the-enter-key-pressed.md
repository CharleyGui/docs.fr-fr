---
title: 'Procédure : Détecter quand la touche entrée est enfoncée'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: e2337826077c836696937f91541d6d261f1270aa
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004823"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a><span data-ttu-id="e123c-102">Procédure : Détecter quand la touche entrée est enfoncée</span><span class="sxs-lookup"><span data-stu-id="e123c-102">How to: Detect When the Enter Key Pressed</span></span>
<span data-ttu-id="e123c-103">Cet exemple montre comment détecter quand la touche <xref:System.Windows.Input.Key.Enter> est enfoncée sur le clavier.</span><span class="sxs-lookup"><span data-stu-id="e123c-103">This example shows how to detect when the <xref:System.Windows.Input.Key.Enter> key is pressed on the keyboard.</span></span>  
  
 <span data-ttu-id="e123c-104">Cet exemple se compose d’un fichier [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et d’un fichier code-behind.</span><span class="sxs-lookup"><span data-stu-id="e123c-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e123c-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="e123c-105">Example</span></span>  
 <span data-ttu-id="e123c-106">Lorsque l’utilisateur appuie sur la touche <xref:System.Windows.Input.Key.Enter> dans la <xref:System.Windows.Controls.TextBox>, le texte entré s’affiche dans une autre zone de la [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e123c-106">When the user presses the <xref:System.Windows.Input.Key.Enter> key in the <xref:System.Windows.Controls.TextBox>, the input in the text box appears in another area of the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="e123c-107">Le code XAML suivant crée l’interface utilisateur, qui se compose d’un <xref:System.Windows.Controls.StackPanel>, d’un <xref:System.Windows.Controls.TextBlock> et d’un <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="e123c-107">The following XAML creates the user interface, which consists of a <xref:System.Windows.Controls.StackPanel>, a <xref:System.Windows.Controls.TextBlock>, and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 <span data-ttu-id="e123c-108">Le code-behind suivant crée le <xref:System.Windows.UIElement.KeyDown> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="e123c-108">The following code behind creates the <xref:System.Windows.UIElement.KeyDown> event handler.</span></span>  <span data-ttu-id="e123c-109">Si la touche enfoncée est la touche <xref:System.Windows.Input.Key.Enter>, un message s’affiche dans le <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="e123c-109">If the key that is pressed is the <xref:System.Windows.Input.Key.Enter> key, a message is displayed in the <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a><span data-ttu-id="e123c-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e123c-110">See also</span></span>

- [<span data-ttu-id="e123c-111">Vue d’ensemble des entrées</span><span class="sxs-lookup"><span data-stu-id="e123c-111">Input Overview</span></span>](input-overview.md)
- [<span data-ttu-id="e123c-112">Vue d’ensemble des événements routés</span><span class="sxs-lookup"><span data-stu-id="e123c-112">Routed Events Overview</span></span>](routed-events-overview.md)
