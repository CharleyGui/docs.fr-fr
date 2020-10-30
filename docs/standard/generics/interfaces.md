---
title: Interfaces génériques
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- generic interfaces [.NET]
- equality comparisons [.NET]
- generics [.NET], interfaces
- ordering comparisons [.NET]
ms.assetid: 88bf5b04-d371-4edb-ba38-01ec7cabaacf
ms.openlocfilehash: 6e107250cef38d532310cd193c9324d1d39c096a
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93064052"
---
# <a name="generic-interfaces"></a>Interfaces génériques

Cet article fournit une vue d’ensemble des interfaces génériques qui fournissent des fonctionnalités communes à toutes les familles de types génériques.  
  
Les interfaces génériques fournissent des contreparties de type sécurisé aux interfaces non génériques pour les comparaisons de classement et d’égalité, et pour les fonctionnalités partagées par les types de collections génériques.  
  
> [!NOTE]
> Les paramètres de type de plusieurs interfaces génériques sont marqués comme étant covariants ou contravariants, ce qui offre une plus grande flexibilité dans l’assignation et l’utilisation des types qui implémentent ces interfaces. Consultez [Covariance et contravariance](covariance-and-contravariance.md).  
  
## <a name="equality-and-ordering-comparisons"></a>Comparaisons d'égalité et de classement  
 Dans l'espace de noms <xref:System>, les interfaces génériques <xref:System.IComparable%601?displayProperty=nameWithType> et <xref:System.IEquatable%601?displayProperty=nameWithType>, comme leurs contreparties non génériques, définissent respectivement des méthodes pour les comparaisons de classement et les comparaisons d'égalité. Les types implémentent ces interfaces pour offrir la capacité à réaliser de telles comparaisons.  
  
 Dans l'espace de noms <xref:System.Collections.Generic>, les interfaces génériques <xref:System.Collections.Generic.IComparer%601> et <xref:System.Collections.Generic.IEqualityComparer%601> offrent un moyen de définir une comparaison de classement ou d'égalité pour les types qui n'implémentent pas les interfaces génériques <xref:System.IComparable%601?displayProperty=nameWithType> ou <xref:System.IEquatable%601?displayProperty=nameWithType>, et ils permettent de redéfinir ces relations pour les types qui les implémentent. Ces interfaces sont utilisées par les méthodes et les constructeurs de nombreuses classes de collection génériques. Par exemple, vous pouvez passer un objet <xref:System.Collections.Generic.IComparer%601> générique au constructeur de la classe <xref:System.Collections.Generic.SortedDictionary%602> pour spécifier un ordre de tri pour un type qui n'implémente pas l'interface générique <xref:System.IComparable%601?displayProperty=nameWithType>. Il existe des surcharges de la méthode statique générique <xref:System.Array.Sort%2A?displayProperty=nameWithType> et de la méthode d'instance <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> pour le tri des tableaux et des listes à l'aide  d'implémentations génériques de <xref:System.Collections.Generic.IComparer%601>.  
  
 Les classes génériques <xref:System.Collections.Generic.Comparer%601> et <xref:System.Collections.Generic.EqualityComparer%601> fournissent des classes de base pour les implémentations des interfaces génériques <xref:System.Collections.Generic.IComparer%601> et <xref:System.Collections.Generic.IEqualityComparer%601>, et fournissent également des comparaisons de classement et d'égalité par défaut via leurs propriétés respectives <xref:System.Collections.Generic.Comparer%601.Default%2A?displayProperty=nameWithType> et <xref:System.Collections.Generic.EqualityComparer%601.Default%2A?displayProperty=nameWithType>.  
  
## <a name="collection-functionality"></a>Fonctionnalités des collections  
 L'interface générique <xref:System.Collections.Generic.ICollection%601> est l'interface de base pour les types de collections génériques. Elle offre des fonctionnalités de base pour l'ajout, la suppression, la copie et l'énumération d'éléments. <xref:System.Collections.Generic.ICollection%601> hérite à la fois de l'interface générique <xref:System.Collections.Generic.IEnumerable%601> et de l'interface non générique <xref:System.Collections.IEnumerable>.  
  
 L'interface générique <xref:System.Collections.Generic.IList%601> étend l'interface générique <xref:System.Collections.Generic.ICollection%601> avec des méthodes pour la récupération indexée.  
  
 L'interface générique <xref:System.Collections.Generic.IDictionary%602> étend l'interface générique <xref:System.Collections.Generic.ICollection%601> avec des méthodes pour la récupération indexée. Les types de dictionnaires génériques dans la bibliothèque de classes de base .NET implémentent également l’interface non générique <xref:System.Collections.IDictionary> .  
  
 L'interface générique <xref:System.Collections.Generic.IEnumerable%601> fournit une structure d'énumérateur générique. L'interface générique <xref:System.Collections.Generic.IEnumerator%601> implémentée par les énumérateurs génériques hérite de l'interface non générique <xref:System.Collections.IEnumerator> ; les membres <xref:System.Collections.IEnumerator.MoveNext%2A> et <xref:System.Collections.IEnumerator.Reset%2A>, qui ne dépendent pas du paramètre de type `T`, apparaissent seulement sur l'interface non générique. Cela signifie que tout consommateur de l'interface non générique peut également consommer l'interface générique.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Génériques](index.md)
- [Collections génériques dans .NET](collections.md)
- [Délégués génériques pour la manipulation de tableaux et de listes](delegates-for-manipulating-arrays-and-lists.md)
- [Covariance et contravariance](covariance-and-contravariance.md)
