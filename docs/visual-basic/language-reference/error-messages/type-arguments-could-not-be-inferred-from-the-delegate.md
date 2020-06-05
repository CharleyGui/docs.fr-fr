---
title: Les arguments de type ne peuvent pas être déduits à partir du délégué
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: f29e92c8245e33c0418d9a387070b03f645c331e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362746"
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a>Les arguments de type ne peuvent pas être déduits à partir du délégué
Une instruction d’assignation utilise `AddressOf` pour assigner l’adresse d’une procédure générique à un délégué, mais elle ne fournit aucun argument de type à la procédure générique.  
  
 En général, lorsque vous appelez un type générique, vous fournissez un argument de type pour chaque paramètre de type défini par le type générique. Si vous ne fournissez pas d’arguments de type, le compilateur tente de déduire les types à passer aux paramètres de type. Si le contexte ne fournit pas au compilateur des informations suffisantes pour déduire les types, une erreur est générée.  
  
 **ID d’erreur :** BC36564  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Spécifiez les arguments de type pour la procédure générique dans l’expression `AddressOf` .  
  
## <a name="see-also"></a>Voir aussi

- [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [AddressOf, opérateur](../operators/addressof-operator.md)
- [Generic Procedures in Visual Basic](../../programming-guide/language-features/data-types/generic-procedures.md)
- [Type List](../statements/type-list.md)
- [Méthodes d’extension](../../programming-guide/language-features/procedures/extension-methods.md)
