---
title: add - Référence C#
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: 323064dcbe7596b5f1d2f0f6aa566b07cee45789
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713808"
---
# <a name="add-c-reference"></a>add (Référence C#)
Le mot clé contextuel `add` est utilisé pour définir un accesseur d’événement personnalisé qui est appelé quand le code client s’abonne à votre événement ([event](./event.md)). Si vous fournissez un accesseur `add` personnalisé, vous devez également fournir un accesseur [remove](./remove.md).  
  
## <a name="example"></a> Exemple  
L’exemple suivant illustre un événement qui a des accesseurs `add` et [remove](./remove.md) personnalisés. Pour l’exemple complet, voir [Comment implémenter des événements d’interface](../../programming-guide/events/how-to-implement-interface-events.md).
  
[!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]
  
 En général, vous n’avez pas besoin de fournir vos propres accesseurs d’événements personnalisés. Les accesseurs générés automatiquement par le compilateur quand vous déclarez un événement sont suffisants pour la plupart des scénarios.  
  
## <a name="see-also"></a>Voir aussi

- [Événements](../../programming-guide/events/index.md)
