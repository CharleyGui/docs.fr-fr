---
title: Limites
ms.date: 07/20/2015
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
ms.openlocfilehash: 46294b68bda8a5d2d21c0e4efea6a78e6a265ffe
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403185"
---
# <a name="visual-basic-limitations"></a>Restrictions liées à Visual Basic
Les versions antérieures de Visual Basic des limites appliquées dans le code, telles que la longueur des noms de variables, le nombre de variables autorisées dans les modules et la taille du module. Dans Visual Basic .NET, ces restrictions ont été assouplies, ce qui vous offre une plus grande liberté dans l’écriture et l’organisation de votre code.  
  
 Les limites physiques dépendent davantage de la mémoire au moment de l’exécution que des considérations relatives à la compilation. Si vous utilisez des pratiques de programmation prudentes et que vous divisez des applications volumineuses en plusieurs classes et modules, il y a très peu de chance de rencontrer une limitation de Visual Basic interne.  
  
 Voici quelques-unes des limitations que vous pouvez rencontrer dans les cas extrêmes :  
  
- **Longueur du nom.** Il y a un nombre maximal de caractères pour le nom de chaque élément de programmation déclaré. Cette valeur maximale s’applique à une chaîne de qualification entière si le nom d’élément est qualifié. Consultez [Declared Element Names](../language-features/declared-elements/declared-element-names.md).  
  
- **Longueur de la ligne.** Il y a un maximum de 65535 caractères dans une ligne physique de code source. La ligne de code source logique peut être plus longue si vous utilisez des caractères de continuation de ligne. Consultez [Comment : arrêter et combiner des instructions dans le code](how-to-break-and-combine-statements-in-code.md).  
  
- **Dimensions du tableau.** Vous pouvez déclarer un nombre maximal de dimensions pour un tableau. Cela limite le nombre d’index que vous pouvez utiliser pour spécifier un élément de tableau. Consultez [dimensions de tableau dans Visual Basic](../language-features/arrays/array-dimensions.md).  
  
- **Longueur de chaîne.** Il y a un nombre maximal de caractères Unicode que vous pouvez stocker dans une chaîne unique. Consultez [type de données String](../../language-reference/data-types/string-data-type.md).  
  
- **Longueur de la chaîne d’environnement.** Il y a un maximum de 32768 caractères pour toute chaîne d’environnement utilisée comme argument de ligne de commande. Il s’agit d’une limitation sur toutes les plateformes.  
  
## <a name="see-also"></a>Voir aussi

- [Structure de programme et conventions de code](program-structure-and-code-conventions.md)
- [Conventions d'affectation de noms Visual Basic](naming-conventions.md)
