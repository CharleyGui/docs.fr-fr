---
title: Option Strict On interdit le passage du type '<typename1>' au type '<typename2>' lors de la recopie de la valeur du paramètre 'ByRef' '<parametername>' dans l'argument correspondant.
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: fced95fe24d42d4af2118706bcaf3337429fea91
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873992"
---
# <a name="implicit-conversion-from-typename1-to-typename2-in-copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument"></a>Option Strict On interdit le passage du type '\<typename1>' au type '\<typename2>' lors de la recopie de la valeur du paramètre 'ByRef' '\<parametername>' dans l'argument correspondant.

Une procédure est appelée avec un argument [ByRef](../modifiers/byref.md) d’un type différent de celui de son paramètre correspondant.  
  
 Si vous passez un argument `ByRef` , Visual Basic copie parfois la valeur de l’argument dans une variable locale de la procédure au lieu de passer une référence. Dans ce cas, quand la procédure est retournée, Visual Basic doit ensuite copier la valeur de la variable locale dans l’argument du code appelant.  
  
 Si une valeur d’argument `ByRef` est copiée dans la procédure, et si l’argument et le paramètre sont du même type, aucune conversion n’est nécessaire. Toutefois, si les types sont différents, Visual Basic doit effectuer une conversion dans les deux directions. Étant donné que vous ne pouvez pas utiliser `CType` ou l’un des autres mots clés de conversion sur un argument ou un paramètre de procédure, une telle conversion est toujours implicite.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC41999  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Si possible, utilisez un argument d’appel du même type que le paramètre de procédure, afin Visual Basic n’a pas besoin d’effectuer de conversion.  
  
- Si vous devez appeler la procédure avec un type d’argument différent du type de paramètre, mais n’avez pas besoin de retourner une valeur dans l’argument d’appel, définissez le paramètre sur [ByVal](../modifiers/byval.md) au lieu de `ByRef`.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](../../programming-guide/language-features/procedures/index.md)
- [Paramètres et arguments d’une procédure](../../programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [Passage des arguments par valeur et par référence](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [Conversions implicites et explicites](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
