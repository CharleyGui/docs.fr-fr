---
title: Création d'attributs personnalisés
ms.date: 07/20/2015
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
ms.openlocfilehash: 84b400c2fa1b2d4019eec32092f954d680e64978
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400692"
---
# <a name="creating-custom-attributes-visual-basic"></a>Créer des attributs personnalisés (Visual Basic)

Vous pouvez créer vos propres attributs personnalisés en définissant une classe d’attributs. Cette classe dérive directement ou indirectement d’<xref:System.Attribute>, ce qui permet d’identifier rapidement et facilement des définitions d’attributs dans des métadonnées. Supposons que vous souhaitiez baliser des types avec le nom du programmeur qui les a écrits. Vous pouvez définir une classe d’attributs `Author` personnalisés :

```vb
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct)>
Public Class Author
    Inherits System.Attribute
    Private name As String
    Public version As Double
    Sub New(ByVal authorName As String)
        name = authorName
        version = 1.0
    End Sub
End Class
```

Le nom de la classe est le nom de l’attribut, `Author`. Étant dérivée de `System.Attribute`, il s’agit donc d’une classe d’attributs personnalisés. Les paramètres du constructeur sont les paramètres positionnels de l’attribut personnalisé. Dans cet exemple, `name` est un paramètre positionnel. Les propriétés ou champs de type public accessibles en lecture/écriture sont des paramètres nommés. Dans le cas présent, `version` est le seul paramètre nommé. Notez l’utilisation de l’attribut `AttributeUsage` pour rendre l’attribut `Author` valide uniquement sur les déclarations de classe et de `Structure`.

Vous pouvez utiliser ce nouvel attribut de la manière suivante :

```vb
<Author("P. Ackerman", Version:=1.1)>
Class SampleClass
    ' P. Ackerman's code goes here...
End Class
```

`AttributeUsage` a un paramètre nommé, `AllowMultiple`, qui permet de déclarer un attribut personnalisé comme étant à usage unique ou multiple. Dans l’exemple de code suivant, un attribut à usage multiple est créé.

```vb
' multiuse attribute
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct,
                       AllowMultiple:=True)>
Public Class Author
    Inherits System.Attribute
```

Dans l’exemple de code suivant, plusieurs attributs du même type sont appliqués à une classe.

```vb
<Author("P. Ackerman", Version:=1.1),
Author("R. Koch", Version:=1.2)>
Class SampleClass
    ' P. Ackerman's code goes here...
    ' R. Koch's code goes here...
End Class
```

> [!NOTE]
> Si votre classe d’attributs contient une propriété, celle-ci doit être en lecture/écriture.

## <a name="see-also"></a>Voir aussi

- <xref:System.Reflection>
- [Guide de programmation Visual Basic](../../index.md)
- [Écriture des attributs personnalisés](../../../../standard/attributes/writing-custom-attributes.md)
- [Réflexion (Visual Basic)](../reflection.md)
- [Attributs (Visual Basic)](../../../language-reference/attributes.md)
- [Accéder à des attributs à l’aide de la réflexion (Visual Basic)](accessing-attributes-by-using-reflection.md)
- [AttributeUsage (Visual Basic)](attributeusage.md)
