---
title: Programmation fonctionnelle et programmation de procédures
description: LINQ to XML prend en charge la construction fonctionnelle et les techniques procédurales pour la création d’applications XML. La construction fonctionnelle est une approche déclarative. Les techniques procédurales prennent en charge la modification en mémoire des arborescences XML.
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: a2753a31e88fd338dad61063f559431869b9e17f
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552436"
---
# <a name="functional-vs-procedural-programming-linq-to-xml"></a>Comparaison entre la programmation fonctionnelle et la programmation procédurale (LINQ to XML)

Il existe différents types d'applications XML :

- Certaines applications prennent des documents XML sources et produisent de nouveaux documents XML d'une forme différente des documents sources.
- Certaines applications prennent des documents XML sources et produisent des documents d'une forme totalement différente, tels que des fichiers texte CSV ou HTML.
- Certaines applications prennent des documents XML sources et insèrent des enregistrements dans une base de données.
- Certaines applications prennent des données à partir d'une autre source, telle qu'une base de données, et créent des documents XML à partir de celle-ci.

Il ne s’agit pas de tous les types d’applications XML, mais il s’agit d’un ensemble représentatif des types de fonctionnalités qu’un programmeur XML doit implémenter.

Avec tous ces types d'applications, un développeur peut suivre deux approches contrastées :

- Construction fonctionnelle à l'aide d'une approche déclarative.
- Modification d'arborescence XML en mémoire à l'aide de procédures de code.

LINQ to XML prend en charge les deux approches.

Lors de l'utilisation de l'approche fonctionnelle, vous écrivez des transformations qui prennent les documents sources et génèrent des documents de résultats complètement nouveaux de la forme souhaitée.

Lors de la modification d'une arborescence XML en place, vous écrivez du code qui traverse et parcourt les nœuds d'une arborescence XML en mémoire, en insérant, supprimant et modifiant des nœuds si nécessaire.

Vous pouvez utiliser LINQ to XML avec l'une ou l'autre de ces approches. Vous utilisez les mêmes classes et, dans certains cas, les mêmes méthodes. Toutefois, la structure et les objectifs des deux approches sont différents. Par exemple, dans différentes situations, l'une ou l'autre approche fournira souvent de meilleures performances et utilisera plus ou moins de mémoire. En outre, l'une ou l'autre approche sera plus facile à écrire et génèrera du code plus facile à maintenir.

Pour voir les deux approches contrastées, consultez [modification de l’arborescence XML en mémoire par rapport à la construction fonctionnelle](in-memory-xml-tree-modification-vs-functional-construction.md).

Pour obtenir un didacticiel sur l’écriture des transformations fonctionnelles, consultez [Introduction aux transformations fonctionnelles pures](introduction-pure-functional-transformations.md).
