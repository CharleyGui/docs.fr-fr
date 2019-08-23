---
title: 'Procédure : déterminer la touche de modification activée'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input
- shift keys
- events [Windows Forms], mouse
- Keys.ControlKey enumeration member
- keys [Windows Forms], control keys
- user input [Windows Forms], checking for keyboard
- keys [Windows Forms], determining last pressed
- keys [Windows Forms], shift keys
- keys [Windows Forms], modifier keys
- control keys
- keys [Windows Forms], alt keys
- alt keys
- Keys.Shift enumeration member
- events [Windows Forms], keyboard
- keyboards [Windows Forms], keyboard input
- Keys.Alt enumeration member
- modifier keys
ms.assetid: 1e184048-0ae3-4067-a200-d4ba31dbc2cb
ms.openlocfilehash: 37fa897f5a2e1c65cbd5db9189f1500e3427c920
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964313"
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a>Procédure : déterminer la touche de modification activée
Lorsque vous créez une application qui accepte les séquences de touches de l’utilisateur, vous pouvez également surveiller les touches de modification telles que les touches Maj, ALT et CTRL. Quand une touche de modification est enfoncée en combinaison avec d’autres touches, ou avec des clics de souris, votre application peut réagir de manière appropriée. Par exemple, si la lettre S est enfoncée, cela peut simplement entraîner l’affichage d’un «s» à l’écran, mais si vous appuyez sur les touches CTRL + S, le document actif peut être enregistré. Si vous gérez l' <xref:System.Windows.Forms.Control.KeyDown> événement, la <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> propriété du <xref:System.Windows.Forms.KeyEventArgs> reçu par le gestionnaire d’événements spécifie quelles touches de modification sont enfoncées. La <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> propriété de spécifie également <xref:System.Windows.Forms.KeyEventArgs> le caractère qui a été activé, ainsi que les touches de modification associées à une opération or au niveau du bit. Toutefois, si vous gérez l' <xref:System.Windows.Forms.Control.KeyPress> événement ou un événement de souris, le gestionnaire d’événements ne reçoit pas ces informations. Dans ce cas, vous devez utiliser la <xref:System.Windows.Forms.Control.ModifierKeys%2A> propriété de la <xref:System.Windows.Forms.Control> classe. Dans les deux cas, vous devez effectuer une opération de bits and <xref:System.Windows.Forms.Keys> de la valeur appropriée et de la valeur que vous testez. L' <xref:System.Windows.Forms.Keys> énumération offre des variations de chaque touche de modification. il est donc important que vous exécutiez l’opération de bits and avec la valeur correcte. Par exemple, la touche Maj est représentée par <xref:System.Windows.Forms.Keys.Shift> <xref:System.Windows.Forms.Keys.RShiftKey> , <xref:System.Windows.Forms.Keys.ShiftKey>et <xref:System.Windows.Forms.Keys.LShiftKey> la valeur correcte pour tester Shift comme touche de modification est <xref:System.Windows.Forms.Keys.Shift>. De même, pour tester les touches Ctrl et Alt en tant que modificateurs, <xref:System.Windows.Forms.Keys.Control> vous <xref:System.Windows.Forms.Keys.Alt> devez utiliser respectivement les valeurs et.  
  
> [!NOTE]
> Visual Basic programmeurs peuvent également accéder aux informations de clé <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> par le biais de la propriété  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a>Pour déterminer la touche de modification qui a été enfoncée  
  
- Utilisez l’opérateur `AND` au niveau du <xref:System.Windows.Forms.Control.ModifierKeys%2A> bit avec la propriété et une <xref:System.Windows.Forms.Keys> valeur de l’énumération pour déterminer si une touche de modification particulière est enfoncée. L’exemple de code suivant montre comment déterminer si la touche Maj est enfoncée <xref:System.Windows.Forms.Control.KeyPress> dans un gestionnaire d’événements.  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.ModifierKeys%2A>
- [Entrée au clavier dans une application Windows Forms](keyboard-input-in-a-windows-forms-application.md)
- [Guide pratique pour Déterminer si CapsLock est activé dans Visual Basic](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))
