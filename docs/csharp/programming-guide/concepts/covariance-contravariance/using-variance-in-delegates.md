---
title: Utilisation de la variance dans les délégués (C#)
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 83e86e760edb17f6d9ae61864c154062d41416e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169764"
---
# <a name="using-variance-in-delegates-c"></a><span data-ttu-id="48038-102">Utilisation de la variance dans les délégués (C#)</span><span class="sxs-lookup"><span data-stu-id="48038-102">Using Variance in Delegates (C#)</span></span>
<span data-ttu-id="48038-103">Quand vous assignez une méthode à un délégué, la *covariance* et la *contravariance* offrent une grande flexibilité pour la mise en correspondance d’un type délégué avec une signature de méthode.</span><span class="sxs-lookup"><span data-stu-id="48038-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="48038-104">La covariance permet à une méthode d’avoir un type de retour qui est plus dérivé que celui défini dans le délégué.</span><span class="sxs-lookup"><span data-stu-id="48038-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="48038-105">La contravariance autorise une méthode qui a des types de paramètres moins dérivés que ceux du type délégué.</span><span class="sxs-lookup"><span data-stu-id="48038-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="48038-106">Exemple 1 : Covariance</span><span class="sxs-lookup"><span data-stu-id="48038-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="48038-107">Description</span><span class="sxs-lookup"><span data-stu-id="48038-107">Description</span></span>  
 <span data-ttu-id="48038-108">Cet exemple montre comment vous pouvez utiliser des délégués avec des méthodes ayant des types de retour dérivés du type de retour dans la signature du délégué.</span><span class="sxs-lookup"><span data-stu-id="48038-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="48038-109">Le type de données retourné par `DogsHandler` est `Dogs`, qui dérive du type `Mammals` défini dans le délégué.</span><span class="sxs-lookup"><span data-stu-id="48038-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="48038-110">Code</span><span class="sxs-lookup"><span data-stu-id="48038-110">Code</span></span>  
  
```csharp  
class Mammals {}  
class Dogs : Mammals {}  
  
class Program  
{  
    // Define the delegate.  
    public delegate Mammals HandlerMethod();  
  
    public static Mammals MammalsHandler()  
    {  
        return null;  
    }  
  
    public static Dogs DogsHandler()  
    {  
        return null;  
    }  
  
    static void Test()  
    {  
        HandlerMethod handlerMammals = MammalsHandler;  
  
        // Covariance enables this assignment.  
        HandlerMethod handlerDogs = DogsHandler;  
    }  
}  
```  
  
## <a name="example-2-contravariance"></a><span data-ttu-id="48038-111">Exemple 2 : Contravariance</span><span class="sxs-lookup"><span data-stu-id="48038-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="48038-112">Description</span><span class="sxs-lookup"><span data-stu-id="48038-112">Description</span></span>

<span data-ttu-id="48038-113">Cet exemple montre comment vous pouvez utiliser des délégués avec des méthodes ayant des paramètres dont les types sont des types de base du type de paramètre de signature de délégué.</span><span class="sxs-lookup"><span data-stu-id="48038-113">This example demonstrates how delegates can be used with methods that have parameters whose types are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="48038-114">Avec la contravariance, vous pouvez maintenant utiliser un gestionnaire d’événements plutôt que des gestionnaires distincts.</span><span class="sxs-lookup"><span data-stu-id="48038-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="48038-115">L’exemple suivant utilise deux délégués :</span><span class="sxs-lookup"><span data-stu-id="48038-115">The following example makes use of two delegates:</span></span>

- <span data-ttu-id="48038-116">Un délégué <xref:System.Windows.Forms.KeyEventHandler> qui définit la signature de l’événement [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown).</span><span class="sxs-lookup"><span data-stu-id="48038-116">A <xref:System.Windows.Forms.KeyEventHandler> delegate that defines the signature of the [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) event.</span></span> <span data-ttu-id="48038-117">Sa signature est :</span><span class="sxs-lookup"><span data-stu-id="48038-117">Its signature is:</span></span>

   ```csharp
   public delegate void KeyEventHandler(object sender, KeyEventArgs e)
   ```

- <span data-ttu-id="48038-118">Un délégué <xref:System.Windows.Forms.MouseEventHandler> qui définit la signature de l’événement [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown).</span><span class="sxs-lookup"><span data-stu-id="48038-118">A <xref:System.Windows.Forms.MouseEventHandler> delegate that defines the signature of the [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) event.</span></span> <span data-ttu-id="48038-119">Sa signature est :</span><span class="sxs-lookup"><span data-stu-id="48038-119">Its signature is:</span></span>

   ```csharp
   public delegate void MouseEventHandler(object sender, MouseEventArgs e)
   ```

<span data-ttu-id="48038-120">L’exemple définit un gestionnaire d’événements avec un paramètre <xref:System.EventArgs> et s’en sert pour gérer les événements `Button.KeyDown` et `Button.MouseClick`.</span><span class="sxs-lookup"><span data-stu-id="48038-120">The example defines an event handler with an <xref:System.EventArgs> parameter and uses it to handle both the `Button.KeyDown` and `Button.MouseClick` events.</span></span> <span data-ttu-id="48038-121">C’est possible parce que <xref:System.EventArgs> est un type de base de <xref:System.Windows.Forms.KeyEventArgs> et <xref:System.Windows.Forms.MouseEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="48038-121">It can do this because <xref:System.EventArgs> is a base type of both <xref:System.Windows.Forms.KeyEventArgs>  and <xref:System.Windows.Forms.MouseEventArgs>.</span></span>
  
### <a name="code"></a><span data-ttu-id="48038-122">Code</span><span class="sxs-lookup"><span data-stu-id="48038-122">Code</span></span>  
  
```csharp  
// Event handler that accepts a parameter of the EventArgs type.  
private void MultiHandler(object sender, System.EventArgs e)  
{  
    label1.Text = System.DateTime.Now.ToString();  
}  
  
public Form1()  
{  
    InitializeComponent();  
  
    // You can use a method that has an EventArgs parameter,  
    // although the event expects the KeyEventArgs parameter.  
    this.button1.KeyDown += this.MultiHandler;  
  
    // You can use the same method
    // for an event that expects the MouseEventArgs parameter.  
    this.button1.MouseClick += this.MultiHandler;  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="48038-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48038-123">See also</span></span>

- [<span data-ttu-id="48038-124">Variance dans les délégués (C#)</span><span class="sxs-lookup"><span data-stu-id="48038-124">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)
- [<span data-ttu-id="48038-125">Utilisation de la variance pour les délégués génériques Func et Action (C#)</span><span class="sxs-lookup"><span data-stu-id="48038-125">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
