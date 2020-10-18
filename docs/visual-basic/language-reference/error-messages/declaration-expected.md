---
title: Déclaration attendue
ms.date: 07/20/2015
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords:
- BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
ms.openlocfilehash: 2755f5afcb96ca7a6c4d140908649390dd66d571
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162698"
---
# <a name="bc30188-declaration-expected"></a>BC30188 : déclaration attendue

Une instruction non déclarative, telle qu’une instruction d’assignation ou de boucle, se produit en dehors de toute procédure. Seules les déclarations sont autorisées en dehors des procédures.

 Un élément de programmation est également déclaré sans mot clé de déclaration, tel que `Dim` ou `Const` .

 **ID d’erreur :** BC30188

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Déplacez l’instruction not Declarative dans le corps d’une procédure.

- Commencez la déclaration par un mot clé de déclaration approprié.

- Assurez-vous qu’un mot clé de déclaration n’est pas mal orthographié.

## <a name="see-also"></a>Voir aussi

- [Procédures](../../programming-guide/language-features/procedures/index.md)
- [Dim (instruction)](../statements/dim-statement.md)
