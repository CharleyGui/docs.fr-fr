---
title: Le type <typename> n'est pas conforme CLS
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: c50e721e9170a402724a11f3aab573c7e8abf4c1
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161164"
---
# <a name="bc40041-type-typename-is-not-cls-compliant"></a>BC40041 : \<typename> le type n’est pas conforme CLS

Une variable, une propriété ou un retour de fonction est déclaré avec un type de données qui n’est pas conforme CLS.

 Pour qu’une application soit conforme à l' [indépendance du langage et aux composants de Language-Independent](../../../standard/language-independence-and-language-independent-components.md) (CLS), elle doit utiliser uniquement des types conformes CLS.

 Les types de données Visual Basics suivants ne sont pas conformes CLS :

- [SByte (type de données)](../data-types/sbyte-data-type.md)

- [UInteger (type de données)](../data-types/uinteger-data-type.md)

- [ULong (type de données)](../data-types/ulong-data-type.md)

- [UShort (type de données)](../data-types/ushort-data-type.md)

 **ID d’erreur :** BC40041

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Si votre application doit être conforme CLS, remplacez le type de données de cet élément par le type conforme CLS le plus proche. Par exemple, vous pouvez utiliser `UInteger` au lieu de `Integer` si vous n’avez pas besoin de la plage de valeurs située au-dessus de 2 147 483 647. Si vous avez besoin de la plage étendue, vous pouvez remplacer `UInteger` par `Long`.

- Si votre application n’a pas besoin d’être conforme à CLS, vous n’avez pas besoin de modifier quoi que ce soit. Toutefois, vous devez être conscient de sa non-conformité.
