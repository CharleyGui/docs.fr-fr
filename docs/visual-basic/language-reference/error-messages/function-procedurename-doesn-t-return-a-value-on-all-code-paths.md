---
title: La fonction '<procedurename>' ne retourne pas une valeur pour tous les chemins de code
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: 19b305e337767dfb34718aed7b665f142851bd36
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163361"
---
# <a name="bc42105-function-procedurename-doesnt-return-a-value-on-all-code-paths"></a>BC42105 : la fonction' \<procedurename> 'ne retourne pas de valeur pour tous les chemins de code

La fonction' \<procedurename> 'ne retourne pas de valeur sur tous les chemins de code. Une instruction’return’est-elle manquante ?

 Une `Function` procédure a au moins un chemin d’accès possible via son code qui ne retourne pas de valeur.

 Vous pouvez retourner une valeur à partir d’une `Function` procédure de l’une des manières suivantes :

- Incluez la valeur dans une [instruction return](../statements/return-statement.md).

- Assignez la valeur au nom de la `Function` procédure, puis exécutez une `Exit Function` instruction.

- Assignez la valeur au nom de la `Function` procédure, puis exécutez l' `End Function` instruction.

 Si le contrôle est transmis à `Exit Function` ou `End Function` et que vous n’avez affecté aucune valeur au nom de la procédure, la procédure retourne la valeur par défaut du type de données de retour. Pour plus d’informations, consultez « Behavior » dans l' [instruction de fonction](../statements/function-statement.md).

 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).

 **ID d’erreur :** BC42105

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Vérifiez votre logique de workflow de contrôle et assurez-vous que vous attribuez une valeur avant chaque instruction qui provoque un retour.

     Il est plus facile de garantir que chaque retour de la procédure retourne une valeur si vous utilisez toujours l' `Return` instruction. Dans ce cas, la dernière instruction avant `End Function` doit être une `Return` instruction.

## <a name="see-also"></a>Voir aussi

- [Function, procédures](../../programming-guide/language-features/procedures/function-procedures.md)
- [Function (instruction)](../statements/function-statement.md)
- [Page Compiler, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
