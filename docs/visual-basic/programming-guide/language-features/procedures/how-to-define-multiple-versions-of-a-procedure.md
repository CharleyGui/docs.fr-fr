---
title: "Comment : définir plusieurs versions d'une procédure"
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: 2661603ba33dd0bc28ac1a192794a4534225b641
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071636"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>Comment : définir plusieurs versions d'une procédure (Visual Basic)

Vous pouvez définir une procédure dans plusieurs versions en la *surchargeant* , à l’aide du même nom mais d’une liste de paramètres différente pour chaque version. L’objectif de la surcharge est de définir plusieurs versions étroitement liées d’une procédure sans avoir à les différencier par nom.  
  
 Pour plus d'informations, consultez [Procedure Overloading](./procedure-overloading.md).  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>Pour définir plusieurs versions d’une procédure  
  
1. Écrivez une `Sub` `Function` instruction de déclaration ou pour chaque version de la procédure que vous souhaitez définir. Utilisez le même nom de procédure dans chaque déclaration.  
  
2. Faites précéder le `Sub` `Function` mot clé ou dans chaque déclaration du mot clé [Overloads](../../../language-reference/modifiers/overloads.md) . Vous pouvez éventuellement omettre `Overloads` dans les déclarations, mais si vous l’incluez dans une des déclarations, vous devez l’inclure dans chaque déclaration.  
  
3. Après chaque instruction de déclaration, écrivez le code de procédure pour gérer le cas spécifique où le code appelant fournit des arguments correspondant à la liste de paramètres de cette version. Vous n’avez pas besoin de tester les paramètres fournis par le code appelant. Visual Basic passe le contrôle à la version correspondante de votre procédure.  
  
4. Mettez fin à chaque version de la procédure avec l' `End Sub` `End Function` instruction ou, le cas échéant.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant définit une `Sub` procédure pour la publication d’une transaction sur le solde d’un client. Elle utilise le `Overloads` mot clé pour définir deux versions de la procédure, une qui accepte le client par nom et l’autre par numéro de compte.  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 Le code appelant peut obtenir l’identification du client en tant que `String` ou `Integer` , puis utiliser la même instruction appelante dans les deux cas.  
  
 Pour plus d’informations sur l’appel de ces versions de la `post` procédure, consultez [Comment : appeler une procédure surchargée](./how-to-call-an-overloaded-procedure.md).  
  
## <a name="compile-the-code"></a>Compiler le code  

 Vérifiez que chaque version surchargée a le même nom de procédure, mais une autre liste de paramètres.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Procédures de dépannage](./troubleshooting-procedures.md)
- [Comment : surcharger une procédure qui accepte des paramètres optionnels](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Considérations sur les surcharges de procédures](./considerations-in-overloading-procedures.md)
- [Résolution de surcharge](./overload-resolution.md)
