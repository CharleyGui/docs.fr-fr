---
title: Tableaux de paramètres (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
ms.openlocfilehash: 372d5fdd2702d6f85f784ee5addea91abe46d3bd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64639017"
---
# <a name="parameter-arrays-visual-basic"></a>Tableaux de paramètres (Visual Basic)
En règle générale, vous ne pouvez pas appeler une procédure avec plus d’arguments que spécifie la déclaration de procédure. Lorsque vous avez besoin d’un nombre indéfini d’arguments, vous pouvez déclarer un *tableau de paramètres*, ce qui permet à la procédure d’accepter un tableau de valeurs pour un paramètre. Il est inutile de connaître le nombre d’éléments dans le tableau de paramètres lorsque vous définissez la procédure. La taille du tableau est déterminée individuellement par chaque appel à la procédure.  
  
## <a name="declaring-a-paramarray"></a>Déclaration d’un paramètre ParamArray  
 Vous utilisez le [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) mot clé pour désigner un tableau de paramètres dans la liste de paramètres. Les règles suivantes s'appliquent :  
  
- Une procédure peut définir qu’un seul tableau de paramètres, et il doit être le dernier paramètre dans la définition de procédure.  
  
- Le tableau de paramètres doit être passé par valeur. Il est conseillé d’inclure explicitement les [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mot clé dans la définition de procédure.  
  
- Le tableau de paramètres est automatiquement facultatif. Sa valeur par défaut est un tableau unidimensionnel vide du type d’élément du tableau de paramètres.  
  
- Tous les paramètres précédant le tableau de paramètres doivent être requis. Le tableau de paramètres doit être le seul paramètre facultatif.  
  
## <a name="calling-a-paramarray"></a>Appel d’un ParamArray  
 Lorsque vous appelez une procédure qui définit un tableau de paramètres, vous pouvez fournir l’argument dans l’une des manières suivantes :  
  
- Aucune valeur, ce qui signifie que vous pouvez omettre le [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argument. Dans ce cas, un tableau vide est passé à la procédure. Vous pouvez également passer le [rien](../../../../visual-basic/language-reference/nothing.md) mot clé, avec le même effet.  
  
- Une liste d’un nombre arbitraire d’arguments, séparés par des virgules. Le type de données de chaque argument doit être implicitement convertible en le `ParamArray` type d’élément.  
  
- Un tableau avec le même type d’élément en tant que type d’élément du tableau de paramètres.  
  
 Dans tous les cas, le code au sein de la procédure traite le tableau de paramètres comme un tableau unidimensionnel avec des éléments du même type de données en tant que le `ParamArray` type de données.  
  
> [!IMPORTANT]
>  Chaque fois que vous avez affaire à un tableau qui peut s’avérer indéfiniment volumineux, il existe un risque de saturer la capacité interne de votre application. Si vous acceptez un tableau de paramètres, vous devez tester la taille du tableau passé le code appelant. Prendre les mesures appropriées si elle est trop grande pour votre application. Pour plus d’informations, consultez [tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant définit et appelle la fonction `calcSum`. Le `ParamArray` modificateur du paramètre `args` permet à la fonction d’accepter un nombre variable d’arguments.  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 L’exemple suivant définit une procédure avec un tableau de paramètres et génère les valeurs de tous les éléments du tableau passés au tableau de paramètres.  
  
 [!code-vb[VbVbcnProcedures#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#48)]  
  
 [!code-vb[VbVbcnProcedures#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#49)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [Procédures](./index.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Passage d’un argument par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)
- [Passage des arguments par position et par nom](./passing-arguments-by-position-and-by-name.md)
- [Paramètres facultatifs](./optional-parameters.md)
- [Surcharge de procédure](./procedure-overloading.md)
- [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)
