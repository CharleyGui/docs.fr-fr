---
title: instruction lock - référence C#
description: Utilisez l’instruction lock en C# pour synchroniser l’accès des threads à une ressource partagée
ms.date: 04/02/2020
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 2f2d42ae02a07a5e1b82cefd004f4d03b2a16dff
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635382"
---
# <a name="lock-statement-c-reference"></a>instruction lock (référence C#)

L’instruction `lock` obtient le verrou d’exclusion mutuelle d’un objet donné, exécute un bloc d’instructions, puis libère le verrou. Tant qu’un verrou est maintenu, le thread qui contient le verrou peut à nouveau obtenir et libérer le verrou. Tout autre thread se voit bloquer l’obtention du verrou et attend que ce dernier soit libéré.

L’instruction `lock` se présente sous la forme

```csharp
lock (x)
{
    // Your code...
}
```

où `x` est une expression de [type référence](reference-types.md). Elle équivaut précisément à

```csharp
object __lockObj = x;
bool __lockWasTaken = false;
try
{
    System.Threading.Monitor.Enter(__lockObj, ref __lockWasTaken);
    // Your code...
}
finally
{
    if (__lockWasTaken) System.Threading.Monitor.Exit(__lockObj);
}
```

Dans la mesure où le code utilise un bloc [try...finally](try-finally.md), le verrou est libéré même si une exception est levée dans le corps d’une instruction `lock`.

Vous ne pouvez pas utiliser l’[opérateur await](../operators/await.md) dans le corps d’une instruction `lock`.

## <a name="guidelines"></a>Consignes

Quand vous synchronisez l’accès des threads à une ressource partagée, verrouillez une instance d’objet dédiée (par exemple `private readonly object balanceLock = new object();`) ou toute autre instance peu susceptible d’être utilisée comme objet de verrouillage par des parties du code non associées. Évitez d’utiliser la même instance d’objet de verrouillage pour différentes ressources partagées, car cela peut entraîner une contention d’interblocage ou de verrouillage. En particulier, évitez d’utiliser les éléments suivants en tant qu’objets de verrouillage :

- `this`, qui peut être utilisé en tant que verrou par les appelants.
- Les instances de <xref:System.Type>, qui peuvent être obtenues par l’opérateur [typeof](../operators/type-testing-and-cast.md#typeof-operator) ou par réflexion.
- Les instances de chaîne, notamment les littéraux de chaîne, qui peuvent être [internés](/dotnet/api/system.string.intern#remarks).

Maintenez un verrou aussi peu de temps que possible pour réduire la contention de verrouillage.

## <a name="example"></a>Exemple

L’exemple suivant définit une classe `Account`, qui synchronise l’accès à son champ `balance` privé en verrouillant une instance `balanceLock` dédiée. L’utilisation de la même instance pour le verrouillage permet de garantir que le champ `balance` ne peut pas être mis à jour simultanément par deux threads qui tentent d’appeler les méthodes `Debit` ou `Credit` en même temps.

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir la section [Instruction lock](~/_csharplang/spec/statements.md#the-lock-statement) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Mots clés C#](index.md)
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [Vue d’ensemble des primitives de synchronisation](../../../standard/threading/overview-of-synchronization-primitives.md)
