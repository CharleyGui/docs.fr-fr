---
title: 'Procédure : créer une interface de style Explorateur Windows dans un formulaire Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: 34a5cd735c350688d9e83003806668e213932c85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960624"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a>Procédure : créer une interface de style Explorateur Windows dans un formulaire Windows
L’Explorateur Windows est un choix d’interface utilisateur courant pour les applications en raison de sa familiarité.

 L’Explorateur Windows est, essentiellement, <xref:System.Windows.Forms.TreeView> un contrôle et <xref:System.Windows.Forms.ListView> un contrôle sur des panneaux distincts. Les panneaux sont rendus redimensionnables par un séparateur. Cette organisation des contrôles est très efficace pour l’affichage et la navigation dans les informations.

 Les étapes suivantes montrent comment organiser les contrôles dans un formulaire de type Explorateur Windows. Ils n’indiquent pas comment ajouter la fonctionnalité de navigation de fichiers de l’application de l’Explorateur Windows.

## <a name="to-create-a-windows-explorer-style-windows-form"></a>Pour créer un Windows Form de style Explorateur Windows

1. Créer un nouveau projet d’application Windows (**fichier** > **nouveau** > **projet** >  **C# visuel** ou **Visual Basic** > **Bureau classique**  >  **Windows Forms application**).

2. À partir de la **boîte à outils**:

    1. Faites glisser <xref:System.Windows.Forms.SplitContainer> un contrôle sur votre formulaire.

    2. Faites glisser <xref:System.Windows.Forms.TreeView> un contrôle dans **splitterPanel1** ( <xref:System.Windows.Forms.SplitContainer> le panneau du contrôle marqué **Panel1**).

    3. Faites glisser <xref:System.Windows.Forms.ListView> un contrôle dans **SplitterPanel2** ( <xref:System.Windows.Forms.SplitContainer> le panneau du contrôle marqué **Panel2**).

3. Sélectionnez les trois contrôles en appuyant sur la touche CTRL et en cliquant successivement sur eux. Lorsque vous sélectionnez le <xref:System.Windows.Forms.SplitContainer> contrôle, cliquez sur la barre de fractionnement, plutôt que sur les panneaux.

    > [!NOTE]
    > N’utilisez pas la commande **Sélectionner tout** du menu **Edition** . Dans ce cas, la propriété nécessaire à l’étape suivante n’apparaîtra pas dans la fenêtre **Propriétés** .

4. Dans la fenêtre **Propriétés** , définissez la propriété <xref:System.Windows.Forms.SplitContainer.Dock%2A> sur <xref:System.Windows.Forms.DockStyle.Fill>.

5. Appuyez sur F5 pour exécuter l'application.

     Le formulaire affiche une interface utilisateur en deux parties, similaire à celle de l’Explorateur Windows.

    > [!NOTE]
    > Lorsque vous faites glisser le séparateur, les panneaux sont redimensionnés eux-mêmes.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.SplitContainer>
- [Guide pratique : Créer une interface utilisateur à volets avec Windows Forms](how-to-create-a-multipane-user-interface-with-windows-forms.md)
- [Guide pratique pour Définir le comportement de redimensionnement et de positionnement dans une fenêtre fractionnée](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)
- [Guide pratique pour Fractionner une fenêtre horizontalement](how-to-split-a-window-horizontally.md)
- [SplitContainer, contrôle](splitcontainer-control-windows-forms.md)
