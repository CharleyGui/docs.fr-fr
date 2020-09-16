---
title: Gestion et déclenchement d'événements
description: Apprenez à gérer et à déclencher des événements .NET, qui sont basés sur le modèle délégué. Ce modèle permet aux abonnés de s’inscrire auprès des fournisseurs ou de recevoir des notifications.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- delegate model for events
- application development [.NET], events
- application development [.NET Framework], events
- application development [.NET Core], events
- events [.NET]
- events [.NET Core]
- events [.NET Framework]
ms.assetid: b6f65241-e0ad-4590-a99f-200ce741bb1f
ms.openlocfilehash: 83799b0f4c6d6503825ce271fed4bffa7a9775b9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545701"
---
# <a name="handling-and-raising-events"></a>Gestion et déclenchement d'événements

Les événements dans .NET Framework sont basés sur le modèle délégué. Le modèle délégué suit le [modèle de conception observateur](observer-design-pattern.md), qui permet à un abonné de s'inscrire pour recevoir des notifications d'un fournisseur. Un émetteur d'événements émet une notification d'événement, et un récepteur d'événements reçoit cette notification et définit une réponse à celle-ci. Cet article décrit les principaux composants du modèle délégué, comment consommer les événements des applications, et comment implémenter des événements dans votre code.  
  
 Pour plus d’informations sur la gestion des événements dans les applications Windows 8.x Store, consultez [Vue d’ensemble des événements et des événements routés](/previous-versions/windows/apps/hh758286(v=win.10)).  
  
## <a name="events"></a>Événements

Un événement est un message envoyé par un objet pour signaler la présence d’une action. L'action peut être provoquée par l'intervention de l'utilisateur, telle qu'un clic de bouton, ou être déclenchée par une autre logique de programme, comme la modification d’une valeur de propriété. L’objet qui déclenche l’événement est appelé *l’émetteur d’événements*. L'émetteur d'événements ne connaît pas l'objet, ni la méthode qui recevront (géreront) les événements qu'il déclenche. L'événement est généralement un membre de l'émetteur d'événements ; par exemple, l'événement <xref:System.Web.UI.WebControls.Button.Click> est membre de la classe <xref:System.Web.UI.WebControls.Button>, et l'événement <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> est membre de la classe qui implémente l'interface <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
Pour définir un événement, vous utilisez le [`event`](../../csharp/language-reference/keywords/event.md) mot clé C# ou Visual Basic [`Event`](../../visual-basic/language-reference/statements/event-statement.md) dans la signature de votre classe d’événements, puis vous spécifiez le type de délégué pour l’événement. Les délégués sont décrits dans la section suivante.  
  
En général, pour déclencher un événement, ajoutez une méthode qui est marquée comme `protected` et `virtual` (C#) ou `Protected` et `Overridable` (en Visual Basic). Nommez cette méthode `On`*EventName* ; par exemple, `OnDataReceived`. La méthode doit prendre un paramètre qui spécifie un objet de données d'événement, qui est un objet de type <xref:System.EventArgs> ou un type dérivé. Vous fournissez cette méthode pour permettre aux classes dérivées de substituer la logique de déclenchement d'événement. Une classe dérivée doit toujours appeler la méthode `On`*EventName* de la classe de base pour garantir que les délégués inscrits reçoivent l’événement.  

L'exemple suivant montre comment déclarer un évènement appelé `ThresholdReached`. L'événement est associé au délégué <xref:System.EventHandler> et déclenché dans une méthode nommée `OnThresholdReached`.  
  
 [!code-csharp[EventsOverview#1](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#1)]
 [!code-vb[EventsOverview#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#1)]  
  
## <a name="delegates"></a>Délégués

Un délégué est un type qui détient une référence à une méthode. Un délégué est déclaré avec une signature qui indique le type de retour et les paramètres des méthodes qu'il référence, et il peut contenir des références à des méthodes qui correspondent à sa signature. Un délégué est donc équivalent à un rappel ou un pointeur de fonction de type sécurisé. Une déclaration Delegate suffit à définir une classe déléguée.  
  
Les délégués ont de nombreux usages dans .NET. Dans le contexte des événements, un délégué est un intermédiaire (ou un mécanisme similaire aux pointeurs) entre la source d'événements et le code qui gère l'événement. Vous associez un délégué à un événement en incluant le type de délégué dans la déclaration de l'événement, comme indiqué dans l'exemple de la section précédente. Pour plus d'informations sur les délégués, consultez la classe <xref:System.Delegate>.  
  
.NET fournit les délégués <xref:System.EventHandler> et <xref:System.EventHandler%601> pour prendre en charge la plupart des scénarios d'événement. Utilisez le délégué <xref:System.EventHandler> pour tous les événements qui n'incluent pas de données d'événement. Utilisez le délégué <xref:System.EventHandler%601> pour les événements qui incluent des données sur l'événement. Ces délégués n’ont aucune valeur de type de retour et prennent deux paramètres (un objet pour la source de l’événement et un objet pour les données d’événement).  
  
Les délégués sont [multidiffusion](xref:System.MulticastDelegate), ce qui signifie qu'ils peuvent contenir des références à plusieurs méthodes de gestion des événements. Pour plus d'informations, consultez la page de référence <xref:System.Delegate>. Les délégués assurent une souplesse et un contrôle précis lors de la gestion des événements. Un délégué agit comme un répartiteur d’événements pour la classe qui déclenche l’événement en gérant une liste de gestionnaires d’événements inscrits pour l’événement.  
  
Pour les scénarios dans lesquels les délégués <xref:System.EventHandler> et <xref:System.EventHandler%601> ne fonctionnent pas, vous pouvez définir un délégué. Les scénarios qui nécessitent de définir un délégué sont très rares, par exemple lorsque vous devez utiliser du code qui ne reconnaît pas les génériques. Vous marquez un délégué avec le [`delegate`](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) mot clé C# et Visual Basic [`Delegate`](../../visual-basic/language-reference/statements/delegate-statement.md) dans la déclaration. L'exemple suivant montre comment déclarer un délégué nommé `ThresholdReachedEventHandler`.  
  
[!code-csharp[EventsOverview#4](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#4)]
[!code-vb[EventsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#4)]  
  
## <a name="event-data"></a>Données d’événement

Les données associées à un événement peuvent être obtenues via une classe de données d'événement. .NET fournit plusieurs classes de données d'événement que vous pouvez utiliser dans vos applications. Par exemple, la classe <xref:System.IO.Ports.SerialDataReceivedEventArgs> est la classe de données d'événement pour l'événement <xref:System.IO.Ports.SerialPort.DataReceived?displayProperty=nameWithType>. .NET suit un modèle d'affectation de nom qui veut que toutes les classes de données d'évènement se terminent par `EventArgs`. Pour savoir quelle classe de données d'événement est associée à un événement, il suffit d'examiner le délégué de l'événement. Par exemple, le délégué <xref:System.IO.Ports.SerialDataReceivedEventHandler> inclut la classe <xref:System.IO.Ports.SerialDataReceivedEventArgs> comme paramètre.  
  
La classe <xref:System.EventArgs> est le type de base pour toutes les classes de données d'événement. <xref:System.EventArgs> est également la classe que vous utilisez quand un événement n'a pas de données associée. Lorsque vous créez un événement qui vise uniquement à notifier à d'autres classes que quelque chose est survenu et n'a pas besoin de passer des données, incluez la classe <xref:System.EventArgs> comme deuxième paramètre du délégué. Vous pouvez passer la valeur <xref:System.EventArgs.Empty?displayProperty=nameWithType> lorsqu'aucune donnée n'est fournie. Le délégué <xref:System.EventHandler> inclut la classe <xref:System.EventArgs> comme paramètre.  
  
Lorsque vous souhaitez créer une classe personnalisée de données d'événement, créez une classe qui dérive de <xref:System.EventArgs>, puis fournissez tous les membres requis pour passer les données liées à l'événement. En général, vous devriez utiliser le même modèle d'affectation de noms que .NET et terminer le nom de classe de données d'événement par `EventArgs`.  
  
L'exemple suivant illustre une classe de données d'événement nommée `ThresholdReachedEventArgs`. Elle contient les propriétés spécifiques à l'événement déclenché.  
  
[!code-csharp[EventsOverview#3](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#3)]
[!code-vb[EventsOverview#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#3)]  
  
## <a name="event-handlers"></a>Gestionnaires d’événements

Pour répondre à un événement, vous définissez une méthode de gestion d'événements dans le récepteur d'événements. Cette méthode doit correspondre à la signature du délégué pour l'événement géré. Dans le gestionnaire des évènements, vous exécutez les actions nécessaires lorsque l'événement est déclenché, comme la collecte de l'entrée d'utilisateur après que l'utilisateur clique sur un bouton. Pour recevoir des notifications lorsque l'événement se produit, la méthode de votre gestionnaire d'événements doit s'abonner à l'événement.  
  
L'exemple suivant présente une méthode de gestionnaire d'événements nommée `c_ThresholdReached` qui correspond à la signature du délégué <xref:System.EventHandler>. La méthode s'abonne à l'événement `ThresholdReached`.  
  
[!code-csharp[EventsOverview#2](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#2)]
[!code-vb[EventsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#2)]  
  
## <a name="static-and-dynamic-event-handlers"></a>Gestionnaires d’événements statiques et dynamiques  

.NET permet aux abonnés de s’inscrire pour les notifications d’événements statiques ou dynamiques. Les gestionnaires d’événements statiques sont en vigueur pendant toute la durée de vie de la classe dont ils gèrent les événements. Les gestionnaires d’événements dynamiques sont explicitement activés et désactivés pendant l’exécution du programme, généralement en réponse à une logique de programme conditionnelle. Par exemple, ils peuvent être utilisés si les notifications d’événements sont nécessaires uniquement dans certaines conditions ou si une application fournit plusieurs gestionnaires d’événements et les conditions d’exécution définissent le gestionnaire approprié à utiliser. L'exemple de la section précédente indique comment ajouter dynamiquement un gestionnaire d'événements. Pour plus d’informations, consultez [Événements](../../visual-basic/programming-guide/language-features/events/index.md) (en Visual Basic) et [Événements](../../csharp/programming-guide/events/index.md) (en C#).  
  
## <a name="raising-multiple-events"></a>Déclenchement de plusieurs événements  
 Si votre classe déclenche plusieurs événements, le compilateur génère un champ par instance de délégué d'événement. Si le nombre d’événements est important, le coût de stockage d’un champ par délégué peut ne pas convenir. Dans ce cas, .NET fournit les propriétés de l’événement que vous pouvez utiliser avec une autre structure de données de votre choix pour stocker les délégués d’événements.  
  
 Les propriétés de l’événement se composent de déclarations d’événement accompagnées d’accesseurs d’événement. Les accesseurs d'événement sont des méthodes que vous définissez pour que des instances de délégué d'événement puissent être ajoutées ou supprimées de la structure des données de stockage. Notez que les propriétés d'événement sont plus lentes que les champs d'événement, car chaque délégué d'événement doit être récupéré avant de pouvoir être appelé. Le compromis réside entre la mémoire et la vitesse. Si votre classe définit de nombreux événements qui sont déclenchés peu fréquemment, vous souhaiterez implémenter les propriétés de l’événement. Pour plus d’informations, consultez [Comment : gérer plusieurs événements à l’aide des propriétés d’événements](how-to-handle-multiple-events-using-event-properties.md).  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Comment : déclencher et utiliser des événements](how-to-raise-and-consume-events.md)|Contient des exemples de déclenchement et de consommation d'événements.|  
|[Comment : gérer plusieurs événements à l'aide des propriétés d'événements](how-to-handle-multiple-events-using-event-properties.md)|Montre comment utiliser des propriétés d'événement pour gérer plusieurs événements.|  
|[Modèle de conception observateur](observer-design-pattern.md)|Décrit le modèle de conception qui permet à un abonné de s’inscrire pour recevoir des notifications d’un fournisseur.|  
|[Comment : consommer des événements dans une application Web Forms](how-to-consume-events-in-a-web-forms-application.md)|Montre comment gérer un événement déclenché par un contrôle Web Forms.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.EventHandler>
- <xref:System.EventHandler%601>
- <xref:System.EventArgs>
- <xref:System.Delegate>
- [Événements (Visual Basic)](../../visual-basic/programming-guide/language-features/events/index.md)
- [Événements (Guide de programmation C#)](../../csharp/programming-guide/events/index.md)
- [Vue d’ensemble des événements et des événements routés (applications UWP)](/windows/uwp/xaml-platform/events-and-routed-events-overview)
