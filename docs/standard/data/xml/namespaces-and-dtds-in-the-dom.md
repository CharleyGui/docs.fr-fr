---
title: Espaces de noms et DTD dans le DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1e9b55c4-76ad-4f54-8d96-7ce4b4cf1e05
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a3a3ec957a55ff23dec728ccd31fe9e1f52ce78f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64590209"
---
# <a name="namespaces-and-dtds-in-the-dom"></a>Espaces de noms et DTD dans le DOM
Les définitions de type de document (DTD) compliquent la prise en charge des espaces de noms. Par exemple, le code XML suivant contient des attributs par défaut, et un de ces noms comporte le signe deux-points.  
  
```xml  
<!ATTLIST item x:id CDATA #IMPLIED>  
```  
  
 Voici les résolutions possibles si cette construction est autorisée :  
  
- `x:` est traité comme un préfixe d'espace de noms, mais il doit pouvoir être résolu à l'aide d'une déclaration d'espace de noms `xmlns:x`, qui doit également figurer dans la DTD. Il est incorrect de mapper ce préfixe à autre chose dans l'instance de document.  
  
- `x:` est traité comme un préfixe d'espace de noms, mais il est toujours résolu dans le contexte des éléments d'instance. Cela signifie que le préfixe peut en réalité être mappé à des URI (Uniform Resource Identifiers) d'espaces de noms différents en fonction de la portée d'espace de noms dans laquelle apparaît l'élément `item`. Ce comportement est plus prévisible que dans le cas de la résolution décrite au point précédent, mais il implique d’autres ramifications compliquées dans la mesure où il nécessite la matérialisation des attributs par défaut.  
  
- Le deux-points est ignoré car il figure dans une DTD et le nom de l'attribut est `x:y`, sans préfixe ni URI d'espace de noms.  
  
- Le deux-points de l'attribut par défaut entraîne la levée d'une exception indiquant que les deux-points ne sont pas pris en charge dans les noms situés dans une DTD. Cela aboutit à un comportement prévisible, mais qui empêche le chargement de la plupart des DTD publiées par le World Wide Web Consortium (W3C).  
  
- Quand l’utilisateur demande une validation DTD, la prise en charge des espaces de noms est désactivée pour le document tout entier. Il est ensuite possible de charger des DTD W3C et cela donne lieu à un comportement prévisible.  
  
 Le langage XML dans Microsoft .NET Framework implémente la deuxième option pour optimiser la compatibilité W3C.  
  
## <a name="see-also"></a>Voir aussi

- [DOM (Document Object Model) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
