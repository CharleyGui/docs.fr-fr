---
title: L'expression a le type '<typename>', qui est un type restreint et qui ne peut pas être utilisé pour accéder aux membres hérités de 'Object' ou 'ValueType'
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: 7fc3f36b28677ed5ebcc0b579f009c796dd431ff
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874221"
---
# <a name="expression-has-the-type-typename-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-object-or-valuetype"></a>L'expression a le type '\<typename>', qui est un type restreint et qui ne peut pas être utilisé pour accéder aux membres hérités de 'Object' ou 'ValueType'

Une expression prend la valeur d’un type qui ne peut pas être boxed par le common language runtime (CLR), mais accède à un membre qui requiert la conversion boxing.  
  
 Le*boxing* est le traitement nécessaire à la conversion d’un type en `Object` ou, à l’occasion, en <xref:System.ValueType>. La common language runtime ne peut pas Box certains types de structures, par exemple, <xref:System.ArgIterator> <xref:System.RuntimeArgumentHandle> et <xref:System.TypedReference> .  
  
 Cette expression tente d’utiliser le type restreint pour appeler une méthode héritée de <xref:System.Object> ou <xref:System.ValueType> , telle que <xref:System.Object.GetHashCode%2A> ou <xref:System.Object.ToString%2A> . Pour accéder à cette méthode, Visual Basic a tenté une conversion boxing implicite qui provoque cette erreur.  
  
 **ID d’erreur :** BC31393  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Recherchez l’expression évaluée comme étant le type cité.  
  
2. Recherchez la partie de votre instruction qui tente d’appeler la méthode héritée de <xref:System.Object> ou <xref:System.ValueType> .  
  
3. Réécrivez l’instruction pour éviter l’appel de la méthode.  
  
## <a name="see-also"></a>Voir aussi

- [Conversions implicites et explicites](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
