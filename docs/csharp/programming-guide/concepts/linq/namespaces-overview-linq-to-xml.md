---
title: Vue d'ensemble des espaces de noms (LINQ to XML)
description: Présentez-vous aux espaces de noms, à la classe XName, à la classe XNamespace et à d’autres aspects des noms XML.
ms.date: 07/20/2015
ms.assetid: 16283322-8238-4918-ab11-802ac6748eb7
ms.openlocfilehash: 56dca481dd5f3066fa5359fc57b3311cf2569ee0
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87300161"
---
# <a name="namespaces-overview-linq-to-xml"></a>Vue d'ensemble des espaces de noms (LINQ to XML)

Cet article présente les espaces de noms, la classe <xref:System.Xml.Linq.XName> et la classe <xref:System.Xml.Linq.XNamespace>.

## <a name="xml-names"></a>Noms XML

Les noms XML constituent souvent une source de complexité dans la programmation XML. Un nom XML est constitué d'un espace de noms XML (également appelé URI d'espace de noms XML) et d'un nom local. Un espace de noms XML est similaire à un espace de noms dans un programme .NET. Il permet de qualifier de manière unique les noms d'éléments et d'attributs. Cela permet d'éviter les conflits de noms entre différentes parties d'un document XML. Lorsque vous avez déclaré un espace de noms XML, vous pouvez sélectionner un nom local qui n'exige d'être unique que dans cet espace de noms.

Les *préfixes d’espace de noms* XML constituent un autre aspect des noms XML. Les préfixes XML sont la cause de la plupart de la complexité des noms XML. Ces préfixes vous permettent de créer un raccourci pour un espace de noms XML, ce qui rend le document XML plus concis et plus compréhensible. Toutefois, la signification des préfixes XML dépend de leur contexte, ce qui augmente la complexité. Par exemple, le préfixe XML `aw` pourrait être associé à un espace de noms XML dans une partie d'une arborescence XML et à un espace de noms XML différent dans une autre partie de l'arborescence XML.

L’un des avantages d’utiliser [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] avec C# est que vous n’avez pas besoin de spécifier des préfixes XML. Quand [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] charge ou analyse un document XML, chaque préfixe XML est résolu à son espace de noms XML correspondant. Après cela, lorsque vous travaillez avec un document qui utilise des espaces de noms, vous accédez presque toujours aux espaces de noms par le biais de l'URI d'espace de noms, et non par le biais du préfixe d'espace de noms. Quand les développeurs utilisent des noms XML dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], ils choisissent toujours un nom XML complet (autrement dit, un espace de noms XML et un nom local). Toutefois, en cas de nécessité, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] vous permet de travailler avec les préfixes d'espaces de noms et de les contrôler.

Dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], la classe qui représente les noms XML est <xref:System.Xml.Linq.XName>. Les noms XML apparaissent fréquemment dans l’API [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], et chaque fois qu’un nom XML est requis, vous trouverez un paramètre <xref:System.Xml.Linq.XName>. Cependant, il est rare de travailler directement dans un objet <xref:System.Xml.Linq.XName>. <xref:System.Xml.Linq.XName> contient une conversion implicite de chaîne.

Pour plus d’informations, consultez <xref:System.Xml.Linq.XNamespace> et <xref:System.Xml.Linq.XName>.
