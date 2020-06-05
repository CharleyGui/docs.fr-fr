---
title: Considérations sur les surcharges de procédures
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
ms.openlocfilehash: c4075c87df8b9daa56ca1d35e0d6661598895fdc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403367"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a>Considérations sur les surcharges de procédures (Visual Basic)
Quand vous surchargez une procédure, vous devez utiliser une *signature* différente pour chaque version surchargée. Cela signifie généralement que chaque version doit spécifier une liste de paramètres différente. Pour plus d’informations, consultez « signature différente » dans surcharge de la [procédure](./procedure-overloading.md).  
  
 Vous pouvez surcharger une `Function` procédure à l’aide d’une `Sub` procédure, et vice versa, à condition qu’elles aient des signatures différentes. Deux surcharges ne peuvent pas différer uniquement si elle a une valeur de retour et que l’autre ne le fait pas.  
  
 Vous pouvez surcharger une propriété de la même façon que vous surchargez une procédure, et avec les mêmes restrictions. Toutefois, vous ne pouvez pas surcharger une procédure avec une propriété, ou vice versa.  
  
## <a name="alternatives-to-overloaded-versions"></a>Alternatives aux versions surchargées  
 Vous avez parfois des alternatives à des versions surchargées, en particulier lorsque la présence d’arguments est facultative ou que leur nombre est variable.  
  
 Gardez à l’esprit que les arguments facultatifs ne sont pas nécessairement pris en charge par tous les langages, et que les tableaux de paramètres sont limités à Visual Basic. Si vous écrivez une procédure qui est susceptible d’être appelée à partir d’un code écrit dans plusieurs langages différents, les versions surchargées offrent la plus grande flexibilité.  
  
### <a name="overloads-and-optional-arguments"></a>Surcharges et arguments facultatifs  
 Lorsque le code appelant peut éventuellement fournir ou omettre un ou plusieurs arguments, vous pouvez définir plusieurs versions surchargées ou utiliser des paramètres facultatifs.  
  
#### <a name="when-to-use-overloaded-versions"></a>Quand utiliser des versions surchargées  
 Vous pouvez envisager de définir une série de versions surchargées dans les cas suivants :  
  
- La logique dans le code de la procédure est très différente selon que le code appelant fournit ou non un argument facultatif.  
  
- Le code de la procédure ne peut pas tester de manière fiable si le code appelant a fourni un argument facultatif. C’est le cas, par exemple, s’il n’y a pas de candidat possible pour une valeur par défaut que le code appelant n’est pas censé fournir.  
  
#### <a name="when-to-use-optional-parameters"></a>Quand utiliser des paramètres facultatifs  
 Vous préférerez peut-être un ou plusieurs paramètres facultatifs dans les cas suivants :  
  
- La seule action requise lorsque le code appelant ne fournit pas d’argument facultatif consiste à définir le paramètre sur une valeur par défaut. Dans ce cas, le code de la procédure peut être moins compliqué si vous définissez une seule version avec un ou plusieurs `Optional` paramètres.  
  
 Pour plus d’informations, consultez [paramètres facultatifs](./optional-parameters.md).  
  
### <a name="overloads-and-paramarrays"></a>Surcharges et ParamArrays  
 Lorsque le code appelant peut passer un nombre variable d’arguments, vous pouvez définir plusieurs versions surchargées ou utiliser un tableau de paramètres.  
  
#### <a name="when-to-use-overloaded-versions"></a>Quand utiliser des versions surchargées  
 Vous pouvez envisager de définir une série de versions surchargées dans les cas suivants :  
  
- Vous savez que le code appelant ne passe jamais plus d’un petit nombre de valeurs au tableau de paramètres.  
  
- La logique dans le code de la procédure est très différente selon le nombre de valeurs que le code appelant transmet.  
  
- Le code appelant peut passer des valeurs de types de données différents.  
  
#### <a name="when-to-use-a-parameter-array"></a>Quand utiliser un tableau de paramètres  
 Vous êtes mieux servi par un `ParamArray` paramètre dans les cas suivants :  
  
- Vous n’êtes pas en mesure de prédire le nombre de valeurs que le code appelant peut passer au tableau de paramètres, et il peut s’agir d’un grand nombre.  
  
- La logique de la procédure se prête à itérer au sein de toutes les valeurs que le code appelant passe, en effectuant essentiellement les mêmes opérations sur chaque valeur.  
  
 Pour plus d’informations, consultez [tableaux de paramètres](./parameter-arrays.md).  
  
## <a name="implicit-overloads-for-optional-parameters"></a>Surcharges implicites pour les paramètres facultatifs  
 Une procédure avec un paramètre [facultatif](../../../language-reference/modifiers/optional.md) équivaut à deux procédures surchargées, l’une avec le paramètre facultatif et l’autre sans celle-ci. Vous ne pouvez pas surcharger une telle procédure avec une liste de paramètres correspondant à l’un ou l’autre de ces. Les déclarations suivantes illustrent cela.  
  
 [!code-vb[VbVbcnProcedures#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#58)]  
  
 [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
 [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
 Pour une procédure avec plusieurs paramètres facultatifs, il existe un ensemble de surcharges implicites, reçues à l’aide d’une logique similaire à celle de l’exemple précédent.  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a>Surcharges implicites pour un paramètre ParamArray  
 Le compilateur considère qu’une procédure avec un paramètre [ParamArray](../../../language-reference/modifiers/paramarray.md) a un nombre infini de surcharges, en distinguant les unes des autres dans ce que le code appelant transmet au tableau de paramètres, comme suit :  
  
- Une surcharge pour lorsque le code appelant ne fournit pas d’argument à la`ParamArray`  
  
- Une surcharge pour lorsque le code appelant fournit un tableau unidimensionnel du type d' `ParamArray` élément  
  
- Pour chaque entier positif, une surcharge pour lorsque le code appelant fournit ce nombre d’arguments, chacun du `ParamArray` type d’élément  
  
 Les déclarations suivantes illustrent ces surcharges implicites.  
  
 [!code-vb[VbVbcnProcedures#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#68)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 Vous ne pouvez pas surcharger une telle procédure avec une liste de paramètres qui prend un tableau unidimensionnel pour le tableau de paramètres. Toutefois, vous pouvez utiliser les signatures des autres surcharges implicites. Les déclarations suivantes illustrent cela.  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a>Programmation non typée comme alternative à la surcharge  
 Si vous souhaitez autoriser le code appelant à passer des types de données différents à un paramètre, une autre approche est la programmation sans type. Vous pouvez définir le commutateur de vérification de type à `Off` l’aide de l’option d' [instruction Option Strict](../../../language-reference/statements/option-strict-statement.md) ou de l’option [-optionstrict](../../../reference/command-line-compiler/optionstrict.md) du compilateur. Vous n’avez pas besoin de déclarer le type de données du paramètre. Toutefois, cette approche présente les inconvénients suivants par rapport à la surcharge :  
  
- La programmation sans type produit un code d’exécution moins efficace.  
  
- La procédure doit tester tous les types de données qu’elle prévoit de passer.  
  
- Le compilateur ne peut pas signaler une erreur si le code appelant passe un type de données que la procédure ne prend pas en charge.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Procédures de dépannage](./troubleshooting-procedures.md)
- [Comment : définir plusieurs versions d'une procédure](./how-to-define-multiple-versions-of-a-procedure.md)
- [Comment : appeler une procédure surchargée](./how-to-call-an-overloaded-procedure.md)
- [Comment : surcharger une procédure qui accepte des paramètres optionnels](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Résolution de surcharge](./overload-resolution.md)
- [Surcharges](../../../language-reference/modifiers/overloads.md)
