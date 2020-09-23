---
title: LINQ et chaînes
ms.date: 07/20/2015
ms.assetid: 75ddb201-d97a-4f98-8cdf-4ad51714529a
ms.openlocfilehash: 28c11dcc3c788ea85516e8b3fbafe2677b6d9b54
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075341"
---
# <a name="linq-and-strings-visual-basic"></a>LINQ et chaînes (Visual Basic)

LINQ peut être utilisé pour interroger et transformer des chaînes et des collections de chaînes. Il peut être particulièrement utile avec des données semi-structurées dans des fichiers texte. Les requêtes LINQ peuvent être combinées avec les fonctions de chaîne traditionnelles et les expressions régulières. Par exemple, vous pouvez utiliser la méthode <xref:System.String.Split%2A> ou <xref:System.Text.RegularExpressions.Regex.Split%2A> pour créer un tableau de chaînes que vous pouvez ensuite interroger ou modifier à l’aide de LINQ. Vous pouvez utiliser la méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> dans la clause `where` d’une requête LINQ. Et vous pouvez utiliser LINQ pour interroger ou modifier les résultats <xref:System.Text.RegularExpressions.MatchCollection> retournés par une expression régulière.  
  
 Vous pouvez également utiliser les techniques décrites dans cette section pour transformer des données texte semi-structurées en XML. Pour plus d’informations, consultez [Comment : générer du code XML à partir de fichiers CSV](../../../../standard/linq/generate-xml-csv-files.md).  
  
 Les exemples de cette section se répartissent en deux catégories :  
  
## <a name="querying-a-block-of-text"></a>Interrogation d’un bloc de texte  

 Vous pouvez interroger, analyser et modifier des blocs de texte en les fractionnant en tableau requêtable de chaînes plus petites à l’aide de la méthode <xref:System.String.Split%2A> ou de la méthode <xref:System.Text.RegularExpressions.Regex.Split%2A>. Vous pouvez fractionner le texte source en mots, en phrases, en paragraphes, en pages ou selon d’autres critères, puis effectuer des fractionnements supplémentaires s’ils sont nécessaires dans votre requête.  
  
 [Comment : compter les occurrences d’un mot dans une chaîne (LINQ) (Visual Basic)](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 Montre comment utiliser LINQ pour des interrogations simples sur du texte.  
  
 [Comment : rechercher des phrases qui contiennent un groupe de mots spécifié (LINQ) (Visual Basic)](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

 Montre comment fractionner des fichiers texte avec des limites arbitraires et comment exécuter des requêtes sur chaque partie.  
  
 [Comment : interroger des caractères dans une chaîne (LINQ) (Visual Basic)](how-to-query-for-characters-in-a-string-linq.md)  
 Montre qu’une chaîne est un type interrogeable.  
  
 [Comment combiner des requêtes LINQ avec des expressions régulières (Visual Basic)](how-to-combine-linq-queries-with-regular-expressions.md)  
 Montre comment utiliser des expressions régulières dans les requêtes LINQ pour des correspondances de modèle complexes sur des résultats de requête filtrés.  
  
## <a name="querying-semi-structured-data-in-text-format"></a>Interrogation de données semi-structurées au format texte  

 De nombreux types différents de fichiers texte sont constitués d’une série de lignes, souvent avec la même mise en forme, comme les fichiers délimités par des tabulations ou des virgules, ou des lignes de longueur fixe. Après avoir lu un tel fichier texte dans la mémoire, vous pouvez utiliser LINQ pour interroger et/ou modifier les lignes. Les requêtes LINQ simplifient également la combinaison de données provenant de plusieurs sources.  
  
 [Comment : Rechercher la différence définie entre deux listes (LINQ) (Visual Basic)](how-to-find-the-set-difference-between-two-lists-linq.md)  
 Montre comment rechercher toutes les chaînes qui sont présentes dans une liste mais pas dans l’autre.  
  
 [Comment : trier ou filtrer des données texte par mot ou par champ (LINQ) (Visual Basic)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 Montre comment trier les lignes de texte en fonction de n’importe quel mot ou champ.  
  
 [Comment : réorganiser les champs d’un fichier délimité (LINQ) (Visual Basic)](how-to-reorder-the-fields-of-a-delimited-file.md)  
 Montre comment réorganiser les champs dans une ligne d’un fichier .csv.  
  
 [Comment : combiner et comparer des collections de chaînes (LINQ) (Visual Basic)](how-to-combine-and-compare-string-collections-linq.md)  
 Montre comment combiner des listes de chaînes de différentes façons.  
  
 [Comment : remplir des collections d’objets à partir de plusieurs sources (LINQ) (Visual Basic)](how-to-populate-object-collections-from-multiple-sources-linq.md)  
 Montre comment créer des collections d’objets à l’aide de plusieurs fichiers texte comme sources de données.  
  
 [Comment : joindre du contenu issu de fichiers différents (LINQ) (Visual Basic)](how-to-join-content-from-dissimilar-files-linq.md)  
 Montre comment combiner des chaînes de deux listes en une seule chaîne en utilisant une clé en correspondance.  
  
 [Comment : fractionner un fichier en plusieurs fichiers à l’aide de groupes (LINQ) (Visual Basic)](how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 Montre comment créer des fichiers en utilisant un seul fichier comme source de données.  
  
 [Comment : calculer des valeurs de colonnes dans un fichier texte CSV (LINQ) (Visual Basic)](how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 Montre comment effectuer des calculs mathématiques sur des données texte dans des fichiers .csv.  
  
## <a name="see-also"></a>Voir aussi

- [LINQ (Language-Integrated Query) (Visual Basic)](index.md)
- [Comment : générer du code XML à partir de fichiers CSV](../../../../standard/linq/generate-xml-csv-files.md)
