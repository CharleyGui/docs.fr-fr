---
title: Prise en charge des espaces de noms dans le DOM
ms.date: 03/30/2017
ms.assetid: f0548ead-0fed-41ee-b33e-117ba900d3bc
ms.openlocfilehash: b3214d77b069b672e8772ec78db51c9d8ee1bf50
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714404"
---
# <a name="namespace-support-in-the-dom"></a>Prise en charge des espaces de noms dans le DOM

Le DOM (Document Object Model ) XML gère parfaitement les espaces de noms. Seuls les documents XML reconnaissant les espaces de noms sont pris en charge. Le World Wide Web Consortium (W3C) établit que les applications DOM implémentant le niveau 1 peuvent ne pas prendre en charge des espaces de noms, alors que les fonctionnalités du DOM de niveau 2 gèrent parfaitement les espaces de noms. Cependant, toutes les fonctionnalités du DOM XML tiennent compte des espaces de noms, peu importe si la méthode émane de la recommandation Document Object Model (DOM) de niveau 1 ou de niveau 2.  
  
 Par exemple, dans un environnement ne prenant pas en charge les espaces de noms, l'appel de `setAttribute("A:b", "123")` conformément à la recommandation Document Object Model (DOM) de niveau 1 ne donne pas pour résultat un attribut doté du préfixe `A` et du nom local `b`. Il produit un attribut dont la valeur est `A:b`.  
  
 Dans un environnement prenant en charge les espaces de noms, par contre, l'appel à `setAttribute("A:b", "123")` de la recommandation Document Object Model (DOM) de niveau 2 génère un attribut dont le préfixe est `A` et le nom local, `b`. Telle est la manière dont Microsoft .NET Framework DOM fonctionne.  
  
 C'est pourquoi, toutes les méthodes qui prennent un paramètre de nom prennent également un préfixe destiné à qualifier ce nom. Le paramètre de nom, tel que `A:b` dans la méthode DOM de niveau 1 **setAttribute**, est analysé comme suit :  
  
- En l'absence de caractère deux-points (:), le nom local correspond à la valeur du paramètre `name`, le préfixe et NamespaceURI étant des chaînes vides.  
  
- En présence d'un caractère deux-points, le nom est scindé en deux parties au niveau de la position du premier caractère deux-points. Le préfixe a la valeur de la chaîne se trouvant avant le deux-points, et le nom local est la chaîne située après ce caractère. Pour les méthodes ne prenant pas de valeur NamespaceURI, NamespaceURI n'est pas résolu et garde comme valeur une chaîne vide. Sinon, NamespaceURI a pour valeur la chaîne passée à la méthode. Si le préfixe n'est pas défini, la méthode **Save** et les propriétés **InnerXml** et **OuterXml** échouent.  
  
## <a name="see-also"></a>Voir aussi

- [DOM (Document Object Model) XML](xml-document-object-model-dom.md)
