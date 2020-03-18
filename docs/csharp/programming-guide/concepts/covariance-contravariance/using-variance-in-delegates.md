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
# <a name="using-variance-in-delegates-c"></a>Utilisation de la variance dans les délégués (C#)
Quand vous assignez une méthode à un délégué, la *covariance* et la *contravariance* offrent une grande flexibilité pour la mise en correspondance d’un type délégué avec une signature de méthode. La covariance permet à une méthode d’avoir un type de retour qui est plus dérivé que celui défini dans le délégué. La contravariance autorise une méthode qui a des types de paramètres moins dérivés que ceux du type délégué.  
  
## <a name="example-1-covariance"></a>Exemple 1 : Covariance  
  
### <a name="description"></a>Description  
 Cet exemple montre comment vous pouvez utiliser des délégués avec des méthodes ayant des types de retour dérivés du type de retour dans la signature du délégué. Le type de données retourné par `DogsHandler` est `Dogs`, qui dérive du type `Mammals` défini dans le délégué.  
  
### <a name="code"></a>Code  
  
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
  
## <a name="example-2-contravariance"></a>Exemple 2 : Contravariance  
  
### <a name="description"></a>Description

Cet exemple montre comment vous pouvez utiliser des délégués avec des méthodes ayant des paramètres dont les types sont des types de base du type de paramètre de signature de délégué. Avec la contravariance, vous pouvez maintenant utiliser un gestionnaire d’événements plutôt que des gestionnaires distincts. L’exemple suivant utilise deux délégués :

- Un délégué <xref:System.Windows.Forms.KeyEventHandler> qui définit la signature de l’événement [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown). Sa signature est :

   ```csharp
   public delegate void KeyEventHandler(object sender, KeyEventArgs e)
   ```

- Un délégué <xref:System.Windows.Forms.MouseEventHandler> qui définit la signature de l’événement [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown). Sa signature est :

   ```csharp
   public delegate void MouseEventHandler(object sender, MouseEventArgs e)
   ```

L’exemple définit un gestionnaire d’événements avec un paramètre <xref:System.EventArgs> et s’en sert pour gérer les événements `Button.KeyDown` et `Button.MouseClick`. C’est possible parce que <xref:System.EventArgs> est un type de base de <xref:System.Windows.Forms.KeyEventArgs> et <xref:System.Windows.Forms.MouseEventArgs>.
  
### <a name="code"></a>Code  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Variance dans les délégués (C#)](./variance-in-delegates.md)
- [Utilisation de la variance pour les délégués génériques Func et Action (C#)](./using-variance-for-func-and-action-generic-delegates.md)
