---
title: Comparaison entre la programmation fonctionnelle et la programmation procédurale (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: ea1015a5-d4c8-4d79-8e1e-ba17a40a4f39
ms.openlocfilehash: 0b525f13298e7402369b890516434cec47e01542
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398433"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-visual-basic"></a>Comparaison entre la programmation fonctionnelle et la programmation procédurale (LINQ to XML) (Visual Basic)
Il existe différents types d'applications XML :  
  
- Certaines applications prennent des documents XML sources et produisent de nouveaux documents XML d'une forme différente des documents sources.  
  
- Certaines applications prennent des documents XML sources et produisent des documents d'une forme totalement différente, tels que des fichiers texte CSV ou HTML.  
  
- Certaines applications prennent des documents XML sources et insèrent des enregistrements dans une base de données.  
  
- Certaines applications prennent des données à partir d'une autre source, telle qu'une base de données, et créent des documents XML à partir de celle-ci.  
  
 Il existe d'autres types d'applications XML, mais ceux-ci sont représentatifs des types de fonctionnalités qu'un programmateur XML doit implémenter.  
  
 Avec tous ces types d'applications, un développeur peut suivre deux approches contrastées :  
  
- Construction fonctionnelle à l'aide d'une approche déclarative.  
  
- Modification d'arborescence XML en mémoire à l'aide de procédures de code.  
  
 LINQ to XML prend en charge les deux approches.  
  
 Lors de l'utilisation de l'approche fonctionnelle, vous écrivez des transformations qui prennent les documents sources et génèrent des documents de résultats complètement nouveaux de la forme souhaitée.  
  
 Lors de la modification d'une arborescence XML en place, vous écrivez du code qui traverse et parcourt les nœuds d'une arborescence XML en mémoire, en insérant, supprimant et modifiant des nœuds si nécessaire.  
  
 Vous pouvez utiliser LINQ to XML avec l'une ou l'autre de ces approches. Vous utilisez les mêmes classes et, dans certains cas, les mêmes méthodes. Toutefois, la structure et les objectifs des deux approches sont très différents. Par exemple, dans différentes situations, l'une ou l'autre approche fournira souvent de meilleures performances et utilisera plus ou moins de mémoire. En outre, l'une ou l'autre approche sera plus facile à écrire et génèrera du code plus facile à maintenir.  
  
 Pour voir les deux approches contrastées, consultez [modification de l’arborescence XML en mémoire par rapport à la construction fonctionnelle (LINQ to XML) (Visual Basic)](in-memory-xml-tree-modification-vs-functional-construction.md).  
  
 Pour obtenir un didacticiel sur l’écriture des transformations fonctionnelles, consultez [transformations fonctionnelles pures de XML (Visual Basic)](pure-functional-transformations-of-xml.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la programmation de LINQ to XML (Visual Basic)](linq-to-xml-programming-overview.md)
