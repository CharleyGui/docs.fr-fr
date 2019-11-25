---
title: LINQ et chaînes (C#)
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: fb1714c54331ead80cd28435cf3ed1c4c54a704e
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140899"
---
# <a name="linq-and-strings-c"></a><span data-ttu-id="a4dbf-102">LINQ et chaînes (C#)</span><span class="sxs-lookup"><span data-stu-id="a4dbf-102">LINQ and strings (C#)</span></span>

<span data-ttu-id="a4dbf-103">LINQ peut être utilisé pour interroger et transformer des chaînes et des collections de chaînes.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-103">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="a4dbf-104">Il peut être particulièrement utile avec des données semi-structurées dans des fichiers texte.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-104">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="a4dbf-105">Les requêtes LINQ peuvent être combinées avec les fonctions de chaîne traditionnelles et les expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-105">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="a4dbf-106">Par exemple, vous pouvez utiliser la méthode <xref:System.String.Split%2A?displayProperty=nameWithType> ou <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> pour créer un tableau de chaînes que vous pouvez ensuite interroger ou modifier à l’aide de LINQ.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-106">For example, you can use the <xref:System.String.Split%2A?displayProperty=nameWithType> or <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="a4dbf-107">Vous pouvez utiliser la méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> dans la clause `where` d’une requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-107">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="a4dbf-108">Et vous pouvez utiliser LINQ pour interroger ou modifier les résultats <xref:System.Text.RegularExpressions.MatchCollection> retournés par une expression régulière.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-108">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>

<span data-ttu-id="a4dbf-109">Vous pouvez également utiliser les techniques décrites dans cette section pour transformer des données texte semi-structurées en XML.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-109">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="a4dbf-110">Pour plus d’informations, consultez [Comment : générer du code XML à partir de fichiers CSV](how-to-generate-xml-from-csv-files.md).</span><span class="sxs-lookup"><span data-stu-id="a4dbf-110">For more information, see [How to: Generate XML from CSV Files](how-to-generate-xml-from-csv-files.md).</span></span>

<span data-ttu-id="a4dbf-111">Les exemples de cette section se répartissent en deux catégories :</span><span class="sxs-lookup"><span data-stu-id="a4dbf-111">The examples in this section fall into two categories:</span></span>

## <a name="querying-a-block-of-text"></a><span data-ttu-id="a4dbf-112">Interrogation d’un bloc de texte</span><span class="sxs-lookup"><span data-stu-id="a4dbf-112">Querying a block of text</span></span>

<span data-ttu-id="a4dbf-113">Vous pouvez interroger, analyser et modifier des blocs de texte en les fractionnant en tableau requêtable de chaînes plus petites à l’aide de la méthode <xref:System.String.Split%2A?displayProperty=nameWithType> ou de la méthode <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-113">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A?displayProperty=nameWithType> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a4dbf-114">Vous pouvez fractionner le texte source en mots, en phrases, en paragraphes, en pages ou selon d’autres critères, puis effectuer des fractionnements supplémentaires s’ils sont nécessaires dans votre requête.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-114">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>

- [<span data-ttu-id="a4dbf-115">Comment compter les occurrences d’un mot dans une chaîne (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a4dbf-115">How to count occurrences of a word in a string (LINQ) (C#)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  <span data-ttu-id="a4dbf-116">Montre comment utiliser LINQ pour des interrogations simples sur du texte.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-116">Shows how to use LINQ for simple querying over text.</span></span>

- [<span data-ttu-id="a4dbf-117">Guide pratique pour rechercher des phrases qui contiennent un groupe de mots spécifié (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a4dbf-117">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  <span data-ttu-id="a4dbf-118">Montre comment fractionner des fichiers texte avec des limites arbitraires et comment exécuter des requêtes sur chaque partie.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-118">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>

- [<span data-ttu-id="a4dbf-119">Guide pratique pour interroger des caractères dans une chaîne (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a4dbf-119">How to: Query for Characters in a String (LINQ) (C#)</span></span>](how-to-query-for-characters-in-a-string-linq.md)

  <span data-ttu-id="a4dbf-120">Montre qu’une chaîne est un type interrogeable.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-120">Demonstrates that a string is a queryable type.</span></span>

- [<span data-ttu-id="a4dbf-121">Comment combiner des requêtes LINQ avec des expressions régulières (C#)</span><span class="sxs-lookup"><span data-stu-id="a4dbf-121">How to combine LINQ queries with regular expressions (C#)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)

  <span data-ttu-id="a4dbf-122">Montre comment utiliser des expressions régulières dans les requêtes LINQ pour des correspondances de modèle complexes sur des résultats de requête filtrés.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-122">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>

## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="a4dbf-123">Interrogation de données semi-structurées au format texte</span><span class="sxs-lookup"><span data-stu-id="a4dbf-123">Querying semi-structured data in text format</span></span>

<span data-ttu-id="a4dbf-124">De nombreux types différents de fichiers texte sont constitués d’une série de lignes, souvent avec la même mise en forme, comme les fichiers délimités par des tabulations ou des virgules, ou des lignes de longueur fixe.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-124">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="a4dbf-125">Après avoir lu un tel fichier texte dans la mémoire, vous pouvez utiliser LINQ pour interroger et/ou modifier les lignes.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-125">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="a4dbf-126">Les requêtes LINQ simplifient également la combinaison de données provenant de plusieurs sources.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-126">LINQ queries also simplify the task of combining data from multiple sources.</span></span>

- [<span data-ttu-id="a4dbf-127">Guide pratique pour rechercher la différence ensembliste entre deux listes (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a4dbf-127">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)

  <span data-ttu-id="a4dbf-128">Montre comment rechercher toutes les chaînes qui sont présentes dans une liste mais pas dans l’autre.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-128">Shows how to find all the strings that are present in one list but not the other.</span></span>

- [<span data-ttu-id="a4dbf-129">Guide pratique pour trier ou filtrer des données texte par mot ou par champ (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a4dbf-129">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  <span data-ttu-id="a4dbf-130">Montre comment trier les lignes de texte en fonction de n’importe quel mot ou champ.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-130">Shows how to sort text lines based on any word or field.</span></span>

- [<span data-ttu-id="a4dbf-131">Guide pratique pour réorganiser les champs d’un fichier délimité (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a4dbf-131">How to: Reorder the Fields of a Delimited File (LINQ) (C#)</span></span>](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  <span data-ttu-id="a4dbf-132">Montre comment réorganiser les champs dans une ligne d’un fichier .csv.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-132">Shows how to reorder fields in a line in a .csv file.</span></span>

- [<span data-ttu-id="a4dbf-133">Comment : combiner et comparer des collections de chaînes (LINQ)C#()</span><span class="sxs-lookup"><span data-stu-id="a4dbf-133">How to: combine and compare string collections (LINQ) (C#)</span></span>](how-to-combine-and-compare-string-collections-linq.md)

  <span data-ttu-id="a4dbf-134">Montre comment combiner des listes de chaînes de différentes façons.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-134">Shows how to combine string lists in various ways.</span></span>

- [<span data-ttu-id="a4dbf-135">Guide pratique pour remplir des collections d’objets issues de plusieurs sources (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a4dbf-135">How to: Populate Object Collections from Multiple Sources (LINQ) (C#)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)

  <span data-ttu-id="a4dbf-136">Montre comment créer des collections d’objets à l’aide de plusieurs fichiers texte comme sources de données.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-136">Shows how to create object collections by using multiple text files as data sources.</span></span>

- [<span data-ttu-id="a4dbf-137">Guide pratique pour joindre du contenu issu de fichiers non similaires (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a4dbf-137">How to: Join Content from Dissimilar Files (LINQ) (C#)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)
  
  <span data-ttu-id="a4dbf-138">Montre comment combiner des chaînes de deux listes en une seule chaîne en utilisant une clé en correspondance.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-138">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>

- [<span data-ttu-id="a4dbf-139">Guide pratique pour fractionner un fichier en plusieurs fichiers à l’aide de groupes (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a4dbf-139">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  <span data-ttu-id="a4dbf-140">Montre comment créer des fichiers en utilisant un seul fichier comme source de données.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-140">Shows how to create new files by using a single file as a data source.</span></span>

- [<span data-ttu-id="a4dbf-141">Calcul des valeurs de colonnes dans un fichier texte CSV (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a4dbf-141">How to compute column values in a CSV text file (LINQ) (C#)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  <span data-ttu-id="a4dbf-142">Montre comment effectuer des calculs mathématiques sur des données texte dans des fichiers .csv.</span><span class="sxs-lookup"><span data-stu-id="a4dbf-142">Shows how to perform mathematical computations on text data in .csv files.</span></span>

## <a name="see-also"></a><span data-ttu-id="a4dbf-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4dbf-143">See also</span></span>

- [<span data-ttu-id="a4dbf-144">LINQ (Language-Integrated Query) (C#)</span><span class="sxs-lookup"><span data-stu-id="a4dbf-144">Language-Integrated Query (LINQ) (C#)</span></span>](index.md)
- [<span data-ttu-id="a4dbf-145">Guide pratique : générer du code XML à partir de fichiers CSV</span><span class="sxs-lookup"><span data-stu-id="a4dbf-145">How to: Generate XML from CSV Files</span></span>](how-to-generate-xml-from-csv-files.md)
