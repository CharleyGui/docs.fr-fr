---
title: Vue d'ensemble du contrôle ToolBar
ms.date: 03/30/2017
f1_keywords:
- ToolBar
helpviewer_keywords:
- toolbars [Windows Forms], about toolbars
- ToolBar control [Windows Forms], about ToolBar controls
ms.assetid: d426b203-0216-4dbe-b834-1641e50a9c29
ms.openlocfilehash: f364e052258703331496f8103b48953a90aa3a9b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735480"
---
# <a name="toolbar-control-overview-windows-forms"></a>Vue d'ensemble du contrôle ToolBar (Windows Forms)
> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.ToolStrip> remplace le contrôle <xref:System.Windows.Forms.ToolBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.ToolBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  
  
 Le contrôle Windows Forms <xref:System.Windows.Forms.ToolBar> est utilisé sur les formulaires comme barre de contrôle affichant une rangée de menus déroulants et de boutons bitmap qui activent des commandes. Ainsi, un clic sur un bouton de barre d’outils peut être équivalent à choisir une commande de menu. Vous pouvez configurer les boutons pour qu’ils apparaissent et se comportent comme des boutons de commande, des menus déroulants ou des séparateurs. En règle générale, une barre d'outils contient des boutons et des menus qui correspondent à des éléments dans la structure de menu de l'application et fournissent un accès rapide aux commandes et aux fonctions les plus fréquemment utilisées d'une application.  
  
## <a name="working-with-the-toolbar-control"></a>Utilisation du contrôle ToolBar  
 Un contrôle de <xref:System.Windows.Forms.ToolBar> est généralement « ancré » en haut de sa fenêtre parente, mais il peut également être ancré à n’importe quel côté de la fenêtre. Une barre d’outils peut afficher des info-bulles quand l’utilisateur pointe avec la souris sur un bouton de barre d’outils. Une info-bulle est une petite fenêtre contextuelle qui décrit brièvement l’objectif du bouton ou du menu. Pour afficher les info-bulles, la propriété <xref:System.Windows.Forms.ToolBar.ShowToolTips%2A> doit être définie sur `true`.  
  
> [!NOTE]
> Certaines applications comportent des contrôles très similaires à la barre d’outils, qui ont la possibilité de « flotter » au-dessus de la fenêtre de l’application et d’être repositionnés. Le contrôle Windows Forms ToolBar n’est pas en mesure d’effectuer ces actions.  
  
 Lorsque la propriété <xref:System.Windows.Forms.ToolBar.Appearance%2A> est définie sur <xref:System.Windows.Forms.ToolBarAppearance>, les boutons de la barre d’outils apparaissent en relief et en trois dimensions. Vous pouvez définir la propriété <xref:System.Windows.Forms.ToolBar.Appearance%2A> de la barre d’outils sur <xref:System.Windows.Forms.ToolBarAppearance> pour attribuer à la barre d’outils et à ses boutons une apparence plate. Quand le pointeur de la souris est placé sur un bouton à deux dimensions, l’apparence du bouton passe à trois dimensions. Les boutons de barre d’outils peut être divisés en groupes logiques à l’aide de séparateurs. Un séparateur est un bouton de barre d’outils avec la propriété <xref:System.Windows.Forms.ToolBarButton.Style%2A> définie sur <xref:System.Windows.Forms.ToolBarButtonStyle>. Il apparaît comme un espace vide dans la barre d’outils. Quand la barre d’outils a une apparence à deux dimensions, les séparateurs de boutons apparaissent comme des lignes (et non pas des espaces) entre les boutons.  
  
 Le contrôle <xref:System.Windows.Forms.ToolBar> vous permet de créer des barres d’outils en ajoutant des objets <xref:System.Windows.Forms.Button> à une collection <xref:System.Windows.Forms.ToolBar.Buttons%2A>. Vous pouvez utiliser l’éditeur de collections pour ajouter des boutons à un contrôle <xref:System.Windows.Forms.ToolBar> ; chaque objet <xref:System.Windows.Forms.Button> doit avoir du texte ou une image affectée, même si vous pouvez assigner les deux. L’image est fournie par un composant [ImageList](imagelist-component-windows-forms.md) associé. Au moment de l’exécution, vous pouvez ajouter ou supprimer des boutons de la <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection> à l’aide des méthodes <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Add%2A> et <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Remove%2A>. Pour programmer les boutons d’une <xref:System.Windows.Forms.ToolBar>, ajoutez du code aux événements <xref:System.Windows.Forms.ToolBar.ButtonClick> de l' <xref:System.Windows.Forms.ToolBar>, à l’aide de la propriété <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> de la classe <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> pour déterminer le bouton sur lequel l’utilisateur a cliqué.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ToolBar>
- [ToolBar, contrôle](toolbar-control-windows-forms.md)
- [Guide pratique pour ajouter des boutons à un contrôle ToolBar](how-to-add-buttons-to-a-toolbar-control.md)
- [Guide pratique pour définir une icône pour un bouton de barre d’outils](how-to-define-an-icon-for-a-toolbar-button.md)
- [Guide pratique pour déclencher des événements de menu pour les boutons de barre d’outils](how-to-trigger-menu-events-for-toolbar-buttons.md)
