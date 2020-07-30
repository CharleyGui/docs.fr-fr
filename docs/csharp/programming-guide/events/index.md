---
title: Événements - Guide de programmation C#
description: En savoir plus sur les événements. Les événements permettent à une classe ou un objet de notifier d'autres classes ou objets lorsqu'une situation intéressante se produit.
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 3160d1e381c6cb3af0f017538f9555b3fded9910
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302072"
---
# <a name="events-c-programming-guide"></a>Événements (Guide de programmation C#)
Les événements permettent à une [classe](../../language-reference/keywords/class.md) ou à un objet de notifier d’autres classes ou objets quand quelque chose de significatif se produit. La classe qui envoie (ou *déclenche*) l’événement est appelée *publieur* et les classes qui reçoivent (ou *gèrent*) l’événement sont appelées *abonnés*.  
  
Dans une application C# Windows Forms ou web classique, vous vous abonnez à des événements déclenchés par des contrôles, comme des boutons et des zones de liste. Vous pouvez utiliser l’IDE Visual C# pour parcourir les événements publiés par un contrôle et sélectionner ceux que vous voulez gérer. L’IDE permet d’ajouter automatiquement une méthode de gestionnaire d’événements vide et le code pour vous abonner à l’événement. Pour plus d’informations, consultez [Comment s’abonner et annuler l’abonnement à des événements](./how-to-subscribe-to-and-unsubscribe-from-events.md).
  
## <a name="events-overview"></a>Vue d'ensemble des événements  
 Les événements ont les propriétés suivantes :  
  
- Le publieur détermine quand un événement est déclenché ; les abonnés déterminent l’action entreprise en réponse à l’événement.  
  
- Un événement peut avoir plusieurs abonnés. Un abonné peut gérer plusieurs événements provenant de plusieurs publieurs.  
  
- Les événements qui n’ont aucun abonné ne sont jamais déclenchés.  
  
- Les événements sont généralement utilisés pour signaler des actions de l’utilisateur, comme les clics de bouton ou les sélections de menu dans les interfaces utilisateur graphiques.  
  
- Quand un événement a plusieurs abonnés, les gestionnaires d’événements sont appelées de façon synchrone quand un événement est déclenché. Pour appeler des événements de façon asynchrone, consultez [Calling Synchronous Methods Asynchronously](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
- Dans la bibliothèque de classes .NET Framework, les événements sont basés sur le délégué <xref:System.EventHandler> et la classe de base <xref:System.EventArgs>.  
  
## <a name="related-sections"></a>Sections connexes  
 Pour plus d'informations, consultez les pages suivantes :  
  
- [Comment s’abonner à des événements et s’en désabonner](./how-to-subscribe-to-and-unsubscribe-from-events.md)

- [Comment publier des événements conformes aux instructions .NET](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)

- [Comment déclencher des événements de la classe de base dans les classes dérivées](./how-to-raise-base-class-events-in-derived-classes.md)

- [Comment implémenter des événements d’interface](./how-to-implement-interface-events.md)

- [Comment implémenter des accesseurs d’événement personnalisés](./how-to-implement-custom-event-accessors.md)

## <a name="c-language-specification"></a>Spécification du langage C#  

Pour plus d’informations, consultez [Événements](~/_csharplang/spec/classes.md#events) dans la [Spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.
  
## <a name="featured-book-chapters"></a>Chapitres proposés  
 [Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) (Délégués, événements et expressions lambda) dans [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
 [Delegates and Events](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) dans [Learning C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.EventHandler>
- [Guide de programmation C#](../index.md)
- [Délégués](../delegates/index.md)
- [Création de gestionnaires d'événements dans les Windows Forms](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
