---
title: 'Comment : implémenter ICommandSource'
ms.date: 12/05/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
ms.openlocfilehash: 6c18e0b77ec53d9bd3e7ce610f2940effe603c88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174691"
---
# <a name="how-to-implement-icommandsource"></a>Comment : implémenter ICommandSource

Cet exemple montre comment créer une <xref:System.Windows.Input.ICommandSource>source de commande en mettant en œuvre . Une source de commande est un objet qui sait invoquer une commande. L’interface <xref:System.Windows.Input.ICommandSource> expose trois membres :

- <xref:System.Windows.Input.ICommandSource.Command%2A>: la commande qui sera invoquée.
- <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: un type de données défini par l’utilisateur qui passe de la source de commande à la méthode qui gère la commande.
- <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: l’objet sur lequel la commande est exécutée.

Dans cet exemple, une classe est <xref:System.Windows.Controls.Slider> créée qui hérite du contrôle et implémente l’interface. <xref:System.Windows.Input.ICommandSource>
  
## <a name="example"></a> Exemple

WPF fournit un certain <xref:System.Windows.Input.ICommandSource>nombre de <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.MenuItem>classes <xref:System.Windows.Documents.Hyperlink>qui mettent en œuvre , tels que , , et . Une source de commande définit comment elle invoque une commande. Ces classes invoquent une commande lorsqu’elles sont cliqués et elles ne deviennent une source de commande que lorsque leur <xref:System.Windows.Input.ICommandSource.Command%2A> propriété est définie.

Dans cet exemple, vous invoquez la commande lorsque le curseur est déplacé, ou plus exactement, lorsque la <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> propriété est modifiée.

Voici la définition de la classe :

[!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]

La prochaine étape consiste <xref:System.Windows.Input.ICommandSource> à mettre en œuvre les membres. Dans cet exemple, les <xref:System.Windows.DependencyProperty> propriétés sont implémentées comme objets. Cela permet aux propriétés d’utiliser la liaison de données. Pour plus d’informations sur la <xref:System.Windows.DependencyProperty> classe, voir le Aperçu des [propriétés de dépendance](dependency-properties-overview.md). Pour plus d’informations sur la liaison des données, voir [l’aperçu de la liaison des données](../../../desktop-wpf/data/data-binding-overview.md).

Seule <xref:System.Windows.Input.ICommandSource.Command%2A> la propriété est montrée ici.

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
Voici le <xref:System.Windows.DependencyProperty> rappel de changement :

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]

L’étape suivante consiste à ajouter et supprimer la commande qui est associée à la source de commande. La <xref:System.Windows.Input.ICommandSource.Command%2A> propriété ne peut pas simplement être écrasée lorsqu’une nouvelle commande est ajoutée, parce que les gestionnaires d’événements associés à la commande précédente, s’il y en avait une, doivent d’abord être supprimés.

[!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]

L’étape suivante consiste à <xref:System.Windows.Input.ICommand.CanExecuteChanged> créer une logique pour le gestionnaire.

L’événement <xref:System.Windows.Input.ICommand.CanExecuteChanged> informe la source de commandement que la capacité de la commande d’exécuter sur la cible de commande actuelle peut avoir changé. Lorsqu’une source de commande reçoit <xref:System.Windows.Input.ICommand.CanExecute%2A> cet événement, elle appelle généralement la méthode sur la commande. Si la commande ne peut pas exécuter sur la cible de commande actuelle, la source de commande se désactive généralement. Si la commande peut s’exécuter sur la cible de commande actuelle, la source de commande s’active généralement.

[!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
[!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]

La dernière étape <xref:System.Windows.Input.ICommand.Execute%2A> est la méthode. Si la commande <xref:System.Windows.Input.RoutedCommand>est <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> un , la méthode est appelée; sinon, <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> la méthode est appelée.

[!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
[!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [Vue d’ensemble des commandes](commanding-overview.md)
