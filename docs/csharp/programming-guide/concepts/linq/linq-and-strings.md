---
title: LINQ et chaînes (C#)
description: LINQ peut interroger et transformer des chaînes et des collections de chaînes. Vous pouvez combiner des requêtes LINQ avec des fonctions de chaîne et des expressions régulières C#.
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: c515a0c56ad6473f93c6339540e4ed0245bb5bd2
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165615"
---
# <a name="linq-and-strings-c"></a>LINQ et chaînes (C#)

LINQ peut être utilisé pour interroger et transformer des chaînes et des collections de chaînes. Il peut être particulièrement utile avec des données semi-structurées dans des fichiers texte. Les requêtes LINQ peuvent être combinées avec les fonctions de chaîne traditionnelles et les expressions régulières. Par exemple, vous pouvez utiliser la méthode <xref:System.String.Split%2A?displayProperty=nameWithType> ou <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> pour créer un tableau de chaînes que vous pouvez ensuite interroger ou modifier à l’aide de LINQ. Vous pouvez utiliser la méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> dans la clause `where` d’une requête LINQ. Et vous pouvez utiliser LINQ pour interroger ou modifier les résultats <xref:System.Text.RegularExpressions.MatchCollection> retournés par une expression régulière.

Vous pouvez également utiliser les techniques décrites dans cette section pour transformer des données texte semi-structurées en XML. Pour plus d’informations, consultez [Comment générer du code XML à partir de fichiers CSV](how-to-generate-xml-from-csv-files.md).

Les exemples de cette section se répartissent en deux catégories :

## <a name="querying-a-block-of-text"></a>Interrogation d’un bloc de texte

Vous pouvez interroger, analyser et modifier des blocs de texte en les fractionnant en tableau requêtable de chaînes plus petites à l’aide de la méthode <xref:System.String.Split%2A?displayProperty=nameWithType> ou de la méthode <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType>. Vous pouvez fractionner le texte source en mots, en phrases, en paragraphes, en pages ou selon d’autres critères, puis effectuer des fractionnements supplémentaires s’ils sont nécessaires dans votre requête.

- [Comment compter les occurrences d’un mot dans une chaîne (LINQ) (C#)](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  Montre comment utiliser LINQ pour des interrogations simples sur du texte.

- [Comment interroger des phrases qui contiennent un ensemble de mots spécifié (LINQ) (C#)](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  Montre comment fractionner des fichiers texte avec des limites arbitraires et comment exécuter des requêtes sur chaque partie.

- [Comment interroger des caractères dans une chaîne (LINQ) (C#)](how-to-query-for-characters-in-a-string-linq.md)

  Montre qu’une chaîne est un type interrogeable.

- [Comment combiner des requêtes LINQ avec des expressions régulières (C#)](how-to-combine-linq-queries-with-regular-expressions.md)

  Montre comment utiliser des expressions régulières dans les requêtes LINQ pour des correspondances de modèle complexes sur des résultats de requête filtrés.

## <a name="querying-semi-structured-data-in-text-format"></a>Interrogation de données semi-structurées au format texte

De nombreux types différents de fichiers texte sont constitués d’une série de lignes, souvent avec la même mise en forme, comme les fichiers délimités par des tabulations ou des virgules, ou des lignes de longueur fixe. Après avoir lu un tel fichier texte dans la mémoire, vous pouvez utiliser LINQ pour interroger et/ou modifier les lignes. Les requêtes LINQ simplifient également la combinaison de données provenant de plusieurs sources.

- [Guide pratique pour rechercher la différence définie entre deux listes (LINQ) (C#)](how-to-find-the-set-difference-between-two-lists-linq.md)

  Montre comment rechercher toutes les chaînes qui sont présentes dans une liste mais pas dans l’autre.

- [Guide pratique pour trier ou filtrer des données texte par mot ou par champ (LINQ) (C#)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  Montre comment trier les lignes de texte en fonction de n’importe quel mot ou champ.

- [Comment réorganiser les champs d’un fichier délimité (LINQ) (C#)](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  Montre comment réorganiser les champs dans une ligne d’un fichier .csv.

- [Comment combiner et comparer des collections de chaînes (LINQ) (C#)](how-to-combine-and-compare-string-collections-linq.md)

  Montre comment combiner des listes de chaînes de différentes façons.

- [Comment remplir des collections d’objets à partir de plusieurs sources (LINQ) (C#)](how-to-populate-object-collections-from-multiple-sources-linq.md)

  Montre comment créer des collections d’objets à l’aide de plusieurs fichiers texte comme sources de données.

- [Comment joindre du contenu issu de fichiers différents (LINQ) (C#)](how-to-join-content-from-dissimilar-files-linq.md)
  
  Montre comment combiner des chaînes de deux listes en une seule chaîne en utilisant une clé en correspondance.

- [Comment fractionner un fichier en plusieurs fichiers à l’aide de groupes (LINQ) (C#)](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  Montre comment créer des fichiers en utilisant un seul fichier comme source de données.

- [Comment calculer des valeurs de colonnes dans un fichier texte CSV (LINQ) (C#)](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  Montre comment effectuer des calculs mathématiques sur des données texte dans des fichiers .csv.

## <a name="see-also"></a>Voir aussi

- [LINQ (Language-Integrated Query) (C#)](index.md)
- [Comment générer du code XML à partir de fichiers CSV](how-to-generate-xml-from-csv-files.md)
