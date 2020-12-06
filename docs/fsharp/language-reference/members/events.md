---
title: Événements
description: 'Découvrez comment les événements F # vous permettent d’associer des appels de fonction à des actions de l’utilisateur, qui sont importantes dans la programmation de l’interface graphique.'
ms.date: 08/15/2020
ms.openlocfilehash: 17e0cc8840053bf24d5c69694fe94d544c44510d
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740339"
---
# <a name="events"></a><span data-ttu-id="b17bd-103">Événements</span><span class="sxs-lookup"><span data-stu-id="b17bd-103">Events</span></span>

<span data-ttu-id="b17bd-104">Les événements vous permettent d'associer des appels de fonction à des actions utilisateur ; ils sont un élément important de la programmation d'interfaces GUI.</span><span class="sxs-lookup"><span data-stu-id="b17bd-104">Events enable you to associate function calls with user actions and are important in GUI programming.</span></span> <span data-ttu-id="b17bd-105">Des événements peuvent également être déclenchés par vos applications ou par le système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="b17bd-105">Events can also be triggered by your applications or by the operating system.</span></span>

## <a name="handling-events"></a><span data-ttu-id="b17bd-106">Gestion des événements</span><span class="sxs-lookup"><span data-stu-id="b17bd-106">Handling Events</span></span>

<span data-ttu-id="b17bd-107">Lorsque vous utilisez une bibliothèque d'interfaces GUI telle que Windows Forms ou Windows Presentation Foundation (WPF), une grande partie du code dans votre application s'exécute en réponse à des événements prédéfinis par la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="b17bd-107">When you use a GUI library like Windows Forms or Windows Presentation Foundation (WPF), much of the code in your application runs in response to events that are predefined by the library.</span></span> <span data-ttu-id="b17bd-108">Ces événements prédéfinis sont membres de classes GUI, comme les formulaires et les contrôles.</span><span class="sxs-lookup"><span data-stu-id="b17bd-108">These predefined events are members of GUI classes such as forms and controls.</span></span> <span data-ttu-id="b17bd-109">Vous pouvez ajouter un comportement personnalisé à un événement préexistant, tel qu'un clic de bouton, en référençant l'événement nommé spécifique présentant un intérêt (par exemple, l'événement `Click` de la classe `Form`) et en appelant la méthode `Add`, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="b17bd-109">You can add custom behavior to a preexisting event, such as a button click, by referencing the specific named event of interest (for example, the `Click` event of the `Form` class) and invoking the `Add` method, as shown in the following code.</span></span> <span data-ttu-id="b17bd-110">Si vous exécutez ceci à partir de F# Interactive, omettez d'appeler `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.</span><span class="sxs-lookup"><span data-stu-id="b17bd-110">If you run this from F# Interactive, omit the call to `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

<span data-ttu-id="b17bd-111">Le type de la méthode `Add` est `('a -> unit) -> unit`.</span><span class="sxs-lookup"><span data-stu-id="b17bd-111">The type of the `Add` method is `('a -> unit) -> unit`.</span></span> <span data-ttu-id="b17bd-112">Par conséquent, la méthode du gestionnaire d’événements prend un paramètre, en général les arguments d’événement, et retourne `unit`.</span><span class="sxs-lookup"><span data-stu-id="b17bd-112">Therefore, the event handler method takes one parameter, typically the event arguments, and returns `unit`.</span></span> <span data-ttu-id="b17bd-113">L’exemple précédent présente le gestionnaire d’événements en tant qu’expression lambda.</span><span class="sxs-lookup"><span data-stu-id="b17bd-113">The previous example shows the event handler as a lambda expression.</span></span> <span data-ttu-id="b17bd-114">Le gestionnaire d'événements peut également être une valeur de fonction, comme dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="b17bd-114">The event handler can also be a function value, as in the following code example.</span></span> <span data-ttu-id="b17bd-115">L'exemple de code suivant illustre également l'utilisation des paramètres du gestionnaire d'événements, qui fournissent des informations spécifiques au type d'événement.</span><span class="sxs-lookup"><span data-stu-id="b17bd-115">The following code example also shows the use of the event handler parameters, which provide information specific to the type of event.</span></span> <span data-ttu-id="b17bd-116">Pour un événement `MouseMove`, le système passe un objet `System.Windows.Forms.MouseEventArgs`, qui contient les positions `X` et `Y` du pointeur.</span><span class="sxs-lookup"><span data-stu-id="b17bd-116">For a `MouseMove` event, the system passes a `System.Windows.Forms.MouseEventArgs` object, which contains the `X` and `Y` position of the pointer.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]

## <a name="creating-custom-events"></a><span data-ttu-id="b17bd-117">Création d'événements personnalisés</span><span class="sxs-lookup"><span data-stu-id="b17bd-117">Creating Custom Events</span></span>

<span data-ttu-id="b17bd-118">Les événements f # sont représentés par le type d' [événement](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpevent-1.html) f #, qui implémente l’interface [IEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-ievent-1.html) .</span><span class="sxs-lookup"><span data-stu-id="b17bd-118">F# events are represented by the F# [Event](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpevent-1.html) type, which implements the [IEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-ievent-1.html) interface.</span></span> <span data-ttu-id="b17bd-119">`IEvent` est lui-même une interface qui combine les fonctionnalités de deux autres interfaces `System.IObservable<'T>` et [IDelegateEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-idelegateevent-1.html).</span><span class="sxs-lookup"><span data-stu-id="b17bd-119">`IEvent` is itself an interface that combines the functionality of two other interfaces, `System.IObservable<'T>` and [IDelegateEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-idelegateevent-1.html).</span></span> <span data-ttu-id="b17bd-120">Par conséquent, les `Event`s ont les fonctionnalités équivalentes des délégués dans d'autres langues, plus les fonctionnalités supplémentaires d'`IObservable`, ce qui signifie que les événements F# prennent en charge le filtrage d'événements, ainsi que l'utilisation de fonctions de première classe F# et expressions lambda comme gestionnaires d'événements.</span><span class="sxs-lookup"><span data-stu-id="b17bd-120">Therefore, `Event`s have the equivalent functionality of delegates in other languages, plus the additional functionality from `IObservable`, which means that F# events support event filtering and using F# first-class functions and lambda expressions as event handlers.</span></span> <span data-ttu-id="b17bd-121">Cette fonctionnalité est fournie dans le [module Event](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-eventmodule.html).</span><span class="sxs-lookup"><span data-stu-id="b17bd-121">This functionality is provided in the [Event module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-eventmodule.html).</span></span>

<span data-ttu-id="b17bd-122">Pour créer un événement sur une classe qui agit juste comme tout autre événement .NET Framework, ajoutez à la classe une liaison `let` qui définit un `Event` comme un champ dans une classe.</span><span class="sxs-lookup"><span data-stu-id="b17bd-122">To create an event on a class that acts just like any other .NET Framework event, add to the class a `let` binding that defines an `Event` as a field in a class.</span></span> <span data-ttu-id="b17bd-123">Vous pouvez spécifier le type d'argument d'événement souhaité comme argument de type ou le laisser vide et indiquer au compilateur de déduire le type approprié.</span><span class="sxs-lookup"><span data-stu-id="b17bd-123">You can specify the desired event argument type as the type argument, or leave it blank and have the compiler infer the appropriate type.</span></span> <span data-ttu-id="b17bd-124">Vous devez également définir un membre d'événement qui expose l'événement comme un événement CLI.</span><span class="sxs-lookup"><span data-stu-id="b17bd-124">You also must define an event member that exposes the event as a CLI event.</span></span> <span data-ttu-id="b17bd-125">Ce membre doit avoir l’attribut [CLIEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-clieventattribute.html) .</span><span class="sxs-lookup"><span data-stu-id="b17bd-125">This member should have the [CLIEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-clieventattribute.html) attribute.</span></span> <span data-ttu-id="b17bd-126">Elle est déclarée comme une propriété et son implémentation est simplement un appel à la propriété [Publish](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpevent-1.html#Publish) de l’événement.</span><span class="sxs-lookup"><span data-stu-id="b17bd-126">It is declared like a property and its implementation is just a call to the [Publish](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpevent-1.html#Publish) property of the event.</span></span> <span data-ttu-id="b17bd-127">Les utilisateurs de votre classe peuvent utiliser la méthode `Add` de l'événement publié pour ajouter un gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="b17bd-127">Users of your class can use the `Add` method of the published event to add a handler.</span></span> <span data-ttu-id="b17bd-128">L'argument de la méthode `Add` peut être une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="b17bd-128">The argument for the `Add` method can be a lambda expression.</span></span> <span data-ttu-id="b17bd-129">Vous pouvez utiliser la propriété `Trigger` de l’événement pour le déclencher, en passant les arguments à la fonction de gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="b17bd-129">You can use the `Trigger` property of the event to raise the event, passing the arguments to the handler function.</span></span> <span data-ttu-id="b17bd-130">L'exemple de code suivant illustre ceci.</span><span class="sxs-lookup"><span data-stu-id="b17bd-130">The following code example illustrates this.</span></span> <span data-ttu-id="b17bd-131">Dans cet exemple, l'argument de type déduit pour l'événement est un tuple, qui représente les arguments de l'expression lambda.</span><span class="sxs-lookup"><span data-stu-id="b17bd-131">In this example, the inferred type argument for the event is a tuple, which represents the arguments for the lambda expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

<span data-ttu-id="b17bd-132">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="b17bd-132">The output is as follows.</span></span>

```console
Event1 occurred! Object data: Hello World!
```

<span data-ttu-id="b17bd-133">Les fonctionnalités supplémentaires fournies par le module `Event` sont illustrées ici.</span><span class="sxs-lookup"><span data-stu-id="b17bd-133">The additional functionality provided by the `Event` module is illustrated here.</span></span> <span data-ttu-id="b17bd-134">L'exemple de code suivant illustre l'utilisation de base d'`Event.create` pour créer un événement et une méthode de déclencheur, ajouter deux gestionnaires d'événements sous forme d'expressions lambda, puis déclencher l'événement pour exécuter les deux expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="b17bd-134">The following code example illustrates the basic use of `Event.create` to create an event and a trigger method, add two event handlers in the form of lambda expressions, and then trigger the event to execute both lambda expressions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

<span data-ttu-id="b17bd-135">La sortie du code précédent est la suivante.</span><span class="sxs-lookup"><span data-stu-id="b17bd-135">The output of the previous code is as follows.</span></span>

```console
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a><span data-ttu-id="b17bd-136">Traitement de flux d'événements</span><span class="sxs-lookup"><span data-stu-id="b17bd-136">Processing Event Streams</span></span>

<span data-ttu-id="b17bd-137">Au lieu d’ajouter simplement un gestionnaire d’événements pour un événement à l’aide de la fonction [Event. Add](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-eventmodule.html#add) , vous pouvez utiliser les fonctions du `Event` module pour traiter des flux d’événements de manière hautement personnalisée.</span><span class="sxs-lookup"><span data-stu-id="b17bd-137">Instead of just adding an event handler for an event by using the [Event.add](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-eventmodule.html#add) function, you can use the functions in the `Event` module to process streams of events in highly customized ways.</span></span> <span data-ttu-id="b17bd-138">Pour cela, vous utilisez le canal (`|>`) avec l'événement comme première valeur dans une série d'appels de fonction, et les fonctions du module `Event` comme appels de fonction suivants.</span><span class="sxs-lookup"><span data-stu-id="b17bd-138">To do this, you use the forward pipe (`|>`) together with the event as the first value in a series of function calls, and the `Event` module functions as subsequent function calls.</span></span>

<span data-ttu-id="b17bd-139">L'exemple de code suivant illustre comment configurer un événement pour lequel le gestionnaire est uniquement appelé sous certaines conditions.</span><span class="sxs-lookup"><span data-stu-id="b17bd-139">The following code example shows how to set up an event for which the handler is only called under certain conditions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

<span data-ttu-id="b17bd-140">Le [module observable](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-observablemodule.html) contient des fonctions similaires qui opèrent sur des objets observables.</span><span class="sxs-lookup"><span data-stu-id="b17bd-140">The [Observable module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-observablemodule.html) contains similar functions that operate on observable objects.</span></span> <span data-ttu-id="b17bd-141">Les objets observables sont semblables aux événements, mais s'abonnent activement aux événements uniquement s'ils font eux-mêmes l'objet d'un abonnement.</span><span class="sxs-lookup"><span data-stu-id="b17bd-141">Observable objects are similar to events but only actively subscribe to events if they themselves are being subscribed to.</span></span>

## <a name="implementing-an-interface-event"></a><span data-ttu-id="b17bd-142">Implémentation d'un évènement d'interface</span><span class="sxs-lookup"><span data-stu-id="b17bd-142">Implementing an Interface Event</span></span>

<span data-ttu-id="b17bd-143">Lorsque vous développez des composants d'interface utilisateur, vous commencez souvent par créer un formulaire ou un contrôle qui héritent d'un formulaire ou d'un contrôle existant.</span><span class="sxs-lookup"><span data-stu-id="b17bd-143">As you develop UI components, you often start by creating a new form or a new control that inherits from an existing form or control.</span></span> <span data-ttu-id="b17bd-144">Les événements sont souvent définis dans une interface, et, dans ce cas, vous devez implémenter l'interface pour implémenter l'événement.</span><span class="sxs-lookup"><span data-stu-id="b17bd-144">Events are frequently defined on an interface, and, in that case, you must implement the interface to implement the event.</span></span> <span data-ttu-id="b17bd-145">L'interface `System.ComponentModel.INotifyPropertyChanged` définit un seul événement `System.ComponentModel.INotifyPropertyChanged.PropertyChanged`.</span><span class="sxs-lookup"><span data-stu-id="b17bd-145">The `System.ComponentModel.INotifyPropertyChanged` interface defines a single `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` event.</span></span> <span data-ttu-id="b17bd-146">Le code suivant illustre comment implémenter l'événement défini par cette interface héritée :</span><span class="sxs-lookup"><span data-stu-id="b17bd-146">The following code illustrates how to implement the event that this inherited interface defined:</span></span>

```fsharp
module CustomForm

open System.Windows.Forms
open System.ComponentModel

type AppForm() as this =
    inherit Form()

    // Define the propertyChanged event.
    let propertyChanged = Event<PropertyChangedEventHandler, PropertyChangedEventArgs>()
    let mutable underlyingValue = "text0"

    // Set up a click event to change the properties.
    do
        this.Click |> Event.add(fun evArgs ->
            this.Property1 <- "text2"
            this.Property2 <- "text3")

    // This property does not have the property-changed event set.
    member val Property1 : string = "text" with get, set

    // This property has the property-changed event set.
    member this.Property2
        with get() = underlyingValue
        and set(newValue) =
            underlyingValue <- newValue
            propertyChanged.Trigger(this, new PropertyChangedEventArgs("Property2"))

    // Expose the PropertyChanged event as a first class .NET event.
    [<CLIEvent>]
    member this.PropertyChanged = propertyChanged.Publish

    // Define the add and remove methods to implement this interface.
    interface INotifyPropertyChanged with
        member this.add_PropertyChanged(handler) = propertyChanged.Publish.AddHandler(handler)
        member this.remove_PropertyChanged(handler) = propertyChanged.Publish.RemoveHandler(handler)

    // This is the event-handler method.
    member this.OnPropertyChanged(args : PropertyChangedEventArgs) =
        let newProperty = this.GetType().GetProperty(args.PropertyName)
        let newValue = newProperty.GetValue(this :> obj) :?> string
        printfn "Property {args.PropertyName} changed its value to {newValue}"

// Create a form, hook up the event handler, and start the application.
let appForm = new AppForm()
let inpc = appForm :> INotifyPropertyChanged
inpc.PropertyChanged.Add(appForm.OnPropertyChanged)
Application.Run(appForm)
```

<span data-ttu-id="b17bd-147">Si vous souhaitez raccorder l'événement dans le constructeur, le code est un peu plus complexe, car la connexion d'événements doit être dans un bloc `then` dans un constructeur supplémentaire, comme dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="b17bd-147">If you want to hook up the event in the constructor, the code is a bit more complicated because the event hookup must be in a `then` block in an additional constructor, as in the following example:</span></span>

```fsharp
module CustomForm

open System.Windows.Forms
open System.ComponentModel

// Create a private constructor with a dummy argument so that the public
// constructor can have no arguments.
type AppForm private (dummy) as this =
    inherit Form()

    // Define the propertyChanged event.
    let propertyChanged = Event<PropertyChangedEventHandler, PropertyChangedEventArgs>()
    let mutable underlyingValue = "text0"

    // Set up a click event to change the properties.
    do
        this.Click |> Event.add(fun evArgs ->
            this.Property1 <- "text2"
            this.Property2 <- "text3")

    // This property does not have the property changed event set.
    member val Property1 : string = "text" with get, set

    // This property has the property changed event set.
    member this.Property2
        with get() = underlyingValue
        and set(newValue) =
            underlyingValue <- newValue
            propertyChanged.Trigger(this, new PropertyChangedEventArgs("Property2"))

    [<CLIEvent>]
    member this.PropertyChanged = propertyChanged.Publish

    // Define the add and remove methods to implement this interface.
    interface INotifyPropertyChanged with
        member this.add_PropertyChanged(handler) = this.PropertyChanged.AddHandler(handler)
        member this.remove_PropertyChanged(handler) = this.PropertyChanged.RemoveHandler(handler)

    // This is the event handler method.
    member this.OnPropertyChanged(args : PropertyChangedEventArgs) =
        let newProperty = this.GetType().GetProperty(args.PropertyName)
        let newValue = newProperty.GetValue(this :> obj) :?> string
        printfn "Property {args.PropertyName} changed its value to {newValue}"

    new() as this =
        new AppForm(0)
        then
            let inpc = this :> INotifyPropertyChanged
            inpc.PropertyChanged.Add(this.OnPropertyChanged)

// Create a form, hook up the event handler, and start the application.
let appForm = new AppForm()
Application.Run(appForm)
```

## <a name="see-also"></a><span data-ttu-id="b17bd-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b17bd-148">See also</span></span>

- <span data-ttu-id="b17bd-149">[Members](index.md) (Membres)</span><span class="sxs-lookup"><span data-stu-id="b17bd-149">[Members](index.md)</span></span>
- [<span data-ttu-id="b17bd-150">Gestion et déclenchement d'événements</span><span class="sxs-lookup"><span data-stu-id="b17bd-150">Handling and Raising Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="b17bd-151">Expressions lambda : `fun` mot clé</span><span class="sxs-lookup"><span data-stu-id="b17bd-151">Lambda Expressions: The `fun` Keyword</span></span>](../functions/lambda-expressions-the-fun-keyword.md)
