---
title: Résolution de surcharge
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- overload resolution
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedure overloading [Visual Basic], overload resolution
- signatures [Visual Basic], procedure
- overloads [Visual Basic], resolution
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
ms.openlocfilehash: 84d52bbbfb34c2e5d67ed6a1810ab3e32fafda22
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266870"
---
# <a name="overload-resolution-visual-basic"></a>Résolution de surcharge (Visual Basic)
Lorsque le compilateur Visual Basic fait face à un appel à une procédure définie en plusieurs versions surchargées, le compilateur doit décider lequel des surcharges appeler. Pour ce faire, il effectue les étapes suivantes :  
  
1. **Accessibilité.** Il élimine toute surcharge avec un niveau d’accès qui empêche le code d’appel de l’appeler.  
  
2. **Nombre de paramètres.** Il élimine toute surcharge qui définit un nombre différent de paramètres que ceux fournis dans l’appel.  
  
3. **Types de données paramètres.** Le compilateur donne aux méthodes d’instance une préférence plutôt que des méthodes d’extension. Si une méthode d’instance est trouvée qui nécessite seulement l’élargissement des conversions pour correspondre à l’appel de procédure, toutes les méthodes d’extension sont abandonnées et le compilateur continue avec seulement les candidats méthode d’instance. Si aucune méthode de ce type n’est trouvée, elle continue avec les méthodes d’instance et d’extension.  
  
     Dans cette étape, il élimine toute surcharge pour laquelle les types de données des arguments d’appel ne peuvent pas être convertis en types de paramètres définis dans la surcharge.  
  
4. **Rétrécissement des conversions.** Il élimine toute surcharge qui nécessite un rétrécissement de la conversion des types d’argument d’appel aux types de paramètres définis. Cela est vrai si le type de `On` commutateur `Off`de vérification[(Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) est ou .  
  
5. **Moins d’élargissement.** Le compilateur considère les surcharges restantes par paires. Pour chaque paire, il compare les types de données des paramètres définis. Si les types dans l’une des surcharges s’élargissent tous aux types correspondants dans l’autre, le compilateur élimine ce dernier. Autrement dit, il conserve la surcharge qui nécessite le moins d’élargissement.  
  
6. **Candidat unique.** Il continue d’envisager des surcharges par paires jusqu’à ce qu’il ne reste qu’une surcharge, et il résout l’appel à cette surcharge. Si le compilateur ne peut pas réduire les surcharges à un seul candidat, il génère une erreur.  
  
 L’illustration suivante montre le processus qui détermine lequel d’un ensemble de versions surchargées à appeler.  
  
 ![Diagramme de flux du processus de résolution de surcharge](./media/overload-resolution/determine-overloaded-version.gif "Résoudre parmi les versions surchargées")
  
 L’exemple suivant illustre ce processus de résolution de surcharge.  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 Dans le premier appel, le compilateur élimine la première surcharge`Short`parce que le type du premier`Byte`argument ( ) se rétrécit au type du paramètre correspondant (). Il élimine ensuite la troisième surcharge parce que chaque`Short` type `Single`d’argument dans la deuxième surcharge`Integer` ( `Single`et ) s’élargit au type correspondant dans la troisième surcharge ( et ). La deuxième surcharge nécessite moins d’élargissement, de sorte que le compilateur l’utilise pour l’appel.  
  
 Dans le deuxième appel, le compilateur ne peut éliminer aucune des surcharges sur la base du rétrécissement. Il élimine la troisième surcharge pour la même raison que dans le premier appel, car il peut appeler la deuxième surcharge avec moins d’élargissement des types d’arguments. Toutefois, le compilateur ne peut pas résoudre entre la première et la deuxième surcharge. Chacun a un type de paramètre défini qui`Byte` s’élargit au type correspondant dans l’autre (à `Short`, mais `Single` à `Double`). Le compilateur génère donc une erreur de résolution de surcharge.  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>Arguments optionnels surchargés et paramArray  
 Si deux surcharges d’une procédure ont des signatures identiques, sauf que le dernier paramètre est déclaré [facultatif](../../../../visual-basic/language-reference/modifiers/optional.md) dans l’un et [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) dans l’autre, le compilateur résout un appel à cette procédure comme suit:  
  
|Si l’appel fournit le dernier argument|Le compilateur résout l’appel à la surcharge déclarant le dernier argument comme|  
|---|---|  
|Aucune valeur (argument omis)|`Optional`|  
|Une valeur unique|`Optional`|  
|Deux valeurs ou plus dans une liste séparée par virgule|`ParamArray`|  
|Un tableau de n’importe quelle longueur (y compris un tableau vide)|`ParamArray`|  
  
## <a name="see-also"></a>Voir aussi

- [Paramètres facultatifs](./optional-parameters.md)
- [Paramètres Arrays](./parameter-arrays.md)
- [Surcharge de procédure](./procedure-overloading.md)
- [Procédures de dépannage](./troubleshooting-procedures.md)
- [Comment : définir plusieurs versions d'une procédure](./how-to-define-multiple-versions-of-a-procedure.md)
- [Comment : appeler une procédure surchargée](./how-to-call-an-overloaded-procedure.md)
- [Comment : surcharger une procédure qui accepte des paramètres optionnels](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Considérations sur les surcharges de procédures](./considerations-in-overloading-procedures.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Méthodes d’extension](./extension-methods.md)
