---
title: 'Comment : connecter plusieurs événements à un même gestionnaire d’événements'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- events [Windows Forms], connecting multiple to single event handler
- event handlers [Windows Forms], connecting events to
- menus [Windows Forms], event-handling methods for multiple menu items
- Windows Forms controls, events
- menu items [Windows Forms], multicasting event-handling methods
ms.assetid: 5a20749a-41b5-4acc-8eb1-9e5040b0a2c4
ms.openlocfilehash: 0591291522ab1da04fef90bf1c0a73cf33ba0518
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739609"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a>Comment : connecter plusieurs événements à un même gestionnaire d'événements dans les Windows Forms
Dans la conception de votre application, il peut s’avérer nécessaire d’utiliser un seul gestionnaire d’événements pour plusieurs événements ou de faire en sorte que plusieurs événements effectuent la même procédure. Par exemple, il est souvent plus efficace de faire en sorte qu’une commande de menu génère le même événement qu’un bouton de votre formulaire si elle expose la même fonctionnalité. Pour ce faire, vous pouvez utiliser la vue événements de la Fenêtre Propriétés C# dans ou à l’aide du mot clé `Handles` et des zones de liste déroulante nom de la **classe** et nom de la **méthode** dans l’éditeur de code Visual Basic.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a>Pour connecter plusieurs événements à un même gestionnaire d’événements dans Visual Basic  
  
1. Cliquez avec le bouton droit sur le formulaire, puis choisissez **afficher le code**.  
  
2. Dans la zone de liste déroulante nom de la **classe** , sélectionnez l’un des contrôles dont vous souhaitez obtenir le handle de gestionnaire d’événements.  
  
3. Dans la zone de liste déroulante nom de la **méthode** , sélectionnez l’un des événements que vous souhaitez que le gestionnaire d’événements gère.  
  
4. L’éditeur de code insère le gestionnaire d’événements approprié et positionne le point d’insertion dans la méthode. Dans l’exemple ci-dessous, il s’agit de l’événement <xref:System.Windows.Forms.Control.Click> pour le contrôle <xref:System.Windows.Forms.Button>.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. Ajoutez les autres événements que vous souhaitez gérer à la clause `Handles`.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6. Ajoutez le code approprié au gestionnaire d’événements.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a>Pour connecter plusieurs événements à un même gestionnaire d’événements en C\#
  
1. Sélectionnez le contrôle auquel vous souhaitez connecter un gestionnaire d’événements.  
  
2. Dans le Fenêtre Propriétés, cliquez sur le bouton **événements** (![bouton événements](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).  
  
3. Cliquez sur le nom de l’événement que vous souhaitez gérer.  
  
4. Dans la section valeur en regard du nom de l’événement, cliquez sur le bouton déroulant pour afficher la liste des gestionnaires d’événements existants qui correspondent à la signature de la méthode de l’événement que vous souhaitez gérer.  
  
5. Sélectionnez le gestionnaire d’événements approprié dans la liste.  
  
     Du code sera ajouté au formulaire pour lier l’événement au gestionnaire d’événements existant.  
  
## <a name="see-also"></a>Voir aussi

- [Création de gestionnaires d’événements dans les Windows Forms](creating-event-handlers-in-windows-forms.md)
- [Vue d'ensemble des gestionnaires d'événements](event-handlers-overview-windows-forms.md)
