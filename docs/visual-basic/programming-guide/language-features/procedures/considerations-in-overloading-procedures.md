---
title: Considérations sur les surcharges de procédures (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- signatures [Visual Basic], ParamArray arguments
- ParamArray keyword [Visual Basic], parameter arrays
- ParamArray keyword [Visual Basic], arguments and signatures
- function overloading [Visual Basic], implicit overloads for ParamArray
- ParamArray keyword [Visual Basic], signatures
- Visual Basic code, procedures
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], overloading
- parameters [Visual Basic], lists
- function overloading [Visual Basic], typeless programming
- typeless programming
- function overloading [Visual Basic], restrictions
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], overloading
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- parameter arrays [Visual Basic], overloading arguments
- Visual Basic code, parameter lists
- procedure overloading [Visual Basic], considerations
- Option Explicit statement [Visual Basic]
- restrictions [Visual Basic], overloading procedures
- procedures [Visual Basic], parameter lists
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
ms.openlocfilehash: b5a26a8b68a2f786213aa49f30247d692b3de2f7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649656"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a>Considérations sur les surcharges de procédures (Visual Basic)
Lorsque vous surchargez une procédure, vous devez utiliser un autre *signature* pour chaque version surchargée. Cela signifie généralement que chaque version doit spécifier une liste de paramètres différente. Pour plus d’informations, consultez « Signature différente » dans [surcharge de procédure](./procedure-overloading.md).  
  
 Vous pouvez surcharger un `Function` procédure avec un `Sub` procédure et inversement, à condition qu’ils ont des signatures différentes. Deux surcharges ne peuvent pas différer uniquement par un a une valeur de retournée et l’autre n’est pas le cas.  
  
 Vous pouvez surcharger une propriété de la même façon que vous surchargez une procédure et avec les mêmes restrictions. Toutefois, vous ne pouvez pas surcharger une procédure avec une propriété, ou vice versa.  
  
## <a name="alternatives-to-overloaded-versions"></a>Alternatives aux Versions surchargées  
 Vous devez parfois des alternatives aux versions surchargées, en particulier lorsque la présence d’arguments est facultative ou leur nombre est variable.  
  
 N’oubliez pas que les arguments facultatifs ne sont pas nécessairement prises en charge par tous les langages et tableaux de paramètres sont limités à Visual Basic. Si vous écrivez une procédure qui est susceptible d’être appelée à partir du code écrit dans un des différents langages, les versions surchargées offrent la plus grande flexibilité.  
  
### <a name="overloads-and-optional-arguments"></a>Surcharges et Arguments facultatifs  
 Lorsque le code appelant peut éventuellement fournir ou omettre un ou plusieurs arguments, vous pouvez définir plusieurs versions surchargées ou utiliser des paramètres facultatifs.  
  
#### <a name="when-to-use-overloaded-versions"></a>Quand utiliser des Versions surchargées  
 Vous pouvez envisager de définir une série de versions surchargées dans les cas suivants :  
  
- La logique dans le code de procédure est considérablement différente selon que le code appelant fournit un argument facultatif ou non.  
  
- Le code de procédure ne peut pas vérifier de manière fiable si le code appelant a fourni un argument facultatif. C’est le cas, par exemple, s’il n’existe aucun candidat possible pour une valeur par défaut que le code appelant n’était pas supposé fournir.  
  
#### <a name="when-to-use-optional-parameters"></a>Quand utiliser les paramètres facultatifs  
 Vous préférerez peut-être un ou plusieurs paramètres facultatifs dans les cas suivants :  
  
- La seule action requise lorsque le code appelant ne fournit pas un argument facultatif consiste à définir le paramètre à une valeur par défaut. Dans ce cas, le code de procédure peut être moins compliqué si vous définissez une version unique avec un ou plusieurs `Optional` paramètres.  
  
 Pour plus d’informations, consultez [paramètres facultatifs](./optional-parameters.md).  
  
### <a name="overloads-and-paramarrays"></a>Surcharges et ParamArrays  
 Lorsque le code appelant peut passer un nombre variable d’arguments, vous pouvez définir plusieurs versions surchargées ou utiliser un tableau de paramètres.  
  
#### <a name="when-to-use-overloaded-versions"></a>Quand utiliser des Versions surchargées  
 Vous pouvez envisager de définir une série de versions surchargées dans les cas suivants :  
  
- Vous savez que le code appelant passe jamais plus qu’un petit nombre de valeurs au tableau de paramètres.  
  
- La logique dans le code de procédure est considérablement différente selon le nombre de valeurs transmet le code appelant.  
  
- Le code appelant peut passer des valeurs de différents types de données.  
  
#### <a name="when-to-use-a-parameter-array"></a>Quand utiliser un tableau de paramètres  
 Il est préférable par un `ParamArray` paramètre dans les cas suivants :  
  
- Vous n’êtes pas en mesure de prédire combien de valeurs le code appelant peut passer au tableau de paramètres, et il peut être un grand nombre.  
  
- La logique de la procédure se prête à l’itération sur toutes les valeurs que le code appelant passe, essentiellement les mêmes opérations sur chaque valeur.  
  
 Pour plus d’informations, consultez [tableaux de paramètres](./parameter-arrays.md).  
  
## <a name="implicit-overloads-for-optional-parameters"></a>Surcharges implicites pour les paramètres facultatifs  
 Une procédure avec un [facultatif](../../../../visual-basic/language-reference/modifiers/optional.md) paramètre équivaut à deux procédures surchargées, une avec le paramètre facultatif et l’autre sans. Vous ne pouvez pas surcharger une procédure avec une liste de paramètres correspondant aux deux. Les déclarations suivantes illustrent ce principe.  
  
 [!code-vb[VbVbcnProcedures#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#58)]  
  
 [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
 [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
 Pour une procédure avec plus d’un paramètre facultatif, il existe un ensemble de surcharges implicites, est arrivé à logique, comme dans l’exemple précédent.  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a>Surcharges implicites pour un paramètre ParamArray  
 Le compilateur considère qu’une procédure avec un [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) paramètre possède un nombre infini de surcharges, qui se différencient selon ce que le code appelant passe au tableau de paramètres, comme suit :  
  
- Une surcharge lorsque le code appelant ne fournit pas un argument à la `ParamArray`  
  
- Une surcharge lorsque le code appelant fournit un tableau unidimensionnel de la `ParamArray` type d’élément  
  
- Pour chaque entier positif, une surcharge lorsque le code appelant fournit ce nombre d’arguments, chacun de la `ParamArray` type d’élément  
  
 Les déclarations suivantes illustrent ces surcharges implicites.  
  
 [!code-vb[VbVbcnProcedures#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#68)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 Vous ne pouvez pas surcharger une procédure avec une liste de paramètres qui accepte un tableau unidimensionnel pour le tableau de paramètres. Toutefois, vous pouvez utiliser les signatures des autres surcharges implicites. Les déclarations suivantes illustrent ce principe.  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a>Programmation sans type comme Alternative à la surcharge  
 Si vous souhaitez autoriser le code appelant à passer différents types de données à un paramètre, une autre approche consiste à la programmation sans type. Vous pouvez définir le commutateur de vérification de type `Off` avec soit le [Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md) ou [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) option du compilateur. Puis vous n’êtes pas obligé de déclarer le type de données du paramètre. Toutefois, cette approche présente les inconvénients suivants par rapport à la surcharge :  
  
- Programmation sans type génère un code d’exécution moins efficace.  
  
- La procédure doit tester pour chaque type de données que pouvant être passés.  
  
- Le compilateur ne peut pas signaler une erreur si le code appelant passe un type de données par la procédure ne prend pas en charge.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Procédures de dépannage](./troubleshooting-procedures.md)
- [Guide pratique pour Définir plusieurs Versions d’une procédure](./how-to-define-multiple-versions-of-a-procedure.md)
- [Guide pratique pour Appeler une procédure surchargée](./how-to-call-an-overloaded-procedure.md)
- [Guide pratique pour Surcharger une procédure qui accepte des paramètres optionnels](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Guide pratique pour Surcharger une procédure qui accepte un nombre indéfini de paramètres](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Résolution de surcharge](./overload-resolution.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
