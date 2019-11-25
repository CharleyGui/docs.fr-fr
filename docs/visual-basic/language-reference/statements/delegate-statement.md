---
title: Delegate, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.Delegate
helpviewer_keywords:
- delegate keyword [Visual Basic]
- Delegate statement [Visual Basic]
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
ms.openlocfilehash: 662d2c3c0767adfe406e0a6f1b1e6dccd704e795
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354072"
---
# <a name="delegate-statement"></a>Delegate, instruction
Used to declare a delegate. A delegate is a reference type that refers to a `Shared` method of a type or to an instance method of an object. Any procedure with matching parameter and return types can be used to create an instance of this delegate class. The procedure can then later be invoked by means of the delegate instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`attrlist`|Optionnel. List of attributes that apply to this delegate. Les attributs multiples sont séparés par des virgules. You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").|  
|`accessmodifier`|Optionnel. Specifies what code can access the delegate. Il peut s'agir d'une des valeurs suivantes :<br /><br /> - [Public](../../../visual-basic/language-reference/modifiers/public.md). Any code that can access the element that declares the delegate can access it.<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md). Only code within the delegate's class or a derived class can access it.<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md). Only code within the same assembly can access the delegate.<br />- [Private](../../../visual-basic/language-reference/modifiers/private.md). Only code within the element that declares the delegate can access it.<br /><br /> - [Protected Friend](../../language-reference/modifiers/protected-friend.md) Only code within the delegate's class, a derived class, or the same assembly can access the delegate. <br />- [Private Protected](../../language-reference/modifiers/private-protected.md) Only code within the delegate's class or in a derived class in the same assembly can access the delegate. |  
|`Shadows`|Optionnel. Indicates that this delegate redeclares and hides an identically named programming element, or set of overloaded elements, in a base class. Vous pouvez occulter tout type d'élément déclaré par un autre type.<br /><br /> Un élément occulté n'est pas disponible à partir de la classe dérivée qui l'occulte, sauf à partir de l'emplacement où l'élément d'occultation est inaccessible. For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.|  
|`Sub`|Optional, but either `Sub` or `Function` must appear. Declares this procedure as a delegate `Sub` procedure that does not return a value.|  
|`Function`|Optional, but either `Sub` or `Function` must appear. Declares this procedure as a delegate `Function` procedure that returns a value.|  
|`name`|Requis. Name of the delegate type; follows standard variable naming conventions.|  
|`typeparamlist`|Optionnel. List of type parameters for this delegate. Multiple type parameters are separated by commas. Optionally, each type parameter can be declared variant by using `In` and `Out` generic modifiers. You must enclose the [Type List](../../../visual-basic/language-reference/statements/type-list.md) in parentheses and introduce it with the `Of` keyword.|  
|`parameterlist`|Optionnel. List of parameters that are passed to the procedure when it is called. You must enclose the [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md) in parentheses.|  
|`type`|Required if you specify a `Function` procedure. Data type of the return value.|  
  
## <a name="remarks"></a>Notes  
 The `Delegate` statement defines the parameter and return types of a delegate class. Any procedure with matching parameters and return types can be used to create an instance of this delegate class. The procedure can then later be invoked by means of the delegate instance, by calling the delegate's `Invoke` method.  
  
 Delegates can be declared at the namespace, module, class, or structure level, but not within a procedure.  
  
 Chaque classe déléguée définit un constructeur auquel les caractéristiques d’une méthode objet sont passées. L’argument d’un constructeur délégué doit être une référence à une méthode ou une expression lambda.  
  
 Pour spécifier une référence à une méthode, utilisez la syntaxe suivante :  
  
 `AddressOf` [`expression`.]`methodname`  
  
 Le type de compilation de `expression` doit être le nom d’une classe ou d’une interface qui contient une méthode portant le nom spécifié, dont la signature corresponde à celle de la classe déléguée. La méthode `methodname` peut être une méthode partagée ou d’instance. `methodname` n’est pas facultatif, même si l’on crée un délégué pour la méthode par défaut de la classe.  
  
 Pour spécifier une expression lambda, utilisez la syntaxe suivante :  
  
 `Function` ([`parm` As `type`, `parm2` As `type2`, ...]) `expression`  
  
 La signature de la fonction doit correspondre à celle du type délégué. Pour plus d’informations sur les expressions lambda, consultez [Expressions Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Pour plus d’informations sur les délégués, consultez [Délégués](../../../visual-basic/programming-guide/language-features/delegates/index.md).  
  
## <a name="example"></a>Exemple  
 The following example uses the `Delegate` statement to declare a delegate for operating on two numbers and returning a number. The `DelegateTest` method takes an instance of a delegate of this type and uses it to operate on pairs of numbers.  
  
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
