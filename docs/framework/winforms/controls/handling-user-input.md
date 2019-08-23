---
title: Gestion des entrées utilisateur
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user input using code
- custom controls [Windows Forms], keyboard events using code
- custom controls [Windows Forms], mouse events using code
ms.assetid: d9b12787-86f6-4022-8e0f-e12d312c4af2
ms.openlocfilehash: f92b742c3f6feec72e5b3150204d7d984636281d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934094"
---
# <a name="handling-user-input"></a>Gestion des entrées utilisateur
Cette rubrique décrit les principaux événements liés au clavier et à <xref:System.Windows.Forms.Control?displayProperty=nameWithType>la souris fournis par. Lors de la gestion d’un événement, les auteurs de contrôle doivent substituer la méthode protégée `On`*EventName* au lieu d’attacher un délégué à l’événement. Pour un examen des événements, consultez [Déclenchement d’événements à partir d’un composant](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).  
  
> [!NOTE]
> Si aucune donnée n’est associée à un événement, une instance de la classe <xref:System.EventArgs> de base est passée comme argument à la `On`méthode *EventName* .  
  
## <a name="keyboard-events"></a>Événements de clavier  
 Les événements de clavier courants que votre contrôle peut gérer <xref:System.Windows.Forms.Control.KeyDown>sont <xref:System.Windows.Forms.Control.KeyPress>, et <xref:System.Windows.Forms.Control.KeyUp>.  
  
|Nom de l'événement|Méthode à substituer|Description de l’événement|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|Déclenché uniquement lorsque l’utilisateur appuie initialement sur une touche.|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|Déclenché à chaque fois que l’utilisateur appuie sur une touche. Si une touche est maintenue enfoncée, un <xref:System.Windows.Forms.Control.KeyPress> événement est déclenché à la fréquence de répétition définie par le système d’exploitation.|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|Déclenché lors du relâchement d’une touche.|  
  
> [!NOTE]
> La gestion des entrées sur le clavier est considérablement plus complexe que la substitution des événements dans le tableau précédent. Ce thème dépasse le cadre de cette rubrique. Pour plus d’informations, consultez [Entrée d’utilisateur dans Windows Forms](../user-input-in-windows-forms.md).  
  
## <a name="mouse-events"></a>Événements de souris  
 Les événements de souris que votre contrôle peut gérer <xref:System.Windows.Forms.Control.MouseDown>sont <xref:System.Windows.Forms.Control.MouseEnter> <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave> <xref:System.Windows.Forms.Control.MouseMove>,,, et <xref:System.Windows.Forms.Control.MouseUp>.  
  
|Nom de l'événement|Méthode à substituer|Description de l’événement|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|Déclenché quand le bouton de la souris est enfoncé alors que le pointeur se trouve sur le contrôle.|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|Déclenché lorsque le pointeur pénètre la première fois dans la zone du contrôle.|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|Déclenché lorsque le pointeur pointe sur le contrôle.|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|Déclenché lorsque le pointeur quitte la zone du contrôle.|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|Déclenché lorsque le pointeur se déplace dans la zone du contrôle.|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|Déclenché lorsque le bouton de la souris est relâché alors que le pointeur se trouve sur le contrôle ou quitte la zone du contrôle.|  
  
 Le fragment de code suivant montre un exemple de substitution de <xref:System.Windows.Forms.Control.MouseDown> l’événement.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 Le fragment de code suivant montre un exemple de substitution de <xref:System.Windows.Forms.Control.MouseMove> l’événement.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 Le fragment de code suivant montre un exemple de substitution de <xref:System.Windows.Forms.Control.MouseUp> l’événement.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 Pour obtenir le code source complet de `FlashTrackBar` l’exemple, [consultez Procédure: Créez un contrôle de Windows Forms qui affiche](how-to-create-a-windows-forms-control-that-shows-progress.md)la progression.  
  
## <a name="see-also"></a>Voir aussi

- [Événements dans les contrôles Windows Forms](events-in-windows-forms-controls.md)
- [Définition d’un événement](defining-an-event-in-windows-forms-controls.md)
- [Événements](../../../standard/events/index.md)
- [Entrées d’utilisateur dans les Windows Forms](../user-input-in-windows-forms.md)
