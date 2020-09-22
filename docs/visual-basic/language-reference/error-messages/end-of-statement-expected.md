---
title: Fin d'instruction attendue
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: 9141400afc651629df381e0a655e2d7b9da2e45d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874417"
---
# <a name="end-of-statement-expected"></a>Fin d'instruction attendue

L’instruction est syntaxiquement terminée, mais un élément de programmation supplémentaire suit l’élément qui termine l’instruction. Une marque de fin de ligne est requise à la fin de chaque instruction.
  
 Une marque de fin de ligne divise les caractères d’un fichier source Visual Basic en lignes. Les marques de fin de ligne sont, par exemple, le caractère de retour chariot Unicode (&HD), le caractère de saut de ligne Unicode (&HA) et le caractère de retour chariot Unicode suivi du caractère de saut de ligne Unicode. Pour plus d’informations sur les terminateurs de ligne, consultez la [spécification du langage Visual Basic](~/_vblang/spec/lexical-grammar.md#line-terminators).
  
 **ID d’erreur :** BC30205
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur
  
1. Vérifiez si deux instructions différentes ont été placées par inadvertance sur la même ligne.
  
2. Insérez un terminateur de ligne après l’élément qui termine l’instruction.
  
## <a name="see-also"></a>Voir aussi

- [Procédure : Diviser et combiner des instructions dans le code](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [Publication](../../programming-guide/language-features/statements.md)
