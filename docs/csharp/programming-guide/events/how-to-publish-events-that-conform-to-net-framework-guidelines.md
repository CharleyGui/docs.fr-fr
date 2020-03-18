---
title: Comment publier des événements conformes aux lignes directrices du cadre .NET - Guide de programmation C
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 90c079b9f7dbf2a1d963b7eee4447145d7a10432
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167531"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a><span data-ttu-id="08a5c-102">Comment publier des événements conformes aux lignes directrices du cadre .NET (Guide de programmation C)</span><span class="sxs-lookup"><span data-stu-id="08a5c-102">How to publish events that conform to .NET Framework Guidelines (C# Programming Guide)</span></span>
<span data-ttu-id="08a5c-103">La procédure suivante montre comment ajouter à vos classes et structs des événements qui respectent le modèle .NET Framework standard.</span><span class="sxs-lookup"><span data-stu-id="08a5c-103">The following procedure demonstrates how to add events that follow the standard .NET Framework pattern to your classes and structs.</span></span> <span data-ttu-id="08a5c-104">Tous les événements de la bibliothèque de classes .NET Framework sont basés sur le délégué <xref:System.EventHandler>, qui est défini comme suit :</span><span class="sxs-lookup"><span data-stu-id="08a5c-104">All events in the .NET Framework class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
> <span data-ttu-id="08a5c-105">.NET Framework 2.0 comprend une version générique de ce délégué : <xref:System.EventHandler%601>.</span><span class="sxs-lookup"><span data-stu-id="08a5c-105">The .NET Framework 2.0 introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="08a5c-106">Les exemples suivants montrent comment utiliser les deux versions.</span><span class="sxs-lookup"><span data-stu-id="08a5c-106">The following examples show how to use both versions.</span></span>  
  
 <span data-ttu-id="08a5c-107">Bien que les événements des classes que vous définissez puissent être basés sur n’importe quel type délégué valide, même les délégués qui retournent une valeur, il est généralement recommandé de baser les événements sur le modèle .NET Framework à l’aide de <xref:System.EventHandler>, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="08a5c-107">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the .NET Framework pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="08a5c-108">Pour publier des événements basés sur le modèle EventHandler</span><span class="sxs-lookup"><span data-stu-id="08a5c-108">To publish events based on the EventHandler pattern</span></span>  
  
1. <span data-ttu-id="08a5c-109">(Passez cette étape et allez à l’étape 3a si vous n’avez pas à envoyer des données personnalisées avec votre événement.) Déclarez la classe pour vos données personnalisées à une portée qui est visible à la fois pour vos classes d’éditeur et d’abonnés.</span><span class="sxs-lookup"><span data-stu-id="08a5c-109">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="08a5c-110">Ajoutez ensuite les membres nécessaires pour contenir vos données d’événement personnalisées.</span><span class="sxs-lookup"><span data-stu-id="08a5c-110">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="08a5c-111">Dans cet exemple, une simple chaîne est retournée.</span><span class="sxs-lookup"><span data-stu-id="08a5c-111">In this example, a simple string is returned.</span></span>  
  
    ```csharp  
    public class CustomEventArgs : EventArgs  
    {  
        public CustomEventArgs(string s)  
        {  
            msg = s;  
        }  
        private string msg;  
        public string Message  
        {  
            get { return msg; }  
        }
    }  
    ```  
  
2. <span data-ttu-id="08a5c-112">(Passer cette étape si vous utilisez <xref:System.EventHandler%601> la version générique de .) Déclarez un délégué dans votre classe d’édition.</span><span class="sxs-lookup"><span data-stu-id="08a5c-112">(Skip this step if you are using the generic version of <xref:System.EventHandler%601> .) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="08a5c-113">Donnez-lui un nom qui se termine par *EventHandler*.</span><span class="sxs-lookup"><span data-stu-id="08a5c-113">Give it a name that ends with *EventHandler*.</span></span> <span data-ttu-id="08a5c-114">Le deuxième paramètre spécifie votre type EventArgs personnalisé.</span><span class="sxs-lookup"><span data-stu-id="08a5c-114">The second parameter specifies your custom EventArgs type.</span></span>  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3. <span data-ttu-id="08a5c-115">Déclarez l’événement dans votre classe de publication en effectuant l’une des étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="08a5c-115">Declare the event in your publishing class by using one of the following steps.</span></span>  
  
    1. <span data-ttu-id="08a5c-116">Si vous n’avez aucune classe EventArgs personnalisée, votre type d’événement sera le délégué EventHandler non générique.</span><span class="sxs-lookup"><span data-stu-id="08a5c-116">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="08a5c-117">Il est inutile de déclarer le délégué, car il l’est déjà dans l’espace de noms <xref:System> inclus au moment où vous créez votre projet C#.</span><span class="sxs-lookup"><span data-stu-id="08a5c-117">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="08a5c-118">Ajoutez le code suivant à votre classe de serveur de publication.</span><span class="sxs-lookup"><span data-stu-id="08a5c-118">Add the following code to your publisher class.</span></span>  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2. <span data-ttu-id="08a5c-119">Si vous utilisez la version non générique de <xref:System.EventHandler> et que vous avez une classe personnalisée dérivée de <xref:System.EventArgs>, déclarez votre événement à l’intérieur de votre classe de publication et utilisez votre délégué de l’étape 2 comme type.</span><span class="sxs-lookup"><span data-stu-id="08a5c-119">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3. <span data-ttu-id="08a5c-120">Si vous utilisez la version générique, vous n’avez pas besoin de délégué personnalisé.</span><span class="sxs-lookup"><span data-stu-id="08a5c-120">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="08a5c-121">Au lieu de cela, dans votre classe de publication, vous spécifiez votre type d’événement en tant que `EventHandler<CustomEventArgs>`, en insérant le nom de votre propre classe entre les crochets.</span><span class="sxs-lookup"><span data-stu-id="08a5c-121">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a><span data-ttu-id="08a5c-122"> Exemple</span><span class="sxs-lookup"><span data-stu-id="08a5c-122">Example</span></span>  
 <span data-ttu-id="08a5c-123">L’exemple suivant est une illustration des étapes précédentes avec l’utilisation d’une classe EventArgs personnalisée et de <xref:System.EventHandler%601> comme type d’événement.</span><span class="sxs-lookup"><span data-stu-id="08a5c-123">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>  
  
 [!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]  
  
## <a name="see-also"></a><span data-ttu-id="08a5c-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08a5c-124">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="08a5c-125">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="08a5c-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="08a5c-126">Événements</span><span class="sxs-lookup"><span data-stu-id="08a5c-126">Events</span></span>](./index.md)
- [<span data-ttu-id="08a5c-127">Délégués</span><span class="sxs-lookup"><span data-stu-id="08a5c-127">Delegates</span></span>](../delegates/index.md)
