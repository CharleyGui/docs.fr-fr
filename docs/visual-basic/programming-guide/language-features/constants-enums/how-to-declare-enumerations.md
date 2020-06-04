---
title: 'Guide pratique : déclarer des énumérations'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: c8f228c205c93adf7f2f555dc840a7daac61950b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414451"
---
# <a name="how-to-declare-enumerations-visual-basic"></a>Comment : déclarer des énumérations (Visual Basic)
Vous créez une énumération avec l' `Enum` instruction dans la section déclarations d’une classe ou d’un module. Vous ne pouvez pas déclarer une énumération dans une méthode. Pour spécifier le niveau d’accès approprié, utilisez `Private` , `Protected` , `Friend` ou `Public` .  
  
 Un `Enum` type a un nom, un type sous-jacent et un ensemble de champs, chacun représentant une constante. Le nom doit être un qualificateur Visual Basic .NET valide. Le type sous-jacent doit être l’un des types d’entiers, `Byte` , `Short` `Long` ou `Integer` . La valeur par défaut est `Integer`. Les énumérations sont toujours fortement typées et ne sont pas interchangeables avec des types de nombres entiers.  
  
 Les énumérations ne peuvent pas avoir de valeurs à virgule flottante. Si une valeur à virgule flottante est assignée à une énumération avec `Option Strict On` , une erreur de compilateur se produit. Si `Option Strict` est `Off` , la valeur est automatiquement convertie en `Enum` type.  
  
 Pour plus d’informations sur les noms et sur l’utilisation de l' `Imports` instruction pour rendre la qualification de nom inutile, consultez [énumérations et qualification de nom](enumerations-and-name-qualification.md).  
  
### <a name="to-declare-an-enumeration"></a>Pour déclarer une énumération  
  
1. Écrivez une déclaration qui comprend un niveau d’accès au code, le `Enum` mot clé et un nom valide, comme dans les exemples suivants, chacun d’eux déclarant un différent `Enum` .  
  
     [!code-vb[VbEnumsTask#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#3)]  
  
2. Définissez les constantes dans l’énumération. Par défaut, la première constante d’une énumération est initialisée sur `0` , et les constantes suivantes sont initialisées à une valeur supérieure à la constante précédente. Par exemple, l’énumération suivante, `Days` , contient une constante nommée `Sunday` avec la valeur `0` , une constante nommée `Monday` avec la valeur `1` , une constante nommée `Tuesday` avec la valeur `2` , et ainsi de suite.  
  
     [!code-vb[VbEnumsTask#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#4)]  
  
3. Vous pouvez assigner explicitement des valeurs à des constantes dans une énumération à l’aide d’une instruction d’assignation. Vous pouvez assigner n’importe quelle valeur entière, y compris des nombres négatifs. Par exemple, vous pouvez souhaiter que les constantes avec des valeurs inférieures à zéro représentent des conditions d’erreur. Dans l’énumération suivante, la constante reçoit `Invalid` explicitement la valeur `–1` et la `Sunday` valeur est affectée à la constante `0` . Étant donné qu’il s’agit de la première constante de l’énumération, `Saturday` est également initialisé à la valeur `0` . La valeur de `Monday` est `1` (une valeur supérieure à la valeur de `Sunday` ); la valeur de `Tuesday` est `2` , et ainsi de suite.  
  
     [!code-vb[VbEnumsTask#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#5)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>Pour déclarer une énumération en tant que type explicite  
  
- Spécifiez le type de l’énumération à l’aide de la `As` clause, comme indiqué dans l’exemple suivant.  
  
     [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations et qualification de noms](enumerations-and-name-qualification.md)
- [Comment : faire référence à un membre d'énumération](how-to-refer-to-an-enumeration-member.md)
- [Comment : itérer au sein d'une énumération dans Visual Basic](how-to-iterate-through-an-enumeration.md)
- [Comment : déterminer la chaîne associée à une valeur d'énumération](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Quand utiliser une énumération](when-to-use-an-enumeration.md)
- [Vue d'ensemble des constantes](constants-overview.md)
- [Constantes et types de données littérales](constant-and-literal-data-types.md)
- [Constantes et énumérations](../../../language-reference/constants-and-enumerations.md)
