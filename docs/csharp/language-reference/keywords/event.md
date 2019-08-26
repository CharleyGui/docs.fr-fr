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
ms.openlocfilehash: 4149663422908069b5b65ed3c32ccc6dbdfd7729
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605810"
---
# <a name="event-c-reference"></a>event (référence C#)
Le mot clé `event` sert à déclarer un événement dans une classe d’éditeur.  
  
## <a name="example"></a>Exemples  
 L’exemple suivant montre comment déclarer et déclencher un événement qui utilise <xref:System.EventHandler> comme type délégué sous-jacent. Pour obtenir l’exemple de code complet qui illustre aussi comment utiliser le type délégué générique <xref:System.EventHandler%601> et comment s’abonner à un événement et créer une méthode de gestionnaire d’événements, consultez [Guide pratique pour publier des événements conformes aux indications du .NET Framework](../../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).  
  
 [!code-csharp[csrefKeywordsModifiers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#7)]
  
 Les événements constituent un type spécial de délégué multicast qui peut uniquement être appelé au sein de la classe ou du struct où ils sont déclarés (la classe d’éditeur). Si d’autres classes ou structs s’abonnent à l’événement, leurs méthodes de gestionnaire d’événements sont appelées quand la classe d’éditeur déclenche l’événement. Pour plus d’informations et pour obtenir des exemples de code, consultez [Événements](../../programming-guide/events/index.md) et [Délégués](../../programming-guide/delegates/index.md).  
  
 Les événements peuvent être marqués comme [public](./public.md), [private](./private.md), [protected](./protected.md), [internal](./internal.md), [protected internal](./protected-internal.md) ou [private protected](./private-protected.md). Ces modificateurs d’accès définissent comment les utilisateurs de la classe peuvent accéder à l’événement. Pour plus d’informations, consultez la page [Modificateurs d’accès](../../programming-guide/classes-and-structs/access-modifiers.md).  
  
## <a name="keywords-and-events"></a>Mots clés et événements  
 Les mots clés suivants s’appliquent aux événements.  
  
|Mot clé|Description|Pour plus d'informations|  
|-------------|-----------------|--------------------------|  
|[static](./static.md)|Rend le champ accessible à tout moment aux appelants, même s’il n’existe aucune instance de la classe.|[Classes statiques et membres de classe statique](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|  
|[virtual](./virtual.md)|Permet aux classes dérivées de substituer le comportement d’événement à l’aide du mot clé [override](./override.md).|[Héritage](../../programming-guide/classes-and-structs/inheritance.md)|  
|[sealed](./sealed.md)|Spécifie que pour les classes dérivées l’événement n’est plus virtuel.||  
|[abstract](./abstract.md)|Le compilateur ne génère pas les blocs d’accesseurs d’événement `add` et `remove`, et par conséquent les classes dérivées doivent fournir leur propre implémentation.||  
  
 Un événement peut être déclaré comme événement statique à l’aide du mot clé [static](./static.md). Cela rend le champ accessible à tout moment aux appelants, même s’il n’existe aucune instance de la classe. Pour plus d’informations, consultez [Classes statiques et membres de classe statique](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Un événement peut être marqué comme événement virtuel à l’aide du mot clé [virtual](./virtual.md). Cela permet aux classes dérivées de substituer le comportement d’événement à l’aide du mot clé [override](./override.md). Pour plus d’informations, consultez [Héritage](../../programming-guide/classes-and-structs/inheritance.md). Un événement qui se substitue à un événement virtuel peut également être [sealed](./sealed.md), ce qui signifie que pour les classes dérivées il n’est plus virtuel. Pour finir, un événement peut être déclaré [abstract](./abstract.md), ce qui signifie que le compilateur ne génère pas les blocs d’accesseurs d’événement `add` et `remove`. Ainsi, les classes dérivées doivent fournir leur propre implémentation.  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](./index.md)
- [add](./add.md)
- [remove](./remove.md)
- [Modificateurs](./modifiers.md)
- [Guide pratique pour combiner des délégués (délégués multicast)](../../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
