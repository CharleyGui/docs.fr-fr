---
title: Conception d'événements
ms.date: 10/22/2008
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
ms.openlocfilehash: d04ffd2cab21177f1342a13259a81df22b65723a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734411"
---
# <a name="event-design"></a>Conception d'événements

Les événements sont la forme de rappels la plus couramment utilisée (les constructions qui permettent à l’infrastructure d’appeler le code utilisateur). D’autres mécanismes de rappel incluent des membres qui prennent des délégués, des membres virtuels et des plug-ins basés sur une interface. Les données des études d’utilisation indiquent que la majorité des développeurs sont plus à l’aise avec les événements qu’ils utilisent les autres mécanismes de rappel. Les événements sont parfaitement intégrés à Visual Studio et de nombreux langages.

 Il est important de noter qu’il existe deux groupes d’événements : les événements déclenchés avant un état des modifications du système, appelés pré-événements et les événements déclenchés après la modification d’un État, appelés événements postérieurs à. Un exemple d’un pré-événement serait `Form.Closing` , qui est déclenché avant la fermeture d’un formulaire. Un exemple d’événement de publication est `Form.Closed` , qui est déclenché après la fermeture d’un formulaire.

 ✔️ Utilisez le terme « Raise » pour les événements plutôt que « déclencher » ou « déclencheur ».

 ✔️ Utilisez <xref:System.EventHandler%601?displayProperty=nameWithType> plutôt que de créer manuellement de nouveaux délégués à utiliser comme gestionnaires d’événements.

 ✔️ envisagez d’utiliser une sous-classe de <xref:System.EventArgs> comme argument d’événement, sauf si vous êtes absolument sûr que l’événement n’aura jamais besoin de transmettre des données à la méthode de gestion des événements, auquel cas vous pouvez utiliser `EventArgs` directement le type.

 Si vous livrez une API à l’aide de `EventArgs` directement, vous ne serez jamais en mesure d’ajouter des données à exécuter avec l’événement sans interrompre la compatibilité. Si vous utilisez une sous-classe, même si elle est initialement vide, vous pouvez ajouter des propriétés à la sous-classe si nécessaire.

 ✔️ Utilisez une méthode virtuelle protégée pour déclencher chaque événement. Cela s’applique uniquement aux événements non statiques sur les classes non scellées, pas aux structs, aux classes scellées ou aux événements statiques.

 L’objectif de la méthode est de fournir un moyen pour une classe dérivée de gérer l’événement à l’aide d’un remplacement. La substitution est un moyen plus flexible, plus rapide et plus naturel de gérer les événements de classe de base dans les classes dérivées. Par Convention, le nom de la méthode doit commencer par « on » et être suivi du nom de l’événement.

 La classe dérivée peut choisir de ne pas appeler l’implémentation de base de la méthode dans sa substitution. Soyez prêt à le faire en n’incluant aucun traitement dans la méthode qui est requis pour que la classe de base fonctionne correctement.

 ✔️ prennent un paramètre à la méthode protégée qui déclenche un événement.

 Le paramètre doit être nommé `e` et doit être typé en tant que classe d’argument d’événement.

 ❌ NE transmettez pas NULL comme expéditeur lors du déclenchement d’un événement non statique.

 ✔️ passer NULL comme expéditeur lors du déclenchement d’un événement statique.

 ❌ NE transmettez pas de valeur null en tant que paramètre de données d’événement lors du déclenchement d’un événement.

 Vous devez passer `EventArgs.Empty` si vous ne souhaitez pas transmettre de données à la méthode de gestion des événements. Les développeurs s’attendent à ce que ce paramètre ne soit pas null.

 ✔️ envisagez de déclencher des événements que l’utilisateur final peut annuler. Cela s’applique uniquement aux pré-événements.

 Utilisez <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> ou sa sous-classe comme argument d’événement pour permettre à l’utilisateur final d’annuler des événements.

### <a name="custom-event-handler-design"></a>Conception du gestionnaire d’événements personnalisé

 Dans certains cas, il `EventHandler<T>` ne peut pas être utilisé, par exemple quand le Framework doit fonctionner avec des versions antérieures du CLR, qui ne prenait pas en charge les génériques. Dans ce cas, vous devrez peut-être concevoir et développer un délégué de gestionnaire d’événements personnalisé.

 ✔️ Utilisez un type de retour void pour les gestionnaires d’événements.

 Un gestionnaire d’événements peut appeler plusieurs méthodes de gestion des événements, éventuellement sur plusieurs objets. Si les méthodes de gestion des événements étaient autorisées à retourner une valeur, il y aurait plusieurs valeurs de retour pour chaque appel d’événement.

 ✔️ Utilisez `object` comme type du premier paramètre du gestionnaire d’événements et appelez-le `sender` .

 ✔️ Utilisez <xref:System.EventArgs?displayProperty=nameWithType> ou sa sous-classe comme type du deuxième paramètre du gestionnaire d’événements et appelez-le `e` .

 ❌ Il n’y a pas plus de deux paramètres sur les gestionnaires d’événements.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Recommandations en matière de conception de membres](member.md)
- [Directives de conception d’infrastructure](index.md)
