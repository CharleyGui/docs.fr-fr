---
title: Modules <keyword>
ms.date: 07/20/2015
f1_keywords:
- vb.ModuleAttribute
helpviewer_keywords:
- Module keyword [Visual Basic]
- Module modifier
- attribute blocks, Module keyword
ms.assetid: d971b940-05ab-4d56-8485-e3b8a661906b
ms.openlocfilehash: 6c4f24ad161302835be683e9d324ce32b16c4087
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867989"
---
# <a name="module-keyword-visual-basic"></a>\<keyword> Module (Visual Basic)

Spécifie qu’un attribut au début d’un fichier source s’applique au module d’assembly actuel.  
  
## <a name="remarks"></a>Notes  

 De nombreux attributs se rapportent à un élément de programmation individuel, tel qu’une classe ou une propriété. Vous appliquez ce type d’attribut en attachant le bloc d’attributs, entre crochets pointus ( `< >` ), directement à l’instruction de déclaration.  
  
 Si un attribut se rapporte non seulement à l’élément suivant mais au module d’assembly actuel, vous placez le bloc d’attributs au début du fichier source et identifiez l’attribut à l’aide du `Module` mot clé. S’il s’applique à l’intégralité de l’assembly, vous utilisez le mot clé [assembly](assembly.md) .  
  
 Le `Module` modificateur n’est pas le même que l' [instruction module](../statements/module-statement.md).  
  
## <a name="see-also"></a>Voir aussi

- [Assembly](assembly.md)
- [Module, instruction](../statements/module-statement.md)
- [Vue d’ensemble des attributs](../../programming-guide/concepts/attributes/index.md)
