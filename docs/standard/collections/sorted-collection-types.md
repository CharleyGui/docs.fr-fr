---
title: Types de collections triées
ms.date: 04/30/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- SortedDictionary collection type
- SortedList class, grouping data in collections
- grouping data in collections, SortedList collection type
- SortedList collection type
- collections [.NET], SortedList collection type
ms.assetid: 3db965b2-36a6-4b12-b76e-7f074ff7275a
ms.openlocfilehash: 339d247f3b7e775de740c6c1ce786b078441c699
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889320"
---
# <a name="sorted-collection-types"></a>Types de collections triées

La classe <xref:System.Collections.SortedList?displayProperty=nameWithType>, la classe générique <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> et la classe générique <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> sont similaires à la classe <xref:System.Collections.Hashtable> et à la classe générique <xref:System.Collections.Generic.Dictionary%602>, car elles implémentent l’interface <xref:System.Collections.IDictionary>, mais conservent leurs éléments triés par clé et ne possèdent pas les caractéristiques d’insertion ni de récupération O(1) des tables de hachage. Les trois classes ont plusieurs fonctionnalités en commun :

- Les trois classes implémentent toutes l’interface <xref:System.Collections.IDictionary?displayProperty=nameWithType>. Les deux classes génériques implémentent également l’interface générique <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>.

- Chaque élément est une paire clé/valeur utilisée à des fins d’énumération.

   > [!NOTE]
   > La classe <xref:System.Collections.SortedList> non générique retourne des objets <xref:System.Collections.DictionaryEntry> quand elle est énumérée, même si les deux types génériques retournent des objets <xref:System.Collections.Generic.KeyValuePair%602>.

- Les éléments sont triés selon une implémentation d’<xref:System.Collections.IComparer?displayProperty=nameWithType> (pour la classe <xref:System.Collections.SortedList> non générique) ou une implémentation d’<xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> (pour les deux classes génériques).

- Chaque classe fournit des propriétés qui retournent des collections contenant uniquement les clés ou uniquement les valeurs.

Le tableau suivant répertorie certaines des différences entre les deux classes de liste triée et la classe <xref:System.Collections.Generic.SortedDictionary%602>.

| <xref:System.Collections.SortedList> (classe non générique) et <xref:System.Collections.Generic.SortedList%602> (classe générique) | <xref:System.Collections.Generic.SortedDictionary%602> (classe générique) |
|--|--|
| Les propriétés qui retournent des clés et des valeurs sont indexées, ce qui permet une récupération indexée efficace. | Aucune récupération indexée. |
| La récupération est O(log `n`). | La récupération est O(log `n`). |
| L’insertion et la suppression correspondent généralement à O(`n`). Toutefois, l’insertion correspond à O(log `n`) pour les données qui se trouvent déjà en ordre de tri, afin que chaque élément soit ajouté à la fin de la liste. (Cela suppose qu’un redimensionnement n’est pas requis.) | L’insertion et la suppression sont O(log `n`). |
| Utilise moins de mémoire qu’un <xref:System.Collections.Generic.SortedDictionary%602>. | Utilise plus de mémoire que la classe non générique <xref:System.Collections.SortedList> et la classe générique <xref:System.Collections.Generic.SortedList%602>. |

Pour les listes ou les dictionnaires triés qui doivent être accessibles simultanément à partir de plusieurs threads, vous pouvez ajouter une logique de tri à une classe qui dérive de <xref:System.Collections.Concurrent.ConcurrentDictionary%602>. Lorsque vous envisagez l’immuabilité, les types immuables correspondants suivants suivent la même sémantique de tri : <xref:System.Collections.Immutable.ImmutableSortedSet%601> et <xref:System.Collections.Immutable.ImmutableSortedDictionary%602> .

> [!NOTE]
> Pour les valeurs qui contiennent leurs propres clés (par exemple, des enregistrements d’employés qui contiennent un numéro d’ID de l’employé), vous pouvez créer une collection à clé qui possède certaines caractéristiques d’une liste et certaines caractéristiques d’un dictionnaire en dérivant de la classe générique <xref:System.Collections.ObjectModel.KeyedCollection%602>.

À partir de .NET Framework 4, la <xref:System.Collections.Generic.SortedSet%601> classe fournit une arborescence à équilibrage automatique qui conserve les données dans l’ordre de tri après les insertions, les suppressions et les recherches. Cette classe et la classe <xref:System.Collections.Generic.HashSet%601> implémentent l’interface <xref:System.Collections.Generic.ISet%601>.

## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.IDictionary?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602>
- [Types de collections couramment utilisés](commonly-used-collection-types.md)
