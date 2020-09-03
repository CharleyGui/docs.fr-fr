---
title: Délégués et événements
description: Découvrez la différence entre les délégués et les événements, et quand utiliser chacune de ces fonctionnalités de .NET Core.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 0fdc8629-2fdb-4a7c-a433-5b9d04eaf911
ms.openlocfilehash: 193a9b0fe0e0c36deb6552449c92135057412225
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414667"
---
# <a name="distinguishing-delegates-and-events"></a>Différenciation des délégués et des événements

[Précédent](modern-events.md)

Les développeurs qui découvrent la plateforme .NET Core éprouvent souvent des difficultés quand il faut choisir entre une conception basée sur les `delegates` et une conception basée sur les `events`. Le choix des délégués ou des événements est souvent difficile, car les deux fonctionnalités de langage sont similaires. Les événements sont même générés à l’aide de la prise en charge linguistique des délégués.

Elles offrent tous deux un scénario de liaison tardive : elles autorisent les scénarios où un composant communique en appelant une méthode qui est connue uniquement au moment de l’exécution. Toutes deux prennent en charge les méthodes à abonnés uniques et multiples. On utilise parfois le terme de prise en charge singlecast et multicast. Toutes deux prennent en charge une syntaxe similaire pour l’ajout et la suppression de gestionnaires. Pour finir, le déclenchement d’un événement et l’appel d’un délégué utilisent exactement la même syntaxe d’appel de méthode. Qui plus est, elles prennent toutes deux en charge la même syntaxe de méthode `Invoke()` pour une utilisation avec l’opérateur `?.`.

Avec tous ces similitudes, il est facile d’avoir des difficultés à déterminer quand utiliser l’une ou l’autre.

## <a name="listening-to-events-is-optional"></a>La détection d’événements est facultative

Pour déterminer laquelle de ces deux fonctionnalités utiliser, il convient avant tout de savoir s’il doit y avoir un abonné attaché ou non. Si votre code doit appeler le code fourni par l’abonné, vous devez utiliser une conception basée sur des délégués lorsque vous devez implémenter le rappel. Si votre code peut effectuer tout son travail sans appeler les abonnés, vous devez utiliser un modèle basé sur les événements.

Examinez les exemples fournis dans cette section. Le code que vous avez créé à l’aide de `List.Sort()` doit disposer d’une fonction de comparaison pour trier correctement les éléments. Des requêtes LINQ doivent être fournies avec les délégués pour identifier les éléments à retourner. Tous deux ont une conception basée sur des délégués.

Prenez l’événement `Progress`. Il signale la progression d’une tâche.
La tâche se poursuit même s’il n’y a aucun détecteur.
`FileSearcher` constitue un autre exemple. Il trouvera tous les fichiers recherchés même si aucun abonné aux événements n’est attaché.
Les contrôles de l’expérience utilisateur fonctionneront toujours correctement, même si aucun abonné n’est à l’écoute des événements. Ils utilisent tous deux des conceptions basées sur les événements.

## <a name="return-values-require-delegates"></a>Les valeurs de retour nécessitent des délégués

Une autre considération à prendre en compte est le prototype de méthode souhaité pour votre méthode déléguée. Comme nous l’avons vu, les délégués utilisés pour les événements ont tous un type de retour void. Nous avons également vu qu’il existait des idiomes pour créer des gestionnaires d’événements qui repassent des informations aux sources d’événements en modifiant des propriétés de l’objet d’argument d’événement. Bien que ces idiomes fonctionnent, ils ne sont pas aussi naturels que le retour d’une valeur à partir d’une méthode.

Notez que ces heuristiques peuvent souvent être toutes deux présentes : si votre méthode déléguée retourne une valeur, elle aura probablement un impact sur l’algorithme.

## <a name="events-have-private-invocation"></a>Les événements ont un appel privé

Les classes autres que celle dans laquelle un événement est contenu peuvent uniquement ajouter et supprimer des écouteurs d’événements. seule la classe contenant l’événement peut appeler l’événement. Les événements sont généralement des membres de classe publics.
Par comparaison, les délégués sont souvent passés comme paramètres et stockés comme membres de classe privée, s’ils sont stockés du tout.

## <a name="event-listeners-often-have-longer-lifetimes"></a>Les détecteurs d’événements ont souvent des durées de vie plus longues

Ces écouteurs d’événements ont une durée de vie légèrement plus faible. Toutefois, vous constaterez peut-être que les conceptions basées sur les événements sont plus naturelles quand la source de l’événement déclenche des événements durant une période prolongée. Vous pouvez voir des exemples de conception basée sur les événements pour les contrôles d’expérience utilisateur sur de nombreux systèmes. Une fois que vous vous êtes abonné à un événement, la source de l’événement peut déclencher des événements pendant toute la durée de vie du programme.
(Vous pouvez vous désabonner à des événements quand vous n’en avez plus besoin.)

Comparez cela à de nombreuses conceptions basées sur les délégués, où un délégué est utilisé comme argument d’une méthode et le délégué n’est pas utilisé après le retour de cette méthode.

## <a name="evaluate-carefully"></a>Évaluez avec soin

Les considérations ci-dessus ne sont pas des règles absolues. Il s’agit plutôt de conseils qui vous aideront à décider de ce qui convient le mieux à votre utilisation particulière. Les deux fonctionnalités étant similaires, vous pouvez même les prototyper et évaluer celle dont l’utilisation serait plus naturelle. Elles gèrent également toutes deux les scénarios de liaison tardive. Utilisez celle qui correspond le mieux à votre conception.
