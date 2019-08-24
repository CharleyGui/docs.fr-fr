---
title: 'Procédure : exposer des propriétés de contrôles constitutifs'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user controls [Windows Forms], exposing constituent controls
- controls [Windows Forms], constituent
- custom controls [Windows Forms], exposing properties
- constituent controls
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
ms.openlocfilehash: f006e42771a5ecc71f6a508fd78d0e2dd8f2d2f2
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015872"
---
# <a name="how-to-expose-properties-of-constituent-controls"></a><span data-ttu-id="cdcd5-102">Procédure : exposer des propriétés de contrôles constitutifs</span><span class="sxs-lookup"><span data-stu-id="cdcd5-102">How to: Expose Properties of Constituent Controls</span></span>
<span data-ttu-id="cdcd5-103">Les contrôles qui composent un contrôle composite sont appelés *contrôles constitutifs*.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-103">The controls that make up a composite control are called *constituent controls*.</span></span> <span data-ttu-id="cdcd5-104">Ces contrôles sont normalement déclarés privés et, par conséquent, ne sont pas accessibles par le développeur.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-104">These controls are normally declared private, and thus cannot be accessed by the developer.</span></span> <span data-ttu-id="cdcd5-105">Si vous souhaitez que les propriétés de ces contrôles soient disponibles pour les futurs utilisateurs, vous devez les exposer à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-105">If you want to make properties of these controls available to future users, you must expose them to the user.</span></span> <span data-ttu-id="cdcd5-106">Une propriété d’un contrôle constitutif est exposée en créant une propriété dans le contrôle utilisateur, et en `get` utilisant `set` les accesseurs et de cette propriété pour appliquer la modification de la propriété privée du contrôle constitutif.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-106">A property of a constituent control is exposed by creating a property in the user control, and using the `get` and `set` accessors of that property to effect the change in the private property of the constituent control.</span></span>

 <span data-ttu-id="cdcd5-107">Imaginez un contrôle utilisateur hypothétique avec un bouton constitutif nommé `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-107">Consider a hypothetical user control with a constituent button named `MyButton`.</span></span> <span data-ttu-id="cdcd5-108">Dans cet exemple, lorsque l’utilisateur demande la `ConstituentButtonBackColor` propriété, la valeur stockée dans <xref:System.Windows.Forms.Control.BackColor%2A> la propriété `MyButton` de est remise.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-108">In this example, when the user requests the `ConstituentButtonBackColor` property, the value stored in the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` is delivered.</span></span> <span data-ttu-id="cdcd5-109">Lorsque l’utilisateur assigne une valeur à cette propriété, cette valeur est passée automatiquement à la <xref:System.Windows.Forms.Control.BackColor%2A> propriété de `MyButton` et le `set` code s’exécute, en modifiant la couleur `MyButton`de.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-109">When the user assigns a value to this property, that value is automatically passed to the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` and the `set` code will execute, changing the color of `MyButton`.</span></span>

 <span data-ttu-id="cdcd5-110">L’exemple suivant montre comment exposer la <xref:System.Windows.Forms.Control.BackColor%2A> propriété du bouton constitutif:</span><span class="sxs-lookup"><span data-stu-id="cdcd5-110">The following example shows how to expose the <xref:System.Windows.Forms.Control.BackColor%2A> property of the constituent button:</span></span>

```vb
Public Property ButtonColor() as System.Drawing.Color
   Get
      Return MyButton.BackColor
   End Get
   Set(Value as System.Drawing.Color)
      MyButton.BackColor = Value
   End Set
End Property
```

```csharp
public Color ButtonColor
{
   get
   {
      return(myButton.BackColor);
   }
   set
   {
      myButton.BackColor = value;
   }
}
```

### <a name="to-expose-a-property-of-a-constituent-control"></a><span data-ttu-id="cdcd5-111">Pour exposer une propriété d’un contrôle constitutif</span><span class="sxs-lookup"><span data-stu-id="cdcd5-111">To expose a property of a constituent control</span></span>

1. <span data-ttu-id="cdcd5-112">Créez une propriété publique pour votre contrôle utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-112">Create a public property for your user control.</span></span>

2. <span data-ttu-id="cdcd5-113">Dans la `get` section de la propriété, écrivez du code qui récupère la valeur de la propriété que vous souhaitez exposer.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-113">In the `get` section of the property, write code that retrieves the value of the property you want to expose.</span></span>

3. <span data-ttu-id="cdcd5-114">Dans la `set` section de la propriété, écrivez le code qui passe la valeur de la propriété à la propriété exposée du contrôle constitutif.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-114">In the `set` section of the property, write code that passes the value of the property to the exposed property of the constituent control.</span></span>

## <a name="see-also"></a><span data-ttu-id="cdcd5-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cdcd5-115">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- [<span data-ttu-id="cdcd5-116">Propriétés dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cdcd5-116">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="cdcd5-117">Variétés de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="cdcd5-117">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
