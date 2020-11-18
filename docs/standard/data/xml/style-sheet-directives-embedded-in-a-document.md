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
# <a name="style-sheet-directives-embedded-in-a-document"></a><span data-ttu-id="9eb79-102">Directives de feuille de style incorporées dans un document</span><span class="sxs-lookup"><span data-stu-id="9eb79-102">Style Sheet Directives Embedded in a Document</span></span>

<span data-ttu-id="9eb79-103">Il arrive parfois que des données XML existantes contiennent la directive de feuille de style de `<?xml:stylesheet?>`.</span><span class="sxs-lookup"><span data-stu-id="9eb79-103">Occasionally, existing XML contains the style sheet directive of `<?xml:stylesheet?>`.</span></span> <span data-ttu-id="9eb79-104">Microsoft Internet Explorer accepte cette directive comme une alternative à la syntaxe `<?xml-stylesheet?>`.</span><span class="sxs-lookup"><span data-stu-id="9eb79-104">Microsoft Internet Explorer accepts this as an alternative to the `<?xml-stylesheet?>` syntax.</span></span> <span data-ttu-id="9eb79-105">Quand les données XML contiennent une directive `<?xml:stylesheet?>`, comme le montrent les données suivantes, une tentative de chargement de ces données dans le DOM (Document Object Model) XML entraîne la levée d'une exception.</span><span class="sxs-lookup"><span data-stu-id="9eb79-105">When the XML data contains an `<?xml:stylesheet?>` directive, as shown in the following data, attempting to load this data into the XML Document Object Model (DOM) throws an exception.</span></span>

```xml
<?xml version="1.0" ?>
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>
<root>
    <test>Node 1</test>
    <test>Node 2</test>
</root>
```

<span data-ttu-id="9eb79-106">Cela est dû au fait que `<?xml:stylesheet?>` est considéré comme un **ProcessingInstruction** non valide pour le DOM.</span><span class="sxs-lookup"><span data-stu-id="9eb79-106">This occurs because the `<?xml:stylesheet?>` is considered an invalid **ProcessingInstruction** to the DOM.</span></span> <span data-ttu-id="9eb79-107">Conformément à la spécification des espaces de noms XML, tout **ProcessingInstruction** peut uniquement comporter des noms sans deux-points (NCNames), par opposition aux noms qualifiés (QNames).</span><span class="sxs-lookup"><span data-stu-id="9eb79-107">Any **ProcessingInstruction**, according to the Namespaces in XML specification, can only be no-colon names (NCNames), as opposed to qualified names (QNames).</span></span>

<span data-ttu-id="9eb79-108">Si l'on s'en tient à la section 6 de cette spécification, la présence des méthodes **Load** et **LoadXml** conformes à cette spécification fait que, dans un document :</span><span class="sxs-lookup"><span data-stu-id="9eb79-108">From Section 6 of the Namespaces in XML specification, the effect of having the **Load** and **LoadXml** methods conform to the specification is that in a document:</span></span>

- <span data-ttu-id="9eb79-109">tous les types d'éléments et noms d'attributs contiennent un deux-points ou n'en contiennent pas ;</span><span class="sxs-lookup"><span data-stu-id="9eb79-109">All element types and attribute names contain either zero or one colon.</span></span>

- <span data-ttu-id="9eb79-110">aucun nom d'entité, aucune cible ProcessingInstruction et aucun nom de notation ne contient de deux-points.</span><span class="sxs-lookup"><span data-stu-id="9eb79-110">No entity names, ProcessingInstruction targets, or notation names contain any colons.</span></span>

<span data-ttu-id="9eb79-111">La présence d'un signe deux-points dans `<?xml:stylesheet?>` provoque la violation de la règle décrite au second point.</span><span class="sxs-lookup"><span data-stu-id="9eb79-111">With the `<?xml:stylesheet?>` containing a colon, you now violate the rule in the second bullet.</span></span>

<span data-ttu-id="9eb79-112">Conformément à la recommandation du W3C (World Wide Web Consortium) sur l’[association de feuilles de style à des documents XML version 1.0](https://www.w3.org/TR/xml-stylesheet/), l’instruction de traitement destinée à associer une feuille de style XSLT à un document XML est `<?xml-stylesheet?>`, où un trait d’union remplace le signe deux-points.</span><span class="sxs-lookup"><span data-stu-id="9eb79-112">According to the World Wide Web Consortium (W3C) [Associating Style Sheets with XML documents Version 1.0 Recommendation](https://www.w3.org/TR/xml-stylesheet/),  the processing instruction to associate an XSLT style sheet with an XML document is `<?xml-stylesheet?>`, with a dash replacing the colon.</span></span>

## <a name="see-also"></a><span data-ttu-id="9eb79-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9eb79-113">See also</span></span>

- [<span data-ttu-id="9eb79-114">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="9eb79-114">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
