---
title: Équivalence des types et types interop incorporés
description: Comprendre l’équivalence de type entre les types et les membres .NET avec un assembly managé, et les types COM incorporés dans cet assembly. Pour .NET 4 et versions ultérieures.
ms.date: 03/30/2017
helpviewer_keywords:
- type equivalence
- embedded interop types
- primary interop assemblies,not necessary in CLR version 4
- NoPIA
ms.assetid: 78892eba-2a58-4165-b4b1-0250ee2f41dc
ms.openlocfilehash: 2d572133c42f01af7d50f6f771588f5173853f9a
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86282006"
---
# <a name="type-equivalence-and-embedded-interop-types"></a>Équivalence des types et types interop incorporés

À compter de .NET Framework 4, le Common Language Runtime prend en charge l’incorporation des informations de type, pour les types COM, directement dans les assemblys managés. Auparavant, les assemblys managés devaient obtenir ces informations des assemblys interop. Étant donné que les informations de type incorporées incluent uniquement les types et les membres qui sont réellement utilisés par un assembly managé, deux assemblys managés peuvent présenter des affichages très différents du même type COM. Chaque assembly managé a un objet <xref:System.Type> différent pour représenter son affichage du type COM. Le Common Language Runtime prend en charge l’équivalence des types entre ces différents affichages pour les interfaces, les structures, les énumérations et les délégués.

Avec l’équivalence des types, un objet COM qui est passé d’un assembly managé à un autre peut être casté en type managé approprié dans l’assembly de réception.

> [!NOTE]
> L’équivalence des types et les types interop incorporés simplifient le déploiement des applications et compléments qui utilisent des composants COM, car cela évite d’avoir à déployer des assemblys interop avec les applications. Les développeurs de composants COM partagés doivent continuer à créer des assemblys PIA (Primary Interop Assemblies) s’ils veulent pouvoir utiliser leurs composants dans des versions de .NET Framework antérieures.

## <a name="type-equivalence"></a>Équivalence des types

 L’équivalence des types COM est prise en charge pour les interfaces, les structures, les énumérations et les délégués. Deux types COM sont considérés comme équivalents s’ils remplissent toutes les conditions suivantes :

- Les deux types sont des interfaces, des structures, des énumérations ou des délégués.

- Les deux types ont la même identité, comme décrit dans la section suivante.

- Les deux types sont éligibles pour l’équivalence de type, comme décrit dans la section [marquage de types com pour l’équivalence de type](#marking-com-types-for-type-equivalence) .

### <a name="type-identity"></a>Identité des types

Deux types sont considérés comme ayant la même identité si leurs portées et identités correspondent ou, en d’autres termes, s’ils sont chacun définis avec l’attribut <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> et si les deux attributs ont les mêmes propriétés <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> et <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A>. La comparaison de <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> est effectuée en respectant la casse.

Si un type n’est pas défini avec l’attribut <xref:System.Runtime.InteropServices.TypeIdentifierAttribute>, ou si son attribut <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> ne spécifie pas de portée ni d’identité, le type reste toutefois disponible pour l’équivalence de la manière suivante :

- Pour les interfaces, la valeur de l’attribut <xref:System.Runtime.InteropServices.GuidAttribute> est utilisée à la place de la propriété <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=nameWithType> et la propriété <xref:System.Type.FullName%2A?displayProperty=nameWithType> (correspondant au nom de type, avec l’espace de noms) est utilisée à la place de la propriété <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=nameWithType>.

- Pour les structures, les énumérations et les délégués, l’attribut <xref:System.Runtime.InteropServices.GuidAttribute> de l’assembly conteneur est utilisé au lieu de la propriété <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> et la propriété <xref:System.Type.FullName%2A?displayProperty=nameWithType> est utilisée au lieu de la propriété <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A>.

### <a name="marking-com-types-for-type-equivalence"></a>Marquer des types COM pour l’équivalence des types

 Vous pouvez marquer un type comme étant disponible pour l’équivalence des types de deux manières :

- Appliquez l’attribut <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> au type.

- Marquez le type comme type d’importation COM. Une interface est un type d’importation COM si elle a l’attribut <xref:System.Runtime.InteropServices.ComImportAttribute>. Une interface, une structure, une énumération ou un délégué est un type d’importation COM si l’assembly dans lequel ils sont définis a l’attribut <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute>.

## <a name="see-also"></a>Voir aussi

- <xref:System.Type.IsEquivalentTo%2A>
- [Utiliser des types COM dans du code managé](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Importation d'une bibliothèque de types sous la forme d'un assembly](importing-a-type-library-as-an-assembly.md)
