---
title: Types de données
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], declaring
- typing
- data types [Visual Basic]
- Visual Basic code, data types
- data types [Visual Basic], improving speed with
ms.assetid: 5e1b9aaf-c7ca-4b29-9b22-0e82ed8e85e2
ms.openlocfilehash: 928d7fb6a40873641ae3e91e057c272b946a0091
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393713"
---
# <a name="data-types-in-visual-basic"></a>Types de données en Visual Basic
Le *type de données* d’un élément de programmation fait référence au type de données qu’il peut contenir et à la façon dont il stocke ces données. Les types de données s’appliquent à toutes les valeurs qui peuvent être stockées dans la mémoire de l’ordinateur ou qui participent à l’évaluation d’une expression. Chaque variable, littéral, constante, énumération, propriété, paramètre de procédure, argument de procédure et valeur de retour de procédure possède un type de données.  
  
## <a name="declared-data-types"></a>Types de données déclarés  
 Vous définissez un élément de programmation avec une instruction de déclaration et spécifiez son type de données avec la clause `As`. Le tableau suivant présente les instructions que vous utilisez pour déclarer divers éléments.  
  
|Élément de programmation|Déclaration de type de données|  
|-------------------------|---------------------------|  
|Variable|Dans une [instruction Dim](../../../language-reference/statements/dim-statement.md)<br /><br /> `Dim`   `amount As Double`<br /><br /> `Static`   `yourName As String`<br /><br /> `Public`   `billsPaid As Decimal = 0`|  
|Littéral|Avec un caractère de type de littéral ; consultez « Caractères de type de littéral » dans [Caractères de type](type-characters.md)<br /><br /> `Dim searchChar As Char = "."`  `C`|  
|Constant|Dans une [instruction Const](../../../language-reference/statements/const-statement.md)<br /><br /> `Const`   `modulus As Single = 4.17825F`|  
|Énumération|Dans une instruction [Enum](../../../language-reference/statements/enum-statement.md)<br /><br /> `Public`   `Enum`   `colors`|  
|Propriété|Dans une [instruction Property](../../../language-reference/statements/property-statement.md)<br /><br /> `Property`   `region() As String`|  
|Paramètre de procédure|Dans une [instruction Sub](../../../language-reference/statements/sub-statement.md), une [instruction Function](../../../language-reference/statements/function-statement.md) ou une [instruction Operator](../../../language-reference/statements/operator-statement.md)<br /><br /> `Sub addSale(ByVal`   `amount`   `As Double)`|  
|Argument de procédure|Dans le code appelant ; chaque argument est un élément de programmation qui a déjà été déclaré, ou une expression qui contient des éléments déclarés<br /><br /> `subString = Left(`  `inputString`  `,`   `5`  `)`|  
|Valeur de retour de procédure|Dans une [instruction Function](../../../language-reference/statements/function-statement.md) ou une [instruction Operator](../../../language-reference/statements/operator-statement.md)<br /><br /> `Function convert(ByVal b As Byte)`   `As String`|  
  
 Pour obtenir la liste des types de données Visual Basic, consultez [Types de données](../../../language-reference/data-types/index.md).  
  
## <a name="see-also"></a>Voir aussi

- [Caractères de type](type-characters.md)
- [Types de données élémentaires](elementary-data-types.md)
- [Types de données composites](composite-data-types.md)
- [Generic Types in Visual Basic](generic-types.md)
- [Types valeur et types référence](value-types-and-reference-types.md)
- [Conversions de type en Visual Basic](type-conversions.md)
- [Structures](structures.md)
- [Tuples](tuples.md)
- [Dépannage des types de données](troubleshooting-data-types.md)
- [Types de données](../../../language-reference/data-types/index.md)
- [Utilisation efficace des types de données](efficient-use-of-data-types.md)
