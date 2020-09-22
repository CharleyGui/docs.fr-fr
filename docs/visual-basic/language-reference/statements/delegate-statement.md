---
title: Delegate, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.Delegate
helpviewer_keywords:
- delegate keyword [Visual Basic]
- Delegate statement [Visual Basic]
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
ms.openlocfilehash: 29de4c174273c3c6c0d4f0cea1ee6dc254a1339b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866653"
---
# <a name="delegate-statement"></a>Delegate, instruction

Utilisé pour déclarer un délégué. Un délégué est un type référence qui fait référence à une `Shared` méthode d’un type ou à une méthode d’instance d’un objet. Toute procédure avec des types de paramètres et de retour correspondants peut être utilisée pour créer une instance de cette classe déléguée. La procédure peut ensuite être appelée par le biais de l’instance de délégué.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>Éléments  
  
|Terme|Définition|  
|---|---|  
|`attrlist`|Optionnel. Liste des attributs qui s’appliquent à ce délégué. Les attributs multiples sont séparés par des virgules. Vous devez placer la [liste des attributs](attribute-list.md) entre crochets pointus (« `<` » et «» `>` ).|  
|`accessmodifier`|Optionnel. Spécifie le code qui peut accéder au délégué. Il peut s'agir d'une des méthodes suivantes :<br /><br /> - [Public](../modifiers/public.md). Tout code pouvant accéder à l’élément qui déclare le délégué peut y accéder.<br />-   [Protégé](../modifiers/protected.md). Seul le code dans la classe du délégué ou une classe dérivée peut y accéder.<br />-   [Friend](../modifiers/friend.md). Seul le code dans le même assembly peut accéder au délégué.<br />- [Privée](../modifiers/private.md). Seul le code de l’élément qui déclare le délégué peut y accéder.<br /><br /> - [Ami protégé](../modifiers/protected-friend.md) Seul le code dans la classe du délégué, une classe dérivée ou le même assembly peut accéder au délégué. <br />- [Protégé privé](../modifiers/private-protected.md) Seul le code dans la classe du délégué ou dans une classe dérivée dans le même assembly peut accéder au délégué. |  
|`Shadows`|Optionnel. Indique que ce délégué redéclare et masque un élément de programmation portant le même nom, ou un ensemble d’éléments surchargés, dans une classe de base. Vous pouvez occulter tout type d'élément déclaré par un autre type.<br /><br /> Un élément occulté n'est pas disponible à partir de la classe dérivée qui l'occulte, sauf à partir de l'emplacement où l'élément d'occultation est inaccessible. Par exemple, si un `Private` élément occulte un élément de classe de base, le code qui n’a pas l’autorisation d’accéder à l' `Private` élément accède à l’élément de classe de base à la place.|  
|`Sub`|Facultatif, mais `Sub` ou `Function` doivent apparaître. Déclare cette procédure comme une procédure déléguée `Sub` qui ne retourne pas de valeur.|  
|`Function`|Facultatif, mais `Sub` ou `Function` doivent apparaître. Déclare cette procédure comme une procédure déléguée `Function` qui retourne une valeur.|  
|`name`|Obligatoire. Nom du type délégué ; suit les conventions d’affectation de noms de variables standard.|  
|`typeparamlist`|Optionnel. Liste des paramètres de type pour ce délégué. Plusieurs paramètres de type sont séparés par des virgules. Éventuellement, chaque paramètre de type peut être déclaré variant à l’aide `In` des `Out` modificateurs génériques et. Vous devez placer la [liste de types](type-list.md) entre parenthèses et l’introduire avec le `Of` mot clé.|  
|`parameterlist`|Optionnel. Liste des paramètres qui sont passés à la procédure quand elle est appelée. Vous devez placer la [liste de paramètres](parameter-list.md) entre parenthèses.|  
|`type`|Obligatoire si vous spécifiez une `Function` procédure. Type de données de la valeur de retour.|  
  
## <a name="remarks"></a>Notes  

 L' `Delegate` instruction définit le paramètre et les types de retour d’une classe déléguée. Toute procédure ayant des paramètres et des types de retour correspondants peut être utilisée pour créer une instance de cette classe déléguée. La procédure peut ensuite être appelée par le biais de l’instance de délégué, en appelant la méthode du délégué `Invoke` .  
  
 Les délégués peuvent être déclarés au niveau de l’espace de noms, du module, de la classe ou de la structure, mais pas au sein d’une procédure.  
  
 Chaque classe déléguée définit un constructeur auquel les caractéristiques d’une méthode objet sont passées. L’argument d’un constructeur délégué doit être une référence à une méthode ou une expression lambda.  
  
 Pour spécifier une référence à une méthode, utilisez la syntaxe suivante :  
  
 `AddressOf` [`expression`.]`methodname`  
  
 Le type de compilation de `expression` doit être le nom d’une classe ou d’une interface qui contient une méthode portant le nom spécifié, dont la signature corresponde à celle de la classe déléguée. La méthode `methodname` peut être une méthode partagée ou d’instance. `methodname` n’est pas facultatif, même si l’on crée un délégué pour la méthode par défaut de la classe.  
  
 Pour spécifier une expression lambda, utilisez la syntaxe suivante :  
  
 `Function` ([`parm` As `type`, `parm2` As `type2`, ...]) `expression`  
  
 La signature de la fonction doit correspondre à celle du type délégué. Pour plus d’informations sur les expressions lambda, consultez [expressions lambda](../../programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Pour plus d’informations sur les délégués, consultez [Délégués](../../programming-guide/language-features/delegates/index.md).  
  
## <a name="example"></a>Exemple  

 L’exemple suivant utilise l' `Delegate` instruction pour déclarer un délégué pour le fonctionnement sur deux nombres et retourner un nombre. La `DelegateTest` méthode prend une instance d’un délégué de ce type et l’utilise pour fonctionner sur des paires de nombres.  
  
 [!code-vb[VbVbalrDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Voir aussi

- [AddressOf, opérateur](../operators/addressof-operator.md)
- [Of](of-clause.md)
- [Délégués](../../programming-guide/language-features/delegates/index.md)
- [Procédure : Utiliser une classe générique](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Covariance et contravariance](../../programming-guide/concepts/covariance-contravariance/index.md)
- [Dans](../modifiers/in-generic-modifier.md)
- [Sortie](../modifiers/out-generic-modifier.md)
