---
title: "'Optional' attendu"
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 9c717cef2052722563e04595ef7a808ea103a75d
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159818"
---
# <a name="bc30202-optional-expected"></a>BC30202 : 'optional’attendu

Un argument facultatif dans une déclaration de procédure est suivi d’un argument obligatoire. Chaque argument qui suit un argument facultatif doit également être facultatif.

 **ID d’erreur :** BC30202

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Si l’argument est destiné à être requis, déplacez-le pour qu’il précède le premier argument facultatif dans la liste d’arguments.

- Si l’argument est destiné à être facultatif, utilisez le `Optional` mot clé.

## <a name="see-also"></a>Voir aussi

- [Paramètres facultatifs](../../programming-guide/language-features/procedures/optional-parameters.md)
