---
title: Copie de nœuds existants
ms.date: 03/30/2017
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
ms.openlocfilehash: b4ae24f9776456033a876e8ae4d1515d2f669fe0
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830946"
---
# <a name="copy-existing-nodes"></a>Copie de nœuds existants
Le DOM (Document Object Model) XML comporte de nombreuses méthodes et propriétés que vous pouvez utiliser pour sélectionner un nœud, par exemple **SelectSingleNode**, **ChildNodes[int i]** ou **Attributes[int i]**. Une fois le nœud sélectionné, vous pouvez l’insérer dans l’arborescence à l’aide de l’une des méthodes d’insertion adaptées à ce type de nœud particulier. La seule restriction à l’insertion d’un nœud dans l’arborescence est que cette opération ne doit pas compromettre la validité du format du document. Quand un nœud existant est inséré dans l’arborescence DOM, il est supprimé de sa position d’origine et ajouté à sa position de destination.  
  
## <a name="see-also"></a>Voir aussi

- [DOM (Document Object Model) XML](xml-document-object-model-dom.md)
