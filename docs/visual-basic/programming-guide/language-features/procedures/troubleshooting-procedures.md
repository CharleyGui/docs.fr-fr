---
title: Procédures de dépannage
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting Visual Basic, procedures
- procedures [Visual Basic], troubleshooting
- Visual Basic code, procedures
- troubleshooting procedures
- procedures [Visual Basic], about procedures
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
ms.openlocfilehash: 8d4c4929e299efb12d283492a101c18ae794110b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352513"
---
# <a name="troubleshooting-procedures-visual-basic"></a>Procédures de résolution des problèmes (Visual Basic)

Cette page répertorie certains problèmes courants qui peuvent se produire lors de l’utilisation de procédures.  
  
## <a name="returning-an-array-type-from-a-function-procedure"></a>Retour d’un type tableau à partir d’une procédure de fonction

Si une procédure `Function` retourne un type de données tableau, vous ne pouvez pas utiliser le nom `Function` pour stocker des valeurs dans les éléments du tableau. Si vous tentez de le faire, le compilateur l’interprète comme un appel à l' `Function`. L’exemple suivant génère des erreurs du compilateur :
  
```vb
Function AllOnes(n As Integer) As Integer()
   For i As Integer = 1 To n - 1  
      ' The following statement generates a COMPILER ERROR.  
      AllOnes(i) = 1  
   Next  

   ' The following statement generates a COMPILER ERROR.  
   Return AllOnes()  
End Function
```

L’instruction `AllOnes(i) = 1` génère une erreur du compilateur, car elle semble appeler `AllOnes` avec un argument de type de données incorrect (un `Integer` scalaire au lieu d’un tableau de `Integer`). L’instruction `Return AllOnes()` génère une erreur du compilateur, car elle semble appeler `AllOnes` sans argument.  
  
 **Approche correcte :** Pour être en mesure de modifier les éléments d’un tableau qui doit être retourné, définissez un tableau interne en tant que variable locale. L’exemple suivant compile sans erreur :

 [!code-vb[VbVbcnProcedures#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#66)]

## <a name="argument-not-modified-by-procedure-call"></a>Argument non modifié par l’appel de procédure

Si vous souhaitez autoriser une procédure à modifier un élément de programmation sous-jacent à un argument dans le code appelant, vous devez le passer par référence. Toutefois, une procédure peut accéder aux éléments d’un argument de type référence même si vous la transmettez par valeur.

- **Variable sous-jacente**. Pour permettre à la procédure de remplacer la valeur de l’élément de variable sous-jacent lui-même, la procédure doit déclarer le paramètre [ByRef](../../../language-reference/modifiers/byref.md). En outre, le code appelant ne doit pas placer l’argument entre parenthèses, car cela substituerait l' `ByRef` mécanisme de passage.

- **Éléments de type référence**. Si vous déclarez un paramètre [ByVal](../../../language-reference/modifiers/byval.md), la procédure ne peut pas modifier l’élément de variable sous-jacent lui-même. Toutefois, si l’argument est un type référence, la procédure peut modifier les membres de l’objet vers lequel il pointe, même s’il ne peut pas remplacer la valeur de la variable. Par exemple, si l’argument est une variable tableau, la procédure ne peut pas lui assigner un nouveau tableau, mais il peut modifier un ou plusieurs de ses éléments. Les éléments modifiés sont reflétés dans la variable de tableau sous-jacente dans le code appelant.

L’exemple suivant définit deux procédures qui prennent une variable tableau par valeur et opèrent sur ses éléments. La procédure `increase` ajoute simplement une à chaque élément. La procédure `replace` affecte un nouveau tableau au paramètre `a()` puis en ajoute un à chaque élément. Toutefois, la réassignation n’affecte pas la variable de tableau sous-jacente dans le code appelant, car `a()` est déclarée `ByVal`.

[!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]

[!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]

L’exemple suivant effectue des appels à `increase` et `replace`:

[!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]
  
Le premier appel `MsgBox` affiche « après l’augmentation (n) : 11, 21, 31, 41 ». Étant donné que `n` est un type référence, `increase` pouvez modifier ses membres, même s’il est passé `ByVal`.

Le deuxième `MsgBox` appel affiche « after Replace (n) : 11, 21, 31, 41 ». Étant donné que `n` est passé `ByVal`, `replace` ne peut pas modifier la variable `n` en lui assignant un nouveau tableau. Lorsque `replace` crée la nouvelle instance de tableau `k` et l’assigne à la variable locale `a`, elle perd la référence à `n` passé par le code appelant. Lorsqu’il incrémente les membres de `a`, seul le groupe local `k` est affecté.

**Approche correcte :** Pour être en mesure de modifier un élément de variable sous-jacent lui-même, transmettez-le par référence. L’exemple suivant illustre la modification apportée à la déclaration de `replace` qui lui permet de remplacer un tableau par un autre dans le code appelant :

[!code-vb[VbVbcnProcedures#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#64)]

## <a name="unable-to-define-an-overload"></a>Impossible de définir une surcharge

Si vous souhaitez définir une version surchargée d’une procédure, vous devez utiliser le même nom, mais une signature différente. Si le compilateur ne peut pas différencier votre déclaration d’une surcharge avec la même signature, il génère une erreur.

La *signature* d’une procédure est déterminée par le nom de la procédure et la liste de paramètres. Chaque surcharge doit avoir le même nom que toutes les autres surcharges, mais elle doit être différente de toutes les autres dans au moins l’un des autres composants de la signature. Pour plus d'informations, consultez [Procedure Overloading](./procedure-overloading.md).

Les éléments suivants, même s’ils se rapportent à la liste de paramètres, ne sont pas des composants de la signature d’une procédure :

- Mots clés de modificateur de procédure, tels que `Public`, `Shared`et `Static`.
- Noms de paramètres.
- Mots clés de modificateur de paramètre, tels que `ByRef` et `Optional`.
- Type de données de la valeur de retour (à l’exception d’un opérateur de conversion).

Vous ne pouvez pas surcharger une procédure en faisant varier un ou plusieurs des éléments précédents.

**Approche correcte :** Pour pouvoir définir une surcharge de procédure, vous devez faire varier la signature. Étant donné que vous devez utiliser le même nom, vous devez faire varier le nombre, l’ordre ou les types de données des paramètres. Dans une procédure générique, vous pouvez faire varier le nombre de paramètres de type. Dans un opérateur de conversion ([fonction CType](../../../language-reference/functions/ctype-function.md)), vous pouvez faire varier le type de retour.

### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>Résolution de surcharge avec des arguments facultatifs et ParamArray

Si vous surchargez une procédure avec un ou plusieurs paramètres [facultatifs](../../../language-reference/modifiers/optional.md) ou un paramètre [ParamArray](../../../language-reference/modifiers/paramarray.md) , vous devez éviter de dupliquer les *surcharges implicites*. Pour plus d’informations, consultez [Considérations sur la surcharge des procédures](./considerations-in-overloading-procedures.md).

## <a name="calling-the-wrong-version-of-an-overloaded-procedure"></a>Appel d’une version incorrecte d’une procédure surchargée

Si une procédure a plusieurs versions surchargées, vous devez connaître toutes les listes de paramètres et comprendre comment Visual Basic résout les appels entre les surcharges. Sinon, vous pouvez appeler une surcharge autre que celle prévue.

Une fois que vous avez déterminé la surcharge que vous souhaitez appeler, veillez à respecter les règles suivantes :

- Fournissez le nombre correct d’arguments et dans le bon ordre.  
- Dans l’idéal, vos arguments doivent avoir exactement les mêmes types de données que les paramètres correspondants. Dans tous les cas, le type de données de chaque argument doit être étendu à celui de son paramètre correspondant. Cela est vrai même si l' [instruction Option Strict](../../../language-reference/statements/option-strict-statement.md) est définie sur `Off`. Si une surcharge requiert une conversion restrictive de la liste d’arguments, cette surcharge ne peut pas être appelée.
- Si vous fournissez des arguments qui requièrent l’élargissement, rendez leurs types de données aussi proches que possible des types de données de paramètre correspondants. Si au moins deux surcharges acceptent vos types de données d’argument, le compilateur résout votre appel à la surcharge qui appelle pour l’élargissement le plus faible.

Vous pouvez réduire le risque d’incompatibilités de type de données à l’aide du mot clé [CType Function](../../../language-reference/functions/ctype-function.md) conversion lors de la préparation de vos arguments.

### <a name="overload-resolution-failure"></a>Échec de résolution de surcharge

Quand vous appelez une procédure surchargée, le compilateur tente d’éliminer toutes les surcharges sauf une. Si elle est réussie, elle résout l’appel à cette surcharge. S’il élimine toutes les surcharges, ou s’il ne peut pas réduire les surcharges éligibles à un seul candidat, il génère une erreur.

L’exemple suivant illustre le processus de résolution de surcharge :

[!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]

[!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]
  
Dans le premier appel, le compilateur élimine la première surcharge, car le type du premier argument (`Short`) est limité au type du paramètre correspondant (`Byte`). Il élimine ensuite la troisième surcharge, car chaque type d’argument de la deuxième surcharge (`Short` et `Single`) s’étend au type correspondant dans la troisième surcharge (`Integer` et `Single`). La deuxième surcharge nécessite moins d’élargissement, donc le compilateur l’utilise pour l’appel.

Dans le deuxième appel, le compilateur ne peut pas éliminer les surcharges sur la base de la fonction restrictive. Elle élimine la troisième surcharge pour la même raison que dans le premier appel, car elle peut appeler la deuxième surcharge avec moins d’élargissement des types d’arguments. Toutefois, le compilateur ne peut pas résoudre entre la première et la deuxième surcharge. Chacun a un type de paramètre défini qui s’étend au type correspondant dans l’autre (`Byte` à `Short`, mais `Single` à `Double`). Par conséquent, le compilateur génère une erreur de résolution de surcharge.

**Approche correcte :** Pour pouvoir appeler une procédure surchargée sans ambiguïté, utilisez la [fonction CType](../../../language-reference/functions/ctype-function.md) pour faire correspondre les types de données d’argument aux types de paramètres. L’exemple suivant montre un appel à `z` qui force la résolution de la deuxième surcharge.

[!code-vb[VbVbcnProcedures#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#65)]

### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>Résolution de surcharge avec des arguments facultatifs et ParamArray

Si deux surcharges d’une procédure ont des signatures identiques, sauf que le dernier paramètre est déclaré [facultatif](../../../language-reference/modifiers/optional.md) dans un et [ParamArray](../../../language-reference/modifiers/paramarray.md) dans l’autre, le compilateur résout un appel à cette procédure en fonction de la correspondance la plus proche. Pour plus d'informations, consultez [Overload Resolution](./overload-resolution.md).

## <a name="see-also"></a>Voir aussi

- [Procédures](index.md)
- [Procédures Sub](sub-procedures.md)
- [Procédures Function](function-procedures.md)
- [Procédures de propriété](property-procedures.md)
- [Procédures d’opérateur](operator-procedures.md)
- [Paramètres et arguments d’une procédure](procedure-parameters-and-arguments.md)
- [Surcharge de procédure](procedure-overloading.md)
- [Considérations sur les surcharges de procédures](considerations-in-overloading-procedures.md)
- [Résolution de surcharge](overload-resolution.md)
