---
title: Le type '<typename>' n'a aucun constructeur
ms.date: 07/20/2015
f1_keywords:
- bc30251
- vbc30251
helpviewer_keywords:
- BC30251
ms.assetid: aff3e1df-abe6-4bc0-9abc-a1e70514c561
ms.openlocfilehash: 249bcb7020f26c7c43d560e91ef7a34e4dc64470
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161177"
---
# <a name="bc30251-type-typename-has-no-constructors"></a>BC30251 : le type' \<typename> 'n’a pas de constructeurs

Un type ne prend pas en charge un appel à `Sub New()`. L'une des causes probables est un fichier compilateur ou binaire endommagé.

 **ID d’erreur :** BC30251

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Si le type se trouve dans un projet différent ou dans un fichier référencé, réinstallez le projet ou le fichier.

2. Si le type se trouve dans le même projet, recompilez l'assembly contenant le type.

3. Si l’erreur se reproduit, réinstallez le compilateur Visual Basic.

4. Si l'erreur persiste, rassemblez des informations sur ses circonstances et avertissez les services de support technique Microsoft.

## <a name="see-also"></a>Voir aussi

- [Objets et classes](../../programming-guide/language-features/objects-and-classes/index.md)
- [Nous contacter](/visualstudio/ide/feedback-options)
