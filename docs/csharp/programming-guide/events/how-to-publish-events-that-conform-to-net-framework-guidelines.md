---
title: Publier des événements conformes aux instructions .NET-Guide de programmation C#
ms.date: 05/26/2020
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: df2f643f867b93b74d04d8fbd673df545c28938e
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240744"
---
# <a name="how-to-publish-events-that-conform-to-net-guidelines-c-programming-guide"></a><span data-ttu-id="5f644-102">Comment publier des événements conformes aux instructions .NET (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="5f644-102">How to publish events that conform to .NET Guidelines (C# Programming Guide)</span></span>

<span data-ttu-id="5f644-103">La procédure suivante montre comment ajouter des événements qui suivent le modèle .NET standard à vos classes et structures.</span><span class="sxs-lookup"><span data-stu-id="5f644-103">The following procedure demonstrates how to add events that follow the standard .NET pattern to your classes and structs.</span></span> <span data-ttu-id="5f644-104">Tous les événements de la bibliothèque de classes .NET Framework sont basés sur le délégué <xref:System.EventHandler>, qui est défini comme suit :</span><span class="sxs-lookup"><span data-stu-id="5f644-104">All events in the .NET Framework class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>

```csharp
public delegate void EventHandler(object sender, EventArgs e);
```

> [!NOTE]
> <span data-ttu-id="5f644-105">.NET Framework 2,0 introduit une version générique de ce délégué, <xref:System.EventHandler%601> .</span><span class="sxs-lookup"><span data-stu-id="5f644-105">.NET Framework 2.0 introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="5f644-106">Les exemples suivants montrent comment utiliser les deux versions.</span><span class="sxs-lookup"><span data-stu-id="5f644-106">The following examples show how to use both versions.</span></span>

<span data-ttu-id="5f644-107">Bien que les événements dans les classes que vous définissez puissent être basés sur n’importe quel type délégué valide, même les délégués qui retournent une valeur, il est généralement recommandé de baser vos événements sur le modèle .NET à l’aide de <xref:System.EventHandler> , comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="5f644-107">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the .NET pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>

<span data-ttu-id="5f644-108">Le nom `EventHandler` peut entraîner un peu de confusion, car il ne gère pas réellement l’événement.</span><span class="sxs-lookup"><span data-stu-id="5f644-108">The name `EventHandler` can lead to a bit of confusion as it doesn't actually handle the event.</span></span> <span data-ttu-id="5f644-109">Le <xref:System.EventHandler> générique et <xref:System.EventHandler%601> sont des types délégués.</span><span class="sxs-lookup"><span data-stu-id="5f644-109">The <xref:System.EventHandler>, and generic <xref:System.EventHandler%601> are delegate types.</span></span> <span data-ttu-id="5f644-110">Une méthode ou une expression lambda dont la signature correspond à la définition de délégué est le *Gestionnaire d’événements* et sera appelée lorsque l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="5f644-110">A method or lambda expression whose signature matches the delegate definition is the *event handler* and will be invoked when the event is raised.</span></span>

## <a name="publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="5f644-111">Publier des événements basés sur le modèle EventHandler</span><span class="sxs-lookup"><span data-stu-id="5f644-111">Publish events based on the EventHandler pattern</span></span>

1. <span data-ttu-id="5f644-112">(Ignorez cette étape et passez à l’étape 3A si vous n’avez pas besoin d’envoyer des données personnalisées avec votre événement.) Déclarez la classe pour vos données personnalisées au niveau d’une étendue qui est visible à la fois pour vos classes de serveur de publication et d’abonné.</span><span class="sxs-lookup"><span data-stu-id="5f644-112">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="5f644-113">Ajoutez ensuite les membres nécessaires pour contenir vos données d’événement personnalisées.</span><span class="sxs-lookup"><span data-stu-id="5f644-113">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="5f644-114">Dans cet exemple, une simple chaîne est retournée.</span><span class="sxs-lookup"><span data-stu-id="5f644-114">In this example, a simple string is returned.</span></span>

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

2. <span data-ttu-id="5f644-115">(Ignorez cette étape si vous utilisez la version générique de <xref:System.EventHandler%601> .) Déclarez un délégué dans votre classe de publication.</span><span class="sxs-lookup"><span data-stu-id="5f644-115">(Skip this step if you are using the generic version of <xref:System.EventHandler%601>.) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="5f644-116">Donnez-lui un nom qui se termine par `EventHandler` .</span><span class="sxs-lookup"><span data-stu-id="5f644-116">Give it a name that ends with `EventHandler`.</span></span> <span data-ttu-id="5f644-117">Le deuxième paramètre spécifie votre `EventArgs` type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="5f644-117">The second parameter specifies your custom `EventArgs` type.</span></span>

    ```csharp
    public delegate void CustomEventHandler(object sender, CustomEventArgs args);
    ```

3. <span data-ttu-id="5f644-118">Déclarez l’événement dans votre classe de publication en effectuant l’une des étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="5f644-118">Declare the event in your publishing class by using one of the following steps.</span></span>

    1. <span data-ttu-id="5f644-119">Si vous n’avez aucune classe EventArgs personnalisée, votre type d’événement sera le délégué EventHandler non générique.</span><span class="sxs-lookup"><span data-stu-id="5f644-119">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="5f644-120">Il est inutile de déclarer le délégué, car il l’est déjà dans l’espace de noms <xref:System> inclus au moment où vous créez votre projet C#.</span><span class="sxs-lookup"><span data-stu-id="5f644-120">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="5f644-121">Ajoutez le code suivant à votre classe de serveur de publication.</span><span class="sxs-lookup"><span data-stu-id="5f644-121">Add the following code to your publisher class.</span></span>

        ```csharp
        public event EventHandler RaiseCustomEvent;
        ```

    2. <span data-ttu-id="5f644-122">Si vous utilisez la version non générique de <xref:System.EventHandler> et que vous avez une classe personnalisée dérivée de <xref:System.EventArgs>, déclarez votre événement à l’intérieur de votre classe de publication et utilisez votre délégué de l’étape 2 comme type.</span><span class="sxs-lookup"><span data-stu-id="5f644-122">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>

        ```csharp
        public event CustomEventHandler RaiseCustomEvent;
        ```

    3. <span data-ttu-id="5f644-123">Si vous utilisez la version générique, vous n’avez pas besoin de délégué personnalisé.</span><span class="sxs-lookup"><span data-stu-id="5f644-123">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="5f644-124">Au lieu de cela, dans votre classe de publication, vous spécifiez votre type d’événement en tant que `EventHandler<CustomEventArgs>`, en insérant le nom de votre propre classe entre les crochets.</span><span class="sxs-lookup"><span data-stu-id="5f644-124">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>

        ```csharp
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;
        ```

## <a name="example"></a><span data-ttu-id="5f644-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="5f644-125">Example</span></span>

<span data-ttu-id="5f644-126">L’exemple suivant est une illustration des étapes précédentes avec l’utilisation d’une classe EventArgs personnalisée et de <xref:System.EventHandler%601> comme type d’événement.</span><span class="sxs-lookup"><span data-stu-id="5f644-126">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>

[!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]

## <a name="see-also"></a><span data-ttu-id="5f644-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f644-127">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="5f644-128">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="5f644-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5f644-129">Événements</span><span class="sxs-lookup"><span data-stu-id="5f644-129">Events</span></span>](index.md)
- [<span data-ttu-id="5f644-130">Délégués</span><span class="sxs-lookup"><span data-stu-id="5f644-130">Delegates</span></span>](../delegates/index.md)
