---
description: '##pragma warning - Référence C#'
title: '##pragma warning - Référence C#'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 16582a74bd34f2c0d89950280f1d5fde25435eea
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99215990"
---
# <a name="pragma-warning-c-reference"></a>#pragma warning (référence C#)

`#pragma warning` peut activer ou désactiver certains avertissements.

## <a name="syntax"></a>Syntaxe

```csharp
#pragma warning disable warning-list
#pragma warning restore warning-list
```

## <a name="parameters"></a>Paramètres

 `warning-list` Liste de numéros d’avertissement séparés par des virgules. Le préfixe « CS » est facultatif.

 Quand aucun numéro d’avertissement n’est spécifié, `disable` désactive tous les avertissements et `restore` active tous les avertissements.

> [!NOTE]
> Pour trouver les numéros d’avertissement dans Visual Studio, générez votre projet, puis recherchez les numéros d’avertissement dans la fenêtre **Sortie**.

## <a name="example"></a>Exemple

```csharp
// pragma_warning.cs
using System;

#pragma warning disable 414, CS3021
[CLSCompliant(false)]
public class C
{
    int i = 1;
    static void Main()
    {
    }
}
#pragma warning restore CS3021
[CLSCompliant(false)]  // CS3021
public class D
{
    int i = 1;
    public static void F()
    {
    }
}
```

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Directives de préprocesseur C#](./index.md)
- [Erreurs du compilateur C#](../compiler-messages/index.md)
- [Comment supprimer des avertissements d’analyse du code](../../../fundamentals/code-analysis/suppress-warnings.md)
