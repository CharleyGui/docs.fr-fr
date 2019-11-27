---
title: 'Comment : déclarer des énumérations'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: 042aea045313bcaf3832274acf1000f87a084b72
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354042"
---
# <a name="how-to-declare-enumerations-visual-basic"></a>Comment : déclarer des énumérations (Visual Basic)
Vous créez une énumération avec l’instruction `Enum` dans la section déclarations d’une classe ou d’un module. Vous ne pouvez pas déclarer une énumération dans une méthode. Pour spécifier le niveau d’accès approprié, utilisez `Private`, `Protected`, `Friend`ou `Public`.  
  
 Un type de `Enum` a un nom, un type sous-jacent et un ensemble de champs, chacun représentant une constante. Le nom doit être un qualificateur Visual Basic .NET valide. Le type sous-jacent doit être l’un des types d’entiers,`Byte`, `Short`, `Long` ou `Integer`. `Integer` est la valeur par défaut. Les énumérations sont toujours fortement typées et ne sont pas interchangeables avec des types de nombres entiers.  
  
 Les énumérations ne peuvent pas avoir de valeurs à virgule flottante. Si une valeur à virgule flottante est assignée à une énumération avec `Option Strict On`, une erreur de compilateur se produit. Si `Option Strict` est `Off`, la valeur est automatiquement convertie en type de `Enum`.  
  
 Pour plus d’informations sur les noms et sur l’utilisation de l’instruction `Imports` pour rendre la qualification de nom inutile, consultez [énumérations et qualification de nom](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
### <a name="to-declare-an-enumeration"></a>Pour déclarer une énumération  
  
1. Écrivez une déclaration qui comprend un niveau d’accès au code, le mot clé `Enum` et un nom valide, comme dans les exemples suivants, chacun d’entre eux déclarant un `Enum`différent.  
  
     [!code-vb[VbEnumsTask#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#3)]  
  
2. Définissez les constantes dans l’énumération. Par défaut, la première constante d’une énumération est initialisée à `0`, et les constantes suivantes sont initialisées à une valeur supérieure à la constante précédente. Par exemple, l’énumération suivante, `Days`, contient une constante nommée `Sunday` avec la valeur `0`, une constante nommée `Monday` avec la valeur `1`, une constante nommée `Tuesday` avec la valeur de `2`, et ainsi de suite.  
  
     [!code-vb[VbEnumsTask#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#4)]  
  
3. Vous pouvez assigner explicitement des valeurs à des constantes dans une énumération à l’aide d’une instruction d’assignation. Vous pouvez assigner n’importe quelle valeur entière, y compris des nombres négatifs. Par exemple, vous pouvez souhaiter que les constantes avec des valeurs inférieures à zéro représentent des conditions d’erreur. Dans l’énumération suivante, la valeur de la constante `Invalid` est explicitement assignée à la valeur `–1`et la valeur `0`est assignée à la constante `Sunday`. Étant donné qu’il s’agit de la première constante de l’énumération, `Saturday` est également initialisé à la valeur `0`. La valeur de `Monday` est `1` (une valeur supérieure à la valeur de `Sunday`); la valeur de `Tuesday` est `2`, et ainsi de suite.  
  
     [!code-vb[VbEnumsTask#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#5)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>Pour déclarer une énumération en tant que type explicite  
  
- Spécifiez le type de l’énumération à l’aide de la clause `As`, comme indiqué dans l’exemple suivant.  
  
     [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations et qualification de noms](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Guide pratique : faire référence à un membre d’énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Comment : itérer au sein d’une énumération dans Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Guide pratique : déterminer la chaîne associée à une valeur d’énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Quand utiliser une énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Vue d’ensemble des constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Constantes et types de données littérales](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Constantes et énumérations](../../../../visual-basic/language-reference/constants-and-enumerations.md)
