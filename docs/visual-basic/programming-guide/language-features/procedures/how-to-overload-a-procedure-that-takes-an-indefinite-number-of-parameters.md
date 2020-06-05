---
title: 'Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
ms.openlocfilehash: ddff8c8cd82593b7d89fb0847e56123c287e364b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387879"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres (Visual Basic)
Si une procédure a un paramètre [ParamArray](../../../language-reference/modifiers/paramarray.md) , vous ne pouvez pas définir une version surchargée qui prend un tableau unidimensionnel pour le tableau de paramètres. Pour plus d’informations, consultez « surcharges implicites pour un paramètre ParamArray » dans [Considérations sur la surcharge des procédures](./considerations-in-overloading-procedures.md).  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>Pour surcharger une procédure qui accepte un nombre variable de paramètres  
  
1. Veillez à ce que la procédure et la logique de code appelant tirent parti des versions surchargées plus qu’à partir d’un `ParamArray` paramètre. Consultez « Overloads and ParamArrays » dans [Considérations sur la surcharge des procédures](./considerations-in-overloading-procedures.md).  
  
2. Déterminez le nombre de valeurs fournies que la procédure doit accepter dans la partie variable de la liste de paramètres. Cela peut inclure la casse sans valeur et peut inclure le cas d’un tableau unidimensionnel unique.  
  
3. Pour chaque nombre acceptable de valeurs fournies, écrivez une `Sub` `Function` instruction de déclaration ou qui définit la liste de paramètres correspondante. N’utilisez pas le `Optional` `ParamArray` mot clé ou dans cette version surchargée.  
  
4. Dans chaque déclaration, faites précéder le `Sub` `Function` mot clé ou du mot clé [Overloads](../../../language-reference/modifiers/overloads.md) .  
  
5. À la suite de chaque déclaration, écrivez le code de la procédure qui doit s’exécuter lorsque le code appelant fournit des valeurs correspondant à la liste de paramètres de cette déclaration.  
  
6. Mettez fin à chaque procédure avec l' `End Sub` `End Function` instruction ou, le cas échéant.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une procédure définie avec un paramètre [ParamArray](../../../language-reference/modifiers/paramarray.md) , puis un ensemble équivalent de procédures surchargées.  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 Vous ne pouvez pas surcharger une telle procédure avec une liste de paramètres qui prend un tableau unidimensionnel pour le tableau de paramètres. Toutefois, vous pouvez utiliser les signatures des autres surcharges implicites. Les déclarations suivantes illustrent cela.  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 Le code dans les versions surchargées n’a pas besoin de tester si le code appelant a fourni une ou plusieurs valeurs pour le `ParamArray` paramètre, ou le cas échéant, combien. Visual Basic passe le contrôle à la version correspondant à la liste d’arguments d’appel.  
  
## <a name="compile-the-code"></a>Compiler le code  
 Étant donné qu’une procédure avec un `ParamArray` paramètre est équivalente à un ensemble de versions surchargées, vous ne pouvez pas surcharger une telle procédure avec une liste de paramètres correspondant à l’une de ces surcharges implicites. Pour plus d’informations, consultez [Considérations sur la surcharge des procédures](./considerations-in-overloading-procedures.md).  
  
## <a name="net-framework-security"></a>Sécurité du .NET Framework  
 Chaque fois que vous traitez un tableau qui peut être indéfiniment volumineux, il existe un risque de surexécution de la capacité interne de votre application. Si vous acceptez un tableau de paramètres, vous devez tester la longueur du tableau auquel le code appelant est passé et prendre les mesures appropriées s’il est trop grand pour votre application.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Paramètres facultatifs](./optional-parameters.md)
- [Tableaux de paramètres](./parameter-arrays.md)
- [Surcharge de procédure](./procedure-overloading.md)
- [Procédures de dépannage](./troubleshooting-procedures.md)
- [Comment : définir plusieurs versions d'une procédure](./how-to-define-multiple-versions-of-a-procedure.md)
- [Comment : appeler une procédure surchargée](./how-to-call-an-overloaded-procedure.md)
- [Comment : surcharger une procédure qui accepte des paramètres optionnels](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Résolution de surcharge](./overload-resolution.md)
