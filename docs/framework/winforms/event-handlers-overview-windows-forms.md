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
ms.openlocfilehash: ffec8a9f8e080dec78152e62e00e2dceefbdaab0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141690"
---
# <a name="event-handlers-overview-windows-forms"></a>Vue d'ensemble des gestionnaires d'événements (Windows Forms)
Un gestionnaire d’événements est une méthode qui est liée à un événement. Lorsque l’événement est déclenché, le code dans le gestionnaire de l’événement est exécuté. Chaque gestionnaire d’événements fournit deux paramètres qui vous permettent de gérer l’événement correctement. L’exemple suivant montre un <xref:System.Windows.Forms.Button> gestionnaire <xref:System.Windows.Forms.Control.Click> d’événements pour l’événement d’un contrôle.  
  
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
  
 Le premier`sender`paramètre, fournit une référence à l’objet qui a soulevé l’événement. Le deuxième `e`paramètre, dans l’exemple ci-dessus, passe un objet spécifique à l’événement qui est manipulé. En faisant référence aux propriétés de l’objet (et, parfois, à ses méthodes), vous pouvez obtenir des informations telles que l’emplacement de la souris pour les événements de souris ou les données transférées lors d’événements de drag-and-drop.  
  
 En règle générale, chaque événement produit un gestionnaire d’événements avec un type d’objet d’événement différent pour le deuxième paramètre. Certains gestionnaires d’événements, comme <xref:System.Windows.Forms.Control.MouseDown> <xref:System.Windows.Forms.Control.MouseUp> ceux pour les événements et les événements, ont le même type d’objet pour leur deuxième paramètre. Pour ce type d’événements, vous pouvez utiliser le même gestionnaire d’événements pour gérer les deux événements.  
  
 Vous pouvez également utiliser le même gestionnaire d’événements pour gérer le même événement pour différents contrôles. Par exemple, si vous <xref:System.Windows.Forms.RadioButton> avez un groupe de contrôles sur un <xref:System.Windows.Forms.Control.Click> formulaire, vous pouvez <xref:System.Windows.Forms.Control.Click> créer un gestionnaire d’événement unique pour l’événement et avoir l’événement de chaque contrôle lié au gestionnaire d’événement unique. Pour plus d’informations, voir [Comment : Connectez plusieurs événements à un gestionnaire d’événements unique dans les formulaires Windows](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).  
  
## <a name="see-also"></a>Voir aussi

- [Création de gestionnaires d’événements dans Windows Forms](creating-event-handlers-in-windows-forms.md)
- [Vue d'ensemble des événements](events-overview-windows-forms.md)
