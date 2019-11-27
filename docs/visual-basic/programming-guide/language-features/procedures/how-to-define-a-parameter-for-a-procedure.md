---
title: 'Comment : définir un paramètre pour une procédure'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
ms.openlocfilehash: 411959a7be92ea49a59558b508e992bfba8eff95
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344883"
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a>Comment : définir un paramètre pour une procédure (Visual Basic)
Un *paramètre* permet au code appelant de passer une valeur à la procédure lorsqu’il l’appelle. Vous déclarez chaque paramètre d’une procédure de la même façon que vous déclarez une variable, en spécifiant son nom et son type de données. Vous spécifiez également le mécanisme de passage et indiquez si le paramètre est facultatif.  
  
 Pour plus d’informations, consultez [paramètres et arguments](./procedure-parameters-and-arguments.md)d’une procédure.  
  
### <a name="to-define-a-procedure-parameter"></a>Pour définir un paramètre de procédure  
  
1. Dans la déclaration de procédure, ajoutez le nom du paramètre à la liste de paramètres de la procédure, en le séparant des autres paramètres par des virgules.  
  
2. Déterminez le type de données du paramètre.  
  
3. Suivez le nom du paramètre avec une clause `As` pour spécifier le type de données.  
  
4. Déterminez le mécanisme de passage souhaité pour le paramètre. Normalement, vous passez un paramètre par valeur, sauf si vous souhaitez que la procédure soit en mesure de modifier sa valeur dans le code appelant.  
  
5. Faites précéder le nom du paramètre de [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) pour spécifier le mécanisme de passage. Pour plus d’informations, consultez [différences entre le passage d’un argument par valeur et par référence](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
6. Si le paramètre est facultatif, faites précéder le mécanisme de passage de la valeur [facultative](../../../../visual-basic/language-reference/modifiers/optional.md) et suivez le type de données du paramètre avec un signe égal (`=`) et une valeur par défaut.  
  
     L’exemple suivant définit le contour d’une procédure `Sub` avec trois paramètres. Les deux premiers sont requis et le troisième est facultatif. Les déclarations de paramètres sont séparées par des virgules dans la liste de paramètres.  
  
     [!code-vb[VbVbcnProcedures#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#33)]  
  
     Le premier paramètre accepte un objet `customer`, et `updateCustomer` peut directement mettre à jour la variable passée à `c`, car l’argument est passé par [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md). La procédure ne peut pas modifier les valeurs des deux derniers arguments, car elles sont passées en [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).  
  
     Si le code appelant ne fournit pas de valeur pour le paramètre `level`, Visual Basic le définit sur la valeur par défaut 0.  
  
     Si le commutateur de vérification de type ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) est `Off`, la clause `As` est facultative lorsque vous définissez un paramètre. Toutefois, si un paramètre utilise une clause `As`, ils doivent tous l’utiliser. Si le commutateur de vérification de type est `On`, la clause `As` est requise pour chaque définition de paramètre.  
  
     La spécification des types de données pour tous vos éléments de programmation est connue sous le nom de *typage fort*. Lorsque vous définissez `Option Strict On`, Visual Basic applique un typage fort. Cette recommandation est vivement recommandée pour les raisons suivantes :  
  
    - Il permet la prise en charge d’IntelliSense pour vos variables et paramètres. Cela vous permet de voir leurs propriétés et d’autres membres au fur et à mesure que vous tapez dans votre code.  
  
    - Elle permet au compilateur d’effectuer une vérification de type. Cela permet d’intercepter les instructions qui peuvent échouer au moment de l’exécution en raison d’erreurs telles que le dépassement de capacité. Il intercepte également les appels aux méthodes sur les objets qui ne les prennent pas en charge.  
  
    - Cela permet d’accélérer l’exécution de votre code. Cela est dû au fait que si vous ne spécifiez pas de type de données pour un élément de programmation, le compilateur Visual Basic lui assigne le type de `Object`. Votre code compilé peut être obligé de passer de l’un à l’autre `Object` et d’autres types de données, ce qui réduit les performances.  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Procédures Sub](./sub-procedures.md)
- [Procédures Function](./function-procedures.md)
- [Guide pratique : passer des arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md)
- [Passage d’un argument par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)
- [Procédures récursives](./recursive-procedures.md)
- [Surcharge de procédure](./procedure-overloading.md)
- [Objets et classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Programmation orientée objet (Visual Basic)](../../concepts/object-oriented-programming.md)
