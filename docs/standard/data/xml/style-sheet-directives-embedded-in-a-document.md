---
title: Directives de feuille de style incorporées dans un document
ms.date: 03/30/2017
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
ms.openlocfilehash: 25946fd14a82428ae4367cd33511df68e9929203
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818568"
---
# <a name="style-sheet-directives-embedded-in-a-document"></a>Directives de feuille de style incorporées dans un document

Il arrive parfois que des données XML existantes contiennent la directive de feuille de style de `<?xml:stylesheet?>`. Microsoft Internet Explorer accepte cette directive comme une alternative à la syntaxe `<?xml-stylesheet?>`. Quand les données XML contiennent une directive `<?xml:stylesheet?>`, comme le montrent les données suivantes, une tentative de chargement de ces données dans le DOM (Document Object Model) XML entraîne la levée d'une exception.

```xml
<?xml version="1.0" ?>
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>
<root>
    <test>Node 1</test>
    <test>Node 2</test>
</root>
```

Cela est dû au fait que `<?xml:stylesheet?>` est considéré comme un **ProcessingInstruction** non valide pour le DOM. Conformément à la spécification des espaces de noms XML, tout **ProcessingInstruction** peut uniquement comporter des noms sans deux-points (NCNames), par opposition aux noms qualifiés (QNames).

Si l'on s'en tient à la section 6 de cette spécification, la présence des méthodes **Load** et **LoadXml** conformes à cette spécification fait que, dans un document :

- tous les types d'éléments et noms d'attributs contiennent un deux-points ou n'en contiennent pas ;

- aucun nom d'entité, aucune cible ProcessingInstruction et aucun nom de notation ne contient de deux-points.

La présence d'un signe deux-points dans `<?xml:stylesheet?>` provoque la violation de la règle décrite au second point.

Conformément à la recommandation du W3C (World Wide Web Consortium) sur l’[association de feuilles de style à des documents XML version 1.0](https://www.w3.org/TR/xml-stylesheet/), l’instruction de traitement destinée à associer une feuille de style XSLT à un document XML est `<?xml-stylesheet?>`, où un trait d’union remplace le signe deux-points.

## <a name="see-also"></a>Voir aussi

- [DOM (Document Object Model) XML](xml-document-object-model-dom.md)
