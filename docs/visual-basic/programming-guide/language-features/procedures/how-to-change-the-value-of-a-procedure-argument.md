---
title: 'Comment : modifier la valeur d’un argument de la procédure'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
ms.openlocfilehash: 46cf9062d01e248b6e90882a923a48210780f7f4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388502"
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a>Comment : modifier la valeur d'un argument de la procédure (Visual Basic)
Lorsque vous appelez une procédure, chaque argument que vous fournissez correspond à l’un des paramètres définis dans la procédure. Dans certains cas, le code de la procédure peut modifier la valeur sous-jacente d’un argument dans le code appelant. Dans d’autres cas, la procédure ne peut modifier que la copie locale d’un argument.  
  
 Quand vous appelez la procédure, Visual Basic effectue une copie locale de chaque argument qui est passé en [ByVal](../../../language-reference/modifiers/byval.md). Pour chaque argument passé [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic donne au code de procédure une référence directe à l’élément de programmation sous-jacent à l’argument dans le code appelant.  
  
 Si l’élément sous-jacent dans le code appelant est un élément modifiable et que l’argument est passé `ByRef` , le code de la procédure peut utiliser la référence directe pour modifier la valeur de l’élément dans le code appelant.  
  
## <a name="changing-the-underlying-value"></a>Modification de la valeur sous-jacente  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a>Pour modifier la valeur sous-jacente d’un argument de procédure dans le code appelant  
  
1. Dans la déclaration de procédure, spécifiez [ByRef](../../../language-reference/modifiers/byref.md) pour le paramètre correspondant à l’argument.  
  
2. Dans le code appelant, passer un élément de programmation modifiable comme argument.  
  
3. Dans le code appelant, ne placez pas l’argument entre parenthèses dans la liste d’arguments.  
  
4. Dans le code de la procédure, utilisez le nom du paramètre pour assigner une valeur à l’élément sous-jacent dans le code appelant.  
  
 Pour une démonstration, reportez-vous à l’exemple.  
  
## <a name="changing-local-copies"></a>Modification des copies locales  
 Si l’élément sous-jacent dans le code appelant est un élément non modifiable, ou si l’argument est passé `ByVal` , la procédure ne peut pas modifier sa valeur dans le code appelant. Toutefois, la procédure peut modifier sa copie locale d’un tel argument.  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a>Pour modifier la copie d’un argument de procédure dans le code de la procédure  
  
1. Dans la déclaration de procédure, spécifiez [ByVal](../../../language-reference/modifiers/byval.md) pour le paramètre correspondant à l’argument.  
  
     -ou-  
  
     Dans le code appelant, mettez l’argument entre parenthèses dans la liste d’arguments. Cela oblige Visual Basic à passer l’argument par valeur, même si le paramètre correspondant spécifie `ByRef` .  
  
2. Dans le code de la procédure, utilisez le nom du paramètre pour assigner une valeur à la copie locale de l’argument. La valeur sous-jacente dans le code appelant n’est pas modifiée.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre deux procédures qui prennent une variable tableau et opèrent sur ses éléments. La `increase` procédure ajoute simplement une à chaque élément. La `replace` procédure assigne un nouveau tableau au paramètre `a()` , puis ajoute un à chaque élément.  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#36)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 Le premier `MsgBox` appel affiche « après l’augmentation (n) : 11, 21, 31, 41 ». Étant donné que le tableau `n` est un type référence, `replace` peut modifier ses membres, même si le mécanisme de passage est `ByVal` .  
  
 Le deuxième `MsgBox` appel affiche « after Replace (n) : 101, 201, 301 ». Étant donné que `n` est passé `ByRef` , `replace` peut modifier la variable `n` dans le code appelant et lui assigner un nouveau tableau. Étant donné que `n` est un type référence, `replace` peut également modifier ses membres.  
  
 Vous pouvez empêcher la procédure de modifier la variable elle-même dans le code appelant. Consultez [Comment : protéger un argument de procédure contre les modifications de valeur](./how-to-protect-a-procedure-argument-against-value-changes.md).  
  
## <a name="compile-the-code"></a>Compiler le code  
 Lorsque vous transmettez une variable par référence, vous devez utiliser le `ByRef` mot clé pour spécifier ce mécanisme.  
  
 La valeur par défaut de Visual Basic consiste à passer des arguments par valeur. Toutefois, il est recommandé d’inclure le mot clé [ByVal](../../../language-reference/modifiers/byval.md) ou [ByRef](../../../language-reference/modifiers/byref.md) avec chaque paramètre déclaré. Cela rend votre code plus facile à lire.  
  
## <a name="net-framework-security"></a>Sécurité du .NET Framework  
 Il existe toujours un risque potentiel d’autoriser une procédure à modifier la valeur sous-jacente d’un argument dans le code appelant. Veillez à ce que cette valeur soit modifiée et soyez prêt à vérifier sa validité avant de l’utiliser.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Comment : passer des arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md)
- [Passage des arguments par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)
- [Différences entre les arguments modifiables et non modifiables](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Différences entre le passage d'un argument par valeur et par référence](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Comment : protéger un argument de procédure contre les modifications de valeur](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Comment : forcer le passage d'un argument par valeur](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Passage des arguments par position et par nom](./passing-arguments-by-position-and-by-name.md)
- [Types valeur et types référence](../data-types/value-types-and-reference-types.md)
