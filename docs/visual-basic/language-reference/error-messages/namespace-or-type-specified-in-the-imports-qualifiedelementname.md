---
title: L'espace de noms ou le type spécifié dans les Imports '<qualifiedelementname>' ne contient aucun membre public ou est introuvable
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 8675d9c3b202200c89e12e7a5f51a19d9e3e0e64
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409463"
---
# <a name="namespace-or-type-specified-in-the-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a>L'espace de noms ou le type spécifié dans les Imports '\<qualifiedelementname>' ne contient aucun membre public ou est introuvable

L’espace de noms ou le type spécifié dans les Imports' \<qualifiedelementname> 'ne contient aucun membre public ou est introuvable. Assurez-vous que l’espace de noms ou le type est défini et contient au moins un membre public. Assurez-vous que le nom d’alias ne contient pas d’autres alias.

Une `Imports` instruction spécifie un élément conteneur qui est introuvable ou ne définit aucun `Public` membre.

Un *élément conteneur* peut être un espace de noms, une classe, une structure, un module, une interface ou une énumération. L’élément conteneur contient des membres, tels que des variables, des procédures ou d’autres éléments conteneurs.

L’objectif de l’importation est de permettre à votre code d’accéder à des membres de type ou d’espace de noms sans avoir à les qualifier. Votre projet peut également avoir besoin d’ajouter une référence à l’espace de noms ou au type. Pour plus d’informations, consultez « importation d’éléments contenants » dans les [références aux éléments déclarés](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).

Si le compilateur ne peut pas trouver l’élément conteneur spécifié, il ne peut pas résoudre les références qui l’utilisent. S’il trouve l’élément mais que l’élément n’expose aucun `Public` membre, aucune référence ne peut être effectuée. Dans les deux cas, il est inutile d’importer l’élément.

N’oubliez pas que si vous importez un élément conteneur et lui affectez un alias d’importation, vous ne pouvez pas utiliser cet alias d’importation pour importer un autre élément. Le code suivant génère une erreur du compilateur.

```vb
Imports winfrm = System.Windows.Forms

' The following statement is INVALID  because it reuses an import alias.

Imports behave = winfrm.Design.Behavior`
```

**ID d’erreur :** BC40056

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Vérifiez que l’élément conteneur est accessible à partir de votre projet.

2. Vérifiez que la spécification de l’élément conteneur n’inclut aucun alias d’importation d’une autre importation.

3. Vérifiez que l’élément conteneur expose au moins un `Public` membre.

## <a name="see-also"></a>Voir aussi

- [Imports, instruction (espace de noms et type .NET)](../statements/imports-statement-net-namespace-and-type.md)
- [Namespace, instruction](../statements/namespace-statement.md)
- [Public](../modifiers/public.md)
- [Espaces de noms dans Visual Basic](../../programming-guide/program-structure/namespaces.md)
- [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
