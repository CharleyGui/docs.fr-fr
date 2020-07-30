---
title: Comment implémenter des événements d’interface-Guide de programmation C#
description: Découvrez comment implémenter des événements d’interface dans une classe. Consultez des exemples de code et affichez des ressources disponibles supplémentaires.
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
ms.openlocfilehash: bd86aed4f8d8ac6e291c11fe441f87ac97593b03
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302124"
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a><span data-ttu-id="16984-104">Comment implémenter des événements d’interface (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="16984-104">How to implement interface events (C# Programming Guide)</span></span>
<span data-ttu-id="16984-105">Une [interface](../../language-reference/keywords/interface.md) peut déclarer un [événement](../../language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="16984-105">An [interface](../../language-reference/keywords/interface.md) can declare an [event](../../language-reference/keywords/event.md).</span></span> <span data-ttu-id="16984-106">L’exemple suivant montre comment implémenter des événements d’interface dans une classe.</span><span class="sxs-lookup"><span data-stu-id="16984-106">The following example shows how to implement interface events in a class.</span></span> <span data-ttu-id="16984-107">En gros, les règles sont les mêmes que quand vous implémentez une propriété ou une méthode d’interface.</span><span class="sxs-lookup"><span data-stu-id="16984-107">Basically the rules are the same as when you implement any interface method or property.</span></span>  
  
## <a name="to-implement-interface-events-in-a-class"></a><span data-ttu-id="16984-108">Pour implémenter des événements d’interface dans une classe</span><span class="sxs-lookup"><span data-stu-id="16984-108">To implement interface events in a class</span></span>  
  
<span data-ttu-id="16984-109">Déclarez l’événement dans votre classe, puis appelez-le aux emplacements appropriés.</span><span class="sxs-lookup"><span data-stu-id="16984-109">Declare the event in your class and then invoke it in the appropriate areas.</span></span>  
  
```csharp
namespace ImplementInterfaceEvents  
{  
    public interface IDrawingObject  
    {  
        event EventHandler ShapeChanged;  
    }  
    public class MyEventArgs : EventArgs
    {  
        // class members  
    }  
    public class Shape : IDrawingObject  
    {  
        public event EventHandler ShapeChanged;  
        void ChangeShape()  
        {  
            // Do something here before the event…  

            OnShapeChanged(new MyEventArgs(/*arguments*/));  

            // or do something here after the event.
        }  
        protected virtual void OnShapeChanged(MyEventArgs e)  
        {  
            ShapeChanged?.Invoke(this, e);  
        }  
    }  

}  
```  
  
## <a name="example"></a><span data-ttu-id="16984-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="16984-110">Example</span></span>  
<span data-ttu-id="16984-111">L’exemple suivant montre comment gérer la situation peu courante dans laquelle votre classe hérite de plusieurs interfaces et chaque interface a un événement ayant le même nom.</span><span class="sxs-lookup"><span data-stu-id="16984-111">The following example shows how to handle the less-common situation in which your class inherits from two or more interfaces and each interface has an event with the same name.</span></span> <span data-ttu-id="16984-112">Dans ce cas, vous devez fournir une implémentation d’interface explicite pour au moins l’un des événements.</span><span class="sxs-lookup"><span data-stu-id="16984-112">In this situation, you must provide an explicit interface implementation for at least one of the events.</span></span> <span data-ttu-id="16984-113">Quand vous écrivez une implémentation d’interface explicite pour un événement, vous devez également écrire les accesseurs d’événement `add` et `remove`.</span><span class="sxs-lookup"><span data-stu-id="16984-113">When you write an explicit interface implementation for an event, you must also write the `add` and `remove` event accessors.</span></span> <span data-ttu-id="16984-114">Normalement, ces éléments sont fournis par le compilateur, mais dans le cas en question le compilateur ne peut pas les fournir.</span><span class="sxs-lookup"><span data-stu-id="16984-114">Normally these are provided by the compiler, but in this case the compiler cannot provide them.</span></span>  
  
<span data-ttu-id="16984-115">En fournissant vos propres accesseurs, vous pouvez spécifier si les deux événements sont représentés par le même événement dans votre classe ou par des événements différents.</span><span class="sxs-lookup"><span data-stu-id="16984-115">By providing your own accessors, you can specify whether the two events are represented by the same event in your class, or by different events.</span></span> <span data-ttu-id="16984-116">Par exemple, si les événements doivent être déclenchés à des moments différents en fonction des spécifications de l’interface, vous pouvez associer chaque événement à une implémentation distincte dans votre classe.</span><span class="sxs-lookup"><span data-stu-id="16984-116">For example, if the events should be raised at different times according to the interface specifications, you can associate each event with a separate implementation in your class.</span></span> <span data-ttu-id="16984-117">Dans l’exemple suivant, les abonnés déterminent l’événement `OnDraw` qu’il recevront en effectuant un cast de la référence de la forme en `IShape` ou `IDrawingObject`.</span><span class="sxs-lookup"><span data-stu-id="16984-117">In the following example, subscribers determine which `OnDraw` event they will receive by casting the shape reference to either an `IShape` or an `IDrawingObject`.</span></span>  
  
 [!code-csharp[csProgGuideEvents#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#10)]
  
## <a name="see-also"></a><span data-ttu-id="16984-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16984-118">See also</span></span>

- [<span data-ttu-id="16984-119">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="16984-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="16984-120">Événements</span><span class="sxs-lookup"><span data-stu-id="16984-120">Events</span></span>](./index.md)
- [<span data-ttu-id="16984-121">Délégués</span><span class="sxs-lookup"><span data-stu-id="16984-121">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="16984-122">Implémentation d'interface explicite</span><span class="sxs-lookup"><span data-stu-id="16984-122">Explicit Interface Implementation</span></span>](../interfaces/explicit-interface-implementation.md)
- [<span data-ttu-id="16984-123">Comment déclencher des événements de la classe de base dans les classes dérivées</span><span class="sxs-lookup"><span data-stu-id="16984-123">How to raise base class events in derived classes</span></span>](./how-to-raise-base-class-events-in-derived-classes.md)
