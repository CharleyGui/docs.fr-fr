---
title: ToolBar, contrôle
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolBar control [Windows Forms]
ms.assetid: 6b40e9ce-6a7a-4784-bfc9-7f1d36b7462e
ms.openlocfilehash: 027c96bb49e9446244e4b08ba93c551ef043b3c0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735455"
---
# <a name="toolbar-control-windows-forms"></a>ToolBar, contrôle (Windows Forms)
> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.ToolStrip> remplace le contrôle `ToolBar` et lui ajoute des fonctionnalités ; toutefois, le contrôle `ToolBar` est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  
  
 Le contrôle Windows Forms `ToolBar` est utilisé sur les formulaires comme barre de contrôle affichant une rangée de menus déroulants et de boutons bitmap qui activent des commandes. Ainsi, un clic sur un bouton de barre d'outils revient à choisir une commande de menu. Vous pouvez configurer les boutons pour qu'ils apparaissent et se comportent comme des boutons de commande, des menus déroulants ou des séparateurs. En règle générale, une barre d'outils contient des boutons et des menus qui correspondent à des éléments dans la structure de menu de l'application et fournissent un accès rapide aux commandes et aux fonctions les plus fréquemment utilisées d'une application.  
  
> [!NOTE]
> La propriété `ToolBar` du contrôle <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> prend une instance de la classe <xref:System.Windows.Forms.ContextMenu> comme référence. Vous devez faire attention à la référence que vous passez lors de l'implémentation de ce genre de bouton sur les barres d'outils de votre application, car la propriété accepte tout objet qui hérite de la classe <xref:System.Windows.Forms.Menu>.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble du contrôle ToolBar](toolbar-control-overview-windows-forms.md)  
 Présente les concepts généraux du contrôle `ToolBar`, qui vous permet de concevoir des barres d'outils personnalisées avec lesquelles les utilisateurs peuvent travailler.  
  
 [Guide pratique pour ajouter des boutons à un contrôle ToolBar](how-to-add-buttons-to-a-toolbar-control.md)  
 Décrit comment ajouter des boutons à un contrôle `ToolBar`.  
  
 [Guide pratique pour définir une icône pour un bouton de barre d’outils](how-to-define-an-icon-for-a-toolbar-button.md)  
 Décrit comment afficher des icônes dans les boutons d'un contrôle `ToolBar`.  
  
 [Guide pratique pour déclencher des événements de menu pour les boutons de barre d’outils](how-to-trigger-menu-events-for-toolbar-buttons.md)  
 Explique comment écrire du code pour interpréter le bouton sur lequel l'utilisateur clique dans un contrôle `ToolBar`.  
  
 Consultez également [Comment : définir une icône pour un bouton de barre d’outils à l’aide du concepteur](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md), [Comment : ajouter des boutons à un contrôle ToolBar à l’aide du concepteur](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md).  
  
## <a name="reference"></a>Référence  
 Classe <xref:System.Windows.Forms.ToolBar>  
 Fournit des informations de référence sur la classe et ses membres.  
  
## <a name="related-sections"></a>Sections connexes  
 [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)  
 Fournit une liste complète de contrôles Windows Forms, avec des liens vers des informations sur leur utilisation.  
  
 [Contrôle ToolStrip](toolstrip-control-windows-forms.md)  
 Décrit les barres d’outils qui peuvent héberger des menus, des contrôles et des contrôles utilisateur dans les applications Windows Forms.
