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
ms.openlocfilehash: bcb99ef3845c1ce3998dc9dc8d9f1d335515c0a9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364368"
---
# <a name="overload-resolution-visual-basic"></a>Résolution de surcharge (Visual Basic)
Lorsque le compilateur Visual Basic rencontre un appel à une procédure qui est définie dans plusieurs versions surchargées, le compilateur doit décider de la surcharge à appeler. Pour ce faire, il effectue les étapes suivantes :  
  
1. **Aux.** Elle élimine toute surcharge avec un niveau d’accès qui empêche le code appelant de l’appeler.  
  
2. **Nombre de paramètres.** Elle élimine toutes les surcharges qui définissent un nombre de paramètres différent de ceux fournis dans l’appel.  
  
3. **Types de données de paramètre.** Le compilateur fournit la préférence des méthodes d’instance sur les méthodes d’extension. Si vous trouvez une méthode d’instance qui requiert que seules les conversions étendues correspondent à l’appel de procédure, toutes les méthodes d’extension sont supprimées et le compilateur continue uniquement avec les candidats de méthode d’instance. Si aucune méthode d’instance n’est trouvée, elle se poursuit avec les méthodes d’instance et d’extension.  
  
     Dans cette étape, il élimine toute surcharge pour laquelle les types de données des arguments d’appel ne peuvent pas être convertis en types de paramètres définis dans la surcharge.  
  
4. **Conversions restrictives.** Elle élimine toute surcharge qui requiert une conversion restrictive des types d’arguments d’appel aux types de paramètres définis. Cela est vrai, que le commutateur de vérification de type ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) soit `On` ou `Off` .  
  
5. **Le moins étendu.** Le compilateur considère les surcharges restantes par paires. Pour chaque paire, il compare les types de données des paramètres définis. Si les types de l’une des surcharges s’étendent aux types correspondants dans l’autre, le compilateur élimine ce dernier. Autrement dit, elle conserve la surcharge qui requiert le moins d’élargissement.  
  
6. **Candidat unique.** Il continue à considérer les surcharges par paires jusqu’à ce qu’une seule surcharge soit conservée et résout l’appel à cette surcharge. Si le compilateur ne peut pas réduire les surcharges à un seul candidat, il génère une erreur.  
  
 L’illustration suivante montre le processus qui détermine le jeu de versions surchargées à appeler.  
  
 ![Diagramme de flux du processus de résolution de surcharge](./media/overload-resolution/determine-overloaded-version.gif "Résolution des versions surchargées")
  
 L’exemple suivant illustre ce processus de résolution de surcharge.  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 Dans le premier appel, le compilateur élimine la première surcharge, car le type du premier argument ( `Short` ) est limité au type du paramètre correspondant ( `Byte` ). Il élimine ensuite la troisième surcharge, car chaque type d’argument de la deuxième surcharge ( `Short` et `Single` ) s’étend au type correspondant dans la troisième surcharge ( `Integer` et `Single` ). La deuxième surcharge nécessite moins d’élargissement, donc le compilateur l’utilise pour l’appel.  
  
 Dans le deuxième appel, le compilateur ne peut pas éliminer les surcharges sur la base de la fonction restrictive. Elle élimine la troisième surcharge pour la même raison que dans le premier appel, car elle peut appeler la deuxième surcharge avec moins d’élargissement des types d’arguments. Toutefois, le compilateur ne peut pas résoudre entre la première et la deuxième surcharge. Chaque possède un type de paramètre défini qui s’étend au type correspondant dans l’autre ( `Byte` à `Short` , mais `Single` à `Double` ). Par conséquent, le compilateur génère une erreur de résolution de surcharge.  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>Arguments facultatifs et ParamArray surchargés  
 Si deux surcharges d’une procédure ont des signatures identiques, sauf que le dernier paramètre est déclaré [facultatif](../../../language-reference/modifiers/optional.md) dans un et [ParamArray](../../../language-reference/modifiers/paramarray.md) dans l’autre, le compilateur résout un appel à cette procédure comme suit :  
  
|Si l’appel fournit le dernier argument comme|Le compilateur résout l’appel à la surcharge en déclarant le dernier argument comme|  
|---|---|  
|Aucune valeur (argument omis)|`Optional`|  
|Une valeur unique|`Optional`|  
|Deux valeurs ou plus dans une liste séparée par des virgules|`ParamArray`|  
|Tableau de n’importe quelle longueur (y compris un tableau vide)|`ParamArray`|  
  
## <a name="see-also"></a>Voir aussi

- [Paramètres facultatifs](./optional-parameters.md)
- [Tableaux de paramètres](./parameter-arrays.md)
- [Surcharge de procédure](./procedure-overloading.md)
- [Procédures de dépannage](./troubleshooting-procedures.md)
- [Comment : définir plusieurs versions d'une procédure](./how-to-define-multiple-versions-of-a-procedure.md)
- [Comment : appeler une procédure surchargée](./how-to-call-an-overloaded-procedure.md)
- [Comment : surcharger une procédure qui accepte des paramètres optionnels](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Considérations sur les surcharges de procédures](./considerations-in-overloading-procedures.md)
- [Surcharges](../../../language-reference/modifiers/overloads.md)
- [Méthodes d’extension](./extension-methods.md)
