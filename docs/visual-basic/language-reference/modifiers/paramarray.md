---
title: ParamArray
ms.date: 07/20/2015
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
ms.openlocfilehash: fbc87bffebc265e6062512e96fc29a64334b3c65
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351373"
---
# <a name="paramarray-visual-basic"></a>ParamArray (Visual Basic)
Spécifie qu’un paramètre de procédure accepte un tableau facultatif d’éléments du type spécifié. `ParamArray` peut être utilisé uniquement sur le dernier paramètre d’une liste de paramètres.  
  
## <a name="remarks"></a>Notes  
 `ParamArray` vous permet de passer un nombre arbitraire d’arguments à la procédure. Un paramètre `ParamArray` est toujours déclaré à l’aide de [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).  
  
 Vous pouvez fournir un ou plusieurs arguments à un paramètre `ParamArray` en passant un tableau du type de données approprié, une liste de valeurs séparées par des virgules, ou rien du tout. Pour plus d’informations, consultez « appel d’un ParamArray » dans les [tableaux de paramètres](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).  
  
> [!IMPORTANT]
> Chaque fois que vous traitez un tableau qui peut être indéfiniment volumineux, il existe un risque de surexécution de la capacité interne de votre application. Si vous acceptez un tableau de paramètres du code appelant, vous devez tester sa longueur et prendre les mesures appropriées s’il est trop grand pour votre application.  
  
 Le modificateur `ParamArray` peut être utilisé dans les contextes suivants :  
  
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- [Mots clés](../../../visual-basic/language-reference/keywords/index.md)
- [tableaux de paramètres](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
