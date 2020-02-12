---
title: 'Comment : ouvrir une boîte de message'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
ms.openlocfilehash: bd2c4dce78e46163eb4628cb3aab829fc0173edf
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77123725"
---
# <a name="how-to-open-a-message-box"></a><span data-ttu-id="18294-102">Comment : ouvrir une boîte de message</span><span class="sxs-lookup"><span data-stu-id="18294-102">How to: Open a Message Box</span></span>
<span data-ttu-id="18294-103">Cet exemple montre comment ouvrir une boîte de message.</span><span class="sxs-lookup"><span data-stu-id="18294-103">This example shows how to open a message box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18294-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="18294-104">Example</span></span>  
 <span data-ttu-id="18294-105">Une boîte de message est une boîte de dialogue modale préfabriquée qui permet d’afficher des informations pour les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="18294-105">A message box is a prefabricated modal dialog box for displaying information to users.</span></span> <span data-ttu-id="18294-106">Pour ouvrir une boîte de message, vous appelez la méthode statique <xref:System.Windows.MessageBox.Show%2A> de la classe <xref:System.Windows.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="18294-106">A message box is opened by calling the static <xref:System.Windows.MessageBox.Show%2A> method of the <xref:System.Windows.MessageBox> class.</span></span> <span data-ttu-id="18294-107">Lorsque <xref:System.Windows.MessageBox.Show%2A> est appelé, le message est passé à l’aide d’un paramètre de chaîne.</span><span class="sxs-lookup"><span data-stu-id="18294-107">When <xref:System.Windows.MessageBox.Show%2A> is called, the message is passed using a string parameter.</span></span> <span data-ttu-id="18294-108">Plusieurs surcharges de <xref:System.Windows.MessageBox.Show%2A> vous permettent de configurer le mode d’affichage d’une boîte de message (consultez <xref:System.Windows.MessageBox>).</span><span class="sxs-lookup"><span data-stu-id="18294-108">Several overloads of <xref:System.Windows.MessageBox.Show%2A> allow you to configure how a message box will appear (see <xref:System.Windows.MessageBox>).</span></span>  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a><span data-ttu-id="18294-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18294-109">See also</span></span>

- [<span data-ttu-id="18294-110">Exemple MessageBox</span><span class="sxs-lookup"><span data-stu-id="18294-110">MessageBox Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox)
