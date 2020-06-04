---
title: La propriété '<propertyname>' ne retourne pas une valeur pour tous les chemins de code
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: 21a1c4dbab6e26cd1cb848e270bbda9a544c2a67
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400420"
---
# <a name="property-propertyname-doesnt-return-a-value-on-all-code-paths"></a>La propriété '\<propertyname>' ne retourne pas une valeur pour tous les chemins de code
La propriété' \<propertyname> 'ne retourne pas de valeur pour tous les chemins de code. Une exception de référence null peut se produire au moment de l'exécution lorsque le résultat est utilisé.  
  
 Une procédure de propriété `Get` possède au moins un chemin d’accès possible via son code qui ne retourne pas de valeur.  
  
 Vous pouvez retourner une valeur à partir d’une procédure de propriété `Get` de l’une des manières suivantes :  
  
- Assignez la valeur au nom de la propriété, puis exécutez une `Exit Property` instruction.  
  
- Assignez la valeur au nom de la propriété, puis exécutez l' `End Get` instruction.  
  
- Incluez la valeur dans une [instruction return](../statements/return-statement.md).  
  
 Si le contrôle est transmis à `Exit Property` ou `End Get` et que vous n’avez affecté aucune valeur au nom de la propriété, la `Get` procédure retourne la valeur par défaut du type de données de la propriété. Pour plus d’informations, consultez « Behavior » dans l' [instruction de fonction](../statements/function-statement.md).  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC42107  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Vérifiez votre logique de workflow de contrôle et assurez-vous que vous attribuez une valeur avant chaque instruction qui provoque un retour.  
  
     Il est plus facile de garantir que chaque retour de la procédure retourne une valeur si vous utilisez toujours l' `Return` instruction. Dans ce cas, la dernière instruction avant `End Get` doit être une `Return` instruction.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures Property](../../programming-guide/language-features/procedures/property-procedures.md)
- [Property Statement](../statements/property-statement.md)
- [Get, instruction](../statements/get-statement.md)
