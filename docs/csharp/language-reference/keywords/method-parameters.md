---
title: Paramètres de méthode - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 6746b572719b3233f3b99afde3dd8b5c0b7abcf1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592975"
---
# <a name="method-parameters-c-reference"></a>Paramètres de méthode (référence C#)

Les paramètres déclarés pour une méthode sans [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) sont passés à la méthode appelée par valeur. Cette valeur peut être modifiée dans la méthode, mais la valeur modifiée n’est pas conservée quand le contrôle repasse à la procédure appelante. En utilisant un mot clé de paramètre de méthode, vous pouvez modifier ce comportement.  
  
 Cette section décrit les mots clés que vous pouvez utiliser pour déclarer des paramètres de méthode :  
  
- [params](../../../csharp/language-reference/keywords/params.md) spécifie que ce paramètre peut prendre un nombre variable d’arguments.
  
- [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) spécifie que ce paramètre est passé par référence, mais qu’il est lu uniquement par la méthode appelée.
  
- [ref](../../../csharp/language-reference/keywords/ref.md) spécifie que ce paramètre est passé par référence et qu’il peut être lu ou écrit par la méthode appelée.
  
- [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) spécifie que ce paramètre est passé par référence et qu’il est écrit par la méthode appelée.
  
## <a name="see-also"></a>Voir aussi

- [Référence C#](../../../csharp/language-reference/index.md)
- [Guide de programmation C#](../../../csharp/programming-guide/index.md)
- [Mots clés C#](../../../csharp/language-reference/keywords/index.md)
