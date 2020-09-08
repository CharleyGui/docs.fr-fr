---
title: Transformation fonctionnelle des LINQ to XML XML
description: Découvrez l’approche de transformation fonctionnelle pure permettant de modifier des documents XML et leurs différences par rapport à une approche procédurale.
ms.date: 07/20/2015
ms.assetid: 0ccb9251-38d7-44e3-9b84-1b5fe25e4b59
ms.openlocfilehash: b23288e013a4104b21523e17e1f266a9f712c451
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552449"
---
# <a name="functional-transformation-of-xml-linq-to-xml"></a>Transformation fonctionnelle de XML (LINQ to XML)

Cet article décrit l’approche de transformation fonctionnelle pure permettant de modifier des documents XML et les compare à une approche procédurale.

## <a name="modifying-an-xml-document"></a>Modification d’un document XML

L'une des tâches les plus courantes pour un programmeur XML consiste à transformer du code XML d'une forme en une autre. La forme d'un document XML est la structure du document, qui inclut les éléments suivants :

- la hiérarchie exprimée par le document ;
- les noms des éléments et des attributs ;
- les types de données des éléments et attributs.

En général, l'approche la plus efficace pour transformer du code XML d'une forme en une autre consiste à utiliser la transformation fonctionnelle pure. Avec cette approche, la principale tâche du programmeur est de créer une transformation qui est appliquée à l'ensemble du document XML (ou à un ou plusieurs nœuds strictement définis). La transformation fonctionnelle offre sans aucun doute la plus grande facilité de codage (une fois que le programmeur s'est familiarisé avec cette approche) et la plus grande facilité de maintenance du code, et elle est souvent plus compacte que les autres approches.

### <a name="xml-functional-transformational-technologies"></a>Technologies de transformation fonctionnelle XML

Microsoft propose deux technologies de transformation fonctionnelle pour une utilisation sur des documents XML : XSLT et LINQ to XML. XSLT est pris en charge dans l'espace de noms managé <xref:System.Xml.Xsl> et dans l'implémentation COM native de MSXML. Bien que XSLT soit une technologie robuste pour la manipulation de documents XML, elle requiert un savoir-faire dans un domaine spécialisé, à savoir le langage XSLT et ses API de prise en charge.

LINQ to XML procure les outils nécessaires pour coder des transformations fonctionnelles pures de manière expressive et puissante, dans du code C# ou Visual Basic. Par exemple, bon nombre des exemples dans la documentation LINQ to XML utilisent une approche fonctionnelle pure. En outre, dans le didacticiel [: manipulation de contenu dans un document WordprocessingML](xml-shape-wordprocessingml-documents.md) , nous utilisons LINQ to XML dans une approche fonctionnelle pour manipuler des informations dans un document Microsoft Word.

Pour une comparaison plus complète des LINQ to XML avec d’autres technologies XML Microsoft, consultez [LINQ to XML différences par rapport à d’autres technologies XML](linq-xml-vs-xml-technologies.md).

XSLT est l'outil recommandé pour les transformations centrées sur les documents lorsque le document source a une structure irrégulière. Toutefois, LINQ to XML peut également effectuer des transformations centrées sur les documents. Pour plus d’informations, consultez [comment utiliser des annotations pour transformer des arbres LINQ to XML dans un style XSLT](use-annotations-transform-linq-xml-trees-xslt-style.md).

## <a name="see-also"></a>Voir aussi

- [Présentation des transformations fonctionnelles pures](introduction-pure-functional-transformations.md)
- [Didacticiel : manipuler du contenu dans un document WordprocessingML](xml-shape-wordprocessingml-documents.md)
- [LINQ to XML différences par rapport à d’autres technologies XML](linq-xml-vs-xml-technologies.md)
