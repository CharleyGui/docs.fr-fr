---
description: volatile - Référence C#
title: volatile - Référence C#
ms.date: 10/24/2018
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: bb89e99e8e28ff1e263817f498619dbfae700a50
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141697"
---
# <a name="volatile-c-reference"></a>volatile (référence C#)

Le mot clé `volatile` indique qu’un champ peut être modifié par plusieurs threads qui s’exécutent simultanément. Le compilateur, le système de runtime et même le matériel sont susceptibles de réorganiser les lectures et les écritures sur des emplacements de mémoire pour des raisons de performances. Les champs déclarés `volatile` ne sont pas soumis à ces optimisations. Le fait d’ajouter le modificateur `volatile` permet de garantir que tous les threads observent les écritures volatiles effectuées par un autre thread dans l’ordre dans lequel elles ont été effectuées. Rien ne garantit que les écritures volatiles présentent un ordre total unique, tel que le voient tous les threads d’exécution.

Le mot clé `volatile` peut être appliqué aux champs des types suivants :

- Types référence.
- Types pointeur (dans un contexte unsafe). Notez que, même si le pointeur lui-même peut être volatile, l’objet sur lequel il pointe ne le peut pas. En d’autres termes, vous ne pouvez pas déclarer un pointeur vers un objet volatile.
- Types simples comme `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float` et `bool`.
- Type `enum` avec l’un des types de base suivants : `byte`, `sbyte`, `short`, `ushort`, `int` ou `uint`.
- Paramètres de type générique connus comme des types référence.
- Voir <xref:System.IntPtr> et <xref:System.UIntPtr>.

Les autres types, notamment `double` et `long`, ne peuvent pas être marqués `volatile`, car il n’y a aucune garantie que les lectures et écritures sur des champs de ce type soient atomiques. Pour protéger l’accès multithread à ces types de champs, utilisez les membres de la <xref:System.Threading.Interlocked> classe ou Protégez l’accès à l’aide de l' [`lock`](lock-statement.md) instruction.

Le mot clé `volatile` ne peut s’appliquer qu’aux champs d’une `class` ou d’un `struct`. Les variables locales ne peuvent pas être déclarées `volatile`.

## <a name="example"></a>Exemple

L’exemple ci-dessous montre comment déclarer une variable de champ public comme `volatile`.

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Declaration)]

L’exemple suivant montre comment il est possible de créer un thread auxiliaire ou de travail et de l’utiliser pour effectuer le traitement en parallèle avec le thread principal. Pour plus d'informations sur le multithreading, voir [Threading managé](../../../standard/threading/index.md).

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Volatile)]

Si vous ajoutez le modificateur `volatile` à la déclaration de `_shouldStop` en place, vous obtiendrez toujours les mêmes résultats (similaires à l’extrait indiqué dans le code précédent). Sans ce modificateur sur le membre `_shouldStop` en revanche, le comportement est imprévisible. La méthode `DoWork` peut optimiser l’accès au membre, ce qui entraîne la lecture de données périmées. En raison de la nature de la programmation multithread, le nombre de lectures obsolètes est imprévisible. Différentes exécutions du programme produiront des résultats légèrement différents.

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Spécification du langage C# : mot clé volatile](../../../../_csharplang/spec/classes.md#volatile-fields)
- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [Modificateurs](index.md)
- [Lock (instruction)](lock-statement.md)
- <xref:System.Threading.Interlocked>
