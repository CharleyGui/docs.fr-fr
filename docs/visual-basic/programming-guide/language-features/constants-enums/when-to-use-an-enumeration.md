---
title: Quand utiliser une énumération
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: ba69249e16b8c0ee06d57d06d192874a283b295e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403535"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a>Quand utiliser une énumération (Visual Basic)
Les énumérations offrent un moyen simple de travailler avec des ensembles de constantes associées. Une énumération, ou `Enum` , est un nom symbolique pour un ensemble de valeurs. Les énumérations sont traitées comme des types de données, et vous pouvez les utiliser pour créer des ensembles de constantes à utiliser avec des variables et des propriétés.  
  
## <a name="when-to-use-an-enumeration"></a>Quand utiliser une énumération  
 Chaque fois qu’une procédure accepte un ensemble limité de variables, envisagez d’utiliser une énumération. Les énumérations rendent le code plus clair et plus lisible, en particulier quand des noms explicites sont utilisés.  
  
 Les avantages de l’utilisation des énumérations sont les suivants :  
  
- Réduit les erreurs dues à la transposition ou à la frappe de nombres.  
  
- Facilite la modification des valeurs à l’avenir.  
  
- Rend le code plus facile à lire, ce qui signifie qu’il est moins probable que des erreurs se produiront.  
  
- Garantit la compatibilité ascendante. Avec les énumérations, votre code risque d’échouer si, à l’avenir, un utilisateur modifie les valeurs correspondant aux noms des membres.  
  
## <a name="naming-enumerations"></a>Énumération des noms  
 Utilisez une convention d’affectation de noms pour les membres de l’énumération. Lorsque Visual Basic rencontre un nom de membre d’énumération, une exception peut être levée si d’autres bibliothèques de types référencées contiennent le même nom. Utilisez un préfixe unique qui identifie les valeurs de votre application ou composant.  
  
 Lorsque vous faites référence à un membre d’une énumération, vous devez qualifier le nom du membre avec le nom de l’énumération ou utiliser l' `Imports` instruction. Pour plus d’informations, consultez [énumérations et qualification de nom](enumerations-and-name-qualification.md).  
  
## <a name="predefined-enumerations"></a>Énumérations prédéfinies  
 Visual Basic fournit un certain nombre d’énumérations prédéfinies, telles que `FirstDayOfWeek` et `MsgBoxResult` , pour faciliter votre code. Pour obtenir la liste de ces [énumérations, consultez constantes et énumérations](../../../language-reference/constants-and-enumerations.md).  
  
## <a name="see-also"></a>Voir aussi

- [How to: Declare an, énumération](how-to-declare-enumerations.md)
- [Comment : faire référence à un membre d'énumération](how-to-refer-to-an-enumeration-member.md)
- [Énumérations et qualification de noms](enumerations-and-name-qualification.md)
- [Comment : itérer au sein d'une énumération dans Visual Basic](how-to-iterate-through-an-enumeration.md)
- [Comment : déterminer la chaîne associée à une valeur d'énumération](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Enum (instruction)](../../../language-reference/statements/enum-statement.md)
- [Constantes et énumérations](../../../language-reference/constants-and-enumerations.md)
