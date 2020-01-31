---
title: Vue d’ensemble des gestionnaires d’événements
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handling [Windows Forms], Windows Forms
- event handlers [Windows Forms], about event handlers
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
ms.openlocfilehash: 10ba458197973ede35849a86fec35003f139b8d2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743494"
---
# <a name="event-handlers-overview-windows-forms"></a>Vue d'ensemble des gestionnaires d'événements (Windows Forms)
Un gestionnaire d’événements est une méthode liée à un événement. Lorsque l’événement est déclenché, le code dans le gestionnaire d’événements est exécuté. Chaque gestionnaire d’événements fournit deux paramètres qui vous permettent de gérer correctement l’événement. L’exemple suivant montre un gestionnaire d’événements pour l’événement <xref:System.Windows.Forms.Control.Click> d’un contrôle <xref:System.Windows.Forms.Button>.  
  
```vb  
Private Sub button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles button1.Click  
  
End Sub  
```  
  
```csharp  
private void button1_Click(object sender, System.EventArgs e)   
{  
  
}  
```  
  
```cpp  
private:  
  void button1_Click(System::Object ^ sender,  
    System::EventArgs ^ e)  
  {  
  
  }  
```  
  
 Le premier paramètre,`sender`, fournit une référence à l’objet qui a déclenché l’événement. Le deuxième paramètre, `e`, dans l’exemple ci-dessus, passe un objet spécifique à l’événement géré. En référençant les propriétés de l’objet (et, parfois, ses méthodes), vous pouvez obtenir des informations telles que l’emplacement de la souris pour les événements de souris ou les données transférées dans les événements de glisser-déplacer.  
  
 En général, chaque événement produit un gestionnaire d’événements avec un type d’objet d’événement différent pour le deuxième paramètre. Certains gestionnaires d’événements, tels que ceux des événements <xref:System.Windows.Forms.Control.MouseDown> et <xref:System.Windows.Forms.Control.MouseUp>, ont le même type d’objet pour leur deuxième paramètre. Pour ces types d’événements, vous pouvez utiliser le même gestionnaire d’événements pour gérer les deux événements.  
  
 Vous pouvez également utiliser le même gestionnaire d’événements pour gérer le même événement pour différents contrôles. Par exemple, si vous avez un groupe de contrôles de <xref:System.Windows.Forms.RadioButton> sur un formulaire, vous pouvez créer un gestionnaire d’événements unique pour l’événement <xref:System.Windows.Forms.Control.Click> et faire en sorte que chaque événement du contrôle <xref:System.Windows.Forms.Control.Click> lié au gestionnaire d’événements unique. Pour plus d’informations, consultez [Comment : connecter plusieurs événements à un même gestionnaire d’événements dans Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).  
  
## <a name="see-also"></a>Voir aussi

- [Création de gestionnaires d’événements dans les Windows Forms](creating-event-handlers-in-windows-forms.md)
- [Vue d'ensemble des événements](events-overview-windows-forms.md)
