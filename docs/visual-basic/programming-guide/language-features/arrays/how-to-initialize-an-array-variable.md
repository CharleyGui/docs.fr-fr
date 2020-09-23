---
title: 'Guide pratique : initialiser une variable tableau'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: 1add054a6cb6468f4581f92ca3a258c5b0cdc77d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058857"
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a>Comment : initialiser une variable tableau en Visual Basic

Vous initialisez une variable tableau en incluant un littéral de tableau dans une `New` clause et en spécifiant les valeurs initiales du tableau. Vous pouvez spécifier le type ou l’autoriser à être déduit à partir des valeurs du littéral de tableau. Pour plus d’informations sur la façon dont le type est déduit, consultez « remplissage d’un tableau avec des valeurs initiales » dans les [tableaux](index.md).  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a>Pour initialiser une variable tableau à l’aide d’un littéral de tableau  
  
- Dans la `New` clause, ou lorsque vous assignez la valeur du tableau, fournissez les valeurs des éléments à l’intérieur des accolades ( `{}` ). L’exemple suivant montre plusieurs façons de déclarer, de créer et d’initialiser une variable qui contient un tableau contenant des éléments de type `Char` .  
  
     [!code-vb[VbVbalrArrays#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#16)]  
  
     Après l’exécution de chaque instruction, le tableau créé a une longueur de 3, avec des éléments à l’index 0 à index 2 contenant les valeurs initiales. Si vous fournissez à la fois la limite supérieure et les valeurs, vous devez inclure une valeur pour chaque élément de l’index 0 jusqu’à la limite supérieure.  
  
     Notez que vous n’avez pas besoin de spécifier la limite supérieure d’index si vous fournissez des valeurs d’élément dans un littéral de tableau. Si aucune limite supérieure n’est spécifiée, la taille du tableau est déduite en fonction du nombre de valeurs dans le littéral de tableau.  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a>Pour initialiser une variable de tableau multidimensionnel à l’aide de littéraux de tableau  
  
- Imbriquez des valeurs à l’intérieur des accolades ( `{}` ) entre accolades. Vérifiez que les littéraux de tableau imbriqués sont tous déduits en tant que tableaux de même type et de même longueur. L’exemple de code suivant illustre plusieurs exemples d’initialisation de tableau multidimensionnel.  
  
     [!code-vb[VbVbalrArrays#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#17)]  
  
- Vous pouvez spécifier explicitement les limites du tableau ou les conserver et faire en sorte que le compilateur déduit les limites du tableau en fonction des valeurs du littéral de tableau. Si vous fournissez à la fois les limites supérieures et les valeurs, vous devez inclure une valeur pour chaque élément de l’index 0 jusqu’à la limite supérieure dans chaque dimension. L’exemple suivant montre plusieurs façons de déclarer, de créer et d’initialiser une variable qui contient un tableau à deux dimensions qui contient des éléments de type. `Short`  
  
     [!code-vb[VbVbalrArrays#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#18)]  
  
     Après l’exécution de chaque instruction, le tableau créé contient six éléments initialisés qui ont des index `(0,0)` ,,,, `(0,1)` `(0,2)` `(1,0)` `(1,1)` et `(1,2)` . Chaque emplacement de tableau contient la valeur `10` .  
  
- L’exemple suivant itère au sein d’un tableau multidimensionnel. Dans une application console Windows écrite en Visual Basic, collez le code à l’intérieur de la `Sub Main()` méthode. Les derniers commentaires montrent la sortie.  
  
     [!code-vb[VbVbalrArrays#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#31)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a>Pour initialiser une variable de tableau en escalier à l’aide de littéraux de tableau  
  
- Imbriquez des valeurs d’objet à l’intérieur des accolades ( `{}` ). Bien que vous puissiez également imbriquer des littéraux de tableau qui spécifient des tableaux de longueurs différentes, dans le cas d’un tableau en escalier, assurez-vous que les littéraux de tableaux imbriqués sont placés entre parenthèses ( `()` ). Les parenthèses forcent l’évaluation des littéraux de tableaux imbriqués, et les tableaux résultants sont utilisés comme valeurs initiales du tableau en escalier. L’exemple de code suivant montre deux exemples d’initialisation de tableau en escalier.  
  
     [!code-vb[VbVbalrArrays#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#19)]  
  
- L’exemple suivant itère au sein d’un tableau en escalier. Dans une application console Windows écrite en Visual Basic, collez le code à l’intérieur de la `Sub Main()` méthode.  Les derniers commentaires du code affichent la sortie.  
  
     [!code-vb[VbVbalrArrays#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>Voir aussi

- [Tableaux](index.md)
- [Résolution des problèmes de tableaux](troubleshooting-arrays.md)
