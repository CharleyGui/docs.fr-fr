---
title: Conventions d'affectation de noms
ms.date: 07/20/2015
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
ms.openlocfilehash: 20531e379ddf9b93a278795e9b3c0eb91b47e077
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398342"
---
# <a name="visual-basic-naming-conventions"></a>Conventions d'affectation de noms Visual Basic
Lorsque vous nommez un élément dans votre application Visual Basic, le premier caractère de ce nom doit être un caractère alphabétique ou un trait de soulignement. Notez, toutefois, que les noms commençant par un trait de soulignement ne sont pas conformes à l' [indépendance du langage et aux composants indépendants du langage](../../../standard/language-independence-and-language-independent-components.md) (CLS).  
  
 Les suggestions suivantes s’appliquent à l’affectation de noms.  
  
- Commencez chaque mot distinct d’un nom par une lettre majuscule, comme dans `FindLastRecord` et `RedrawMyForm` .  
  
- Commencer les noms de fonction et de méthode par un verbe, comme dans `InitNameArray` ou `CloseDialog` .  
  
- Commencez les noms de classe, de structure, de module et de propriété par un nom, comme dans `EmployeeName` ou `CarAccessory` .  
  
- Commencez les noms d’interface par le préfixe « I », suivi d’un nom ou d’une expression nominale, comme `IComponent` , ou avec un adjectif décrivant le comportement de l’interface, par exemple `IPersistable` . N’utilisez pas de trait de soulignement et utilisez des abréviations avec modération, car les abréviations peuvent entraîner des confusions.  
  
- Commencez les noms de gestionnaires d’événements par un nom décrivant le type d’événement suivi du `EventHandler` suffixe « », comme dans « `MouseEventHandler` ».  
  
- Dans les noms des classes d’arguments d’événement, incluez le `EventArgs` suffixe «».  
  
- Si un événement a le concept « Before » ou « after », utilisez un suffixe dans le présent ou le passé, comme dans « `ControlAdd` » ou « `ControlAdded` ».  
  
- Pour les termes longs ou fréquemment utilisés, utilisez des abréviations pour conserver les longueurs de noms raisonnables, par exemple, « HTML », au lieu de « langage HTML ». En général, les noms de variables de plus de 32 caractères sont difficiles à lire sur une analyse définie sur une résolution faible. En outre, assurez-vous que vos abréviations sont cohérentes dans toute l’application. Le basculement aléatoire d’un projet entre « HTML » et « langage HTML » peut entraîner des confusions.  
  
- Évitez d’utiliser des noms dans une portée interne qui sont identiques aux noms dans une portée externe. Des erreurs peuvent se produire en cas d’accès à la mauvaise variable. Si un conflit se produit entre une variable et le mot clé du même nom, vous devez identifier le mot clé en le faisant précéder de la bibliothèque de types appropriée. Par exemple, si vous avez une variable appelée `Date` , vous pouvez utiliser la `Date` fonction intrinsèque uniquement en appelant <xref:System.DateTime.Date%2A?displayProperty=nameWithType> .  
  
## <a name="see-also"></a>Voir aussi

- [Mots clés comme noms d’éléments dans le code](keywords-as-element-names-in-code.md)
- [Me, My, MyBase et MyClass](me-my-mybase-and-myclass.md)
- [Declared Element Names](../language-features/declared-elements/declared-element-names.md)
- [Structure de programme et conventions de code](program-structure-and-code-conventions.md)
- [Informations de référence sur le langage Visual Basic](../../language-reference/index.md)
