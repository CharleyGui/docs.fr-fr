---
title: event - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- event
- remove
- event_CSharpKeyword
- add
helpviewer_keywords:
- event keyword [C#]
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
ms.openlocfilehash: 9575d6e998ff709b06f1da21abd17a3629c17029
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251040"
---
# <a name="event-c-reference"></a>event (référence C#)
Le mot clé `event` sert à déclarer un événement dans une classe d’éditeur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment déclarer et déclencher un événement qui utilise <xref:System.EventHandler> comme type délégué sous-jacent. Pour obtenir l’exemple de code complet qui illustre aussi comment utiliser le type délégué générique <xref:System.EventHandler%601> et comment s’abonner à un événement et créer une méthode de gestionnaire d’événements, consultez [Guide pratique pour publier des événements conformes aux indications du .NET Framework](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).  
  
 [!code-csharp[csrefKeywordsModifiers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#7)]
  
 Les événements constituent un type spécial de délégué multicast qui peut uniquement être appelé au sein de la classe ou du struct où ils sont déclarés (la classe d’éditeur). Si d’autres classes ou structs s’abonnent à l’événement, leurs méthodes de gestionnaire d’événements sont appelées quand la classe d’éditeur déclenche l’événement. Pour plus d’informations et pour obtenir des exemples de code, consultez [Événements](../../../csharp/programming-guide/events/index.md) et [Délégués](../../../csharp/programming-guide/delegates/index.md).  
  
 Les événements peuvent être marqués comme [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [protected internal](../../../csharp/language-reference/keywords/protected-internal.md) ou [private protected](../../../csharp/language-reference/keywords/private-protected.md). Ces modificateurs d’accès définissent comment les utilisateurs de la classe peuvent accéder à l’événement. Pour plus d’informations, consultez la page [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
## <a name="keywords-and-events"></a>Mots clés et événements  
 Les mots clés suivants s’appliquent aux événements.  
  
|Mot clé|Description|Pour plus d'informations|  
|-------------|-----------------|--------------------------|  
|[static](../../../csharp/language-reference/keywords/static.md)|Rend le champ accessible à tout moment aux appelants, même s’il n’existe aucune instance de la classe.|[Classes statiques et membres de classe statique](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|  
|[virtual](../../../csharp/language-reference/keywords/virtual.md)|Permet aux classes dérivées de substituer le comportement d’événement à l’aide du mot clé [override](../../../csharp/language-reference/keywords/override.md).|[Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md)|  
|[sealed](../../../csharp/language-reference/keywords/sealed.md)|Spécifie que pour les classes dérivées l’événement n’est plus virtuel.||  
|[abstract](../../../csharp/language-reference/keywords/abstract.md)|Le compilateur ne génère pas les blocs d’accesseurs d’événement `add` et `remove`, et par conséquent les classes dérivées doivent fournir leur propre implémentation.||  
  
 Un événement peut être déclaré comme événement statique à l’aide du mot clé [static](../../../csharp/language-reference/keywords/static.md). Cela rend le champ accessible à tout moment aux appelants, même s’il n’existe aucune instance de la classe. Pour plus d’informations, consultez [Classes statiques et membres de classe statique](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Un événement peut être marqué comme événement virtuel à l’aide du mot clé [virtual](../../../csharp/language-reference/keywords/virtual.md). Cela permet aux classes dérivées de substituer le comportement d’événement à l’aide du mot clé [override](../../../csharp/language-reference/keywords/override.md). Pour plus d’informations, consultez [Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md). Un événement qui se substitue à un événement virtuel peut également être [sealed](../../../csharp/language-reference/keywords/sealed.md), ce qui signifie que pour les classes dérivées il n’est plus virtuel. Pour finir, un événement peut être déclaré [abstract](../../../csharp/language-reference/keywords/abstract.md), ce qui signifie que le compilateur ne génère pas les blocs d’accesseurs d’événement `add` et `remove`. Ainsi, les classes dérivées doivent fournir leur propre implémentation.  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence C#](../../../csharp/language-reference/index.md)
- [Guide de programmation C#](../../../csharp/programming-guide/index.md)
- [Mots clés C#](../../../csharp/language-reference/keywords/index.md)
- [add](../../../csharp/language-reference/keywords/add.md)
- [remove](../../../csharp/language-reference/keywords/remove.md)
- [Modificateurs](../../../csharp/language-reference/keywords/modifiers.md)
- [Guide pratique pour combiner des délégués (délégués multicast)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
