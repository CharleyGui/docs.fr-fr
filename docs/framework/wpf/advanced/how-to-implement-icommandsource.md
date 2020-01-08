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
# <a name="how-to-implement-icommandsource"></a><span data-ttu-id="42f88-102">Comment : implémenter ICommandSource</span><span class="sxs-lookup"><span data-stu-id="42f88-102">How to: Implement ICommandSource</span></span>

<span data-ttu-id="42f88-103">Cet exemple montre comment créer une source de commande en implémentant <xref:System.Windows.Input.ICommandSource>.</span><span class="sxs-lookup"><span data-stu-id="42f88-103">This example shows how to create a command source by implementing <xref:System.Windows.Input.ICommandSource>.</span></span> <span data-ttu-id="42f88-104">Une source de commande est un objet qui sait comment appeler une commande.</span><span class="sxs-lookup"><span data-stu-id="42f88-104">A command source is an object that knows how to invoke a command.</span></span> <span data-ttu-id="42f88-105">L’interface <xref:System.Windows.Input.ICommandSource> expose trois membres :</span><span class="sxs-lookup"><span data-stu-id="42f88-105">The <xref:System.Windows.Input.ICommandSource> interface exposes three members:</span></span>

- <span data-ttu-id="42f88-106"><xref:System.Windows.Input.ICommandSource.Command%2A>: commande qui sera appelée.</span><span class="sxs-lookup"><span data-stu-id="42f88-106"><xref:System.Windows.Input.ICommandSource.Command%2A>: the command that will be invoked.</span></span>
- <span data-ttu-id="42f88-107"><xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: type de données défini par l’utilisateur qui est passé de la source de commande à la méthode qui gère la commande.</span><span class="sxs-lookup"><span data-stu-id="42f88-107"><xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: a user-defined data type which is passed from the command source to the method that handles the command.</span></span>
- <span data-ttu-id="42f88-108"><xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: objet sur lequel la commande est exécutée.</span><span class="sxs-lookup"><span data-stu-id="42f88-108"><xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: the object that the command is being executed on.</span></span>

<span data-ttu-id="42f88-109">Dans cet exemple, une classe qui hérite du contrôle <xref:System.Windows.Controls.Slider> est créée et implémente l’interface <xref:System.Windows.Input.ICommandSource>.</span><span class="sxs-lookup"><span data-stu-id="42f88-109">In this example, a class is created that inherits from the <xref:System.Windows.Controls.Slider> control and implements the  <xref:System.Windows.Input.ICommandSource> interface.</span></span>
  
## <a name="example"></a><span data-ttu-id="42f88-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="42f88-110">Example</span></span>

<span data-ttu-id="42f88-111">WPF fournit un certain nombre de classes qui implémentent <xref:System.Windows.Input.ICommandSource>, comme <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>et <xref:System.Windows.Documents.Hyperlink>.</span><span class="sxs-lookup"><span data-stu-id="42f88-111">WPF provides a number of classes which implement <xref:System.Windows.Input.ICommandSource>, such as <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>, and <xref:System.Windows.Documents.Hyperlink>.</span></span> <span data-ttu-id="42f88-112">Une source de commande définit la manière dont elle appelle une commande.</span><span class="sxs-lookup"><span data-stu-id="42f88-112">A command source defines how it invokes a command.</span></span> <span data-ttu-id="42f88-113">Ces classes appellent une commande lorsque l’utilisateur clique dessus et elles deviennent uniquement une source de commande lorsque leur propriété <xref:System.Windows.Input.ICommandSource.Command%2A> est définie.</span><span class="sxs-lookup"><span data-stu-id="42f88-113">These classes invoke a command when they're clicked and they only become a command source when their <xref:System.Windows.Input.ICommandSource.Command%2A> property is set.</span></span>

<span data-ttu-id="42f88-114">Dans cet exemple, vous allez appeler la commande lorsque le curseur est déplacé, ou plus précisément, lorsque la propriété <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> est modifiée.</span><span class="sxs-lookup"><span data-stu-id="42f88-114">In this example, you'll invoke the command when the slider is moved, or more accurately, when the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property is changed.</span></span>

<span data-ttu-id="42f88-115">Voici la définition de classe :</span><span class="sxs-lookup"><span data-stu-id="42f88-115">The following is the class definition:</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]

<span data-ttu-id="42f88-116">L’étape suivante consiste à implémenter les membres de <xref:System.Windows.Input.ICommandSource>.</span><span class="sxs-lookup"><span data-stu-id="42f88-116">The next step is to implement the <xref:System.Windows.Input.ICommandSource> members.</span></span> <span data-ttu-id="42f88-117">Dans cet exemple, les propriétés sont implémentées en tant qu’objets <xref:System.Windows.DependencyProperty>.</span><span class="sxs-lookup"><span data-stu-id="42f88-117">In this example, the properties are implemented as <xref:System.Windows.DependencyProperty> objects.</span></span> <span data-ttu-id="42f88-118">Cela permet aux propriétés d’utiliser la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="42f88-118">This enables the properties to use data binding.</span></span> <span data-ttu-id="42f88-119">Pour plus d’informations sur la classe <xref:System.Windows.DependencyProperty>, consultez la [vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="42f88-119">For more information about the <xref:System.Windows.DependencyProperty> class, see the [Dependency Properties Overview](dependency-properties-overview.md).</span></span> <span data-ttu-id="42f88-120">Pour plus d’informations sur la liaison de données, consultez [vue d’ensemble](../../../desktop-wpf/data/data-binding-overview.md)de la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="42f88-120">For more information about data binding, see the [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<span data-ttu-id="42f88-121">Seule la propriété <xref:System.Windows.Input.ICommandSource.Command%2A> est présentée ici.</span><span class="sxs-lookup"><span data-stu-id="42f88-121">Only the <xref:System.Windows.Input.ICommandSource.Command%2A> property is shown here.</span></span>
 
[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
<span data-ttu-id="42f88-122">Le rappel de modification de <xref:System.Windows.DependencyProperty> est le suivant :</span><span class="sxs-lookup"><span data-stu-id="42f88-122">The following is the <xref:System.Windows.DependencyProperty> change callback:</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]

<span data-ttu-id="42f88-123">L’étape suivante consiste à ajouter et supprimer la commande associée à la source de la commande.</span><span class="sxs-lookup"><span data-stu-id="42f88-123">The next step is to add and remove the command which is associated with the command source.</span></span> <span data-ttu-id="42f88-124">La propriété <xref:System.Windows.Input.ICommandSource.Command%2A> ne peut pas être remplacée simplement quand une nouvelle commande est ajoutée, car les gestionnaires d’événements associés à la commande précédente, le cas échéant, doivent être supprimés en premier.</span><span class="sxs-lookup"><span data-stu-id="42f88-124">The <xref:System.Windows.Input.ICommandSource.Command%2A> property cannot simply be overwritten when a new command is added, because the event handlers associated with the previous command, if there was one, must be removed first.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]

<span data-ttu-id="42f88-125">L’étape suivante consiste à créer une logique pour le gestionnaire de <xref:System.Windows.Input.ICommand.CanExecuteChanged>.</span><span class="sxs-lookup"><span data-stu-id="42f88-125">The next step is to create logic for the <xref:System.Windows.Input.ICommand.CanExecuteChanged> handler.</span></span>

<span data-ttu-id="42f88-126">L’événement <xref:System.Windows.Input.ICommand.CanExecuteChanged> avertit la source de la commande que la capacité de la commande à s’exécuter sur la cible de commande actuelle a peut-être changé.</span><span class="sxs-lookup"><span data-stu-id="42f88-126">The <xref:System.Windows.Input.ICommand.CanExecuteChanged> event notifies the command source that the ability of the command to execute on the current command target may have changed.</span></span> <span data-ttu-id="42f88-127">Quand une source de commande reçoit cet événement, elle appelle généralement la méthode <xref:System.Windows.Input.ICommand.CanExecute%2A> sur la commande.</span><span class="sxs-lookup"><span data-stu-id="42f88-127">When a command source receives this event, it typically calls the <xref:System.Windows.Input.ICommand.CanExecute%2A> method on the command.</span></span> <span data-ttu-id="42f88-128">Si la commande ne peut pas s’exécuter sur la cible de commande actuelle, la source de la commande se désactivera généralement elle-même.</span><span class="sxs-lookup"><span data-stu-id="42f88-128">If the command cannot execute on the current command target, the command source will typically disable itself.</span></span> <span data-ttu-id="42f88-129">Si la commande peut s’exécuter sur la cible de commande actuelle, la source de la commande s’active généralement elle-même.</span><span class="sxs-lookup"><span data-stu-id="42f88-129">If the command can execute on the current command target, the command source will typically enable itself.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
[!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]

<span data-ttu-id="42f88-130">La dernière étape est la méthode <xref:System.Windows.Input.ICommand.Execute%2A>.</span><span class="sxs-lookup"><span data-stu-id="42f88-130">The last step is the <xref:System.Windows.Input.ICommand.Execute%2A> method.</span></span> <span data-ttu-id="42f88-131">Si la commande est un <xref:System.Windows.Input.RoutedCommand>, la méthode <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> est appelée ; dans le cas contraire, la méthode <xref:System.Windows.Input.ICommand.Execute%2A> <xref:System.Windows.Input.ICommand> est appelée.</span><span class="sxs-lookup"><span data-stu-id="42f88-131">If the command is a <xref:System.Windows.Input.RoutedCommand>, the <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> method is called; otherwise, the <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> method is called.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
[!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]

## <a name="see-also"></a><span data-ttu-id="42f88-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42f88-132">See also</span></span>

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [<span data-ttu-id="42f88-133">Vue d’ensemble des commandes</span><span class="sxs-lookup"><span data-stu-id="42f88-133">Commanding Overview</span></span>](commanding-overview.md)
