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
# <a name="how-to-open-a-message-box"></a>Comment : ouvrir une boîte de message
Cet exemple montre comment ouvrir une boîte de message.  
  
## <a name="example"></a>Exemple  
 Une boîte de message est une boîte de dialogue modale préfabriquée qui permet d’afficher des informations pour les utilisateurs. Pour ouvrir une boîte de message, vous appelez la méthode statique <xref:System.Windows.MessageBox.Show%2A> de la classe <xref:System.Windows.MessageBox>. Lorsque <xref:System.Windows.MessageBox.Show%2A> est appelé, le message est passé à l’aide d’un paramètre de chaîne. Plusieurs surcharges de <xref:System.Windows.MessageBox.Show%2A> vous permettent de configurer le mode d’affichage d’une boîte de message (consultez <xref:System.Windows.MessageBox>).  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a>Voir aussi

- [Exemple MessageBox](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox)
