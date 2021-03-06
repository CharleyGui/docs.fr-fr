---
title: Initialiseur attendu
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: cbe77bab3e4f8bf2094c70c1c16d95ee897c729e
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163010"
---
# <a name="bc30996-initializer-expected"></a>BC30996 : initialiseur ATTENDU

Vous avez tenté de déclarer une instance d’une classe à l’aide d’un initialiseur d’objet dans lequel la liste d’initialisation est vide, comme illustré dans l’exemple suivant.

 `' Not valid.`

 `' Dim aStudent As New Student With {}`

 Au moins un champ ou une propriété doit être initialisé dans la liste d’initialiseurs, comme indiqué dans l’exemple suivant.

 `Dim aStudent As New Student With {.year = "Senior"}`

 **ID d’erreur :** BC30996

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Initialisez au moins un champ ou une propriété dans l’initialiseur, ou n’utilisez pas d’initialiseur d’objet.

## <a name="see-also"></a>Voir aussi

- [Initialiseurs d'objets : types nommés et anonymes](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Comment : déclarer un objet à l'aide d'un initialiseur d'objet](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
