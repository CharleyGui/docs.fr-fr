---
title: 'Comment : implémenter ICommandSource'
ms.date: 12/05/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
ms.openlocfilehash: 755377d25a2deb48aa9da86d4182075e30763530
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345096"
---
# <a name="how-to-implement-icommandsource"></a>Comment : implémenter ICommandSource

Cet exemple montre comment créer une source de commande en implémentant <xref:System.Windows.Input.ICommandSource>. Une source de commande est un objet qui sait comment appeler une commande. L’interface <xref:System.Windows.Input.ICommandSource> expose trois membres :

- <xref:System.Windows.Input.ICommandSource.Command%2A>: commande qui sera appelée.
- <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: type de données défini par l’utilisateur qui est passé de la source de commande à la méthode qui gère la commande.
- <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: objet sur lequel la commande est exécutée.

Dans cet exemple, une classe qui hérite du contrôle <xref:System.Windows.Controls.Slider> est créée et implémente l’interface <xref:System.Windows.Input.ICommandSource>.
  
## <a name="example"></a>Exemple

WPF fournit un certain nombre de classes qui implémentent <xref:System.Windows.Input.ICommandSource>, comme <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>et <xref:System.Windows.Documents.Hyperlink>. Une source de commande définit la manière dont elle appelle une commande. Ces classes appellent une commande lorsque l’utilisateur clique dessus et elles deviennent uniquement une source de commande lorsque leur propriété <xref:System.Windows.Input.ICommandSource.Command%2A> est définie.

Dans cet exemple, vous allez appeler la commande lorsque le curseur est déplacé, ou plus précisément, lorsque la propriété <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> est modifiée.

Voici la définition de classe :

[!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]

L’étape suivante consiste à implémenter les membres de <xref:System.Windows.Input.ICommandSource>. Dans cet exemple, les propriétés sont implémentées en tant qu’objets <xref:System.Windows.DependencyProperty>. Cela permet aux propriétés d’utiliser la liaison de données. Pour plus d’informations sur la classe <xref:System.Windows.DependencyProperty>, consultez la [vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md). Pour plus d’informations sur la liaison de données, consultez [vue d’ensemble](../../../desktop-wpf/data/data-binding-overview.md)de la liaison de données.

Seule la propriété <xref:System.Windows.Input.ICommandSource.Command%2A> est présentée ici.
 
[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
Le rappel de modification de <xref:System.Windows.DependencyProperty> est le suivant :

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]

L’étape suivante consiste à ajouter et supprimer la commande associée à la source de la commande. La propriété <xref:System.Windows.Input.ICommandSource.Command%2A> ne peut pas être remplacée simplement quand une nouvelle commande est ajoutée, car les gestionnaires d’événements associés à la commande précédente, le cas échéant, doivent être supprimés en premier.

[!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]

L’étape suivante consiste à créer une logique pour le gestionnaire de <xref:System.Windows.Input.ICommand.CanExecuteChanged>.

L’événement <xref:System.Windows.Input.ICommand.CanExecuteChanged> avertit la source de la commande que la capacité de la commande à s’exécuter sur la cible de commande actuelle a peut-être changé. Quand une source de commande reçoit cet événement, elle appelle généralement la méthode <xref:System.Windows.Input.ICommand.CanExecute%2A> sur la commande. Si la commande ne peut pas s’exécuter sur la cible de commande actuelle, la source de la commande se désactivera généralement elle-même. Si la commande peut s’exécuter sur la cible de commande actuelle, la source de la commande s’active généralement elle-même.

[!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
[!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]

La dernière étape est la méthode <xref:System.Windows.Input.ICommand.Execute%2A>. Si la commande est un <xref:System.Windows.Input.RoutedCommand>, la méthode <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> est appelée ; dans le cas contraire, la méthode <xref:System.Windows.Input.ICommand.Execute%2A> <xref:System.Windows.Input.ICommand> est appelée.

[!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
[!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [Vue d’ensemble des commandes](commanding-overview.md)
