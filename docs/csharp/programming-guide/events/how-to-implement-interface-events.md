---
title: Comment mettre en œuvre des événements d’interface - Guide de programmation C
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
ms.openlocfilehash: 8c0d221ef1272a43e2682ef2af3fa37d2d12d35e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167478"
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a>Comment implémenter des événements d’interface (Guide de programmation C)
Une [interface](../../language-reference/keywords/interface.md) peut déclarer un [événement](../../language-reference/keywords/event.md). L’exemple suivant montre comment implémenter des événements d’interface dans une classe. En gros, les règles sont les mêmes que quand vous implémentez une propriété ou une méthode d’interface.  
  
## <a name="to-implement-interface-events-in-a-class"></a>Pour implémenter des événements d’interface dans une classe  
  
Déclarez l’événement dans votre classe, puis appelez-le aux emplacements appropriés.  
  
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
  
## <a name="example"></a> Exemple  
L’exemple suivant montre comment gérer la situation peu courante dans laquelle votre classe hérite de plusieurs interfaces et chaque interface a un événement ayant le même nom. Dans ce cas, vous devez fournir une implémentation d’interface explicite pour au moins l’un des événements. Quand vous écrivez une implémentation d’interface explicite pour un événement, vous devez également écrire les accesseurs d’événement `add` et `remove`. Normalement, ces éléments sont fournis par le compilateur, mais dans le cas en question le compilateur ne peut pas les fournir.  
  
En fournissant vos propres accesseurs, vous pouvez spécifier si les deux événements sont représentés par le même événement dans votre classe ou par des événements différents. Par exemple, si les événements doivent être déclenchés à des moments différents en fonction des spécifications de l’interface, vous pouvez associer chaque événement à une implémentation distincte dans votre classe. Dans l’exemple suivant, les abonnés déterminent l’événement `OnDraw` qu’il recevront en effectuant un cast de la référence de la forme en `IShape` ou `IDrawingObject`.  
  
 [!code-csharp[csProgGuideEvents#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#10)]
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Événements](./index.md)
- [Délégués](../delegates/index.md)
- [Mise en œuvre explicite de l’interface](../interfaces/explicit-interface-implementation.md)
- [Comment déclencher des événements de la classe de base dans les classes dérivées](./how-to-raise-base-class-events-in-derived-classes.md)
