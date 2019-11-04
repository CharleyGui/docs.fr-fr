---
title: 'Comment : implémenter ICommandSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
ms.openlocfilehash: 974b145a125a158bcafff93f8e9bc11001e00bf1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453587"
---
# <a name="how-to-implement-icommandsource"></a>Comment : implémenter ICommandSource
Cet exemple montre comment créer une source de commande en implémentant <xref:System.Windows.Input.ICommandSource>.  Une source de commande est un objet qui sait comment appeler une commande.  L’interface <xref:System.Windows.Input.ICommandSource> expose trois membres : <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>et <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>.  <xref:System.Windows.Input.ICommandSource.Command%2A> est la commande qui sera appelée. Le <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> est un type de données défini par l’utilisateur qui est passé de la source de commande à la méthode qui gère la commande. Le <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> est l’objet sur lequel la commande est exécutée.  
  
 Dans cet exemple, une classe est créée, qui sous-classe le contrôle <xref:System.Windows.Controls.Slider> et implémente <xref:System.Windows.Input.ICommandSource>.  
  
## <a name="example"></a>Exemple  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit un certain nombre de classes qui implémentent <xref:System.Windows.Input.ICommandSource>, telles que <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>et <xref:System.Windows.Controls.ListBoxItem>.  Une source de commande définit la manière dont elle appelle une commande.   <xref:System.Windows.Controls.Button> et <xref:System.Windows.Controls.MenuItem> appeler une commande lorsque l’utilisateur clique dessus.  <xref:System.Windows.Controls.ListBoxItem> appelle une commande lorsque l’utilisateur double-clique dessus. Ces classes deviennent uniquement une source de commande lorsque leur propriété <xref:System.Windows.Input.ICommandSource.Command%2A> est définie.  
  
 Pour cet exemple, nous allons appeler la commande lorsque le curseur est déplacé, ou plus précisément, lorsque la propriété <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> est modifiée.  
  
 Voici la définition de classe.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]  
  
 L’étape suivante consiste à implémenter les membres de <xref:System.Windows.Input.ICommandSource>.  Dans cet exemple, les propriétés sont implémentées en tant qu’objets <xref:System.Windows.DependencyProperty>.  Cela permet aux propriétés d’utiliser la liaison de données.  Pour plus d’informations sur la classe <xref:System.Windows.DependencyProperty>, consultez la [vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md).  Pour plus d’informations sur la liaison de données, consultez [vue d’ensemble](../../../desktop-wpf/data/data-binding-overview.md)de la liaison de données.  
  
 Seule la propriété <xref:System.Windows.Input.ICommandSource.Command%2A> est présentée ici.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
 Voici le rappel de modification de <xref:System.Windows.DependencyProperty>.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]  
  
 L’étape suivante consiste à ajouter et supprimer la commande associée à la source de la commande.  La propriété <xref:System.Windows.Input.ICommandSource.Command%2A> ne peut pas être remplacée simplement quand une nouvelle commande est ajoutée, car les gestionnaires d’événements associés à la commande précédente, le cas échéant, doivent être supprimés en premier.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]  
  
 La dernière étape consiste à créer une logique pour le gestionnaire de <xref:System.Windows.Input.ICommand.CanExecuteChanged> et la méthode <xref:System.Windows.Input.ICommand.Execute%2A>.  
  
 L’événement <xref:System.Windows.Input.ICommand.CanExecuteChanged> avertit la source de la commande que la capacité de la commande à s’exécuter sur la cible de commande actuelle a peut-être changé.  Quand une source de commande reçoit cet événement, elle appelle généralement la méthode <xref:System.Windows.Input.ICommand.CanExecute%2A> sur la commande.  Si la commande ne peut pas s’exécuter sur la cible de commande actuelle, la source de la commande se désactivera généralement elle-même.  Si la commande peut s’exécuter sur la cible de commande actuelle, la source de la commande s’active généralement elle-même.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]  
  
 La dernière étape est la méthode <xref:System.Windows.Input.ICommand.Execute%2A>.  Si la commande est un <xref:System.Windows.Input.RoutedCommand>, la méthode <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> est appelée ; dans le cas contraire, la méthode <xref:System.Windows.Input.ICommand.Execute%2A> <xref:System.Windows.Input.ICommand> est appelée.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
 [!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [Vue d’ensemble des commandes](commanding-overview.md)
