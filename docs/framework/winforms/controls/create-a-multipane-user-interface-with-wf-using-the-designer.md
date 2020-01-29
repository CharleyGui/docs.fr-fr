---
title: Créer une interface utilisateur à volets à l’aide du concepteur
ms.date: 03/30/2017
helpviewer_keywords:
- user interface [Windows Forms], multipane
- SplitContainer control [Windows Forms], using the designer
- multipane user interface
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
ms.openlocfilehash: 6b41d538f1cd1633cec51c89e27adf3c5b47f9a6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737275"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms-using-the-designer"></a>Comment : créer une interface utilisateur à plusieurs volets avec des Windows Forms à l'aide du concepteur
Dans la procédure suivante, vous allez créer une interface utilisateur à plusieurs volets similaire à celle utilisée dans Microsoft Outlook, avec une liste de **dossiers** , un volet **messages** et un volet de **visualisation** . Cette organisation est réalisée principalement via l’ancrage des contrôles au formulaire.

 Lorsque vous ancrez un contrôle, vous déterminez le bord du conteneur parent auquel un contrôle est attaché. Ainsi, si vous affectez à la propriété <xref:System.Windows.Forms.SplitContainer.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle.Right>, le bord droit du contrôle est ancré au bord droit de son contrôle parent. En outre, le bord ancré du contrôle est redimensionné pour correspondre à celui de son contrôle conteneur. Pour plus d’informations sur le fonctionnement de la propriété <xref:System.Windows.Forms.SplitContainer.Dock%2A>, consultez [Comment : ancrer des contrôles sur des Windows Forms](how-to-dock-controls-on-windows-forms.md).

 Cette procédure est axée sur l’organisation de la <xref:System.Windows.Forms.SplitContainer> et des autres contrôles du formulaire, et non sur l’ajout de fonctionnalités pour que l’application imite Microsoft Outlook.

 Pour créer cette interface utilisateur, vous placez tous les contrôles dans un contrôle <xref:System.Windows.Forms.SplitContainer>, qui contient un contrôle <xref:System.Windows.Forms.TreeView> dans le panneau gauche. Le panneau de droite du contrôle <xref:System.Windows.Forms.SplitContainer> contient un deuxième contrôle <xref:System.Windows.Forms.SplitContainer> avec un contrôle <xref:System.Windows.Forms.ListView> au-dessus d’un contrôle <xref:System.Windows.Forms.RichTextBox>. Ces contrôles <xref:System.Windows.Forms.SplitContainer> permettent un redimensionnement indépendant des autres contrôles du formulaire. Vous pouvez adapter les techniques de cette procédure pour créer vos propres interfaces utilisateur personnalisées.

## <a name="to-create-an-outlook-style-user-interface-at-design-time"></a>Pour créer une interface utilisateur de style Outlook au moment du design

1. Créez un projet d’application Windows (**fichier** > **nouveau** **projet** >  > **Visual C#**  ou **Visual Basic** > **application** > de **Bureau classique** .

2. Faites glisser un contrôle <xref:System.Windows.Forms.SplitContainer> de la **boîte à outils** vers le formulaire. Dans la fenêtre **Propriétés** , définissez la propriété <xref:System.Windows.Forms.SplitContainer.Dock%2A> sur <xref:System.Windows.Forms.DockStyle.Fill>.

3. Faites glisser un contrôle <xref:System.Windows.Forms.TreeView> de la **boîte à outils** vers le panneau gauche du contrôle <xref:System.Windows.Forms.SplitContainer>. Dans la fenêtre **Propriétés** , affectez à la propriété <xref:System.Windows.Forms.SplitContainer.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle.Left> en cliquant sur le panneau de gauche dans l’éditeur de valeurs qui s’affiche lorsque vous cliquez sur la flèche bas.

4. Faites glisser un autre contrôle <xref:System.Windows.Forms.SplitContainer> à partir de la **boîte à outils**; Placez-le dans le panneau de droite du contrôle de <xref:System.Windows.Forms.SplitContainer> que vous avez ajouté à votre formulaire. Dans la fenêtre **Propriétés** , affectez à la propriété <xref:System.Windows.Forms.SplitContainer.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle.Fill> et à la propriété <xref:System.Windows.Forms.SplitContainer.Orientation%2A> la valeur <xref:System.Windows.Forms.Orientation.Horizontal>.

5. Faites glisser un contrôle <xref:System.Windows.Forms.ListView> de la **boîte à outils** vers le volet supérieur du deuxième contrôle <xref:System.Windows.Forms.SplitContainer> que vous avez ajouté à votre formulaire. Affectez à la propriété <xref:System.Windows.Forms.SplitContainer.Dock%2A> du contrôle <xref:System.Windows.Forms.ListView> la valeur <xref:System.Windows.Forms.DockStyle.Fill>.

6. Faites glisser un contrôle <xref:System.Windows.Forms.RichTextBox> de la **boîte à outils** vers le panneau inférieur du deuxième contrôle <xref:System.Windows.Forms.SplitContainer>. Affectez à la propriété <xref:System.Windows.Forms.SplitContainer.Dock%2A> du contrôle <xref:System.Windows.Forms.RichTextBox> la valeur <xref:System.Windows.Forms.DockStyle.Fill>.

     À ce stade, si vous appuyez sur F5 pour exécuter l’application, le formulaire affiche une interface utilisateur en trois parties, similaire à celle de Microsoft Outlook.

    > [!NOTE]
    > Lorsque vous placez le pointeur de la souris sur l’un des séparateurs dans les contrôles <xref:System.Windows.Forms.SplitContainer>, vous pouvez redimensionner les dimensions internes.

À ce stade du développement d’applications, vous avez créé une interface utilisateur sophistiquée. L’étape suivante consiste à poursuivre la programmation de l’application elle-même, par exemple en connectant le contrôle <xref:System.Windows.Forms.TreeView> et <xref:System.Windows.Forms.ListView> contrôles à un type de source de données. Pour plus d’informations sur la connexion des contrôles aux données, consultez [liaison de données et Windows Forms](../data-binding-and-windows-forms.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.SplitContainer>
- [SplitContainer, contrôle](splitcontainer-control-windows-forms.md)
