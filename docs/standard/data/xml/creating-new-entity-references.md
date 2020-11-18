---
title: Création de nouvelles références d'entité
ms.date: 03/30/2017
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
ms.openlocfilehash: 5d1411b38ee79705cad3375aea1b95265c1ab61a
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829321"
---
# <a name="creating-new-entity-references"></a>Création de nouvelles références d'entité
La méthode **CreateEntityReference** crée un nouveau nœud **XmlEntityReference**. Le DOM (Document Object Model) XML vérifie si le nom de l'entité référencée a déjà été déclaré. Si tel est le cas, les nœuds enfants du nœud **XmlEntityReference** sont copiés à partir du nœud de la déclaration d'entité. Si aucune déclaration d'entité ne correspond, un nœud de texte vide est joint en tant qu'unique enfant du nœud de référence d'entité. Les nœuds enfants du nœud **XmlEntityReference** étant des copies d'autres nœuds, ils sont en lecture seule et ne peuvent pas être modifiés.  
  
 Lorsque les nœuds sont copiés, il est possible qu'un espace de noms soit dans la portée à la position de la référence d'entité. Cet espace de noms a une incidence sur la configuration de tous les nœuds d'élément ou d'attribut générés.  
  
> [!NOTE]
> Le DOM ajoute des nœuds enfants à **EntityReference** uniquement si vous insérez le nœud **EntityReference** dans le document. Les nœuds **EntityReference** nouvellement créés ne possèdent pas de nœuds enfants.  
  
 Même si **XmlDataDocument** est une classe dérivée de **XmlDocument**, **XmlDataDocument** ne prend pas en charge la création de références d'entité. Cela tient au fait que les enfants **EntityReference** sont en lecture seule. Les enfants d'un nœud **EntityReference** peuvent s'étendre sur plus d'une région. Dans ce cas, une partie d'une ligne associée à la région qui contient une partie de **EntityReference** sera en lecture seule.  
  
## <a name="see-also"></a>Voir aussi

- [DOM (Document Object Model) XML](xml-document-object-model-dom.md)
