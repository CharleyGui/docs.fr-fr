---
title: Publier des événements conformes aux instructions .NET-Guide de programmation C#
description: Découvrez comment publier des événements conformes aux instructions .NET. Tous les événements de la bibliothèque de classes .NET sont basés sur le délégué EventHandler.
ms.date: 05/26/2020
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 8cc8b0a9fdaeeb6ab6290630c5d78044c2696b9a
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89466168"
---
# <a name="how-to-publish-events-that-conform-to-net-guidelines-c-programming-guide"></a><span data-ttu-id="9d57c-104">Comment publier des événements conformes aux instructions .NET (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="9d57c-104">How to publish events that conform to .NET Guidelines (C# Programming Guide)</span></span>

<span data-ttu-id="9d57c-105">La procédure suivante montre comment ajouter des événements qui suivent le modèle .NET standard à vos classes et structures.</span><span class="sxs-lookup"><span data-stu-id="9d57c-105">The following procedure demonstrates how to add events that follow the standard .NET pattern to your classes and structs.</span></span> <span data-ttu-id="9d57c-106">Tous les événements de la bibliothèque de classes .NET sont basés sur le <xref:System.EventHandler> délégué, qui est défini comme suit :</span><span class="sxs-lookup"><span data-stu-id="9d57c-106">All events in the .NET class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>

```csharp
public delegate void EventHandler(object sender, EventArgs e);
```

> [!NOTE]
> <span data-ttu-id="9d57c-107">.NET Framework 2,0 introduit une version générique de ce délégué, <xref:System.EventHandler%601> .</span><span class="sxs-lookup"><span data-stu-id="9d57c-107">.NET Framework 2.0 introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="9d57c-108">Les exemples suivants montrent comment utiliser les deux versions.</span><span class="sxs-lookup"><span data-stu-id="9d57c-108">The following examples show how to use both versions.</span></span>

<span data-ttu-id="9d57c-109">Bien que les événements dans les classes que vous définissez puissent être basés sur n’importe quel type délégué valide, même les délégués qui retournent une valeur, il est généralement recommandé de baser vos événements sur le modèle .NET à l’aide de <xref:System.EventHandler> , comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9d57c-109">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the .NET pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>

<span data-ttu-id="9d57c-110">Le nom `EventHandler` peut entraîner un peu de confusion, car il ne gère pas réellement l’événement.</span><span class="sxs-lookup"><span data-stu-id="9d57c-110">The name `EventHandler` can lead to a bit of confusion as it doesn't actually handle the event.</span></span> <span data-ttu-id="9d57c-111">Le <xref:System.EventHandler> générique et <xref:System.EventHandler%601> sont des types délégués.</span><span class="sxs-lookup"><span data-stu-id="9d57c-111">The <xref:System.EventHandler>, and generic <xref:System.EventHandler%601> are delegate types.</span></span> <span data-ttu-id="9d57c-112">Une méthode ou une expression lambda dont la signature correspond à la définition de délégué est le *Gestionnaire d’événements* et sera appelée lorsque l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="9d57c-112">A method or lambda expression whose signature matches the delegate definition is the *event handler* and will be invoked when the event is raised.</span></span>

## <a name="publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="9d57c-113">Publier des événements basés sur le modèle EventHandler</span><span class="sxs-lookup"><span data-stu-id="9d57c-113">Publish events based on the EventHandler pattern</span></span>

1. <span data-ttu-id="9d57c-114">(Ignorez cette étape et passez à l’étape 3A si vous n’avez pas besoin d’envoyer des données personnalisées avec votre événement.) Déclarez la classe pour vos données personnalisées au niveau d’une étendue qui est visible à la fois pour vos classes de serveur de publication et d’abonné.</span><span class="sxs-lookup"><span data-stu-id="9d57c-114">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="9d57c-115">Ajoutez ensuite les membres nécessaires pour contenir vos données d’événement personnalisées.</span><span class="sxs-lookup"><span data-stu-id="9d57c-115">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="9d57c-116">Dans cet exemple, une simple chaîne est retournée.</span><span class="sxs-lookup"><span data-stu-id="9d57c-116">In this example, a simple string is returned.</span></span>

    ```csharp
    public class CustomEventArgs : EventArgs
    {
        public CustomEventArgs(string message)
        {
            Message = message;
        }

        public string Message { get; set; }
    }
    ```

2. <span data-ttu-id="9d57c-117">(Ignorez cette étape si vous utilisez la version générique de <xref:System.EventHandler%601> .) Déclarez un délégué dans votre classe de publication.</span><span class="sxs-lookup"><span data-stu-id="9d57c-117">(Skip this step if you are using the generic version of <xref:System.EventHandler%601>.) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="9d57c-118">Donnez-lui un nom qui se termine par `EventHandler` .</span><span class="sxs-lookup"><span data-stu-id="9d57c-118">Give it a name that ends with `EventHandler`.</span></span> <span data-ttu-id="9d57c-119">Le deuxième paramètre spécifie votre `EventArgs` type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="9d57c-119">The second parameter specifies your custom `EventArgs` type.</span></span>

    ```csharp
    public delegate void CustomEventHandler(object sender, CustomEventArgs args);
    ```

3. <span data-ttu-id="9d57c-120">Déclarez l’événement dans votre classe de publication en effectuant l’une des étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="9d57c-120">Declare the event in your publishing class by using one of the following steps.</span></span>

    1. <span data-ttu-id="9d57c-121">Si vous n’avez aucune classe EventArgs personnalisée, votre type d’événement sera le délégué EventHandler non générique.</span><span class="sxs-lookup"><span data-stu-id="9d57c-121">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="9d57c-122">Il est inutile de déclarer le délégué, car il l’est déjà dans l’espace de noms <xref:System> inclus au moment où vous créez votre projet C#.</span><span class="sxs-lookup"><span data-stu-id="9d57c-122">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="9d57c-123">Ajoutez le code suivant à votre classe de serveur de publication.</span><span class="sxs-lookup"><span data-stu-id="9d57c-123">Add the following code to your publisher class.</span></span>

        ```csharp
        public event EventHandler RaiseCustomEvent;
        ```

    2. <span data-ttu-id="9d57c-124">Si vous utilisez la version non générique de <xref:System.EventHandler> et que vous avez une classe personnalisée dérivée de <xref:System.EventArgs>, déclarez votre événement à l’intérieur de votre classe de publication et utilisez votre délégué de l’étape 2 comme type.</span><span class="sxs-lookup"><span data-stu-id="9d57c-124">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>

        ```csharp
        public event CustomEventHandler RaiseCustomEvent;
        ```

    3. <span data-ttu-id="9d57c-125">Si vous utilisez la version générique, vous n’avez pas besoin de délégué personnalisé.</span><span class="sxs-lookup"><span data-stu-id="9d57c-125">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="9d57c-126">Au lieu de cela, dans votre classe de publication, vous spécifiez votre type d’événement en tant que `EventHandler<CustomEventArgs>`, en insérant le nom de votre propre classe entre les crochets.</span><span class="sxs-lookup"><span data-stu-id="9d57c-126">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>

        ```csharp
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;
        ```

## <a name="example"></a><span data-ttu-id="9d57c-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="9d57c-127">Example</span></span>

<span data-ttu-id="9d57c-128">L’exemple suivant est une illustration des étapes précédentes avec l’utilisation d’une classe EventArgs personnalisée et de <xref:System.EventHandler%601> comme type d’événement.</span><span class="sxs-lookup"><span data-stu-id="9d57c-128">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>

[!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]

## <a name="see-also"></a><span data-ttu-id="9d57c-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d57c-129">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="9d57c-130">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="9d57c-130">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9d57c-131">Événements</span><span class="sxs-lookup"><span data-stu-id="9d57c-131">Events</span></span>](index.md)
- [<span data-ttu-id="9d57c-132">Délégués</span><span class="sxs-lookup"><span data-stu-id="9d57c-132">Delegates</span></span>](../delegates/index.md)
