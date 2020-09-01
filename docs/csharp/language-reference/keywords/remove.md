---
description: remove, mot clé contextuel - Référence C#
title: remove, mot clé contextuel - Référence C#
ms.date: 07/20/2015
f1_keywords:
- remove_CSharpKeyword
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
ms.openlocfilehash: a5514e72a04daa1232dbdf9a37813f09de791590
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136952"
---
# <a name="remove-c-reference"></a>remove (Référence C#)

Le mot clé contextuel `remove` est utilisé pour définir un accesseur d’événement personnalisé qui est appelé quand le code client annule son abonnement à votre événement ([event](event.md)). Si vous fournissez un accesseur `remove` personnalisé, vous devez également fournir un accesseur [add](add.md).

## <a name="example"></a>Exemple

L’exemple suivant illustre un événement qui a des accesseurs [add](add.md) et `remove` personnalisés. Pour obtenir un exemple complet, consultez [comment implémenter des événements d’interface](../../programming-guide/events/how-to-implement-interface-events.md).

 [!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]

En général, vous n’avez pas besoin de fournir vos propres accesseurs d’événements personnalisés. Les accesseurs générés automatiquement par le compilateur quand vous déclarez un événement sont suffisants pour la plupart des scénarios.

## <a name="see-also"></a>Voir aussi

- [Événements](../../programming-guide/events/index.md)
