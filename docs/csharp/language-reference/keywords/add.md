---
description: 'Découvrez comment créer des accesseurs d’événement personnalisés à l’aide de l’ajout de mot clé en C #'
title: add - Référence C#
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: 9daf635206ff9727a4bf333c123f68be812723cd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168762"
---
# <a name="add-c-reference"></a>add (Référence C#)

Le mot clé contextuel `add` est utilisé pour définir un accesseur d’événement personnalisé qui est appelé quand le code client s’abonne à votre événement ([event](./event.md)). Si vous fournissez un accesseur `add` personnalisé, vous devez également fournir un accesseur [remove](./remove.md).  
  
## <a name="example"></a>Exemple  

L’exemple suivant illustre un événement qui a des accesseurs `add` et [remove](./remove.md) personnalisés. Pour obtenir un exemple complet, consultez [comment implémenter des événements d’interface](../../programming-guide/events/how-to-implement-interface-events.md).
  
[!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]
  
 En général, vous n’avez pas besoin de fournir vos propres accesseurs d’événements personnalisés. Les accesseurs générés automatiquement par le compilateur quand vous déclarez un événement sont suffisants pour la plupart des scénarios.  
  
## <a name="see-also"></a>Voir aussi

- [Événements](../../programming-guide/events/index.md)
