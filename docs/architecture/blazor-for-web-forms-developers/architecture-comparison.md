---
title: Comparaison de l’architecture des Web Forms ASP.NET et Blazor
description: Découvrez comment les architectures de ASP.NET Web Forms et Blazor comparer.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 11/20/2020
ms.openlocfilehash: afb5d4025b81c2ddef782c462c94d32edc872a21
ms.sourcegitcommit: 2f485e721f7f34b87856a51181b5b56624b31fd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96509726"
---
# <a name="architecture-comparison-of-aspnet-web-forms-and-no-locblazor"></a>Comparaison de l’architecture des Web Forms ASP.NET et Blazor

Bien que les ASP.NET Web Forms et Blazor présentent de nombreux concepts similaires, il existe des différences en matière de fonctionnement. Ce chapitre examine les travaux internes et les architectures de ASP.NET Web Forms et Blazor .

## <a name="aspnet-web-forms"></a>Formulaires web ASP.NET

ASP.NET Web Forms Framework est basé sur une architecture centrée sur la page. Chaque requête HTTP pour un emplacement dans l’application est une page distincte avec laquelle ASP.NET répond. Au fur et à mesure que des pages sont demandées, le contenu du navigateur est remplacé par les résultats de la page demandée.

Les pages comportent les composants suivants :

- Balisage HTML
- Code C# ou Visual Basic
- Classe code-behind contenant des fonctionnalités de logique et de gestion des événements
- Contrôles

Les contrôles sont des unités réutilisables de l’interface utilisateur Web qui peuvent être placées par programmation et interagir avec sur une page. Les pages sont composées de fichiers qui se terminent par *. aspx* contenant le balisage, les contrôles et du code. Les classes code-behind se trouvent dans des fichiers portant le même nom de base et une extension. *aspx.cs* ou *. aspx. vb* , selon le langage de programmation utilisé. Il est intéressant de faire en sorte que le serveur Web interprète le contenu des fichiers *. aspx* et les compile chaque fois qu’ils évoluent. Cette recompilation se produit même si le serveur Web est déjà en cours d’exécution.

Les contrôles peuvent être générés avec le balisage et fournis en tant que contrôles utilisateur. Un contrôle utilisateur dérive de la `UserControl` classe et a une structure similaire à la page. Le balisage des contrôles utilisateur est stocké dans un fichier *. ascx* . Une classe code-behind qui l’accompagne se trouve dans un fichier *. ascx.cs* ou *. ascx. vb* . Les contrôles peuvent également être entièrement générés avec du code, en héritant de la `WebControl` `CompositeControl` classe de base ou.

Les pages ont également un long cycle de vie des événements. Chaque page déclenche des événements pour les événements d’initialisation, de chargement, de prérendu et de déchargement qui se produisent lorsque le runtime ASP.NET exécute le code de la page pour chaque requête.

Les contrôles sur une page sont généralement renvoyés à la même page que celle qui a présenté le contrôle et envoient une charge utile à partir d’un champ de formulaire masqué appelé `ViewState` . Le `ViewState` champ contient des informations sur l’état des contrôles au moment où ils ont été rendus et présentés sur la page, ce qui permet au runtime ASP.net de comparer et d’identifier les modifications apportées au contenu soumis au serveur.

## Blazor

Blazor est une infrastructure d’interface utilisateur Web côté client similaire à celle des infrastructures frontales JavaScript comme l’angulaire ou la réaction. Blazor gère les interactions de l’utilisateur et restitue les mises à jour nécessaires de l’interface utilisateur. Blazor*n’est pas* basé sur un modèle de demande-réponse. Les interactions de l’utilisateur sont gérées en tant qu’événements qui ne sont pas dans le contexte d’une requête HTTP particulière.

Blazor les applications se composent d’un ou plusieurs composants racine qui sont rendus sur une page HTML.

![::: No-Loc (éblouissant) ::: Components en HTML](./media/architecture-comparison/blazor-components-in-html.png)

Comment l’utilisateur spécifie l’emplacement où les composants doivent être rendus et comment les composants sont ensuite associés pour que les interactions de l’utilisateur [hébergent un modèle](hosting-models.md) spécifique.

Blazorles [composants](components.md) sont des classes .net qui représentent un élément réutilisable de l’interface utilisateur. Chaque composant gère son propre État et spécifie sa propre logique de rendu, qui peut inclure le rendu d’autres composants. Les composants spécifient des gestionnaires d’événements pour les interactions utilisateur spécifiques afin de mettre à jour l’état du composant.

Une fois qu’un composant a géré un événement, Blazor restitue le composant et effectue le suivi des modifications apportées à la sortie rendue. Les composants ne sont pas rendus directement dans le Document Object Model (DOM). Elles s’affichent à la place dans une représentation en mémoire du DOM appelée `RenderTree` pour que Blazor puisse effectuer le suivi des modifications. Blazor compare la sortie nouvellement rendue avec la sortie précédente pour calculer une comparaison d’interface utilisateur qui s’applique ensuite efficacement au DOM.

![::: No-Loc (éblouissant) ::: DOM interaction](./media/architecture-comparison/blazor-dom-interaction.png)

Les composants peuvent également indiquer manuellement qu’ils doivent être rendus si leur état change en dehors d’un événement d’interface utilisateur normal. Blazor utilise un `SynchronizationContext` pour appliquer un seul thread logique d’exécution. Les méthodes de cycle de vie d’un composant et les rappels d’événements déclenchés par Blazor sont exécutés sur ce `SynchronizationContext` .

>[!div class="step-by-step"]
>[Précédent](introduction.md) 
> [Suivant](hosting-models.md)
