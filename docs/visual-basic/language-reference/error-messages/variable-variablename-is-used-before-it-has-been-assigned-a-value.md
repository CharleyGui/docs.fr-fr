---
title: La variable '<variablename>' est utilisée avant qu'une valeur ne lui ait été assignée
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: 34718243172d3b1a238a813268e672d62c4eeb6c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406532"
---
# <a name="variable-variablename-is-used-before-it-has-been-assigned-a-value"></a>La variable '\<variablename>' est utilisée avant qu'une valeur ne lui ait été assignée
La variable' \<variablename> 'est utilisée avant qu’une valeur ne lui ait été assignée. Cela peut provoquer une exception de référence null au moment de l’exécution.  
  
 Une application a au moins un chemin d’accès possible via son code qui lit une variable avant qu’une valeur ne lui soit assignée.  
  
 Si aucune valeur n’a jamais été assignée à une variable, elle contient la valeur par défaut de son type de données. Pour un type de données référence, cette valeur par défaut est [Nothing](../nothing.md). La lecture d’une variable de référence qui a la valeur `Nothing` peut provoquer une <xref:System.NullReferenceException> dans certaines circonstances.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** COMPILATION BC42104  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Vérifiez votre logique de workflow de contrôle et assurez-vous que la variable a une valeur valide avant que le contrôle ne passe à une instruction qui la lit.  
  
- Pour garantir que la variable a toujours une valeur valide, vous pouvez l’initialiser dans le cadre de sa déclaration. Consultez « initialisation » dans l' [instruction Dim](../statements/dim-statement.md).  
  
## <a name="see-also"></a>Voir aussi

- [Dim (instruction)](../statements/dim-statement.md)
- [Déclaration de variable](../../programming-guide/language-features/variables/variable-declaration.md)
- [Dépannage des variables](../../programming-guide/language-features/variables/troubleshooting-variables.md)
