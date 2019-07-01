---
title: Tableau des conversions numériques implicites - Référence C#
ms.custom: seodec18
ms.date: 09/05/2018
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: 9c3efe1dbea355e8bc00ef44e08efcc9d0e0bdca
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424180"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a>Tableau des conversions numériques implicites (référence C#)

Le tableau suivant montre les conversions implicites prédéfinies entre les types numériques .NET.
  
|From|À|  
|----------|--------|  
|[sbyte](../builtin-types/integral-numeric-types.md)|`short`, `int`, `long`, `float`, `double` ou `decimal`|  
|[byte](../builtin-types/integral-numeric-types.md)|`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`|  
|[char](char.md)|`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`|  
|[short](../builtin-types/integral-numeric-types.md)|`int`, `long`, `float`, `double` ou `decimal`|  
|[ushort](../builtin-types/integral-numeric-types.md)|`int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`|  
|[int](../builtin-types/integral-numeric-types.md)|`long`, `float`, `double` ou `decimal`|  
|[uint](../builtin-types/integral-numeric-types.md)|`long`, `ulong`, `float`, `double` ou `decimal`|  
|[long](../builtin-types/integral-numeric-types.md)|`float`, `double`ou `decimal`|  
|[ulong](../builtin-types/integral-numeric-types.md)|`float`, `double`ou `decimal`|  
|[float](float.md)|`double`|  
  
## <a name="remarks"></a>Remarques  

- Un [type intégral](../builtin-types/integral-numeric-types.md) est implicitement convertible en [type à virgule flottante](floating-point-types-table.md).

- La précision, et non la magnitude, peut être perdue dans les conversions de `int`, `uint`, `long` ou `ulong` à `float`, et de `long` ou `ulong` à `double`.  
  
- Il n’existe aucune conversion implicite vers les types `char`, `byte` et `sbyte`.  

- Il n’existe aucune conversion implicite à partir des types `double` et `decimal`.
  
- Il n’existe aucune conversion implicite entre le type `decimal` et le type `float` ou `double`.  
  
- La valeur d’une expression constante de type `int` (par exemple, une valeur représentée par un littéral intégral) peut être convertie en `sbyte`, `byte`, `short`, `ushort`, `uint` ou `ulong`, à condition qu’elle se trouve dans la plage du type de destination :

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

Pour plus d’informations sur les conversions implicites, consultez la section [Conversions implicites](~/_csharplang/spec/conversions.md#implicit-conversions) de la [Spécification du langage C#](../language-specification/index.md).
  
## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Types intégraux](../builtin-types/integral-numeric-types.md)
- [Tableau des types à virgule flottante](floating-point-types-table.md)
- [Tableaux des types intégrés](built-in-types-table.md)
- [Tableau des conversions numériques explicites](explicit-numeric-conversions-table.md)
- [Cast et conversions de types](../../programming-guide/types/casting-and-type-conversions.md)
