---
title: Effet des espaces de noms sur le développement des références d'entité avec les nouveaux nœuds contenant des éléments et attributs
ms.date: 03/30/2017
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
ms.openlocfilehash: 1d3d0a8bddfa2ca68a7be63d09ae6873e994ed44
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714430"
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a>Effet des espaces de noms sur le développement des références d'entité avec les nouveaux nœuds contenant des éléments et attributs

Le contenu d’une déclaration d’entité peut contenir pratiquement n’importe quel élément, c’est pourquoi il est possible qu’il comporte un élément tel que `<!ENTITY aname "<elem>test</elem>">`.  
  
 Lorsque le document XML est analysé, `&aname;` n’est pas développé avec son contenu de remplacement au moment de l’analyse. Le développement XML n’a pas lieu car la résolution de l’espace de noms pour l’élément ne peut se produire tant que le nœud n’est pas placé dans le document. Jusqu'alors, l'espace de noms figurant dans la portée n'est pas détectable. Lorsque le nœud est placé dans le document, la résolution de l’espace de noms se produit et le contenu d’entité résultant est analysé dans ses nœuds adéquats.  
  
> [!NOTE]
> Après que le développement a eu lieu sur un nœud de référence d'entité à peine créé, il ne peut se produire à nouveau. C'est pourquoi les espaces de noms utilisés dans le texte de remplacement de l'élément sont liés au moment de la définition du nœud parent. Toutefois, l'espace de noms peut être modifié pour des nœuds de référence d'entité existants lorsque vous les supprimez ou les insérez ailleurs, ou bien pour des nœuds de référence d'entité clonés à l'aide de la méthode **CloneNode**.  
  
## <a name="see-also"></a>Voir aussi

- [DOM (Document Object Model) XML](xml-document-object-model-dom.md)
