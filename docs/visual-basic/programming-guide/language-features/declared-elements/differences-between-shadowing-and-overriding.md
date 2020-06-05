---
title: Différences entre l'occultation et la substitution
ms.date: 07/20/2015
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
ms.openlocfilehash: a6ea83fadf18ef3be778e6de31c0eb4e65e74824
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392868"
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a>Différences entre l'occultation et la substitution (Visual Basic)
Quand vous définissez une classe qui hérite d’une classe de base, vous souhaitez parfois redéfinir un ou plusieurs des éléments de la classe de base dans la classe dérivée. L’occultation et la substitution sont toutes deux disponibles à cet effet.  
  
## <a name="comparison"></a>Comparaison  
 L’occultation et la substitution sont toutes deux utilisées lorsqu’une classe dérivée hérite d’une classe de base, et toutes deux redéfinissent un élément déclaré avec un autre. Mais il existe des différences significatives entre les deux.  
  
 Le tableau suivant compare l’occultation et la substitution.  
  
||||  
|---|---|---|  
|Point de comparaison|Copie shadow|Remplacement|  
|Objectif|Protège contre une modification de classe de base suivante qui introduit un membre que vous avez déjà défini dans votre classe dérivée.|Atteint le polymorphisme en définissant une implémentation différente d’une procédure ou d’une propriété avec la même séquence d’appel<sup>1</sup>|  
|Élément redéfini|Tout type d’élément déclaré|Seule une procédure ( `Function` , `Sub` ou `Operator` ) ou une propriété|  
|Redéfinissant l’élément|Tout type d’élément déclaré|Seule une procédure ou une propriété avec la séquence d’appel<sup>1</sup> identique|  
|Niveau d’accès de l’élément redéfinissant|Tout niveau d’accès|Impossible de modifier le niveau d’accès de l’élément substitué|  
|Lisibilité et accessibilité de l’élément redéfinissant|Toute combinaison|Impossible de modifier la lisibilité ou l’écriture dans la propriété substituée|  
|Contrôle de la redéfinition|L’élément de classe de base ne peut pas appliquer ou interdire l’occultation|L’élément de classe de base peut spécifier `MustOverride` , `NotOverridable` ou`Overridable`|  
|Utilisation des mots clés|`Shadows`recommandé dans la classe dérivée ; `Shadows`pris par défaut si ni `Shadows` ni `Overrides` spécifié<sup>2</sup>|`Overridable`ou `MustOverride` requis dans la classe de base ; `Overrides` obligatoire dans la classe dérivée|  
|Héritage de la redéfinition d’un élément par des classes dérivant de votre classe dérivée|Élément occultant hérité par des classes dérivées supplémentaires ; élément occulté toujours masqué<sup>3</sup>|Substitution d’un élément hérité par des classes dérivées supplémentaires ; élément substitué toujours substitué|  
  
 <sup>1</sup> la *séquence appelante* se compose du type d’élément ( `Function` , `Sub` , `Operator` ou `Property` ), du nom, de la liste de paramètres et du type de retour. Vous ne pouvez pas substituer une procédure avec une propriété, ou l’inverse. Vous ne pouvez pas remplacer un genre de procédure ( `Function` , `Sub` ou `Operator` ) par un autre type.  
  
 <sup>2</sup> si vous ne spécifiez pas `Shadows` ou `Overrides` , le compilateur émet un message d’avertissement pour vous aider à vérifier le genre de redéfinition que vous souhaitez utiliser. Si vous ignorez l’avertissement, le mécanisme d’occultation est utilisé.  
  
 <sup>3</sup> si l’élément d’occultation est inaccessible dans une classe dérivée supplémentaire, l’occultation n’est pas héritée. Par exemple, si vous déclarez l’élément d’occultation comme `Private` , une classe dérivant de votre classe dérivée hérite de l’élément d’origine au lieu de l’élément d’occultation.  
  
## <a name="guidelines"></a>Recommandations  
 Normalement, vous utilisez la substitution dans les cas suivants :  
  
- Vous définissez des classes dérivées polymorphes.  
  
- Vous souhaitez que le compilateur applique le type d’élément identique et la séquence d’appel.  
  
 Normalement, vous utilisez l’occultation dans les cas suivants :  
  
- Vous pensez que votre classe de base peut être modifiée et définir un élément en utilisant le même nom que le vôtre.  
  
- Vous souhaitez la liberté de modifier le type d’élément ou la séquence d’appel.  
  
## <a name="see-also"></a>Voir aussi

- [References to Declared Elements](references-to-declared-elements.md)
- [Occultation dans Visual Basic](shadowing.md)
- [Comment : masquer une variable portant le même nom que votre variable](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Comment : masquer une variable héritée](how-to-hide-an-inherited-variable.md)
- [Comment : accéder à une variable masquée par une classe dérivée](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Shadows](../../../language-reference/modifiers/shadows.md)
- [Remplacements](../../../language-reference/modifiers/overrides.md)
