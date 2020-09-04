---
title: Introduction aux événements
description: En savoir plus sur les événements dans .NET Core et nos objectifs de conception de langage pour les événements dans cette vue d’ensemble.
ms.date: 06/20/2016
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: 4da44c151244e8b5de34f550040c271131d9598c
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465232"
---
# <a name="introduction-to-events"></a>Introduction aux événements

[Précédent](delegates-patterns.md)

Les événements sont, comme les délégués, un mécanisme de *liaison tardive*. En fait, les événements reposent sur la prise en charge linguistique des délégués.

Ils permettent à un objet de signaler (à tous les composants du système intéressés), que quelque chose s’est produit. Tous les autres composants peuvent s’abonner à l’événement et être averti quand un événement est déclenché.

Vous avez sans doute déjà utilisé des événements durant vos tâches de programmation. De nombreux systèmes graphiques ont un modèle d’événement pour signaler l’interaction utilisateur. Ces événements signalent les mouvements de la souris, les pressions sur des boutons et autres interactions similaires. C’est l’un des scénarios les plus courants, mais certainement pas le seul, où des événements sont utilisés.

Vous pouvez définir les événements qui doivent être déclenchés pour vos classes. Quand vous travaillez avec des événements, vous devez prendre en compte le fait qu’il se peut qu’aucun objet ne soit inscrit pour un événement particulier. Vous devez écrire votre code pour qu’il ne déclenche pas d’événement quand aucun détecteur n’est configuré.

L’abonnement à un événement crée également un couplage entre deux objets (la source de l’événement et le récepteur d’événements). Vous devez vérifier que le récepteur d’événements annule l’abonnement à la source de l’événement quand il n’est plus intéressé par les événements.

## <a name="design-goals-for-event-support"></a>Objectifs de conception pour la prise en charge des événements

La conception de langage pour les événements cible ces objectifs :

- Activez un couplage très minimal entre une source d’événement et un récepteur d’événements. Ces deux composants peuvent ne pas avoir été écrits par la même organisation, et peuvent même être mis à jour d’après une planification totalement différente.

- Il doit être très simple de s’abonner à un événement et de se désabonner de ce même événement.

- Les sources d’événements doivent prendre en charge plusieurs abonnés aux événements. Elles doivent aussi prendre en charge les scénarios où aucun abonné aux événements n’est attaché.

Vous pouvez constater que les objectifs pour les événements sont très similaires aux objectifs pour les délégués.
C’est pourquoi la prise en charge linguistique des événements repose sur la prise en charge linguistique des délégués.

## <a name="language-support-for-events"></a>Prise en charge linguistique pour les événements

La syntaxe de définition des événements, et d’abonnement ou d’annulation des abonnements, est une extension de la syntaxe des délégués.

Pour définir un événement, vous devez utiliser le mot clé `event` :

```csharp
public event EventHandler<FileListArgs> Progress;
```

Le type de l’événement (`EventHandler<FileListArgs>` dans cet exemple) doit être un type délégué. Vous devez respecter plusieurs conventions lors de la déclaration d’un événement. En général, le type délégué d’événement a un retour void.
Les déclarations d’événements doivent être un verbe ou une phrase verbale.
Utilisez des dizaines lorsque l’événement signale une action qui s’est produite. Utilisez un verbe au présent (par exemple, `Closing`) pour signaler quelque chose qui est sur le point de se produire. Souvent, le présent indique que votre classe prend en charge un type de comportement de personnalisation. L’un des scénarios les plus courants consiste à prendre en charge l’annulation. Par exemple, un événement `Closing` peut inclure un argument qui indique si l’opération de fermeture doit continuer ou non.  D’autres scénarios peuvent permettre aux appelants de modifier le comportement en mettant à jour les propriétés des arguments de l’événement. Vous pouvez déclencher un événement pour indiquer une action suivante qu’un algorithme effectuera. Le gestionnaire d’événements peut imposer une action différente en modifiant les propriétés de l’argument d’événement.

Quand vous souhaitez déclencher l’événement, vous appelez les gestionnaires d’événements à l’aide de la syntaxe d’appel de délégué :

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

Comme indiqué dans la section sur les [délégués](delegates-patterns.md), l’opérateur ?.
permet de s’assurer facilement que vous n’essayez pas de déclencher l’événement quand il n’y a aucun abonné à cet événement.

Vous vous abonnez à un événement à l’aide de l’opérateur `+=` :

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) =>
    Console.WriteLine(eventArgs.FoundFile);

fileLister.Progress += onProgress;
```

La méthode de gestionnaire a généralement le préfixe « on » suivi du nom de l’événement, comme indiqué ci-dessus.

Vous pouvez vous désinscrire à l’aide de l’opérateur `-=` :

```csharp
fileLister.Progress -= onProgress;
```

Il est important de déclarer une variable locale pour l’expression qui représente le gestionnaire d’événements. Cela garantit que le désabonnement supprime le gestionnaire.
Si au lieu de cela vous utilisez le corps de l’expression lambda, vous essayez de supprimer un gestionnaire qui n’a jamais été attaché, ce qui ne fait rien.

Dans l’article suivant, vous en apprendrez davantage sur les modèles d’événements les plus courants et sur les différentes variantes de cet exemple.

[Next](event-pattern.md)
