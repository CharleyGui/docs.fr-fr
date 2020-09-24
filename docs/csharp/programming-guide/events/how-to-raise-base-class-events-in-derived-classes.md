---
title: Comment déclencher des événements de classe de base dans des classes dérivées-Guide de programmation C#
description: Découvrez comment déclencher des événements de classe de base dans des classes dérivées. Consultez un exemple de code et affichez des ressources supplémentaires disponibles.
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: b9708876e7d46072439ae498fd551a7b3b23a29e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167520"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a><span data-ttu-id="3c130-104">Comment déclencher des événements de classe de base dans des classes dérivées (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="3c130-104">How to raise base class events in derived classes (C# Programming Guide)</span></span>

<span data-ttu-id="3c130-105">L’exemple suivant montre la méthode standard employée pour déclarer des événements dans une classe de base pour qu’ils puissent être déclenchés à partir de classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="3c130-105">The following simple example shows the standard way to declare events in a base class so that they can also be raised from derived classes.</span></span> <span data-ttu-id="3c130-106">Ce modèle est largement utilisé dans les classes Windows Forms dans les bibliothèques de classes .NET.</span><span class="sxs-lookup"><span data-stu-id="3c130-106">This pattern is used extensively in Windows Forms classes in the .NET class libraries.</span></span>  
  
 <span data-ttu-id="3c130-107">Lorsque vous créez une classe qui peut être utilisée comme classe de base pour d’autres classes, tenez compte du fait que les événements constituent un type spécial de délégué qui ne peut être appelé qu’à partir de la classe qui les a déclarés.</span><span class="sxs-lookup"><span data-stu-id="3c130-107">When you create a class that can be used as a base class for other classes, you should consider the fact that events are a special type of delegate that can only be invoked from within the class that declared them.</span></span> <span data-ttu-id="3c130-108">Les classes dérivées ne peuvent pas appeler directement les événements qui sont déclarés dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="3c130-108">Derived classes cannot directly invoke events that are declared within the base class.</span></span> <span data-ttu-id="3c130-109">Même si vous pouvez avoir besoin d’un événement qui ne peut être déclenché que par la classe de base, la plupart du temps, vous devez permettre à la classe dérivée d’appeler les événements de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="3c130-109">Although sometimes you may want an event that can only be raised by the base class, most of the time, you should enable the derived class to invoke base class events.</span></span> <span data-ttu-id="3c130-110">Pour ce faire, vous pouvez créer une méthode d’appel protégée dans la classe de base qui encapsule l’événement.</span><span class="sxs-lookup"><span data-stu-id="3c130-110">To do this, you can create a protected invoking method in the base class that wraps the event.</span></span> <span data-ttu-id="3c130-111">En appelant ou en substituant cette méthode d’appel, les classes dérivées peuvent appeler indirectement l’événement.</span><span class="sxs-lookup"><span data-stu-id="3c130-111">By calling or overriding this invoking method, derived classes can invoke the event indirectly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3c130-112">Ne déclarez pas les événements virtuels dans une classe de base et substituez-les dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="3c130-112">Do not declare virtual events in a base class and override them in a derived class.</span></span> <span data-ttu-id="3c130-113">Le compilateur C# ne gère pas correctement ce type d’événement et il n’est pas possible de prévoir si un abonné de l’événement dérivé s’abonnera à l’événement de classe de base.</span><span class="sxs-lookup"><span data-stu-id="3c130-113">The C# compiler does not handle these correctly and it is unpredictable whether a subscriber to the derived event will actually be subscribing to the base class event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c130-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="3c130-114">Example</span></span>  

 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3c130-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c130-115">See also</span></span>

- [<span data-ttu-id="3c130-116">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="3c130-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3c130-117">Événements</span><span class="sxs-lookup"><span data-stu-id="3c130-117">Events</span></span>](./index.md)
- [<span data-ttu-id="3c130-118">Délégués</span><span class="sxs-lookup"><span data-stu-id="3c130-118">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="3c130-119">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="3c130-119">Access Modifiers</span></span>](../classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="3c130-120">Création de gestionnaires d'événements dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3c130-120">Creating Event Handlers in Windows Forms</span></span>](/dotnet/desktop/winforms/creating-event-handlers-in-windows-forms)
