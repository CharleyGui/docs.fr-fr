---
title: Extension des métadonnées à l'aide des attributs
description: Découvrez comment étendre les métadonnées à l’aide d’attributs dans .NET. Les attributs sont des déclarations descriptives de type mot clé pour annoter des éléments de programmation, tels que les types et les champs.
ms.date: 10/14/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- metadata, extending
- attributes [.NET], metadata
- elements [.NET], attributes
- common language runtime, attributes
- annotating programming elements
- keyword-like descriptive declarations
- runtime, attributes
- extending metadata
ms.assetid: 30386922-1e00-4602-9ebf-526b271a8b87
ms.openlocfilehash: 9a83c0e8ee3476f43ccc2e88c21ccbbc0661bd19
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889216"
---
# <a name="extend-metadata-using-attributes"></a>Étendre des métadonnées en utilisant des attributs

Le common language runtime vous permet d’ajouter des déclarations descriptives de type mot clé, appelées attributs, pour annoter les éléments de programmation comme des types, des champs, des méthodes et des propriétés. Quand vous compilez votre code pour le runtime, il est converti en langage MSIL (Microsoft Intermediate Language) et placé dans un fichier exécutable portable avec des métadonnées générées par le compilateur. Les attributs vous permettent de placer des informations descriptives supplémentaires dans les métadonnées, qui peuvent être extraites à l'aide des services de réflexion du runtime. Le compilateur crée des attributs quand vous déclarez des instances de classes spéciales qui dérivent de <xref:System.Attribute?displayProperty=nameWithType>.

.NET utilise des attributs pour diverses raisons et pour répondre à un certain nombre de problèmes. Les attributs décrivent comment sérialiser les données, spécifient des caractéristiques qui sont utilisées pour appliquer la sécurité et limitent les optimisations du compilateur juste-à-temps (JIT) pour que le code reste facile à déboguer. Les attributs peuvent également enregistrer le nom d'un fichier ou l'auteur du code, ou bien contrôler la visibilité des contrôles et des membres pendant le développement des formulaires.

## <a name="related-articles"></a>Articles connexes

|Intitulé|Description|
|-----------|-----------------|
|[Application des attributs](applying-attributes.md)|Décrit comment appliquer un attribut à un élément de votre code.|
|[Écriture des attributs personnalisés](writing-custom-attributes.md)|Décrit comment concevoir des classes d'attributs personnalisés.|
|[Récupération des informations stockées dans les attributs](retrieving-information-stored-in-attributes.md)|Décrit comment récupérer des attributs personnalisés pour le code qui est chargé dans le contexte d'exécution.|
|[Métadonnées et composants de Self-Describing](../metadata-and-self-describing-components.md)|Fournit une vue d’ensemble des métadonnées et décrit comment elles sont implémentées dans un fichier exécutable portable (PE) .NET.|
|[Guide pratique pour charger des assemblys dans le contexte de réflexion uniquement](../../framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|Explique comment récupérer les informations des attributs personnalisés dans le contexte de réflexion uniquement.|

## <a name="reference"></a>Informations de référence

- <xref:System.Attribute?displayProperty=nameWithType>
