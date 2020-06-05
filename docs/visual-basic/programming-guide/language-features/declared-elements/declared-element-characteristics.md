---
title: Caractéristiques des éléments déclarés
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], lifetime
- access levels, declared elements
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- elements [Visual Basic], programming
- scope [Visual Basic], declared elements
- lifetime [Visual Basic], declared elements
- declared elements [Visual Basic], access level
- data types [Visual Basic], declared elements
- declared elements [Visual Basic], visibility
ms.assetid: 1bc40fb8-b67c-4428-90a4-76b630ae2583
ms.openlocfilehash: 9d1e327c25689bed1405ea9a627da6232abb707b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392946"
---
# <a name="declared-element-characteristics-visual-basic"></a>Caractéristiques d'éléments déclarés (Visual Basic)
Une *caractéristique* d’un élément déclaré est un aspect de cet élément qui affecte la façon dont le code peut interagir avec lui. Chaque élément déclaré est associé à une ou plusieurs des caractéristiques suivantes :  
  
- *Type de données* : les valeurs que l’élément peut contenir et la manière dont il stocke ces valeurs. Pour plus d’informations, consultez [Types de données](../../../language-reference/data-types/index.md).  
  
- Durée de *vie* : période d’exécution pendant laquelle l’élément peut être utilisé. Pour plus d’informations, consultez [durée de vie dans Visual Basic](lifetime.md).  
  
- *Portée* : ensemble de tout le code qui peut faire référence à l’élément sans qualifier son nom. Pour plus d’informations, consultez [Comment : contrôler la portée d’une variable](how-to-control-the-scope-of-a-variable.md).  
  
- *Niveau d’accès* : autorisation permettant au code d’utiliser l’élément. Pour plus d’informations, consultez [Comment : contrôler la disponibilité d’une variable](how-to-control-the-availability-of-a-variable.md).  
  
## <a name="characteristics-of-the-elements"></a>Caractéristiques des éléments  
 Le tableau suivant présente les éléments déclarés et les caractéristiques qui s’appliquent à chacun d’eux.  
  
|Élément|Type de données|Durée de vie|Étendue <sup>1</sup>|Niveau d’accès|  
|-------------|---------------|--------------|------------------------|------------------|  
|Variable|Oui|Oui|Oui|Oui|  
|Constant|Oui|Non|Oui|Oui|  
|Énumération|Oui|Non|Oui|Oui|  
|Structure|Non|Non|Oui|Oui|  
|Propriété|Oui|Oui|Oui|Oui|  
|Méthode|Non|Oui|Oui|Oui|  
|Procédure ( `Sub` ou `Function` )|Non|Oui|Oui|Oui|  
|Paramètre de procédure|Oui|Oui|Oui|Non|  
|Retour de fonction|Oui|Oui|Oui|Non|  
|Opérateur|Oui|Non|Oui|Oui|  
|Interface|Non|Non|Oui|Oui|  
|Class|Non|Non|Oui|Oui|  
|Événement|Non|Non|Oui|Oui|  
|Délégué|Non|Non|Oui|Oui|  
  
 <sup>1</sup> la portée est parfois appelée *visibilité*.  
  
## <a name="see-also"></a>Voir aussi

- [Éléments déclarés](index.md)
- [Declared Element Names](declared-element-names.md)
- [References to Declared Elements](references-to-declared-elements.md)
- [Durée de vie dans Visual Basic](lifetime.md)
- [Portée dans Visual Basic](scope.md)
- [Niveaux d’accès dans Visual Basic](access-levels.md)
- [Types de données](../data-types/index.md)
- [Déclaration de variable](../variables/variable-declaration.md)
