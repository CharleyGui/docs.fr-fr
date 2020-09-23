---
title: Types de données divers
ms.date: 07/20/2015
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
ms.openlocfilehash: 45b44abc24b968f19b456cbe0be0f25efc8f0ce8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095458"
---
# <a name="miscellaneous-data-types-visual-basic"></a>Types de données divers (Visual Basic)

Visual Basic fournit plusieurs types de données qui ne sont pas orientés vers des nombres ou des caractères. Au lieu de cela, ils gèrent des données spécialisées telles que les valeurs Oui/non, les valeurs de date/heure et les adresses d’objets.  
  
 Pour obtenir un tableau présentant une comparaison côte à côte des types de données Visual Basic, consultez [types de données](../../../language-reference/data-types/index.md).  
  
## <a name="boolean-type"></a>Type booléen  

 Le [type de données booléen](../../../language-reference/data-types/boolean-data-type.md) est une valeur non signée qui est interprétée comme `True` ou `False` . Sa largeur de données dépend de la plateforme d’implémentation. Si une variable peut contenir uniquement des valeurs à deux États, telles que true/false, yes/no ou on/off, déclarez-la comme `Boolean` .  
  
## <a name="date-type"></a>Type de date  

 Le [type de données date](../../../language-reference/data-types/date-data-type.md) est une valeur 64 bits qui contient des informations de date et d’heure. Chaque incrément représente 100 nanosecondes de temps écoulé depuis le début (12:00 AM) du 1er janvier de l’année 1 dans le calendrier grégorien. Si une variable peut contenir une valeur de date, une valeur d’heure, ou les deux, déclarez-la comme `Date` .  
  
## <a name="object-type"></a>Type d'objet  

 Le [type de données Object](../../../language-reference/data-types/object-data-type.md) est une adresse 32 bits qui pointe vers une instance d’objet dans votre application ou dans une autre application. Une `Object` variable peut faire référence à n’importe quel objet que votre application reconnaît, ou à des données de n’importe quel type de données. Cela comprend à la fois les *types valeur*, tels que `Integer` , `Boolean` et les instances de structure, et les *types référence*, qui sont des instances d’objets créés à partir de classes telles que `String` et <xref:System.Windows.Forms.Form> , ainsi que des instances de tableau.  
  
 Si une variable stocke un pointeur vers une instance d’une classe que vous ne connaissez pas au moment de la compilation, ou si elle peut pointer vers des données de différents types de données, déclarez-la comme `Object` .  
  
 L’avantage du `Object` type de données est que vous pouvez l’utiliser pour stocker des données de n’importe quel type de données. L’inconvénient est que vous devez effectuer des opérations supplémentaires qui prennent plus de temps pour s’exécuter et ralentir l’exécution de votre application. Si vous utilisez une `Object` variable pour les types valeur, vous subissez une *conversion boxing* et *unboxing*. Si vous l’utilisez pour des types référence, vous subissez une *liaison tardive*.  
  
## <a name="see-also"></a>Voir aussi

- [Caractères de type](type-characters.md)
- [Types de données élémentaires](elementary-data-types.md)
- [Types de données numériques](numeric-data-types.md)
- [Types de données caractères](character-data-types.md)
- [Dépannage des types de données](troubleshooting-data-types.md)
- [Liaison précoce et tardive](../early-late-binding/index.md)
