---
title: Instruction Delegate (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Delegate
helpviewer_keywords:
- delegate keyword [Visual Basic]
- Delegate statement [Visual Basic]
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
ms.openlocfilehash: 4a8260da4d2224551de71fd54f734007c7fa214f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583458"
---
# <a name="delegate-statement"></a>Delegate, instruction
Utilisé pour déclarer un délégué. Un délégué est un type référence qui fait référence à une méthode `Shared` d’un type ou à une méthode d’instance d’un objet. Toute procédure avec des types de paramètres et de retour correspondants peut être utilisée pour créer une instance de cette classe déléguée. La procédure peut ensuite être appelée par le biais de l’instance de délégué.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`attrlist`|Optionnel. Liste des attributs qui s’appliquent à ce délégué. Les attributs multiples sont séparés par des virgules. Vous devez placer la [liste des attributs](../../../visual-basic/language-reference/statements/attribute-list.md) entre crochets pointus (« `<` » et « `>` »).|  
|`accessmodifier`|Optionnel. Spécifie le code qui peut accéder au délégué. Il peut s'agir d'une des valeurs suivantes :<br /><br /> - [public](../../../visual-basic/language-reference/modifiers/public.md). Tout code pouvant accéder à l’élément qui déclare le délégué peut y accéder.<br />-   [protégé](../../../visual-basic/language-reference/modifiers/protected.md). Seul le code dans la classe du délégué ou une classe dérivée peut y accéder.<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md). Seul le code dans le même assembly peut accéder au délégué.<br />- [privé](../../../visual-basic/language-reference/modifiers/private.md). Seul le code de l’élément qui déclare le délégué peut y accéder.<br /><br /> -  code[Friend protégé](../../language-reference/modifiers/protected-friend.md) uniquement dans la classe du délégué, dans une classe dérivée ou dans le même assembly peut accéder au délégué. <br />-  code[privé protégé](../../language-reference/modifiers/private-protected.md) uniquement dans la classe du délégué ou dans une classe dérivée dans le même assembly peut accéder au délégué. |  
|`Shadows`|Optionnel. Indique que ce délégué redéclare et masque un élément de programmation portant le même nom, ou un ensemble d’éléments surchargés, dans une classe de base. Vous pouvez occulter tout type d'élément déclaré par un autre type.<br /><br /> Un élément occulté n'est pas disponible à partir de la classe dérivée qui l'occulte, sauf à partir de l'emplacement où l'élément d'occultation est inaccessible. Par exemple, si un élément `Private` occulte un élément de classe de base, le code qui n’est pas autorisé à accéder à l’élément `Private` accède à l’élément de classe de base à la place.|  
|`Sub`|Facultatif, mais `Sub` ou `Function` doivent apparaître. Déclare cette procédure en tant que délégué `Sub` procédure qui ne retourne pas de valeur.|  
|`Function`|Facultatif, mais `Sub` ou `Function` doivent apparaître. Déclare cette procédure en tant que délégué `Function` procédure qui retourne une valeur.|  
|`name`|Requis. Nom du type délégué ; suit les conventions d’affectation de noms de variables standard.|  
|`typeparamlist`|Optionnel. Liste des paramètres de type pour ce délégué. Plusieurs paramètres de type sont séparés par des virgules. Si vous le souhaitez, chaque paramètre de type peut être déclaré variant à l’aide des modificateurs génériques `In` et `Out`. Vous devez placer la [liste de types](../../../visual-basic/language-reference/statements/type-list.md) entre parenthèses et l’introduire avec le mot clé `Of`.|  
|`parameterlist`|Optionnel. Liste des paramètres qui sont passés à la procédure quand elle est appelée. Vous devez placer la [liste de paramètres](../../../visual-basic/language-reference/statements/parameter-list.md) entre parenthèses.|  
|`type`|Obligatoire si vous spécifiez une procédure `Function`. Type de données de la valeur de retour.|  
  
## <a name="remarks"></a>Notes  
 L’instruction `Delegate` définit le paramètre et les types de retour d’une classe déléguée. Toute procédure ayant des paramètres et des types de retour correspondants peut être utilisée pour créer une instance de cette classe déléguée. La procédure peut ensuite être appelée par le biais de l’instance de délégué, en appelant la méthode `Invoke` du délégué.  
  
 Les délégués peuvent être déclarés au niveau de l’espace de noms, du module, de la classe ou de la structure, mais pas au sein d’une procédure.  
  
 Chaque classe déléguée définit un constructeur auquel les caractéristiques d’une méthode objet sont passées. L’argument d’un constructeur délégué doit être une référence à une méthode ou une expression lambda.  
  
 Pour spécifier une référence à une méthode, utilisez la syntaxe suivante :  
  
 `AddressOf` [`expression`.]`methodname`  
  
 Le type de compilation de `expression` doit être le nom d’une classe ou d’une interface qui contient une méthode portant le nom spécifié, dont la signature corresponde à celle de la classe déléguée. La méthode `methodname` peut être une méthode partagée ou d’instance. `methodname` n’est pas facultatif, même si l’on crée un délégué pour la méthode par défaut de la classe.  
  
 Pour spécifier une expression lambda, utilisez la syntaxe suivante :  
  
 `Function` ([`parm` As `type`, `parm2` As `type2`, ...]) `expression`  
  
 La signature de la fonction doit correspondre à celle du type délégué. Pour plus d’informations sur les expressions lambda, consultez [Expressions Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Pour plus d’informations sur les délégués, consultez [Délégués](../../../visual-basic/programming-guide/language-features/delegates/index.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’instruction `Delegate` pour déclarer un délégué pour le fonctionnement sur deux nombres et retourner un nombre. La méthode `DelegateTest` prend une instance d’un délégué de ce type et l’utilise pour fonctionner sur des paires de nombres.  
  
 [!code-vb[VbVbalrDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Voir aussi

- [AddressOf (opérateur)](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Of](../../../visual-basic/language-reference/statements/of-clause.md)
- [Délégués](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Guide pratique : utiliser une classe générique](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Covariance et contravariance](../../programming-guide/concepts/covariance-contravariance/index.md)
- [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
