---
title: Les constantes doivent être de type intrinsèque ou énuméré, et non de type classe, structure, paramètre de type ou tableau
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: e820287f0ddf462b30867d90501f7d730c9c6739
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163153"
---
# <a name="bc30424-constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a>BC30424 : les constantes doivent être de type intrinsèque ou énuméré, et non une classe, une structure, un paramètre de type ou un type tableau

Vous avez tenté de déclarer une constante en tant que type de classe, de structure ou de tableau, ou en tant que paramètre de type défini par un type générique conteneur.

 Les constantes doivent être de type intrinsèque ( `Boolean` , `Byte` , `Date` , `Decimal` , `Double` , `Integer` , `Long` , `Object` , `SByte` , `Short` , `Single` , `String` , `UInteger` , `ULong` ou `UShort` ) ou d’un `Enum` type basé sur l’un des types intégraux.

 **ID d’erreur :** BC30424

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Déclarez la constante en tant que `Enum` type intrinsèque ou.

2. Une constante peut également être une valeur spéciale telle que `True` , `False` ou `Nothing` . Le compilateur considère ces valeurs prédéfinies comme étant du type intrinsèque approprié.

## <a name="see-also"></a>Voir aussi

- [Constantes et énumérations](../constants-and-enumerations.md)
- [Data types](../../programming-guide/language-features/data-types/index.md)
- [Data types](../data-types/index.md)
