---
title: "'Optional' attendu"
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 411e3248409ab0184666f4efefb4ec4becf7cab1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409346"
---
# <a name="optional-expected"></a>'Optional' attendu
Un argument facultatif dans une déclaration de procédure est suivi d’un argument obligatoire. Chaque argument qui suit un argument facultatif doit également être facultatif.  
  
 **ID d’erreur :** BC30202  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Si l’argument est destiné à être requis, déplacez-le pour qu’il précède le premier argument facultatif dans la liste d’arguments.  
  
2. Si l’argument est destiné à être facultatif, utilisez le `Optional` mot clé.  
  
## <a name="see-also"></a>Voir aussi

- [Paramètres facultatifs](../../programming-guide/language-features/procedures/optional-parameters.md)
