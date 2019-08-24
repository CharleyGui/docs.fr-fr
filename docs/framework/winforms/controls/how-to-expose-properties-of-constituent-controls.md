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
# <a name="how-to-expose-properties-of-constituent-controls"></a>Procédure : exposer des propriétés de contrôles constitutifs
Les contrôles qui composent un contrôle composite sont appelés *contrôles constitutifs*. Ces contrôles sont normalement déclarés privés et, par conséquent, ne sont pas accessibles par le développeur. Si vous souhaitez que les propriétés de ces contrôles soient disponibles pour les futurs utilisateurs, vous devez les exposer à l’utilisateur. Une propriété d’un contrôle constitutif est exposée en créant une propriété dans le contrôle utilisateur, et en `get` utilisant `set` les accesseurs et de cette propriété pour appliquer la modification de la propriété privée du contrôle constitutif.

 Imaginez un contrôle utilisateur hypothétique avec un bouton constitutif nommé `MyButton`. Dans cet exemple, lorsque l’utilisateur demande la `ConstituentButtonBackColor` propriété, la valeur stockée dans <xref:System.Windows.Forms.Control.BackColor%2A> la propriété `MyButton` de est remise. Lorsque l’utilisateur assigne une valeur à cette propriété, cette valeur est passée automatiquement à la <xref:System.Windows.Forms.Control.BackColor%2A> propriété de `MyButton` et le `set` code s’exécute, en modifiant la couleur `MyButton`de.

 L’exemple suivant montre comment exposer la <xref:System.Windows.Forms.Control.BackColor%2A> propriété du bouton constitutif:

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

### <a name="to-expose-a-property-of-a-constituent-control"></a>Pour exposer une propriété d’un contrôle constitutif

1. Créez une propriété publique pour votre contrôle utilisateur.

2. Dans la `get` section de la propriété, écrivez du code qui récupère la valeur de la propriété que vous souhaitez exposer.

3. Dans la `set` section de la propriété, écrivez le code qui passe la valeur de la propriété à la propriété exposée du contrôle constitutif.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.UserControl>
- [Propriétés dans les contrôles Windows Forms](properties-in-windows-forms-controls.md)
- [Variétés de contrôles personnalisés](varieties-of-custom-controls.md)
