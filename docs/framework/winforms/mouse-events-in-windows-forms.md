---
title: Événements de souris
description: Apprenez à obtenir l’emplacement de la souris à partir des événements de souris et à comprendre l’ordre dans lequel les événements de clic de souris sont déclenchés dans les contrôles Windows Forms.
ms.date: 03/30/2017
helpviewer_keywords:
- MouseLeave event [Windows Forms]
- events [Windows Forms], mouse
- Click event [Windows Forms], raising order
- Windows Forms controls, click events
- MouseDoubleClick event [Windows Forms]
- MouseEnter event [Windows Forms]
- MouseHover event [Windows Forms]
- MouseDown event [Windows Forms]
- MouseClick event [Windows Forms]
- MouseMove event [Windows Forms]
- mouse [Windows Forms], events
- MouseUp event
ms.assetid: 8cf0070d-793b-4876-b09e-d20d28280fab
ms.openlocfilehash: 640448109961ea5fdf3600ef9e72d7d10e8c9e49
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174378"
---
# <a name="mouse-events-in-windows-forms"></a>Événements liés à la souris dans les Windows Forms

Quand vous gérez l'entrée de souris, vous souhaitez habituellement connaître l'emplacement du pointeur de la souris et l'état de ses boutons. Cette rubrique fournit des détails sur la façon d'obtenir des informations à partir des événements de souris et explique l'ordre dans lequel les événements de clic de souris sont déclenchés dans les contrôles Windows Forms. Pour obtenir la liste et la description de tous les événements de la souris, consultez [fonctionnement de l’entrée de la souris dans Windows Forms](how-mouse-input-works-in-windows-forms.md).  Consultez également [vue d’ensemble des gestionnaires d’événements (Windows Forms)](event-handlers-overview-windows-forms.md) et [vue d’ensemble des événements (Windows Forms)](events-overview-windows-forms.md).

## <a name="mouse-information"></a>Informations sur la souris

Un <xref:System.Windows.Forms.MouseEventArgs> est envoyé aux gestionnaires d'événements de souris liés aux clics de souris et au suivi des mouvements de souris. <xref:System.Windows.Forms.MouseEventArgs> fournit des informations sur l'état actuel de la souris, y compris l'emplacement du pointeur de la souris sous forme de coordonnées clientes, les boutons de souris qui sont enfoncés et si la roulette a défilé. Plusieurs événements de souris, tels que ceux qui indiquent simplement si le pointeur de souris pénétré ou quitté les limites d'un contrôle, envoient un <xref:System.EventArgs> au gestionnaire d'événements sans aucune information complémentaire.

Si vous souhaitez connaître l'état actuel des boutons de la souris ou l'emplacement du pointeur de la souris et que vous souhaitez éviter de gérer un événement de souris, vous pouvez aussi utiliser les propriétés <xref:System.Windows.Forms.Control.MouseButtons%2A> et <xref:System.Windows.Forms.Control.MousePosition%2A> de la classe <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control.MouseButtons%2A> retourne des informations sur les boutons de souris qui sont actuellement enfoncés. <xref:System.Windows.Forms.Control.MousePosition%2A> retourne les coordonnées d'écran du pointeur de la souris et est équivalente à la valeur retournée par <xref:System.Windows.Forms.Cursor.Position%2A>.

## <a name="converting-between-screen-and-client-coordinates"></a>Conversion entre les coordonnées clientes et d'écran

Étant donné que certaines informations sur l'emplacement de la souris sont spécifiées en coordonnées clientes et d'autres en coordonnées d'écran, vous devrez peut-être convertir un point d'un système de coordonnées en un autre. Cette opération peut être effectuée facilement à l'aide des méthodes <xref:System.Windows.Forms.Control.PointToClient%2A> et <xref:System.Windows.Forms.Control.PointToScreen%2A> disponibles sur la classe <xref:System.Windows.Forms.Control>.

## <a name="standard-click-event-behavior"></a>Comportement d'événement de clic standard

Si vous souhaitez gérer les événements de clic de souris dans l'ordre approprié, vous devez connaître l'ordre dans lequel les événements de clic sont déclenchés dans les contrôles Windows Forms. Tous les contrôles Windows Forms déclenchent les événements de clic dans le même ordre quand un bouton de souris est enfoncé et relâché (quel que soit le bouton), sauf indication contraire mentionnée dans la liste suivante pour un contrôle spécifique. La liste ci-dessous indique l'ordre des événements déclenchés pour un clic sur un bouton de souris :

1. Événement<xref:System.Windows.Forms.Control.MouseDown> .

2. Événement<xref:System.Windows.Forms.Control.Click> .

3. Événement<xref:System.Windows.Forms.Control.MouseClick> .

4. Événement<xref:System.Windows.Forms.Control.MouseUp> .

Voici l’ordre des événements déclenchés pour un clic double-bouton de la souris :

1. Événement<xref:System.Windows.Forms.Control.MouseDown> .

2. Événement<xref:System.Windows.Forms.Control.Click> .

3. Événement<xref:System.Windows.Forms.Control.MouseClick> .

4. Événement<xref:System.Windows.Forms.Control.MouseUp> .

5. Événement<xref:System.Windows.Forms.Control.MouseDown> .

6. Événement<xref:System.Windows.Forms.Control.DoubleClick> . (Cela peut varier, selon que le contrôle en question a la valeur <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> définie comme bit de style `true`. Pour plus d'informations sur la façon de définir un bit <xref:System.Windows.Forms.ControlStyles>, consultez la méthode <xref:System.Windows.Forms.Control.SetStyle%2A>.)

7. Événement<xref:System.Windows.Forms.Control.MouseDoubleClick> .

8. Événement<xref:System.Windows.Forms.Control.MouseUp> .

Pour obtenir un exemple de code illustrant l’ordre des événements de clic de souris, consultez [Comment : gérer des événements d’entrée d’utilisateur dans les contrôles de Windows Forms](how-to-handle-user-input-events-in-windows-forms-controls.md).

### <a name="individual-controls"></a>Contrôles spécifiques

Les contrôles suivants n'ont pas le comportement d'événement de clic de souris standard :

- <xref:System.Windows.Forms.Button>
- <xref:System.Windows.Forms.CheckBox>
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.RadioButton>

  > [!NOTE]
  > Pour le contrôle <xref:System.Windows.Forms.ComboBox>, le comportement d'événement détaillé plus loin se produit si l'utilisateur clique sur le champ d'édition, le bouton ou un élément dans la liste.

  - Clic gauche : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Clic droit : aucun événement de clic déclenché

  - Double-clic gauche : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Double-clic droit : aucun événement de clic déclenché

- Contrôles <xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox> et <xref:System.Windows.Forms.CheckedListBox>

  > [!NOTE]
  > Le comportement d'événement détaillé plus loin se produit quand l'utilisateur clique dans ces contrôles.

  - Clic gauche : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Clic droit : aucun événement de clic déclenché

  - Double-clic gauche : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>

  - Double-clic droit : aucun événement de clic déclenché

- Contrôle <xref:System.Windows.Forms.ListView>

  > [!NOTE]
  > Le comportement d'événement détaillé plus loin se produit quand l'utilisateur clique sur les éléments dans le contrôle <xref:System.Windows.Forms.ListView>. Aucun événement n'est déclenché si l'utilisateur clique ailleurs sur le contrôle. Outre les événements décrits plus loin, il existe les événements <xref:System.Windows.Forms.ListView.BeforeLabelEdit> et <xref:System.Windows.Forms.ListView.AfterLabelEdit>, qui peuvent être utiles si vous souhaitez utiliser la validation avec le contrôle <xref:System.Windows.Forms.ListView>.

  - Clic gauche : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Clic droit : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Double-clic gauche : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>

  - Double-clic droit : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>

- Contrôle <xref:System.Windows.Forms.TreeView>

  > [!NOTE]
  > Le comportement d'événement détaillé plus loin se produit uniquement quand l'utilisateur clique sur les éléments proprement dits ou à droite des éléments dans le contrôle <xref:System.Windows.Forms.TreeView>. Aucun événement n'est déclenché si l'utilisateur clique ailleurs sur le contrôle. Outre ceux décrits plus loin, il existe les événements <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck> et <xref:System.Windows.Forms.TreeView.AfterLabelEdit>, qui peuvent être utiles si vous souhaitez utiliser la validation avec le contrôle <xref:System.Windows.Forms.TreeView>.

  - Clic gauche : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Clic droit : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>

  - Double-clic gauche : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>

  - Double-clic droit : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>

### <a name="painting-behavior-of-toggle-controls"></a>Comportement de peinture des contrôles Toggle

Les contrôles de basculement, tels que ceux dérivant de la classe <xref:System.Windows.Forms.ButtonBase>, présentent le comportement de peinture distinctif suivant en cas de combinaison avec des événements de clic de souris :

1. L'utilisateur appuie sur le bouton de la souris.

2. Le contrôle est peint à l'état enfoncé.

3. L'événement <xref:System.Windows.Forms.Control.MouseDown> est déclenché.

4. L’utilisateur relâche le bouton de la souris.

5. Le contrôle est peint à l'état déclenché.

6. L'événement <xref:System.Windows.Forms.Control.Click> est déclenché.

7. L'événement <xref:System.Windows.Forms.Control.MouseClick> est déclenché.

8. L'événement <xref:System.Windows.Forms.Control.MouseUp> est déclenché.

    > [!NOTE]
    > Si l'utilisateur déplace le pointeur hors du contrôle de basculement alors que le bouton de la souris est enfoncé (par exemple en cas de déplacement de la souris hors du contrôle <xref:System.Windows.Forms.Button> pendant qu'il est enfoncé), le contrôle de basculement est peint à l'état déclenché et seul l'événement <xref:System.Windows.Forms.Control.MouseUp> se produit. L'événement <xref:System.Windows.Forms.Control.Click> ou <xref:System.Windows.Forms.Control.MouseClick> ne se produira pas dans cette situation.

## <a name="see-also"></a>Voir aussi

- [Entrée de la souris dans une application Windows Forms](mouse-input-in-a-windows-forms-application.md)
