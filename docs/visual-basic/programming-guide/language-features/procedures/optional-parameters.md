---
title: Paramètres facultatifs
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [Visual Basic], optional
- Visual Basic code, procedures
- procedures [Visual Basic], optional arguments
- optional arguments
- named arguments [Visual Basic], and optional arguments
- optional parameters
- Optional keyword [Visual Basic], optional arguments
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], and named arguments
ms.assetid: 398d2845-1069-4e94-b934-a73b545c8b87
ms.openlocfilehash: 73a51ab65a8ea4c38b6fd6737279fb19fb1cfe73
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071857"
---
# <a name="optional-parameters-visual-basic"></a>Paramètres facultatifs (Visual Basic)

Vous pouvez spécifier qu’un paramètre de procédure est facultatif et qu’il n’est pas nécessaire de fournir un argument lorsque la procédure est appelée. Les *paramètres facultatifs* sont indiqués par le `Optional` mot clé dans la définition de la procédure. Les règles suivantes s’appliquent :  
  
- Chaque paramètre facultatif dans la définition de la procédure doit spécifier une valeur par défaut.  
  
- La valeur par défaut d'un paramètre facultatif doit être une expression constante.  
  
- Tous les paramètres qui suivent un paramètre facultatif dans la définition de la procédure doivent également être facultatifs.  
  
 La syntaxe suivante montre une déclaration de procédure comprenant un paramètre facultatif :  
  
```vb  
Sub name(ByVal parameter1 As datatype1, Optional ByVal parameter2 As datatype2 = defaultvalue)  
```  
  
## <a name="calling-procedures-with-optional-parameters"></a>Appel de procédures à l'aide de paramètres facultatifs  

 Lorsque vous appelez une procédure à l'aide d'un paramètre facultatif, vous pouvez choisir de fournir l'argument ou non. Dans le cas contraire, la procédure utilise la valeur par défaut déclarée pour ce paramètre.  
  
 Pour omettre un ou plusieurs arguments facultatifs dans la liste des arguments, utilisez des virgules successives afin de marquer leurs positions. L’exemple d’appel suivant fournit le premier et le quatrième argument, mais pas le deuxième ni le troisième :  
  
```vb  
Sub name(argument 1, , , argument 4)  
```  
  
 L'exemple suivant effectue plusieurs appels à la fonction `MsgBox`. `MsgBox` comporte un paramètre obligatoire et deux paramètres facultatifs.  
  
 Le premier appel à `MsgBox` fournit les trois arguments dans l'ordre dans lequel `MsgBox` les définit. Le deuxième appel fournit uniquement l’argument requis. Le troisième et le quatrième appel fournissent le premier et le troisième argument. Le troisième appel le fait par position et le quatrième appel le fait par nom.  
  
 [!code-vb[VbVbcnProcedures#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#47)]  
  
## <a name="determining-whether-an-optional-argument-is-present"></a>Détermination de la présence d’un argument facultatif  

 Une procédure ne peut pas détecter au moment de l’exécution si un argument donné a été omis ou si le code appelant a explicitement fourni la valeur par défaut. Pour établir cette distinction, vous pouvez définir une valeur improbable comme valeur par défaut. La procédure suivante définit le paramètre facultatif `office` et teste sa valeur par défaut, `QJZ` , pour voir s’il a été omis dans l’appel :  
  
 [!code-vb[VbVbcnProcedures#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#46)]  
  
 Si le paramètre facultatif est un type référence tel que `String`, vous pouvez utiliser `Nothing` comme valeur par défaut, à condition qu’il ne s’agisse pas d’une valeur attendue pour l’argument.  
  
## <a name="optional-parameters-and-overloading"></a>Paramètres facultatifs et surcharge  

 La surcharge est une autre méthode permettant de définir une procédure à l'aide de paramètres facultatifs. Si vous disposez d'un seul paramètre facultatif, vous pouvez définir deux versions surchargées de la procédure, l'une avec le paramètre et l'autre sans. Cette approche se complique au fur et à mesure que le nombre de paramètres facultatifs augmente. Cependant, vous avez l’avantage de savoir avec certitude si le programme appelant a fourni chaque argument facultatif.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Passage des arguments par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)
- [Passage des arguments par position et par nom](./passing-arguments-by-position-and-by-name.md)
- [Tableaux de paramètres](./parameter-arrays.md)
- [Surcharge de procédure](./procedure-overloading.md)
- [Facultatif](../../../language-reference/modifiers/optional.md)
- [ParamArray](../../../language-reference/modifiers/paramarray.md)
