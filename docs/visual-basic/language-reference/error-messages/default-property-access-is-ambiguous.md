---
title: L'accès à la propriété par défaut est ambigu entre le membre '<defaultpropertyname>' de l'interface héritée '<interfacename1>' et le membre '<defaultpropertyname>' de l'interface héritée '<interfacename2>'
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: a36cfe8e5496bbfd1941afa8a46086491ae96a2a
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512755"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a>L’accès à la propriété par défaut est ambigu entre les\<membres d’interface hérités'\<defaultpropertyname > 'de l'\<interface’interfacename1 > 'et\< 'defaultpropertyname > 'de l’interface' interfacename2 >»

Une interface hérite de deux interfaces, chacune déclarant une propriété par défaut portant le même nom. Le compilateur ne peut pas résoudre un accès à cette propriété par défaut sans qualification. L'exemple suivant illustre ce comportement.

```vb
Public Interface Iface1
    Default Property prop(ByVal arg As Integer) As Integer
End Interface
Public Interface Iface2
    Default Property prop(ByVal arg As Integer) As Integer
End Interface
Public Interface Iface3
    Inherits Iface1, Iface2
End Interface
Public Class testClass
    Public Sub accessDefaultProperty()
        Dim testObj As Iface3
        Dim testInt As Integer = testObj(1)
    End Sub
End Class
```

Lorsque vous spécifiez `testObj(1)`, le compilateur essaie de le résoudre en propriété par défaut. Toutefois, il existe deux propriétés par défaut possibles en raison des interfaces héritées, de sorte que le compilateur signale cette erreur.

**ID d’erreur:** BC30686

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Évitez d’hériter des membres portant le même nom. Dans l’exemple précédent, si `testObj` n’a pas besoin des membres de, par `Iface2`exemple,, déclarez-le comme suit:

  ```vb
  Dim testObj As Iface1
  ```

  \- ou -

- Implémentez l’interface qui hérite dans une classe. Vous pouvez ensuite implémenter chacune des propriétés héritées avec des noms différents. Toutefois, une seule d’entre elles peut être la propriété par défaut de la classe d’implémentation. L'exemple suivant illustre ce comportement.

  ```vb
  Public Class useIface3
      Implements Iface3
      Default Public Property prop1(ByVal arg As Integer) As Integer Implements Iface1.prop
          ' Insert code to define Get and Set procedures for prop1.
      End Property
      Public Property prop2(ByVal arg As Integer) As Integer Implements Iface2.prop
          ' Insert code to define Get and Set procedures for prop2.
      End Property
  End Class
  ```

## <a name="see-also"></a>Voir aussi

- [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
