---
title: 'Comment : connecter plusieurs événements à un même gestionnaire d’événements'
description: Découvrez comment connecter plusieurs événements à un même gestionnaire d’événements dans Windows Forms à l’aide de la vue événements du Fenêtre Propriétés en C#.
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
ms.openlocfilehash: cca85c223b46d9a82dbc3e34e3377fb83c075959
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621884"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a>Procédure : connecter plusieurs événements à un seul gestionnaire d’événements dans Windows Forms
Dans la conception de votre application, il peut s’avérer nécessaire d’utiliser un seul gestionnaire d’événements pour plusieurs événements ou de faire en sorte que plusieurs événements effectuent la même procédure. Par exemple, il est souvent plus efficace de faire en sorte qu’une commande de menu génère le même événement qu’un bouton de votre formulaire si elle expose la même fonctionnalité. Pour ce faire, vous pouvez utiliser la vue événements de l’Fenêtre Propriétés en C# ou le `Handles` mot clé et les zones de liste déroulante nom de la **classe** et nom de la **méthode** dans l’éditeur de code Visual Basic.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a>Pour connecter plusieurs événements à un même gestionnaire d’événements dans Visual Basic  
  
1. Cliquez avec le bouton droit sur le formulaire, puis choisissez **afficher le code**.  
  
2. Dans la zone de liste déroulante nom de la **classe** , sélectionnez l’un des contrôles dont vous souhaitez obtenir le handle de gestionnaire d’événements.  
  
3. Dans la zone de liste déroulante nom de la **méthode** , sélectionnez l’un des événements que vous souhaitez que le gestionnaire d’événements gère.  
  
4. L’éditeur de code insère le gestionnaire d’événements approprié et positionne le point d’insertion dans la méthode. Dans l’exemple ci-dessous, il s’agit <xref:System.Windows.Forms.Control.Click> de l’événement pour le <xref:System.Windows.Forms.Button> contrôle.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. Ajoutez les autres événements que vous souhaitez gérer à la `Handles` clause.  
  
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

- [Création de gestionnaires d'événements dans les Windows Forms](creating-event-handlers-in-windows-forms.md)
- [Vue d’ensemble des gestionnaires d’événements](event-handlers-overview-windows-forms.md)
