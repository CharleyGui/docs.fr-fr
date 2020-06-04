---
title: Assembly
ms.date: 07/20/2015
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
helpviewer_keywords:
- Assembly modifier
- Assembly keyword [Visual Basic]
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
ms.openlocfilehash: 7d313dee1015362bd0215ed98ab7e898312cfbcd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373158"
---
# <a name="assembly-visual-basic"></a>Assembly (Visual Basic)
Spécifie qu’un attribut au début d’un fichier source s’applique à l’assembly entier.  
  
## <a name="remarks"></a>Notes  
 De nombreux attributs se rapportent à un élément de programmation individuel, tel qu’une classe ou une propriété. Vous appliquez ce type d’attribut en attachant le bloc d’attributs, entre crochets pointus ( `< >` ), directement à l’instruction de déclaration.  
  
 Si un attribut se rapporte non seulement à l’élément suivant mais à l’assembly entier, vous placez le bloc d’attributs au début du fichier source et identifiez l’attribut à l’aide du `Assembly` mot clé. S’il s’applique au module d’assembly actuel, vous utilisez le mot clé [module](module-keyword.md) .  
  
 Vous pouvez également appliquer un attribut à un assembly dans le fichier AssemblyInfo. vb. dans ce cas, il n’est pas nécessaire d’utiliser un bloc d’attributs dans votre fichier de code source principal.  
  
## <a name="see-also"></a>Voir aussi

- [Modules\<keyword>](module-keyword.md)
- [Vue d’ensemble des attributs](../../programming-guide/concepts/attributes/index.md)
