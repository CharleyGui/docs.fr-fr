---
title: "Comment : forcer le passage d'un argument par valeur"
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], in parentheses
- procedure arguments [Visual Basic], in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
ms.openlocfilehash: 0be49e7d4aacbb30956bda7f6ee8494a7ded8b78
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071623"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a>Comment : forcer le passage d’un argument par valeur (Visual Basic)

La déclaration de procédure détermine le mécanisme de passage. Si un paramètre est déclaré [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic s’attend à passer l’argument correspondant par référence. Cela permet à la procédure de modifier la valeur de l’élément de programmation sous-jacent à l’argument dans le code appelant. Si vous souhaitez protéger l’élément sous-jacent contre une telle modification, vous pouvez remplacer le `ByRef` mécanisme de passage dans l’appel de procédure en plaçant le nom de l’argument entre parenthèses. Ces parenthèses s’ajoutent aux parenthèses entourant la liste d’arguments dans l’appel.  
  
 Le code appelant ne peut pas substituer un mécanisme [ByVal](../../../language-reference/modifiers/byval.md) .  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a>Pour forcer le passage d’un argument par valeur  
  
- Si le paramètre correspondant est déclaré `ByVal` dans la procédure, vous n’avez pas besoin d’effectuer d’autres étapes. Visual Basic s’attend déjà à passer l’argument par valeur.  
  
- Si le paramètre correspondant est déclaré `ByRef` dans la procédure, mettez l’argument entre parenthèses dans l’appel de procédure.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant substitue une `ByRef` déclaration de paramètre. Dans l’appel qui force `ByVal` , notez les deux niveaux de parenthèses.  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 Lorsque `str` est placé entre parenthèses supplémentaires dans la liste d’arguments, la `setNewString` procédure ne peut pas modifier sa valeur dans le code appelant et `MsgBox` affiche « ne peut pas être remplacé si passé ByVal ». Lorsque `str` n’est pas placé entre parenthèses supplémentaires, la procédure peut le modifier et `MsgBox` affiche « il s’agit d’une nouvelle valeur pour l’argument inString ».  
  
## <a name="compile-the-code"></a>Compiler le code  

 Lorsque vous transmettez une variable par référence, vous devez utiliser le `ByRef` mot clé pour spécifier ce mécanisme.  
  
 La valeur par défaut de Visual Basic consiste à passer des arguments par valeur. Toutefois, il est recommandé d’inclure le mot clé [ByVal](../../../language-reference/modifiers/byval.md) ou [ByRef](../../../language-reference/modifiers/byref.md) avec chaque paramètre déclaré. Cela rend votre code plus facile à lire.  
  
## <a name="robust-programming"></a>Programmation fiable  

 Si une procédure déclare un paramètre [ByRef](../../../language-reference/modifiers/byref.md), l’exécution correcte du code peut dépendre de la possibilité de modifier l’élément sous-jacent dans le code appelant. Si le code appelant remplace ce mécanisme d’appel en mettant l’argument entre parenthèses, ou s’il passe un argument non modifiable, la procédure ne peut pas modifier l’élément sous-jacent. Cela peut produire des résultats inattendus dans le code appelant.  
  
## <a name="net-framework-security"></a>Sécurité du .NET Framework  

 Il existe toujours un risque potentiel d’autoriser une procédure à modifier la valeur sous-jacente d’un argument dans le code appelant. Veillez à ce que cette valeur soit modifiée et soyez prêt à vérifier sa validité avant de l’utiliser.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Comment : passer des arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md)
- [Passage des arguments par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)
- [Différences entre les arguments modifiables et non modifiables](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Différences entre le passage d'un argument par valeur et par référence](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Comment : modifier la valeur d’un argument de la procédure](./how-to-change-the-value-of-a-procedure-argument.md)
- [Comment : protéger un argument de procédure contre les modifications de valeur](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Passage des arguments par position et par nom](./passing-arguments-by-position-and-by-name.md)
- [Types valeur et types référence](../data-types/value-types-and-reference-types.md)
