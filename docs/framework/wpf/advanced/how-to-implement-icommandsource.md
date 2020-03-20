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
# <a name="how-to-implement-icommandsource"></a><span data-ttu-id="89561-102">Comment : implémenter ICommandSource</span><span class="sxs-lookup"><span data-stu-id="89561-102">How to: Implement ICommandSource</span></span>

<span data-ttu-id="89561-103">Cet exemple montre comment créer une <xref:System.Windows.Input.ICommandSource>source de commande en mettant en œuvre .</span><span class="sxs-lookup"><span data-stu-id="89561-103">This example shows how to create a command source by implementing <xref:System.Windows.Input.ICommandSource>.</span></span> <span data-ttu-id="89561-104">Une source de commande est un objet qui sait invoquer une commande.</span><span class="sxs-lookup"><span data-stu-id="89561-104">A command source is an object that knows how to invoke a command.</span></span> <span data-ttu-id="89561-105">L’interface <xref:System.Windows.Input.ICommandSource> expose trois membres :</span><span class="sxs-lookup"><span data-stu-id="89561-105">The <xref:System.Windows.Input.ICommandSource> interface exposes three members:</span></span>

- <span data-ttu-id="89561-106"><xref:System.Windows.Input.ICommandSource.Command%2A>: la commande qui sera invoquée.</span><span class="sxs-lookup"><span data-stu-id="89561-106"><xref:System.Windows.Input.ICommandSource.Command%2A>: the command that will be invoked.</span></span>
- <span data-ttu-id="89561-107"><xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: un type de données défini par l’utilisateur qui passe de la source de commande à la méthode qui gère la commande.</span><span class="sxs-lookup"><span data-stu-id="89561-107"><xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: a user-defined data type which is passed from the command source to the method that handles the command.</span></span>
- <span data-ttu-id="89561-108"><xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: l’objet sur lequel la commande est exécutée.</span><span class="sxs-lookup"><span data-stu-id="89561-108"><xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: the object that the command is being executed on.</span></span>

<span data-ttu-id="89561-109">Dans cet exemple, une classe est <xref:System.Windows.Controls.Slider> créée qui hérite du contrôle et implémente l’interface. <xref:System.Windows.Input.ICommandSource></span><span class="sxs-lookup"><span data-stu-id="89561-109">In this example, a class is created that inherits from the <xref:System.Windows.Controls.Slider> control and implements the  <xref:System.Windows.Input.ICommandSource> interface.</span></span>
  
## <a name="example"></a><span data-ttu-id="89561-110"> Exemple</span><span class="sxs-lookup"><span data-stu-id="89561-110">Example</span></span>

<span data-ttu-id="89561-111">WPF fournit un certain <xref:System.Windows.Input.ICommandSource>nombre de <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.MenuItem>classes <xref:System.Windows.Documents.Hyperlink>qui mettent en œuvre , tels que , , et .</span><span class="sxs-lookup"><span data-stu-id="89561-111">WPF provides a number of classes which implement <xref:System.Windows.Input.ICommandSource>, such as <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>, and <xref:System.Windows.Documents.Hyperlink>.</span></span> <span data-ttu-id="89561-112">Une source de commande définit comment elle invoque une commande.</span><span class="sxs-lookup"><span data-stu-id="89561-112">A command source defines how it invokes a command.</span></span> <span data-ttu-id="89561-113">Ces classes invoquent une commande lorsqu’elles sont cliqués et elles ne deviennent une source de commande que lorsque leur <xref:System.Windows.Input.ICommandSource.Command%2A> propriété est définie.</span><span class="sxs-lookup"><span data-stu-id="89561-113">These classes invoke a command when they're clicked and they only become a command source when their <xref:System.Windows.Input.ICommandSource.Command%2A> property is set.</span></span>

<span data-ttu-id="89561-114">Dans cet exemple, vous invoquez la commande lorsque le curseur est déplacé, ou plus exactement, lorsque la <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> propriété est modifiée.</span><span class="sxs-lookup"><span data-stu-id="89561-114">In this example, you'll invoke the command when the slider is moved, or more accurately, when the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property is changed.</span></span>

<span data-ttu-id="89561-115">Voici la définition de la classe :</span><span class="sxs-lookup"><span data-stu-id="89561-115">The following is the class definition:</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]

<span data-ttu-id="89561-116">La prochaine étape consiste <xref:System.Windows.Input.ICommandSource> à mettre en œuvre les membres.</span><span class="sxs-lookup"><span data-stu-id="89561-116">The next step is to implement the <xref:System.Windows.Input.ICommandSource> members.</span></span> <span data-ttu-id="89561-117">Dans cet exemple, les <xref:System.Windows.DependencyProperty> propriétés sont implémentées comme objets.</span><span class="sxs-lookup"><span data-stu-id="89561-117">In this example, the properties are implemented as <xref:System.Windows.DependencyProperty> objects.</span></span> <span data-ttu-id="89561-118">Cela permet aux propriétés d’utiliser la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="89561-118">This enables the properties to use data binding.</span></span> <span data-ttu-id="89561-119">Pour plus d’informations sur la <xref:System.Windows.DependencyProperty> classe, voir le Aperçu des [propriétés de dépendance](dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="89561-119">For more information about the <xref:System.Windows.DependencyProperty> class, see the [Dependency Properties Overview](dependency-properties-overview.md).</span></span> <span data-ttu-id="89561-120">Pour plus d’informations sur la liaison des données, voir [l’aperçu de la liaison des données](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="89561-120">For more information about data binding, see the [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<span data-ttu-id="89561-121">Seule <xref:System.Windows.Input.ICommandSource.Command%2A> la propriété est montrée ici.</span><span class="sxs-lookup"><span data-stu-id="89561-121">Only the <xref:System.Windows.Input.ICommandSource.Command%2A> property is shown here.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
<span data-ttu-id="89561-122">Voici le <xref:System.Windows.DependencyProperty> rappel de changement :</span><span class="sxs-lookup"><span data-stu-id="89561-122">The following is the <xref:System.Windows.DependencyProperty> change callback:</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]

<span data-ttu-id="89561-123">L’étape suivante consiste à ajouter et supprimer la commande qui est associée à la source de commande.</span><span class="sxs-lookup"><span data-stu-id="89561-123">The next step is to add and remove the command which is associated with the command source.</span></span> <span data-ttu-id="89561-124">La <xref:System.Windows.Input.ICommandSource.Command%2A> propriété ne peut pas simplement être écrasée lorsqu’une nouvelle commande est ajoutée, parce que les gestionnaires d’événements associés à la commande précédente, s’il y en avait une, doivent d’abord être supprimés.</span><span class="sxs-lookup"><span data-stu-id="89561-124">The <xref:System.Windows.Input.ICommandSource.Command%2A> property cannot simply be overwritten when a new command is added, because the event handlers associated with the previous command, if there was one, must be removed first.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]

<span data-ttu-id="89561-125">L’étape suivante consiste à <xref:System.Windows.Input.ICommand.CanExecuteChanged> créer une logique pour le gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="89561-125">The next step is to create logic for the <xref:System.Windows.Input.ICommand.CanExecuteChanged> handler.</span></span>

<span data-ttu-id="89561-126">L’événement <xref:System.Windows.Input.ICommand.CanExecuteChanged> informe la source de commandement que la capacité de la commande d’exécuter sur la cible de commande actuelle peut avoir changé.</span><span class="sxs-lookup"><span data-stu-id="89561-126">The <xref:System.Windows.Input.ICommand.CanExecuteChanged> event notifies the command source that the ability of the command to execute on the current command target may have changed.</span></span> <span data-ttu-id="89561-127">Lorsqu’une source de commande reçoit <xref:System.Windows.Input.ICommand.CanExecute%2A> cet événement, elle appelle généralement la méthode sur la commande.</span><span class="sxs-lookup"><span data-stu-id="89561-127">When a command source receives this event, it typically calls the <xref:System.Windows.Input.ICommand.CanExecute%2A> method on the command.</span></span> <span data-ttu-id="89561-128">Si la commande ne peut pas exécuter sur la cible de commande actuelle, la source de commande se désactive généralement.</span><span class="sxs-lookup"><span data-stu-id="89561-128">If the command cannot execute on the current command target, the command source will typically disable itself.</span></span> <span data-ttu-id="89561-129">Si la commande peut s’exécuter sur la cible de commande actuelle, la source de commande s’active généralement.</span><span class="sxs-lookup"><span data-stu-id="89561-129">If the command can execute on the current command target, the command source will typically enable itself.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
[!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]

<span data-ttu-id="89561-130">La dernière étape <xref:System.Windows.Input.ICommand.Execute%2A> est la méthode.</span><span class="sxs-lookup"><span data-stu-id="89561-130">The last step is the <xref:System.Windows.Input.ICommand.Execute%2A> method.</span></span> <span data-ttu-id="89561-131">Si la commande <xref:System.Windows.Input.RoutedCommand>est <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> un , la méthode est appelée; sinon, <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> la méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="89561-131">If the command is a <xref:System.Windows.Input.RoutedCommand>, the <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> method is called; otherwise, the <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> method is called.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
[!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]

## <a name="see-also"></a><span data-ttu-id="89561-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89561-132">See also</span></span>

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [<span data-ttu-id="89561-133">Vue d’ensemble des commandes</span><span class="sxs-lookup"><span data-stu-id="89561-133">Commanding Overview</span></span>](commanding-overview.md)
