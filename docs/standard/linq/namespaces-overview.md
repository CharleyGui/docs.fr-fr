---
title: Vue d’ensemble des espaces de noms-LINQ to XML
description: En savoir plus sur les noms XML, les espaces de noms XML et les préfixes d’espaces de noms XML, ainsi que sur les classes XName et XNamespace.
ms.date: 07/20/2015
ms.assetid: 16283322-8238-4918-ab11-802ac6748eb7
ms.openlocfilehash: 81fe678a8d6be32461c675cc527595033e826165
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552533"
---
# <a name="namespaces-overview-linq-to-xml"></a>Vue d’ensemble des espaces de noms (LINQ to XML)

Cet article présente les *noms XML*, les *espaces de noms XML*, les *préfixes d’espaces de noms XML*et les <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XNamespace> classes et.

Les noms XML constituent souvent une source de complexité dans la programmation XML. Un nom XML est constitué d'un espace de noms XML (également appelé URI d'espace de noms XML) et d'un nom local. Un espace de noms XML est similaire à un espace de noms dans un programme .NET. Elle vous permet de qualifier de manière unique les noms d’éléments et d’attributs afin d’éviter les conflits de noms entre les différentes parties d’un document XML. Lorsque vous avez déclaré un espace de noms XML, vous pouvez sélectionner un nom local qui doit uniquement être unique au sein de cet espace de noms.

Un autre aspect des noms XML est le préfixe d’espace de noms XML, qui provoque la plus grande partie de la complexité des noms XML. Ces préfixes vous permettent de créer un raccourci pour un espace de noms XML, ce qui rend le document XML plus concis et plus compréhensible. Toutefois, la signification d’un préfixe XML dépend du contexte, ce qui augmente la complexité. Par exemple, le préfixe XML `aw` peut être associé à un espace de noms XML dans une partie d’une arborescence XML, et avec un espace de noms différent dans une autre partie.

L’un des avantages de l’utilisation de LINQ to XML avec C# est que vous n’avez pas besoin d’utiliser des préfixes XML. Lorsque LINQ to XML charge ou analyse un document XML, chaque préfixe XML est résolu à son espace de noms XML correspondant. Après cela, lorsque vous travaillez avec un document qui utilise des espaces de noms, vous accédez presque toujours aux espaces de noms par le biais de l'URI d'espace de noms, et non par le biais du préfixe d'espace de noms. Lorsque les développeurs travaillent avec des noms XML dans LINQ to XML ils travaillent toujours avec un nom XML complet (autrement dit, un espace de noms XML et un nom local). Toutefois, LINQ to XML vous permet de travailler avec les préfixes d’espaces de noms et de les contrôler si nécessaire.

Lorsque vous utilisez LINQ to XML avec des littéraux Visual Basic et XML, vous devez utiliser des préfixes d’espaces de noms lors de l’utilisation de documents dans des espaces de noms.

Dans LINQ to XML, la classe qui représente les noms XML est <xref:System.Xml.Linq.XName> . Les noms XML apparaissent fréquemment dans l’API LINQ to XML, et chaque fois qu’un nom XML est requis, vous trouverez un <xref:System.Xml.Linq.XName> paramètre. Cependant, il est rare de travailler directement dans un objet <xref:System.Xml.Linq.XName>. <xref:System.Xml.Linq.XName> contient une conversion implicite de chaîne.

Pour plus d’informations, consultez <xref:System.Xml.Linq.XNamespace> et <xref:System.Xml.Linq.XName>.
