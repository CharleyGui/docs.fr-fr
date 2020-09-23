---
title: 'Comment : surcharger une procédure qui accepte des paramètres optionnels'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
ms.openlocfilehash: 78ca6b2b95dfd5a7f208e5251f08dfccc5514946
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071519"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a>Comment : surcharger une procédure qui accepte des paramètres optionnels (Visual Basic)

Si une procédure a un ou plusieurs paramètres [facultatifs](../../../language-reference/modifiers/optional.md) , vous ne pouvez pas définir une version surchargée correspondant à l’une de ses surcharges implicites. Pour plus d’informations, consultez « surcharges implicites pour les paramètres facultatifs » dans [Considérations sur la surcharge des procédures](./considerations-in-overloading-procedures.md).  
  
## <a name="one-optional-parameter"></a>Un paramètre facultatif  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a>Pour surcharger une procédure qui accepte un paramètre facultatif  
  
1. Écrivez une `Sub` `Function` instruction de déclaration ou qui comprend le paramètre facultatif dans la liste de paramètres. N’utilisez pas le `Optional` mot clé dans cette version surchargée.  
  
2. Faites précéder le `Sub` `Function` mot clé ou du mot clé [Overloads](../../../language-reference/modifiers/overloads.md) .  
  
3. Écrivez le code de procédure qui doit s’exécuter lorsque le code appelant fournit l’argument facultatif.  
  
4. Mettez fin à la procédure avec l' `End Sub` `End Function` instruction ou, le cas échéant.  
  
5. Écrivez une deuxième instruction de déclaration qui est identique à la première déclaration, sauf qu’elle n’inclut pas le paramètre facultatif dans la liste de paramètres.  
  
6. Écrivez le code de procédure qui doit s’exécuter lorsque le code appelant ne fournit pas l’argument facultatif. Mettez fin à la procédure avec l' `End Sub` `End Function` instruction ou, le cas échéant.  
  
     L’exemple suivant montre une procédure définie avec un paramètre facultatif, un jeu équivalent de deux procédures surchargées, et enfin des exemples de versions surchargées non valides et valides.  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a>Paramètres facultatifs multiples  

 Pour une procédure avec plusieurs paramètres facultatifs, vous avez généralement besoin de plus de deux versions surchargées. Par exemple, s’il existe deux paramètres facultatifs, et que le code appelant peut fournir ou omettre chacun indépendamment de l’autre, vous avez besoin de quatre versions surchargées, une pour chaque combinaison possible d’arguments fournis.  
  
 À mesure que le nombre de paramètres facultatifs augmente, la complexité de la surcharge augmente. Sauf si certaines combinaisons d’arguments fournis ne sont pas acceptables, pour N paramètres facultatifs, vous avez besoin de 2 ^ N versions surchargées. Selon la nature de la procédure, vous pouvez constater que la clarté de la logique justifie l’effort supplémentaire de définition de toutes les versions surchargées.  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a>Pour surcharger une procédure qui accepte plusieurs paramètres facultatifs  
  
1. Déterminez quelles combinaisons d’arguments facultatifs fournis sont acceptables pour la logique de la procédure. Une combinaison inacceptable peut survenir si un paramètre facultatif dépend d’un autre. Par exemple, si un paramètre accepte le nom d’une personne et qu’un autre accepte l’âge de la personne, une combinaison d’arguments fournissant l’âge, mais en omettant le nom, n’est pas acceptable.  
  
2. Pour chaque combinaison acceptable d’arguments facultatifs fournis, écrivez `Sub` une `Function` instruction de déclaration ou qui définit la liste de paramètres correspondante. N’utilisez pas le `Optional` mot clé.  
  
3. Dans chaque déclaration, faites précéder le `Sub` `Function` mot clé ou du mot clé [Overloads](../../../language-reference/modifiers/overloads.md) .  
  
4. À la suite de chaque déclaration, écrivez le code de la procédure qui doit s’exécuter lorsque le code appelant fournit une liste d’arguments correspondant à la liste de paramètres de cette déclaration.  
  
5. Mettez fin à chaque procédure avec l' `End Sub` `End Function` instruction ou, le cas échéant.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Paramètres facultatifs](./optional-parameters.md)
- [Tableaux de paramètres](./parameter-arrays.md)
- [Surcharge de procédure](./procedure-overloading.md)
- [Procédures de dépannage](./troubleshooting-procedures.md)
- [Comment : définir plusieurs versions d'une procédure](./how-to-define-multiple-versions-of-a-procedure.md)
- [Comment : appeler une procédure surchargée](./how-to-call-an-overloaded-procedure.md)
- [Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Résolution de surcharge](./overload-resolution.md)
