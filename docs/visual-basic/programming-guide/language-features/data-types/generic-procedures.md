---
title: Procédures génériques
ms.date: 07/20/2015
helpviewer_keywords:
- generic methods [Visual Basic], type inference
- generics [Visual Basic], type inference
- procedures [Visual Basic], generic
- generic procedures
- type inference, generics
- generic methods [Visual Basic]
- type inference
- generics [Visual Basic], procedures
- generic procedures [Visual Basic], type inference
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
ms.openlocfilehash: 16a629e07cf711778b3d8d1863958ec7a6300649
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350081"
---
# <a name="generic-procedures-in-visual-basic"></a>Procédures génériques dans Visual Basic
Une *procédure générique*, également appelée *méthode générique*, est une procédure définie avec au moins un paramètre de type. Cela permet au code appelant d’adapter les types de données à ses exigences chaque fois qu’il appelle la procédure.  
  
 Une procédure n’est pas générique simplement en raison d’une définition à l’intérieur d’une classe générique ou d’une structure générique. Pour être générique, la procédure doit accepter au moins un paramètre de type, en plus des paramètres normaux qu’il peut prendre. Une classe ou une structure générique peut contenir des procédures non génériques, et une classe, une structure ou un module non générique peut contenir des procédures génériques.  
  
 Une procédure générique peut utiliser ses paramètres de type dans sa liste de paramètres normale, dans son type de retour, le cas échéant, et dans son code de procédure.  
  
## <a name="type-inference"></a>Inférence de type  
 Vous pouvez appeler une procédure générique sans fournir de tout argument de type. Si vous l’appelez de cette manière, le compilateur tente de déterminer les types de données appropriés à passer aux arguments de type de la procédure. C’est ce que l’on appelle l' *inférence de type*. Le code suivant illustre un appel dans lequel le compilateur déduit qu’il doit passer le type `String` au paramètre de type `t`.  
  
 [!code-vb[VbVbalrDataTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#15)]  
  
 Si le compilateur ne peut pas déduire les arguments de type à partir du contexte de votre appel, il signale une erreur. Une erreur de ce type peut être due à une incompatibilité de rang de tableau. Supposons, par exemple, que vous définissiez un paramètre normal en tant que tableau d’un paramètre de type. Si vous appelez la procédure générique fournissant un tableau d’un rang différent (nombre de dimensions), l’incompatibilité entraîne l’échec de l’inférence de type. Le code suivant illustre un appel dans lequel un tableau à deux dimensions est passé à une procédure qui attend un tableau unidimensionnel.  
  
```vb  
Public Sub demoSub(Of t)(ByVal arg() As t)
End Sub

Public Sub callDemoSub()
    Dim twoDimensions(,) As Integer
    demoSub(twoDimensions)
End Sub
```
  
 Vous pouvez appeler l’inférence de type uniquement en omettant tous les arguments de type. Si vous fournissez un argument de type, vous devez tous les fournir.  
  
 L’inférence de type est prise en charge uniquement pour les procédures génériques. Vous ne pouvez pas appeler l’inférence de type sur des classes, des structures, des interfaces ou des délégués génériques.  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L’exemple suivant définit une procédure `Function` générique pour rechercher un élément particulier dans un tableau. Il définit un paramètre de type et l’utilise pour construire les deux paramètres dans la liste de paramètres.  
  
### <a name="code"></a>Code  
 [!code-vb[VbVbalrDataTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#14)]  
  
### <a name="comments"></a>Commentaires  
 L’exemple précédent nécessite la possibilité de comparer `searchValue` par rapport à chaque élément de `searchArray`. Pour garantir cette capacité, il limite le paramètre de type `T` à implémenter l’interface <xref:System.IComparable%601>. Le code utilise la méthode <xref:System.IComparable%601.CompareTo%2A> à la place de l’opérateur `=`, car il n’y a aucune garantie qu’un argument de type fourni pour `T` prenne en charge l’opérateur `=`.  
  
 Vous pouvez tester la procédure `findElement` à l’aide du code suivant.  
  
 [!code-vb[VbVbalrDataTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#13)]  
  
 Les appels précédents à `MsgBox` afficher respectivement « 0 », « 1 » et « -1 ».  
  
## <a name="see-also"></a>Voir aussi

- [Generic Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Guide pratique : définir une classe qui fournisse des fonctionnalités identiques pour différents types de données](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)
- [Guide pratique : utiliser une classe générique](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Procédures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Paramètres et arguments d’une procédure](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [Liste de types](../../../../visual-basic/language-reference/statements/type-list.md)
- [Liste de paramètres](../../../../visual-basic/language-reference/statements/parameter-list.md)
