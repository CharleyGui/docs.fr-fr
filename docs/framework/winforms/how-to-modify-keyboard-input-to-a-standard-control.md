---
title: 'Procédure : changer l’entrée de clavier en contrôle standard'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyboard input [Windows Forms], modifying
- modifying keyboard input
- Windows Forms, modifying keyboard input
- keyboards [Windows Forms], keyboard input
ms.assetid: 626d3712-d866-4988-bcda-a2d5b36ec0ba
ms.openlocfilehash: 1aa22501eb3d15b30be4ea4918473cf5a48cfe94
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964289"
---
# <a name="how-to-modify-keyboard-input-to-a-standard-control"></a>Procédure : changer l’entrée de clavier en contrôle standard
Windows Forms offre la possibilité de consommer et de modifier l'entrée au clavier. Consommer une touche signifie gérer une touche dans une méthode ou un gestionnaire d'événements pour que d'autres méthodes et événements plus loin dans la file d'attente de messages ne reçoivent pas la valeur de la touche. Modifier une touche signifie modifier sa valeur pour que les méthodes et les gestionnaires d'événements plus loin dans la file d'attente de messages reçoivent une valeur de touche différente. Cette rubrique montre comment accomplir ces tâches.  
  
### <a name="to-consume-a-key"></a>Pour consommer une touche  
  
- Dans un gestionnaire d'événements <xref:System.Windows.Forms.Control.KeyPress>, affectez la valeur `true` à la propriété <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> de la classe <xref:System.Windows.Forms.KeyPressEventArgs>.  
  
     ou  
  
     Dans un gestionnaire d'événements <xref:System.Windows.Forms.Control.KeyDown>, affectez la valeur `true` à la propriété <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> de la classe <xref:System.Windows.Forms.KeyEventArgs>.  
  
    > [!NOTE]
    > La définition de la propriété <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> dans le gestionnaire d'événements <xref:System.Windows.Forms.Control.KeyDown> n'empêche pas les événements <xref:System.Windows.Forms.Control.KeyPress> et <xref:System.Windows.Forms.Control.KeyUp> d'être déclenchés pour la séquence de touches actuelle. Vous devez pour cela utiliser la propriété <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A>.  
  
     L'exemple suivant est un extrait d'instruction `switch` qui examine la propriété <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> du <xref:System.Windows.Forms.KeyPressEventArgs> reçu par un gestionnaire d'événements <xref:System.Windows.Forms.Control.KeyPress>. Ce code consomme les touches de caractère « A » et « a ».  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#6)]  
  
### <a name="to-modify-a-standard-character-key"></a>Pour modifier une touche de caractère standard  
  
- Dans un gestionnaire d'événements <xref:System.Windows.Forms.Control.KeyPress>, affectez à la propriété <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> de la classe <xref:System.Windows.Forms.KeyPressEventArgs> la valeur de la nouvelle touche de caractère.  
  
     L'exemple suivant est un extrait d'instruction `switch` qui remplace « B » par « A » et « b » par « a ». Notez que la propriété <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> du paramètre <xref:System.Windows.Forms.KeyPressEventArgs> a la valeur `false`, pour que la nouvelle valeur de touche soit propagée aux autres méthodes et événements dans la file d'attente de messages.  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#7)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#7)]  
  
### <a name="to-modify-a-noncharacter-key"></a>Pour modifier une touche non-caractère  
  
- Substituez une méthode <xref:System.Windows.Forms.Control> qui traite les messages Windows, détectez le message WM_KEYDOWN ou WM_SYSKEYDOWN et affectez à la propriété <xref:System.Windows.Forms.Message.WParam%2A> du paramètre <xref:System.Windows.Forms.Message> la valeur <xref:System.Windows.Forms.Keys> qui représente la nouvelle touche non-caractère.  
  
     L'exemple de code suivant montre comment substituer la méthode <xref:System.Windows.Forms.Control.PreProcessMessage%2A> d'un contrôle pour détecter les touches F1 à F9 et modifier toute activation de la touche F3 en F1. Pour plus d’informations <xref:System.Windows.Forms.Control> sur les méthodes que vous pouvez substituer pour intercepter des messages de clavier, consultez [entrée d’utilisateur dans une application Windows Forms](user-input-in-a-windows-forms-application.md) et fonctionnement de [l’entrée au clavier](how-keyboard-input-works.md).  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#12)]  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant est l'application complète pour les exemples de code des sections précédentes. L'application utilise un contrôle personnalisé dérivé de la classe <xref:System.Windows.Forms.TextBox> pour consommer et modifier l'entrée au clavier.  
  
 [!code-csharp[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- des références aux assemblys System, System.Drawing et System.Windows.Forms.  
  
## <a name="see-also"></a>Voir aussi

- [Entrée au clavier dans une application Windows Forms](keyboard-input-in-a-windows-forms-application.md)
- [Entrée d’utilisateur dans une application Windows Forms](user-input-in-a-windows-forms-application.md)
- [Fonctionnement de l’entrée au clavier](how-keyboard-input-works.md)
