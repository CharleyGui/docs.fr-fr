---
title: Différences entre les arguments modifiables et non modifiables
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: 733f92cc2cdaa6e923c57649774ceb64de172c18
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403341"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a>Différences entre les arguments modifiables et non modifiables (Visual Basic)
Lorsque vous appelez une procédure, vous lui transmettez généralement un ou plusieurs arguments. Chaque argument correspond à un élément de programmation sous-jacent. Les éléments sous-jacents et les arguments peuvent eux-mêmes être modifiables ou non modifiables.  
  
## <a name="modifiable-and-nonmodifiable-elements"></a>Éléments modifiables et non modifiables  
 Un élément de programmation peut être un *élément modifiable*, dont la valeur peut être modifiée ou un *élément non modifiable*, qui a une valeur fixe une fois qu’il a été créé.  
  
 Le tableau suivant répertorie les éléments de programmation modifiables et non modifiables.  
  
|Éléments modifiables|Éléments non modifiables|  
|-------------------------|----------------------------|  
|Variables locales (déclarées dans les procédures), y compris les variables objets, à l’exception de en lecture seule|Variables, champs et propriétés en lecture seule|  
|Champs (variables de membre de modules, classes et structures), à l’exception de en lecture seule|Constantes et littéraux|  
|Propriétés, à l’exception de lecture seule|Membres de l’énumération|  
|Éléments de tableau|Expressions (même si leurs éléments sont modifiables)|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a>Arguments modifiables et non modifiables  
 Un *argument modifiable* est un argument avec un élément sous-jacent modifiable. Le code appelant peut stocker une nouvelle valeur à tout moment, et si vous transmettez l’argument [ByRef](../../../language-reference/modifiers/byref.md), le code de la procédure peut également modifier l’élément sous-jacent dans le code appelant.  
  
 Un *argument non modifiable* a un élément sous-jacent non modifiable ou est passé avec la valeur [ByVal](../../../language-reference/modifiers/byval.md). La procédure ne peut pas modifier l’élément sous-jacent dans le code appelant, même s’il s’agit d’un élément modifiable. S’il s’agit d’un élément non modifiable, le code appelant lui-même ne peut pas le modifier.  
  
 La procédure appelée peut modifier sa copie locale d’un argument non modifiable, mais cette modification n’affecte pas l’élément sous-jacent dans le code appelant.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Comment : passer des arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md)
- [Passage des arguments par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)
- [Différences entre le passage d'un argument par valeur et par référence](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Comment : modifier la valeur d’un argument de la procédure](./how-to-change-the-value-of-a-procedure-argument.md)
- [Comment : protéger un argument de procédure contre les modifications de valeur](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Comment : forcer le passage d'un argument par valeur](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Passage des arguments par position et par nom](./passing-arguments-by-position-and-by-name.md)
- [Types valeur et types référence](../data-types/value-types-and-reference-types.md)
