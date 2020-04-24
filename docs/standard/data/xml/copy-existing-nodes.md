---
title: Copie de nœuds existants
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
ms.openlocfilehash: fb9ccd7b16d00355ba87bb32f5447906feeecd94
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711062"
---
# <a name="copy-existing-nodes"></a>Copie de nœuds existants
Le DOM (Document Object Model) XML comporte de nombreuses méthodes et propriétés que vous pouvez utiliser pour sélectionner un nœud, par exemple **SelectSingleNode**, **ChildNodes[int i]** ou **Attributes[int i]**. Une fois le nœud sélectionné, vous pouvez l’insérer dans l’arborescence à l’aide de l’une des méthodes d’insertion adaptées à ce type de nœud particulier. La seule restriction à l’insertion d’un nœud dans l’arborescence est que cette opération ne doit pas compromettre la validité du format du document. Quand un nœud existant est inséré dans l’arborescence DOM, il est supprimé de sa position d’origine et ajouté à sa position de destination.  
  
## <a name="see-also"></a>Voir aussi

- [DOM (Document Object Model) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
