---
title: Regrouper des résultats par clés contiguës (LINQ en C#)
description: Guide pratique pour regrouper des résultats par clés contiguës à l’aide de LINQ en C#.
ms.date: 08/14/2018
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: b5753c85bb07be4fc84b78a299eece961969ff9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659902"
---
# <a name="group-results-by-contiguous-keys"></a>Regrouper des résultats par clés contiguës

L’exemple suivant montre comment regrouper des éléments dans des blocs représentant des sous-séquences de clés contiguës. Par exemple, supposons que vous disposiez de la séquence de paires clé-valeur suivante :

|Clé|Valeur|
|---------|-----------|
|Un|Nous|
|Un|pensons|
|Un|que|
|B|Linq|
|C|is|
|Un|vraiment|
|B|chouette|
|B|!|

Les groupes suivants seront créés dans cet ordre :

1. Nous, pensons, que

2. Linq

3. is

4. vraiment

5. chouette, !

La solution est implémentée comme une méthode d’extension thread-safe qui retourne ses résultats en continu. En d’autres termes, elle produit ses groupes à mesure qu’elle se déplace dans la séquence source. Contrairement aux opérateurs `group` ou `orderby`, elle peut commencer à retourner des groupes à l’appelant avant que l’intégralité de la séquence ait été lue.

La cohérence de thread est obtenue en effectuant une copie de chaque groupe ou bloc pendant l’itération de la séquence source, comme expliqué dans les commentaires du code source. Si la séquence source comporte une longue séquence d’éléments contigus, le common language runtime peut lever une <xref:System.OutOfMemoryException>.

## <a name="example"></a> Exemple

L’exemple suivant montre la méthode d’extension et le code client qui l’utilise :

[!code-csharp[cscsrefContiguousGroups#1](~/samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]

Pour utiliser la méthode d’extension dans votre projet, copiez la classe statique `MyExtensions` dans un fichier de code source nouveau ou existant et, si nécessaire, ajoutez une directive `using` pour l’espace de noms dans lequel elle se trouve.

## <a name="see-also"></a>Voir aussi

- [Requête intégrée linguistique (LINQ)](index.md)
