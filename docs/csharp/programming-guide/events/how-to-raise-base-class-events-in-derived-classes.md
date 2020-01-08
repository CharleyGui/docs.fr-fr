---
title: Comment déclencher des événements de classe de base dans des C# classes dérivées-Guide de programmation
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: 6176b94b15edccb139ddd7de3101930b505d98a8
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346307"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a><span data-ttu-id="88b39-102">Comment déclencher des événements de classe de base dans desC# classes dérivées (Guide de programmation)</span><span class="sxs-lookup"><span data-stu-id="88b39-102">How to raise base class events in derived classes (C# Programming Guide)</span></span>
<span data-ttu-id="88b39-103">L’exemple suivant montre la méthode standard employée pour déclarer des événements dans une classe de base pour qu’ils puissent être déclenchés à partir de classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="88b39-103">The following simple example shows the standard way to declare events in a base class so that they can also be raised from derived classes.</span></span> <span data-ttu-id="88b39-104">Ce modèle est largement utilisé dans les classes Windows Forms de la bibliothèque de classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="88b39-104">This pattern is used extensively in Windows Forms classes in the .NET Framework class library.</span></span>  
  
 <span data-ttu-id="88b39-105">Lorsque vous créez une classe qui peut être utilisée comme classe de base pour d’autres classes, tenez compte du fait que les événements constituent un type spécial de délégué qui ne peut être appelé qu’à partir de la classe qui les a déclarés.</span><span class="sxs-lookup"><span data-stu-id="88b39-105">When you create a class that can be used as a base class for other classes, you should consider the fact that events are a special type of delegate that can only be invoked from within the class that declared them.</span></span> <span data-ttu-id="88b39-106">Les classes dérivées ne peuvent pas appeler directement les événements qui sont déclarés dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="88b39-106">Derived classes cannot directly invoke events that are declared within the base class.</span></span> <span data-ttu-id="88b39-107">Même si vous pouvez avoir besoin d’un événement qui ne peut être déclenché que par la classe de base, la plupart du temps, vous devez permettre à la classe dérivée d’appeler les événements de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="88b39-107">Although sometimes you may want an event that can only be raised by the base class, most of the time, you should enable the derived class to invoke base class events.</span></span> <span data-ttu-id="88b39-108">Pour ce faire, vous pouvez créer une méthode d’appel protégée dans la classe de base qui encapsule l’événement.</span><span class="sxs-lookup"><span data-stu-id="88b39-108">To do this, you can create a protected invoking method in the base class that wraps the event.</span></span> <span data-ttu-id="88b39-109">En appelant ou en substituant cette méthode d’appel, les classes dérivées peuvent appeler indirectement l’événement.</span><span class="sxs-lookup"><span data-stu-id="88b39-109">By calling or overriding this invoking method, derived classes can invoke the event indirectly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="88b39-110">Ne déclarez pas les événements virtuels dans une classe de base et substituez-les dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="88b39-110">Do not declare virtual events in a base class and override them in a derived class.</span></span> <span data-ttu-id="88b39-111">Le compilateur C# ne gère pas correctement ce type d’événement et il n’est pas possible de prévoir si un abonné de l’événement dérivé s’abonnera à l’événement de classe de base.</span><span class="sxs-lookup"><span data-stu-id="88b39-111">The C# compiler does not handle these correctly and it is unpredictable whether a subscriber to the derived event will actually be subscribing to the base class event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88b39-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="88b39-112">Example</span></span>  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="88b39-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88b39-113">See also</span></span>

- [<span data-ttu-id="88b39-114">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="88b39-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="88b39-115">Événements</span><span class="sxs-lookup"><span data-stu-id="88b39-115">Events</span></span>](./index.md)
- [<span data-ttu-id="88b39-116">Délégués</span><span class="sxs-lookup"><span data-stu-id="88b39-116">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="88b39-117">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="88b39-117">Access Modifiers</span></span>](../classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="88b39-118">Création de gestionnaires d’événements dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="88b39-118">Creating Event Handlers in Windows Forms</span></span>](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
