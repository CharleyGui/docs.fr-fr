---
title: Quand utiliser une énumération
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: 5daae8d487ddfe079a54e305e59e32e8ded8f65e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353962"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a>Quand utiliser une énumération (Visual Basic)
Les énumérations offrent un moyen simple de travailler avec des ensembles de constantes associées. Une énumération, ou `Enum`, est un nom symbolique pour un ensemble de valeurs. Les énumérations sont traitées comme des types de données, et vous pouvez les utiliser pour créer des ensembles de constantes à utiliser avec des variables et des propriétés.  
  
## <a name="when-to-use-an-enumeration"></a>Quand utiliser une énumération  
 Chaque fois qu’une procédure accepte un ensemble limité de variables, envisagez d’utiliser une énumération. Les énumérations rendent le code plus clair et plus lisible, en particulier quand des noms explicites sont utilisés.  
  
 Les avantages de l’utilisation des énumérations sont les suivants :  
  
- Réduit les erreurs dues à la transposition ou à la frappe de nombres.  
  
- Facilite la modification des valeurs à l’avenir.  
  
- Rend le code plus facile à lire, ce qui signifie qu’il est moins probable que des erreurs se produiront.  
  
- Garantit la compatibilité ascendante. Avec les énumérations, votre code risque d’échouer si, à l’avenir, un utilisateur modifie les valeurs correspondant aux noms des membres.  
  
## <a name="naming-enumerations"></a>Énumération des noms  
 Utilisez une convention d’affectation de noms pour les membres de l’énumération. Lorsque Visual Basic rencontre un nom de membre d’énumération, une exception peut être levée si d’autres bibliothèques de types référencées contiennent le même nom. Utilisez un préfixe unique qui identifie les valeurs de votre application ou composant.  
  
 Lorsque vous faites référence à un membre d’une énumération, vous devez qualifier le nom du membre avec le nom de l’énumération ou utiliser l’instruction `Imports`. Pour plus d’informations, consultez [énumérations et qualification de nom](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
## <a name="predefined-enumerations"></a>Énumérations prédéfinies  
 Visual Basic fournit un certain nombre d’énumérations prédéfinies, telles que `FirstDayOfWeek` et `MsgBoxResult`, pour faciliter votre code. Pour obtenir la liste de ces [énumérations, consultez constantes et énumérations](../../../../visual-basic/language-reference/constants-and-enumerations.md).  
  
## <a name="see-also"></a>Voir aussi

- [Comment : déclarer une énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Guide pratique : faire référence à un membre d’énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Énumérations et qualification de noms](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Comment : itérer au sein d’une énumération dans Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Guide pratique : déterminer la chaîne associée à une valeur d’énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Enum (instruction)](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [Constantes et énumérations](../../../../visual-basic/language-reference/constants-and-enumerations.md)
