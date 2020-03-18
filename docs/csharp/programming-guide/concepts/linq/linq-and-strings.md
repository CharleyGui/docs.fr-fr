---
title: LINQ et chaînes (C#)
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: b805bc7318b8c5fe70ab1c060d1058a6bbc4f177
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635533"
---
# <a name="linq-and-strings-c"></a>LINQ et chaînes (C#)

LINQ peut être utilisé pour interroger et transformer des chaînes et des collections de chaînes. Il peut être particulièrement utile avec des données semi-structurées dans des fichiers texte. Les requêtes LINQ peuvent être combinées avec les fonctions de chaîne traditionnelles et les expressions régulières. Par exemple, vous pouvez utiliser la méthode <xref:System.String.Split%2A?displayProperty=nameWithType> ou <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> pour créer un tableau de chaînes que vous pouvez ensuite interroger ou modifier à l’aide de LINQ. Vous pouvez utiliser la méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> dans la clause `where` d’une requête LINQ. Et vous pouvez utiliser LINQ pour interroger ou modifier les résultats <xref:System.Text.RegularExpressions.MatchCollection> retournés par une expression régulière.

Vous pouvez également utiliser les techniques décrites dans cette section pour transformer des données texte semi-structurées en XML. Pour plus d’informations, voir [Comment générer XML à partir de fichiers CSV](how-to-generate-xml-from-csv-files.md).

Les exemples de cette section se répartissent en deux catégories :

## <a name="querying-a-block-of-text"></a>Interrogation d’un bloc de texte

Vous pouvez interroger, analyser et modifier des blocs de texte en les fractionnant en tableau requêtable de chaînes plus petites à l’aide de la méthode <xref:System.String.Split%2A?displayProperty=nameWithType> ou de la méthode <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType>. Vous pouvez fractionner le texte source en mots, en phrases, en paragraphes, en pages ou selon d’autres critères, puis effectuer des fractionnements supplémentaires s’ils sont nécessaires dans votre requête.

- [Comment compter les occurrences d’un mot dans une chaîne (LINQ) (C)](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  Montre comment utiliser LINQ pour des interrogations simples sur du texte.

- [Comment interroger les phrases qui contiennent un ensemble de mots spécifiés (LINQ) (C)](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  Montre comment fractionner des fichiers texte avec des limites arbitraires et comment exécuter des requêtes sur chaque partie.

- [Comment interroger les personnages d’une chaîne (LINQ) (C)](how-to-query-for-characters-in-a-string-linq.md)

  Montre qu’une chaîne est un type interrogeable.

- [Comment combiner les requêtes LINQ avec des expressions régulières (C)](how-to-combine-linq-queries-with-regular-expressions.md)

  Montre comment utiliser des expressions régulières dans les requêtes LINQ pour des correspondances de modèle complexes sur des résultats de requête filtrés.

## <a name="querying-semi-structured-data-in-text-format"></a>Interrogation de données semi-structurées au format texte

De nombreux types différents de fichiers texte sont constitués d’une série de lignes, souvent avec la même mise en forme, comme les fichiers délimités par des tabulations ou des virgules, ou des lignes de longueur fixe. Après avoir lu un tel fichier texte dans la mémoire, vous pouvez utiliser LINQ pour interroger et/ou modifier les lignes. Les requêtes LINQ simplifient également la combinaison de données provenant de plusieurs sources.

- [Comment trouver la différence entre deux listes (LINQ) (C)](how-to-find-the-set-difference-between-two-lists-linq.md)

  Montre comment rechercher toutes les chaînes qui sont présentes dans une liste mais pas dans l’autre.

- [Comment trier ou filtrer les données de texte par n’importe quel mot ou champ (LINQ) (C)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  Montre comment trier les lignes de texte en fonction de n’importe quel mot ou champ.

- [Comment réorganiser les champs d’un fichier délimité (LINQ) (C)](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  Montre comment réorganiser les champs dans une ligne d’un fichier .csv.

- [Comment combiner et comparer les collections de cordes (LINQ) (C)](how-to-combine-and-compare-string-collections-linq.md)

  Montre comment combiner des listes de chaînes de différentes façons.

- [Comment remplir les collections d’objets à partir de sources multiples (LINQ) (C)](how-to-populate-object-collections-from-multiple-sources-linq.md)

  Montre comment créer des collections d’objets à l’aide de plusieurs fichiers texte comme sources de données.

- [Comment joindre le contenu des fichiers différents (LINQ) (C)](how-to-join-content-from-dissimilar-files-linq.md)
  
  Montre comment combiner des chaînes de deux listes en une seule chaîne en utilisant une clé en correspondance.

- [Comment diviser un fichier en plusieurs fichiers en utilisant des groupes (LINQ) (C)](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  Montre comment créer des fichiers en utilisant un seul fichier comme source de données.

- [Comment calculer les valeurs de colonne dans un fichier texte CSV (LINQ) (C)](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  Montre comment effectuer des calculs mathématiques sur des données texte dans des fichiers .csv.

## <a name="see-also"></a>Voir aussi

- [LINQ (Language-Integrated Query) (C#)](index.md)
- [Comment générer du code XML à partir de fichiers CSV](how-to-generate-xml-from-csv-files.md)
