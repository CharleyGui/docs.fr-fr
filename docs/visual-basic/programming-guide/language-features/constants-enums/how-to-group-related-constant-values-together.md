---
title: 'Comment : regrouper les valeurs de constante connexes'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: d2393af8b0c2b0c2e528f9908a78fbc7f182c8cf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414438"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a>Comment : regrouper les valeurs de constante connexes (Visual Basic)
Une énumération est la meilleure façon de regrouper des constantes associées. Vous créez une énumération avec l' `Enum` instruction dans la section déclarations d’une classe ou d’un module. Pour plus d’informations, consultez [Comment : déclarer une énumération](how-to-declare-enumerations.md).  
  
### <a name="to-group-related-constant-values"></a>Pour regrouper des valeurs de constante associées  
  
1. Écrivez une déclaration qui comprend un niveau d’accès au code, le `Enum` mot clé et un nom valide. Cet exemple crée l' `Private` énumération, `temperatureValues` .  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. Définissez les constantes dans l’énumération. Cet exemple crée l' `Public` énumération `temperatureValues` et assigne ses valeurs.  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations et qualification de noms](enumerations-and-name-qualification.md)
- [Comment : faire référence à un membre d'énumération](how-to-refer-to-an-enumeration-member.md)
- [Quand utiliser une énumération](when-to-use-an-enumeration.md)
- [Vue d'ensemble des constantes](constants-overview.md)
- [Constantes et types de données littérales](constant-and-literal-data-types.md)
- [Constantes et énumérations](../../../language-reference/constants-and-enumerations.md)
