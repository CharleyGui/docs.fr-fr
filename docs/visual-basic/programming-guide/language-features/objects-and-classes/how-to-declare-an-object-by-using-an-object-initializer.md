---
title: 'Procédure : Déclarez un objet à l’aide d’un initialiseur d’objet (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: 850e20fe8b5b6bfd392c80c87950a81a1a8a5c24
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755199"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a>Procédure : Déclarez un objet à l’aide d’un initialiseur d’objet (Visual Basic)
Initialiseurs d’objets permettent de déclarer et instancier une instance d’une classe dans une instruction unique. En outre, vous pouvez initialiser un ou plusieurs membres de l’instance en même temps, sans appeler un constructeur paramétrable.  
  
 Lorsque vous utilisez un initialiseur d’objet pour créer une instance d’un type nommé, le constructeur sans paramètre pour la classe est appelé, suivie de l’initialisation de membres désignés dans l’ordre que vous spécifiez.  
  
 La procédure suivante montre comment créer une instance d’un `Student` classe de trois façons différentes. La classe a prénom, nom de famille, propriétés et de classe année, entre autres. Chacune des trois déclarations de crée une nouvelle instance de `Student`, avec la propriété `First` défini sur « Michael, « propriété `Last` défini sur « Tucker », et tous les autres membres définissent à leurs valeurs par défaut. Le résultat de chaque déclaration dans la procédure est équivalent à l’exemple suivant, qui n’utilise pas un initialiseur d’objet.  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 Pour une implémentation de la `Student` de classe, consultez [Comment : Créer une liste d’éléments](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md). Vous pouvez copier le code de cette rubrique pour définir la classe et créer une liste de `Student` objets à utiliser.  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a>Pour créer un objet d’une classe nommée à l’aide d’un initialiseur d’objet  
  
1. Commencez la déclaration comme si vous aviez prévu d’utiliser un constructeur.  
  
     `Dim student1 As New Student`  
  
2. Tapez le mot clé `With`, suivie d’une liste d’initialisation entre accolades.  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3. Dans la liste d’initialisation, incluez chaque propriété que vous souhaitez initialiser et lui affecter une valeur initiale. Le nom de la propriété est précédé d’un point.  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     Vous pouvez initialiser un ou plusieurs membres de la classe.  
  
4. Vous pouvez également déclarer une nouvelle instance de la classe et puis affectez-lui une valeur. Tout d’abord, déclarez une instance de `Student`:  
  
     `Dim student2 As Student`  
  
5. Commencer la création d’une instance de `Student` de façon normale.  
  
     `Dim student2 As Student = New Student`  
  
6. Type `With` et un initialiseur d’objet pour initialiser un ou plusieurs membres de la nouvelle instance.  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7. Vous pouvez simplifier la définition dans l’étape précédente en omettant `As Student`. Si vous procédez ainsi, le compilateur détermine que `student3` est une instance de `Student` à l’aide de l’inférence de type local.  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     Pour plus d’informations, consultez [l’inférence de Type Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
## <a name="see-also"></a>Voir aussi

- [Inférence de type local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Guide pratique : Créer une liste d’éléments](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
- [Initialiseurs d’objets : Types nommés et anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
