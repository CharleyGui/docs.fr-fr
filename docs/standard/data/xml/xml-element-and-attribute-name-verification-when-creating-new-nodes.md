---
title: Vérification des noms d'attribut et d'élément XML lors de la création de nœuds
ms.date: 03/30/2017
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
ms.openlocfilehash: 0678f7daf5276a905ce890a5f6a0f64993fb08b0
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828815"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a>Vérification des noms d'attribut et d'élément XML lors de la création de nœuds
Le DOM (Document Object Model) XML contrôle la validité des noms lors de la création de nœuds d'élément ou d'attribut. Si ces noms contiennent des caractères non conformes, une exception est levée. Pour être certain que les noms sont valides et encodés correctement, vous devez recourir à la classe **XmlConvert** pour encoder le nom et le décoder à nouveau au niveau de l'application. **XmlWriter** possède des méthodes qui effectuent des opérations supplémentaires afin de garantir un format correct pour le code XML qui est généré.  
  
## <a name="see-also"></a>Voir aussi

- [DOM (Document Object Model) XML](xml-document-object-model-dom.md)
