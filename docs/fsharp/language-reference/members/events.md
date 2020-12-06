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
# <a name="events"></a>Événements

Les événements vous permettent d'associer des appels de fonction à des actions utilisateur ; ils sont un élément important de la programmation d'interfaces GUI. Des événements peuvent également être déclenchés par vos applications ou par le système d'exploitation.

## <a name="handling-events"></a>Gestion des événements

Lorsque vous utilisez une bibliothèque d'interfaces GUI telle que Windows Forms ou Windows Presentation Foundation (WPF), une grande partie du code dans votre application s'exécute en réponse à des événements prédéfinis par la bibliothèque. Ces événements prédéfinis sont membres de classes GUI, comme les formulaires et les contrôles. Vous pouvez ajouter un comportement personnalisé à un événement préexistant, tel qu'un clic de bouton, en référençant l'événement nommé spécifique présentant un intérêt (par exemple, l'événement `Click` de la classe `Form`) et en appelant la méthode `Add`, comme indiqué dans le code suivant. Si vous exécutez ceci à partir de F# Interactive, omettez d'appeler `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

Le type de la méthode `Add` est `('a -> unit) -> unit`. Par conséquent, la méthode du gestionnaire d’événements prend un paramètre, en général les arguments d’événement, et retourne `unit`. L’exemple précédent présente le gestionnaire d’événements en tant qu’expression lambda. Le gestionnaire d'événements peut également être une valeur de fonction, comme dans l'exemple de code suivant. L'exemple de code suivant illustre également l'utilisation des paramètres du gestionnaire d'événements, qui fournissent des informations spécifiques au type d'événement. Pour un événement `MouseMove`, le système passe un objet `System.Windows.Forms.MouseEventArgs`, qui contient les positions `X` et `Y` du pointeur.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]

## <a name="creating-custom-events"></a>Création d'événements personnalisés

Les événements f # sont représentés par le type d' [événement](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpevent-1.html) f #, qui implémente l’interface [IEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-ievent-1.html) . `IEvent` est lui-même une interface qui combine les fonctionnalités de deux autres interfaces `System.IObservable<'T>` et [IDelegateEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-idelegateevent-1.html). Par conséquent, les `Event`s ont les fonctionnalités équivalentes des délégués dans d'autres langues, plus les fonctionnalités supplémentaires d'`IObservable`, ce qui signifie que les événements F# prennent en charge le filtrage d'événements, ainsi que l'utilisation de fonctions de première classe F# et expressions lambda comme gestionnaires d'événements. Cette fonctionnalité est fournie dans le [module Event](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-eventmodule.html).

Pour créer un événement sur une classe qui agit juste comme tout autre événement .NET Framework, ajoutez à la classe une liaison `let` qui définit un `Event` comme un champ dans une classe. Vous pouvez spécifier le type d'argument d'événement souhaité comme argument de type ou le laisser vide et indiquer au compilateur de déduire le type approprié. Vous devez également définir un membre d'événement qui expose l'événement comme un événement CLI. Ce membre doit avoir l’attribut [CLIEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-clieventattribute.html) . Elle est déclarée comme une propriété et son implémentation est simplement un appel à la propriété [Publish](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpevent-1.html#Publish) de l’événement. Les utilisateurs de votre classe peuvent utiliser la méthode `Add` de l'événement publié pour ajouter un gestionnaire. L'argument de la méthode `Add` peut être une expression lambda. Vous pouvez utiliser la propriété `Trigger` de l’événement pour le déclencher, en passant les arguments à la fonction de gestionnaire. L'exemple de code suivant illustre ceci. Dans cet exemple, l'argument de type déduit pour l'événement est un tuple, qui représente les arguments de l'expression lambda.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

La sortie est la suivante.

```console
Event1 occurred! Object data: Hello World!
```

Les fonctionnalités supplémentaires fournies par le module `Event` sont illustrées ici. L'exemple de code suivant illustre l'utilisation de base d'`Event.create` pour créer un événement et une méthode de déclencheur, ajouter deux gestionnaires d'événements sous forme d'expressions lambda, puis déclencher l'événement pour exécuter les deux expressions lambda.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

La sortie du code précédent est la suivante.

```console
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a>Traitement de flux d'événements

Au lieu d’ajouter simplement un gestionnaire d’événements pour un événement à l’aide de la fonction [Event. Add](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-eventmodule.html#add) , vous pouvez utiliser les fonctions du `Event` module pour traiter des flux d’événements de manière hautement personnalisée. Pour cela, vous utilisez le canal (`|>`) avec l'événement comme première valeur dans une série d'appels de fonction, et les fonctions du module `Event` comme appels de fonction suivants.

L'exemple de code suivant illustre comment configurer un événement pour lequel le gestionnaire est uniquement appelé sous certaines conditions.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

Le [module observable](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-observablemodule.html) contient des fonctions similaires qui opèrent sur des objets observables. Les objets observables sont semblables aux événements, mais s'abonnent activement aux événements uniquement s'ils font eux-mêmes l'objet d'un abonnement.

## <a name="implementing-an-interface-event"></a>Implémentation d'un évènement d'interface

Lorsque vous développez des composants d'interface utilisateur, vous commencez souvent par créer un formulaire ou un contrôle qui héritent d'un formulaire ou d'un contrôle existant. Les événements sont souvent définis dans une interface, et, dans ce cas, vous devez implémenter l'interface pour implémenter l'événement. L'interface `System.ComponentModel.INotifyPropertyChanged` définit un seul événement `System.ComponentModel.INotifyPropertyChanged.PropertyChanged`. Le code suivant illustre comment implémenter l'événement défini par cette interface héritée :

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

Si vous souhaitez raccorder l'événement dans le constructeur, le code est un peu plus complexe, car la connexion d'événements doit être dans un bloc `then` dans un constructeur supplémentaire, comme dans l'exemple suivant :

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

## <a name="see-also"></a>Voir aussi

- [Members](index.md) (Membres)
- [Gestion et déclenchement d'événements](../../../standard/events/index.md)
- [Expressions lambda : `fun` mot clé](../functions/lambda-expressions-the-fun-keyword.md)
