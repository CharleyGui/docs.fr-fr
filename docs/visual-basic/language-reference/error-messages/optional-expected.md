---
title: "'Optional' attendu"
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: e212939cf814a9ac632571b2203f2f256dea61ae
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873603"
---
# <a name="optional-expected"></a>'Optional' attendu

Un argument facultatif dans une déclaration de procédure est suivi d’un argument obligatoire. Chaque argument qui suit un argument facultatif doit également être facultatif.  
  
 **ID d’erreur :** BC30202  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Si l’argument est destiné à être requis, déplacez-le pour qu’il précède le premier argument facultatif dans la liste d’arguments.  
  
2. Si l’argument est destiné à être facultatif, utilisez le `Optional` mot clé.  
  
## <a name="see-also"></a>Voir aussi

- [Paramètres facultatifs](../../programming-guide/language-features/procedures/optional-parameters.md)
