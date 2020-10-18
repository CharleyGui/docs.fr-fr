---
title: Le nom de la variable de portée peut être déduit uniquement à partir d’un nom qualifié ou d’un nom simple sans arguments
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: 63990b7d37388057ff2cdb430d29878a1c7b39ba
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162360"
---
# <a name="bc36599-range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>BC36599 : le nom de la variable de portée ne peut être déduit qu’à partir d’un nom simple ou qualifié sans argument

Un élément de programmation qui accepte un ou plusieurs arguments est inclus dans une requête LINQ. Le compilateur ne peut pas déduire une variable de portée à partir de cet élément de programmation.

**ID d’erreur :** BC36599

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

Fournissez un nom de variable explicite pour l’élément de programmation, comme illustré dans le code suivant :

```vb
Dim query = From var1 In collection1
            Select VariableAlias= SampleFunction(var1), var1
```

## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Clause SELECT](../queries/select-clause.md)
