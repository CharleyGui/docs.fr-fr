---
title: L'accès à la propriété par défaut est ambigu entre le membre '<defaultpropertyname>' de l'interface héritée '<interfacename1>' et le membre '<defaultpropertyname>' de l'interface héritée '<interfacename2>'
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: b7c4c9c75de1b3777f34a70470b89f323a5699f9
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162061"
---
# <a name="bc30686-default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a>BC30686 : l’accès à la propriété par défaut est ambigu entre les membres de l’interface héritée' 'de l’interface \<defaultpropertyname> ' \<interfacename1> 'et le' \<defaultpropertyname> 'de l’interface' \<interfacename2> '

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

Lorsque vous spécifiez `testObj(1)` , le compilateur essaie de le résoudre en propriété par défaut. Toutefois, il existe deux propriétés par défaut possibles en raison des interfaces héritées, de sorte que le compilateur signale cette erreur.

**ID d’erreur :** BC30686

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Évitez d’hériter des membres portant le même nom. Dans l’exemple précédent, si `testObj` n’a pas besoin des membres de, par exemple, `Iface2` , déclarez-le comme suit :

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

- [Interfaces](../../programming-guide/language-features/interfaces/index.md)
