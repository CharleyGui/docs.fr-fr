---
title: Mises à jour dynamiques de NodeList et NamedNodeMap
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
ms.openlocfilehash: 0199f24e9ef8dd28f91976edd50f78399dc893ef
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292083"
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a>Mises à jour dynamiques de NodeList et NamedNodeMap
Dans la mesure où **XmlNodeList** et **XmlNamedNodeMap** contiennent une collection de nœuds, mais où le document XML est chargé en mémoire et est modifié, le World Wide Web Consortium (W3C) établit que ces objets contenant des collections de nœuds doivent être dynamiques. Dès lors, si le document sous-jacent change, les données figurant dans ces deux objets doivent changer également. C'est pourquoi, si vous avez un **XmlNodeList** contenant tous les éléments enfants d'un élément particulier (par exemple, l'élément X), vous ajoutez un élément supplémentaire, l'élément Q, au document sous l'élément X. Le **XmlNodeList** doit également avoir le nouvel élément Q ajouté à sa collection. L'inverse est vrai également. Si un nœud est ajouté à **XmlNodeList**, le document sous-jacent est mis à jour en conséquence.  
  
## <a name="see-also"></a>Voir aussi

- [DOM (Document Object Model) XML](xml-document-object-model-dom.md)
