---
title: Introduction aux événements
description: En savoir plus sur les événements dans .NET Core et nos objectifs de conception de langage pour les événements dans cette vue d’ensemble.
ms.date: 06/20/2016
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: 4e660f85eecfd5668919baf21a0d26f858faf5a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146112"
---
# <a name="introduction-to-events"></a><span data-ttu-id="d36f9-103">Introduction aux événements</span><span class="sxs-lookup"><span data-stu-id="d36f9-103">Introduction to events</span></span>

[<span data-ttu-id="d36f9-104">Précédent</span><span class="sxs-lookup"><span data-stu-id="d36f9-104">Previous</span></span>](delegates-patterns.md)

<span data-ttu-id="d36f9-105">Les événements sont, comme les délégués, un mécanisme de *liaison tardive*.</span><span class="sxs-lookup"><span data-stu-id="d36f9-105">Events are, like delegates, a *late binding* mechanism.</span></span> <span data-ttu-id="d36f9-106">En fait, les événements reposent sur la prise en charge linguistique des délégués.</span><span class="sxs-lookup"><span data-stu-id="d36f9-106">In fact, events are built on the language support for delegates.</span></span>

<span data-ttu-id="d36f9-107">Ils permettent à un objet de signaler (à tous les composants du système intéressés), que quelque chose s’est produit.</span><span class="sxs-lookup"><span data-stu-id="d36f9-107">Events are a way for an object to broadcast (to all interested components in the system) that something has happened.</span></span> <span data-ttu-id="d36f9-108">Tous les autres composants peuvent s’abonner à l’événement et être averti quand un événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="d36f9-108">Any other component can subscribe to the event, and be notified when an event is raised.</span></span>

<span data-ttu-id="d36f9-109">Vous avez sans doute déjà utilisé des événements durant vos tâches de programmation.</span><span class="sxs-lookup"><span data-stu-id="d36f9-109">You've probably used events in some of your programming.</span></span> <span data-ttu-id="d36f9-110">De nombreux systèmes graphiques ont un modèle d’événement pour signaler l’interaction utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d36f9-110">Many graphical systems have an event model to report user interaction.</span></span> <span data-ttu-id="d36f9-111">Ces événements signalent les mouvements de la souris, les pressions sur des boutons et autres interactions similaires.</span><span class="sxs-lookup"><span data-stu-id="d36f9-111">These events would report mouse movement, button presses and similar interactions.</span></span> <span data-ttu-id="d36f9-112">C’est l’un des scénarios les plus courants, mais certainement pas le seul, où des événements sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="d36f9-112">That's one of the most common, but certainly not the only scenario where events are used.</span></span>

<span data-ttu-id="d36f9-113">Vous pouvez définir les événements qui doivent être déclenchés pour vos classes.</span><span class="sxs-lookup"><span data-stu-id="d36f9-113">You can define events that should be raised for your classes.</span></span> <span data-ttu-id="d36f9-114">Quand vous travaillez avec des événements, vous devez prendre en compte le fait qu’il se peut qu’aucun objet ne soit inscrit pour un événement particulier.</span><span class="sxs-lookup"><span data-stu-id="d36f9-114">One important consideration when working with events is that there may not be any object registered for a particular event.</span></span> <span data-ttu-id="d36f9-115">Vous devez écrire votre code pour qu’il ne déclenche pas d’événement quand aucun détecteur n’est configuré.</span><span class="sxs-lookup"><span data-stu-id="d36f9-115">You must write your code so that it does not raise events when no listeners are configured.</span></span>

<span data-ttu-id="d36f9-116">L’abonnement à un événement crée également un couplage entre deux objets (la source de l’événement et le récepteur d’événements).</span><span class="sxs-lookup"><span data-stu-id="d36f9-116">Subscribing to an event also creates a coupling between two objects (the event source, and the event sink).</span></span> <span data-ttu-id="d36f9-117">Vous devez vérifier que le récepteur d’événements annule l’abonnement à la source de l’événement quand il n’est plus intéressé par les événements.</span><span class="sxs-lookup"><span data-stu-id="d36f9-117">You need to ensure that the event sink unsubscribes from the event source when no longer interested in events.</span></span>

## <a name="design-goals-for-event-support"></a><span data-ttu-id="d36f9-118">Objectifs de conception pour le soutien de l’événement</span><span class="sxs-lookup"><span data-stu-id="d36f9-118">Design goals for event support</span></span>

<span data-ttu-id="d36f9-119">La conception linguistique des événements cible ces objectifs :</span><span class="sxs-lookup"><span data-stu-id="d36f9-119">The language design for events targets these goals:</span></span>

- <span data-ttu-id="d36f9-120">Activez un couplage très minime entre une source d’événement et un évier d’événement.</span><span class="sxs-lookup"><span data-stu-id="d36f9-120">Enable very minimal coupling between an event source and an event sink.</span></span> <span data-ttu-id="d36f9-121">Ces deux composants peuvent ne pas avoir été écrits par la même organisation, et peuvent même être mis à jour d’après une planification totalement différente.</span><span class="sxs-lookup"><span data-stu-id="d36f9-121">These two components may not be written by the same organization, and may even be updated on totally different schedules.</span></span>

- <span data-ttu-id="d36f9-122">Il devrait être très simple de s’abonner à un événement, et de se désabonner de ce même événement.</span><span class="sxs-lookup"><span data-stu-id="d36f9-122">It should be very simple to subscribe to an event, and to unsubscribe from that same event.</span></span>

- <span data-ttu-id="d36f9-123">Les sources d’événements devraient prendre en charge plusieurs abonnés à l’événement.</span><span class="sxs-lookup"><span data-stu-id="d36f9-123">Event sources should support multiple event subscribers.</span></span> <span data-ttu-id="d36f9-124">Elles doivent aussi prendre en charge les scénarios où aucun abonné aux événements n’est attaché.</span><span class="sxs-lookup"><span data-stu-id="d36f9-124">It should also support having no event subscribers attached.</span></span>

<span data-ttu-id="d36f9-125">Vous pouvez constater que les objectifs pour les événements sont très similaires aux objectifs pour les délégués.</span><span class="sxs-lookup"><span data-stu-id="d36f9-125">You can see that the goals for events are very similar to the goals for delegates.</span></span>
<span data-ttu-id="d36f9-126">C’est pourquoi la prise en charge linguistique des événements repose sur la prise en charge linguistique des délégués.</span><span class="sxs-lookup"><span data-stu-id="d36f9-126">That's why the event language support is built on the delegate language support.</span></span>

## <a name="language-support-for-events"></a><span data-ttu-id="d36f9-127">Soutien linguistique aux événements</span><span class="sxs-lookup"><span data-stu-id="d36f9-127">Language support for events</span></span>

<span data-ttu-id="d36f9-128">La syntaxe de définition des événements, et d’abonnement ou d’annulation des abonnements, est une extension de la syntaxe des délégués.</span><span class="sxs-lookup"><span data-stu-id="d36f9-128">The syntax for defining events, and subscribing or unsubscribing from events is an extension of the syntax for delegates.</span></span>

<span data-ttu-id="d36f9-129">Pour définir un événement, vous devez utiliser le mot clé `event` :</span><span class="sxs-lookup"><span data-stu-id="d36f9-129">To define an event you use the `event` keyword:</span></span>

```csharp
public event EventHandler<FileListArgs> Progress;
```

<span data-ttu-id="d36f9-130">Le type de l’événement (`EventHandler<FileListArgs>` dans cet exemple) doit être un type délégué.</span><span class="sxs-lookup"><span data-stu-id="d36f9-130">The type of the event (`EventHandler<FileListArgs>` in this example) must be a delegate type.</span></span> <span data-ttu-id="d36f9-131">Vous devez respecter plusieurs conventions lors de la déclaration d’un événement.</span><span class="sxs-lookup"><span data-stu-id="d36f9-131">There are a number of conventions that you should follow when declaring an event.</span></span> <span data-ttu-id="d36f9-132">En général, le type délégué d’événement a un retour void.</span><span class="sxs-lookup"><span data-stu-id="d36f9-132">Typically, the event delegate type has a void return.</span></span>
<span data-ttu-id="d36f9-133">Les déclarations d’événements doivent être un verbe ou une phrase verbale.</span><span class="sxs-lookup"><span data-stu-id="d36f9-133">Event declarations should be a verb, or a verb phrase.</span></span>
<span data-ttu-id="d36f9-134">Utilisez le passé tendu lorsque l’événement signale quelque chose qui s’est passé.</span><span class="sxs-lookup"><span data-stu-id="d36f9-134">Use past tense when the event reports something that has happened.</span></span> <span data-ttu-id="d36f9-135">Utilisez un verbe au présent (par exemple, `Closing`) pour signaler quelque chose qui est sur le point de se produire.</span><span class="sxs-lookup"><span data-stu-id="d36f9-135">Use a present tense verb (for example, `Closing`) to report something that is about to happen.</span></span> <span data-ttu-id="d36f9-136">Souvent, le présent indique que votre classe prend en charge un type de comportement de personnalisation.</span><span class="sxs-lookup"><span data-stu-id="d36f9-136">Often, using present tense indicates that your class supports some kind of customization behavior.</span></span> <span data-ttu-id="d36f9-137">L’un des scénarios les plus courants consiste à prendre en charge l’annulation.</span><span class="sxs-lookup"><span data-stu-id="d36f9-137">One of the most common scenarios is to support cancellation.</span></span> <span data-ttu-id="d36f9-138">Par exemple, un événement `Closing` peut inclure un argument qui indique si l’opération de fermeture doit continuer ou non.</span><span class="sxs-lookup"><span data-stu-id="d36f9-138">For example, a `Closing` event may include an argument that would indicate if the close operation should continue, or not.</span></span>  <span data-ttu-id="d36f9-139">D’autres scénarios peuvent permettre aux appelants de modifier le comportement en mettant à jour les propriétés des arguments de l’événement.</span><span class="sxs-lookup"><span data-stu-id="d36f9-139">Other scenarios may enable callers to modify behavior by updating properties of the event arguments.</span></span> <span data-ttu-id="d36f9-140">Vous pouvez déclencher un événement pour indiquer une action suivante qu’un algorithme effectuera.</span><span class="sxs-lookup"><span data-stu-id="d36f9-140">You may raise an event to indicate a proposed next action an algorithm will take.</span></span> <span data-ttu-id="d36f9-141">Le gestionnaire d’événements peut imposer une action différente en modifiant les propriétés de l’argument d’événement.</span><span class="sxs-lookup"><span data-stu-id="d36f9-141">The event handler may mandate a different action by modifying  properties of the event argument.</span></span>

<span data-ttu-id="d36f9-142">Quand vous souhaitez déclencher l’événement, vous appelez les gestionnaires d’événements à l’aide de la syntaxe d’appel de délégué :</span><span class="sxs-lookup"><span data-stu-id="d36f9-142">When you want to raise the event, you call the event handlers using the delegate invocation syntax:</span></span>

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

<span data-ttu-id="d36f9-143">Comme indiqué dans la section sur les [délégués](delegates-patterns.md), l’opérateur ?.</span><span class="sxs-lookup"><span data-stu-id="d36f9-143">As discussed in the section on [delegates](delegates-patterns.md), the ?.</span></span>
<span data-ttu-id="d36f9-144">permet de s’assurer facilement que vous n’essayez pas de déclencher l’événement quand il n’y a aucun abonné à cet événement.</span><span class="sxs-lookup"><span data-stu-id="d36f9-144">operator makes it easy to ensure that you do not attempt to raise the event when there are no subscribers to that event.</span></span>

<span data-ttu-id="d36f9-145">Vous vous abonnez à un événement à l’aide de l’opérateur `+=` :</span><span class="sxs-lookup"><span data-stu-id="d36f9-145">You subscribe to an event by using the `+=` operator:</span></span>

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) =>
    Console.WriteLine(eventArgs.FoundFile);

fileLister.Progress += onProgress;
```

<span data-ttu-id="d36f9-146">La méthode du gestionnaire a généralement le préfixe 'On' suivi du nom de l’événement, comme indiqué ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="d36f9-146">The handler method typically has the prefix 'On' followed by the event name, as shown above.</span></span>

<span data-ttu-id="d36f9-147">Vous pouvez vous désinscrire à l’aide de l’opérateur `-=` :</span><span class="sxs-lookup"><span data-stu-id="d36f9-147">You unsubscribe using the `-=` operator:</span></span>

```csharp
fileLister.Progress -= onProgress;
```

<span data-ttu-id="d36f9-148">Il est important de noter que j’ai déclaré une variable locale pour l’expression qui représente le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="d36f9-148">It's important to note that I declared a local variable for the expression that represents the event handler.</span></span> <span data-ttu-id="d36f9-149">Cela garantit que le désabonnement supprime le gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="d36f9-149">That ensures the unsubscribe removes the handler.</span></span>
<span data-ttu-id="d36f9-150">Si au lieu de cela vous utilisez le corps de l’expression lambda, vous essayez de supprimer un gestionnaire qui n’a jamais été attaché, ce qui ne fait rien.</span><span class="sxs-lookup"><span data-stu-id="d36f9-150">If, instead, you used the body of the lambda expression, you are attempting to remove a handler that has never been attached, which does nothing.</span></span>

<span data-ttu-id="d36f9-151">Dans l’article suivant, vous en apprendrez davantage sur les modèles d’événements les plus courants et sur les différentes variantes de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="d36f9-151">In the next article, you'll learn more about typical event patterns, and different variations on this example.</span></span>

[<span data-ttu-id="d36f9-152">Suivant</span><span class="sxs-lookup"><span data-stu-id="d36f9-152">Next</span></span>](event-pattern.md)
