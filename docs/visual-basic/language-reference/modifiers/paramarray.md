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
ms.openlocfilehash: baf9303101eea9eed27e8a4eee9e04d255c798e9
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867822"
---
# <a name="paramarray-visual-basic"></a>ParamArray (Visual Basic)

Spécifie qu’un paramètre de procédure accepte un tableau facultatif d’éléments du type spécifié. `ParamArray` peut être utilisé uniquement sur le dernier paramètre d’une liste de paramètres.  
  
## <a name="remarks"></a>Notes  

 `ParamArray` vous permet de passer un nombre arbitraire d’arguments à la procédure. Un `ParamArray` paramètre est toujours déclaré à l’aide de [ByVal](byval.md).  
  
 Vous pouvez fournir un ou plusieurs arguments à un `ParamArray` paramètre en passant un tableau du type de données approprié, une liste de valeurs séparées par des virgules, ou rien du tout. Pour plus d’informations, consultez « appel d’un ParamArray » dans les [tableaux de paramètres](../../programming-guide/language-features/procedures/parameter-arrays.md).  
  
> [!IMPORTANT]
> Chaque fois que vous traitez un tableau qui peut être indéfiniment volumineux, il existe un risque de surexécution de la capacité interne de votre application. Si vous acceptez un tableau de paramètres du code appelant, vous devez tester sa longueur et prendre les mesures appropriées s’il est trop grand pour votre application.  
  
 Le modificateur `ParamArray` peut être utilisé dans les contextes suivants :  
  
 [Declare Statement](../statements/declare-statement.md)  
  
 [Function (instruction)](../statements/function-statement.md)  
  
 [Property Statement](../statements/property-statement.md)  
  
 [Sub (instruction)](../statements/sub-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- [Mots clés](../keywords/index.md)
- [Tableaux de paramètres](../../programming-guide/language-features/procedures/parameter-arrays.md)
