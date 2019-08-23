---
title: 'Procédure : créer une interface utilisateur à plusieurs volets avec Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- user interface [Windows Forms], multipane
- SplitContainer control [Windows Forms], using the designer
- multipane user interface
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
ms.openlocfilehash: 97888a77dfc731be591d5f0284e87f45ef7dc437
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930169"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms-using-the-designer"></a>Procédure : créer une interface utilisateur à plusieurs volets avec Windows Forms à l’aide du concepteur
Dans la procédure suivante, vous allez créer une interface utilisateur à plusieurs volets similaire à celle utilisée dans Microsoft Outlook, avec une liste de **dossiers** , un volet **messages** et un volet de **visualisation** . Cette organisation est réalisée principalement via l’ancrage des contrôles au formulaire.

 Lorsque vous ancrez un contrôle, vous déterminez le bord du conteneur parent auquel un contrôle est attaché. Ainsi, si vous affectez <xref:System.Windows.Forms.SplitContainer.Dock%2A> à <xref:System.Windows.Forms.DockStyle.Right>la propriété la valeur, le bord droit du contrôle est ancré au bord droit de son contrôle parent. En outre, le bord ancré du contrôle est redimensionné pour correspondre à celui de son contrôle conteneur. Pour plus d’informations sur le <xref:System.Windows.Forms.SplitContainer.Dock%2A> fonctionnement de la propriété [, consultez Procédure: Ancrez les contrôles](how-to-dock-controls-on-windows-forms.md)sur Windows Forms.

 Cette procédure est axée sur l’organisation <xref:System.Windows.Forms.SplitContainer> de et sur les autres contrôles du formulaire, et non sur l’ajout de fonctionnalités pour que l’application imite Microsoft Outlook.

 Pour créer cette interface utilisateur, vous placez tous les contrôles dans un <xref:System.Windows.Forms.SplitContainer> contrôle, qui contient un <xref:System.Windows.Forms.TreeView> contrôle dans le panneau gauche. Le panneau de droite <xref:System.Windows.Forms.SplitContainer> du contrôle contient un deuxième <xref:System.Windows.Forms.SplitContainer> contrôle avec un <xref:System.Windows.Forms.ListView> contrôle au-dessus d' <xref:System.Windows.Forms.RichTextBox> un contrôle. Ces <xref:System.Windows.Forms.SplitContainer> contrôles permettent un redimensionnement indépendant des autres contrôles du formulaire. Vous pouvez adapter les techniques de cette procédure pour créer vos propres interfaces utilisateur personnalisées.

## <a name="to-create-an-outlook-style-user-interface-at-design-time"></a>Pour créer une interface utilisateur de style Outlook au moment du design

1. Créer un nouveau projet d’application Windows (**fichier** > **nouveau** > **projet** >  **C# visuel** ou **Visual Basic** > **Bureau classique**  >  **Windows Forms application**).

2. Faites glisser <xref:System.Windows.Forms.SplitContainer> un contrôle de la **boîte à outils** vers le formulaire. Dans la fenêtre **Propriétés** , définissez la propriété <xref:System.Windows.Forms.SplitContainer.Dock%2A> sur <xref:System.Windows.Forms.DockStyle.Fill>.

3. Faites glisser <xref:System.Windows.Forms.TreeView> un contrôle de la **boîte à outils** vers le panneau de gauche <xref:System.Windows.Forms.SplitContainer> du contrôle. Dans la fenêtre **Propriétés** , affectez <xref:System.Windows.Forms.SplitContainer.Dock%2A> à la <xref:System.Windows.Forms.DockStyle.Left> propriété la valeur en cliquant sur le panneau de gauche dans l’éditeur de valeurs qui s’affiche quand l’utilisateur clique sur la flèche bas.

4. Faites glisser <xref:System.Windows.Forms.SplitContainer> un autre contrôle de la **boîte à outils**, placez-le dans le panneau <xref:System.Windows.Forms.SplitContainer> de droite du contrôle que vous avez ajouté à votre formulaire. Dans la fenêtre **Propriétés** , affectez <xref:System.Windows.Forms.SplitContainer.Dock%2A> à <xref:System.Windows.Forms.DockStyle.Fill> la propriété la <xref:System.Windows.Forms.SplitContainer.Orientation%2A> valeur et <xref:System.Windows.Forms.Orientation.Horizontal>à la propriété la valeur.

5. Faites glisser <xref:System.Windows.Forms.ListView> un contrôle de la **boîte à outils** vers le volet supérieur <xref:System.Windows.Forms.SplitContainer> du deuxième contrôle que vous avez ajouté à votre formulaire. Affectez à la propriété <xref:System.Windows.Forms.SplitContainer.Dock%2A> du contrôle <xref:System.Windows.Forms.ListView> la valeur <xref:System.Windows.Forms.DockStyle.Fill>.

6. Faites glisser <xref:System.Windows.Forms.RichTextBox> un contrôle de la **boîte à outils** vers le panneau inférieur <xref:System.Windows.Forms.SplitContainer> du deuxième contrôle. Affectez à la propriété <xref:System.Windows.Forms.SplitContainer.Dock%2A> du contrôle <xref:System.Windows.Forms.RichTextBox> la valeur <xref:System.Windows.Forms.DockStyle.Fill>.

     À ce stade, si vous appuyez sur F5 pour exécuter l’application, le formulaire affiche une interface utilisateur en trois parties, similaire à celle de Microsoft Outlook.

    > [!NOTE]
    > Lorsque vous placez le pointeur de la souris sur l’un des séparateurs dans <xref:System.Windows.Forms.SplitContainer> les contrôles, vous pouvez redimensionner les dimensions internes.

À ce stade du développement d’applications, vous avez créé une interface utilisateur sophistiquée. L’étape suivante consiste à poursuivre la programmation de l’application elle-même, peut- <xref:System.Windows.Forms.TreeView> être en <xref:System.Windows.Forms.ListView> connectant le contrôle et les contrôles à un type de source de données. Pour plus d’informations sur la connexion des contrôles aux données, consultez [liaison de données et Windows Forms](../data-binding-and-windows-forms.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.SplitContainer>
- [SplitContainer, contrôle](splitcontainer-control-windows-forms.md)
