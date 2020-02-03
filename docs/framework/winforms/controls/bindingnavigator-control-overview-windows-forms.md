---
title: Vue d'ensemble du contrôle BindingNavigator
ms.date: 03/30/2017
f1_keywords:
- DataNavigator
helpviewer_keywords:
- BindingNavigator control [Windows Forms], about BindingNavigator control
- records [Windows Forms], navigating on a form
- data [Windows Forms], navigating
- data navigation
ms.assetid: 4423eede-f8d1-4d02-822f-5bf8432680d0
ms.openlocfilehash: c2747a6801d4aa9cfde4227ffd5c29ca1de78d48
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744102"
---
# <a name="bindingnavigator-control-overview-windows-forms"></a>Vue d'ensemble du contrôle BindingNavigator (Windows Forms)
Vous pouvez utiliser le contrôle <xref:System.Windows.Forms.BindingNavigator> pour créer un mécanisme normalisé permettant aux utilisateurs de rechercher et de modifier des données sur un Windows Form. Vous utilisez fréquemment <xref:System.Windows.Forms.BindingNavigator> avec le composant <xref:System.Windows.Forms.BindingSource> pour permettre aux utilisateurs de parcourir les enregistrements de données sur un formulaire et d'interagir avec eux.  
  
## <a name="how-the-bindingnavigator-works"></a>Fonctionnement de BindingNavigator  

 Le contrôle <xref:System.Windows.Forms.BindingNavigator> est composé d'un <xref:System.Windows.Forms.ToolStrip> avec une série d'objets <xref:System.Windows.Forms.ToolStripItem> pour la plupart des actions courantes liées aux données : ajout de données, suppression de données et navigation parmi les données. Par défaut, le contrôle <xref:System.Windows.Forms.BindingNavigator> contient ces boutons standard. La capture d’écran suivante montre le contrôle <xref:System.Windows.Forms.BindingNavigator> sur un formulaire :
  
 ![Capture d’écran montrant le contrôle BindingNavigator.](./media/bindingnavigator-control-overview-windows-forms/bindingnavigator-control-form.gif)  
  
 Le tableau suivant répertorie les contrôles et décrit leurs fonctions.  
  
|Contrôle|Fonction|  
|-------------|--------------|  
|Bouton <xref:System.Windows.Forms.BindingNavigator.AddNewItem%2A>|Insère une nouvelle ligne dans la source de données sous-jacente.|  
|Bouton <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A>|Supprime la ligne actuelle de la source de données sous-jacente.|  
|Bouton <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A>|Accède au premier élément dans la source de données sous-jacente.|  
|Bouton <xref:System.Windows.Forms.BindingNavigator.MoveLastItem%2A>|Accède au dernier élément dans la source de données sous-jacente.|  
|Bouton <xref:System.Windows.Forms.BindingNavigator.MoveNextItem%2A>|Accède à l'élément suivant dans la source de données sous-jacente.|  
|Bouton <xref:System.Windows.Forms.BindingNavigator.MovePreviousItem%2A>|Accède à l'élément précédent dans la source de données sous-jacente.|  
|Zone de texte <xref:System.Windows.Forms.BindingNavigator.PositionItem%2A>|Retourne la position actuelle dans la source de données sous-jacente.|  
|Zone de texte <xref:System.Windows.Forms.BindingNavigator.CountItem%2A>|Retourne le nombre total d'éléments dans la source de données sous-jacente.|  
  
 À chaque contrôle de cette collection correspond un membre du composant <xref:System.Windows.Forms.BindingSource> qui fournit la même fonctionnalité par programmation. Par exemple, le bouton <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> correspond à la méthode <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> du composant <xref:System.Windows.Forms.BindingSource>, le bouton <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> correspond à la méthode <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A>, et ainsi de suite.  
  
 Si les boutons par défaut ne conviennent pas à votre application ou si vous avez besoin de boutons supplémentaires pour prendre en charge d'autres types de fonctionnalités, vous pouvez fournir vos propres boutons <xref:System.Windows.Forms.ToolStrip>. Consultez également [Comment : ajouter des boutons Charger, Enregistrer et Annuler au contrôle BindingNavigator Windows Forms](load-save-and-cancel-bindingnavigator.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- [BindingNavigator, contrôle](bindingnavigator-control-windows-forms.md)
