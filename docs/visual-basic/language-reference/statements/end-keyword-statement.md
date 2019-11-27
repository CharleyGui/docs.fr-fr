---
title: End <keyword> (instruction)
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: 87f4724cc036e6e0bdf0b558854a4034f45b9ab5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343734"
---
# <a name="end-keyword-statement-visual-basic"></a>End \<mot clé >, instruction (Visual Basic)

Lorsqu’il est suivi d’un mot clé supplémentaire, termine la définition du bloc d’instructions introduit par ce mot clé.

## <a name="syntax"></a>Syntaxe

```vb
End AddHandler
End Class
End Enum
End Event
End Function
End Get
End If
End Interface
End Module
End Namespace
End Operator
End Property
End RaiseEvent  
End RemoveHandler  
End Select
End Set
End Structure
End Sub
End SyncLock
End Try
End While
End With  
```  
  
## <a name="parts"></a>Composants

|Élément|Description|
|---|---|
|`End`|Requis. Termine la définition de l’élément de programmation.|
|`AddHandler`|Requis pour terminer un accesseur `AddHandler` commencé par une instruction `AddHandler` correspondante dans une [instruction d’événement](event-statement.md)personnalisée.|
|`Class`|Requis pour terminer une définition de classe commencée par une [instruction de classe](class-statement.md)correspondante.|
|`Enum`|Requis pour terminer une définition d’énumération commencée par une [instruction enum](enum-statement.md)correspondante.|
|`Event`|Requis pour mettre fin à une définition d’événement `Custom` commencée par une [instruction Event](event-statement.md)correspondante.|  
|`Function`|Requis pour terminer une définition de procédure `Function` commencée par une [instruction de fonction](function-statement.md)correspondante. Si l’exécution rencontre une instruction `End Function`, le contrôle retourne au code appelant.|
|`Get`|Requis pour terminer une définition de procédure `Property` commencée par une [instruction d’extraction](get-statement.md)correspondante. Si l’exécution rencontre une instruction `End Get`, le contrôle retourne à l’instruction qui demande la valeur de la propriété.|
|`If`|Requis pour mettre fin à une définition de bloc `If`...`Then`...`Else` commencé par une instruction `If` correspondante. Voir [si... Puis... Instruction Else](if-then-else-statement.md).|
|`Interface`|Requis pour terminer une définition d’interface commencée par une [instruction d’interface](interface-statement.md)correspondante.|
|`Module`|Requis pour terminer une définition de module commencée par une [instruction de module](module-statement.md)correspondante.|
|`Namespace`|Requis pour terminer une définition d’espace de noms commencée par une [instruction d’espace de noms](namespace-statement.md)correspondante.|
|`Operator`|Requis pour terminer une définition d’opérateur commencée par une [instruction d’opérateur](operator-statement.md)correspondante.|
|`Property`|Requis pour terminer une définition de propriété commencée par une [instruction de propriété](property-statement.md)correspondante.|
|`RaiseEvent`|Requis pour terminer un accesseur `RaiseEvent` commencé par une instruction `RaiseEvent` correspondante dans une [instruction d’événement](event-statement.md)personnalisée.|
|`RemoveHandler`|Requis pour terminer un accesseur `RemoveHandler` commencé par une instruction `RemoveHandler` correspondante dans une [instruction d’événement](event-statement.md)personnalisée.|
|`Select`|Requis pour mettre fin à une définition de bloc `Select`...`Case` commencé par une instruction `Select` correspondante. Voir [Sélectionner... Instruction case](select-case-statement.md).  
|`Set`|Requis pour terminer une définition de procédure `Property` commencée par une [instruction Set](set-statement.md)correspondante. Si l’exécution rencontre une instruction `End Set`, le contrôle retourne à l’instruction qui définit la valeur de la propriété.  
|`Structure`|Requis pour terminer une définition de structure commencée par une [instruction de structure](structure-statement.md)correspondante.  
|`Sub`|Requis pour terminer une définition de procédure `Sub` commencée par une [sous-instruction](sub-statement.md)correspondante. Si l’exécution rencontre une instruction `End Sub`, le contrôle retourne au code appelant.  
|`SyncLock`|Requis pour terminer une définition de bloc `SyncLock` commencée par une instruction `SyncLock` correspondante. Consultez [instruction SyncLock](synclock-statement.md).  
|`Try`|Requis pour mettre fin à une définition de bloc `Try`...`Catch`...`Finally` commencé par une instruction `Try` correspondante. Voir [essayer... Catch... Finally, instruction](try-catch-finally-statement.md).  
|`While`|Requis pour terminer une définition de boucle `While` commencée par une instruction `While` correspondante. Voir [tout cela... Instruction End While](while-end-while-statement.md).  
|`With`| Requis pour terminer une définition de bloc `With` commencée par une instruction `With` correspondante. Voir [avec... End With](with-end-with-statement.md).  
|||
  
## <a name="directives"></a>Directives

Lorsqu’il est précédé d’un signe dièse (`#`), le mot clé `End` met fin à un bloc de prétraitement introduit par la directive correspondante.  

```vb
#End ExternalSource
#End If
#End Region
```

|Élément|Description|
|---|---|
|`#End`|Requis. Termine la définition du bloc de prétraitement.|
|`ExternalSource`|Requis pour terminer un bloc source externe commencé par une [Directive #ExternalSource](../directives/externalsource-directive.md)correspondante.|
|`If`|Requis pour terminer un bloc de compilation conditionnelle commencé par une directive de `#If` correspondante. Voir [#If... Then... #Else directives](../directives/if-then-else-directives.md).|
|`Region`|Requis pour terminer un bloc de région source commencé par une [directive de #Region](../directives/region-directive.md)correspondante.|
|||

## <a name="remarks"></a>Notes

L' [instruction end](end-statement.md), sans mot clé supplémentaire, termine immédiatement l’exécution.

## <a name="smart-device-developer-notes"></a>Notes de développement Smart Device  

L’instruction `End`, sans mot clé supplémentaire, n’est pas prise en charge.  
  
## <a name="see-also"></a>Voir aussi

- [End (instruction)](end-statement.md)
