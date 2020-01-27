---
title: Vue d'ensemble des événements
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, event handling
- events [Windows Forms], about events
- delegates [Windows Forms], multicast
- delegates [Windows Forms], events and
- multicast event delegates
- Windows Forms controls, events
ms.assetid: 814a6a43-a312-4791-88d8-f75f9a4f8c4c
ms.openlocfilehash: 59085597789d12ce80648efb77859228e4718a3f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743486"
---
# <a name="events-overview-windows-forms"></a>Vue d'ensemble des événements (Windows Forms)
Un événement est une action à laquelle vous pouvez répondre ou que vous pouvez « gérer » dans le code. Les événements peuvent être déclenchés par une action de l'utilisateur (quand il clique sur un bouton de la souris ou appuie sur une touche), par le code d'un programme ou par le système.

 Les applications pilotées par événements exécutent du code en réponse à un événement. Chaque formulaire et chaque contrôle exposent un ensemble prédéfini d'événements que vous pouvez programmer. Si l'un de ces événements se produit et que le gestionnaire d'événements associé contient du code, celui-ci est appelé.

 Les types d'événements déclenchés par un objet sont divers, mais bon nombre d'entre eux sont communs à la plupart des contrôles. Par exemple, la plupart des objets peuvent gérer un événement <xref:System.Windows.Forms.Control.Click>. Si un utilisateur clique sur un formulaire, le code du gestionnaire de l'événement <xref:System.Windows.Forms.Control.Click> de ce dernier est exécuté.

> [!NOTE]
> De nombreux événements se produisent conjointement à d'autres événements. Par exemple, les événements <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDown> et <xref:System.Windows.Forms.Control.MouseUp> se produisent en même temps que l'événement <xref:System.Windows.Forms.Control.Click>.

 Pour plus d’informations sur la façon de déclencher et de consommer un événement, consultez [événements](../../standard/events/index.md).

## <a name="delegates-and-their-role"></a>Rôle des délégués
 Les délégués sont des classes couramment utilisées dans le .NET Framework pour créer des mécanismes de gestion des événements. Les délégués sont à peu près équivalents aux pointeurs de fonction C++ , couramment utilisés dans des langages visuels et d’autres langages orientés objet. Toutefois à la différence des pointeurs de fonction, les délégués sont orientés objet, de type sécurisé et sûrs. De plus, alors qu'un pointeur de fonction ne contient qu'une référence à une fonction spécifique, un délégué consiste en une référence à un objet et des références à une ou plusieurs méthodes de cet objet.

 Ce modèle d’événement utilise des *délégués* pour lier des événements aux méthodes utilisées pour les gérer. Le délégué permet aux autres classes de s'inscrire pour la notification d'événement en spécifiant une méthode de gestionnaire. Quand l'événement se produit, le délégué appelle la méthode liée. Pour plus d’informations sur la façon de définir des délégués, consultez [événements](../../standard/events/index.md).

Les délégués peuvent être liés à une ou plusieurs méthodes (ou multidiffusion). Lorsque vous créez un délégué pour un événement, vous (ou les fenêtres) créez généralement un événement de multidiffusion. Il existe cependant une exception à cette règle : quand un événement déclenche une procédure particulière (par exemple, l'affichage d'une boîte de dialogue) qui logiquement ne se répéterait pas plusieurs fois par événement. Pour plus d’informations sur la création d’un délégué multicast, consultez [Comment combiner des délégués (délégués multicast)](../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md).

 Un délégué multidiffusion tient à jour une liste d'appel des méthodes auxquelles il est lié. Celui-ci prend en charge une méthode <xref:System.Delegate.Combine%2A> pour ajouter une méthode à la liste d'appel et une méthode <xref:System.Delegate.Remove%2A> pour la supprimer.

 Quand un événement est enregistré par l'application, le contrôle le déclenche en appelant son délégué. Le délégué appelle à son tour la méthode liée. Dans le cas le plus courant (délégué multidiffusion), le délégué appelle à tour de rôle chaque méthode liée de la liste d'appel, ce qui produit une notification un à plusieurs. Cette stratégie signifie que le contrôle n'a pas besoin de tenir à jour une liste des objets cible pour la notification d'événement car le délégué gère totalement l'inscription et la notification.

 Les délégués permettent également de lier plusieurs événements à la même méthode et par conséquent de produire une notification plusieurs-à-un. Par exemple, un événement button-click et un événement menu-command–click peuvent tous deux appeler le même délégué, lequel appelle à son tour une méthode unique pour qu'elle prenne en charge ces deux événements distincts de la même façon.

 Le mécanisme de liaison utilisé avec les délégués est dynamique : un délégué peut être lié au moment de l'exécution à n'importe quelle méthode dont la signature correspond à celle du gestionnaire d'événements. Cette fonctionnalité vous permet de configurer ou de modifier la méthode de liaison en fonction d’une condition et d’attacher dynamiquement un gestionnaire d’événements à un contrôle.

## <a name="see-also"></a>Voir aussi

- [Création de gestionnaires d’événements dans les Windows Forms](creating-event-handlers-in-windows-forms.md)
- [Vue d'ensemble des gestionnaires d'événements](event-handlers-overview-windows-forms.md)
