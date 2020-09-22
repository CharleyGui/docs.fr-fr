---
title: Le type <typename> n'est pas conforme CLS
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: 369516fb12b24981eaecfe467bf421dec279aa01
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875095"
---
# <a name="type-typename-is-not-cls-compliant"></a>Le type \<typename> n'est pas conforme CLS

Une variable, une propriété ou un retour de fonction est déclaré avec un type de données qui n’est pas conforme CLS.  
  
 Pour qu’une application soit conforme à l' [indépendance du langage et aux composants indépendants du langage (CLS, Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) ), elle doit utiliser uniquement des types conformes CLS.  
  
 Les types de données Visual Basics suivants ne sont pas conformes CLS :  
  
- [SByte (type de données)](../data-types/sbyte-data-type.md)  
  
- [UInteger (type de données)](../data-types/uinteger-data-type.md)  
  
- [ULong (type de données)](../data-types/ulong-data-type.md)  
  
- [UShort (type de données)](../data-types/ushort-data-type.md)  
  
 **ID d’erreur :** BC40041  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Si votre application doit être conforme CLS, remplacez le type de données de cet élément par le type conforme CLS le plus proche. Par exemple, vous pouvez utiliser `UInteger` au lieu de `Integer` si vous n’avez pas besoin de la plage de valeurs située au-dessus de 2 147 483 647. Si vous avez besoin de la plage étendue, vous pouvez remplacer `UInteger` par `Long`.  
  
- Si votre application n’a pas besoin d’être conforme à CLS, vous n’avez pas besoin de modifier quoi que ce soit. Toutefois, vous devez être conscient de sa non-conformité.
