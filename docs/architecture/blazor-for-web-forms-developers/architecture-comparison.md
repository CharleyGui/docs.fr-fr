---
title: Comparaison de l’architecture de ASP.NET Web Forms et de éblouissant
description: Découvrez comment les architectures de ASP.NET Web Forms et éblouissantes sont comparées.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 1137218e1cd99a39240592be415f734223e90b77
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183958"
---
# <a name="architecture-comparison-of-aspnet-web-forms-and-blazor"></a>Comparaison de l’architecture de ASP.NET Web Forms et de éblouissant

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Bien que ASP.NET Web Forms et éblouissant présentent de nombreux concepts similaires, il existe des différences en matière de fonctionnement. Ce chapitre examine le fonctionnement interne et les architectures de ASP.NET Web Forms et de éblouissant.

## <a name="aspnet-web-forms"></a>ASP.NET Web Forms

ASP.NET Web Forms Framework est basé sur une architecture centrée sur la page. Chaque requête HTTP pour un emplacement dans l’application est une page distincte avec laquelle ASP.NET répond. Au fur et à mesure que des pages sont demandées, le contenu du navigateur est remplacé par les résultats de la page demandée.

Les pages comportent les composants suivants :

* Balisage HTML
* Code C# ou Visual Basic
* Classe code-behind contenant des fonctionnalités de logique et de gestion des événements
* Contrôles

Les contrôles sont des unités réutilisables de l’interface utilisateur Web qui peuvent être placées par programmation et interagir avec sur une page. Les pages sont composées de fichiers qui se terminent par *. aspx* contenant le balisage, les contrôles et du code. Les classes code-behind se trouvent dans des fichiers portant le même nom de base et une extension. *aspx.cs* ou *. aspx. vb* , selon le langage de programmation utilisé. Il est intéressant de faire en sorte que le serveur Web interprète le contenu des fichiers *. aspx* et les compile chaque fois qu’ils évoluent. Cette recompilation se produit même si le serveur Web est déjà en cours d’exécution.

Les contrôles peuvent être générés avec le balisage et fournis en tant que contrôles utilisateur. Un contrôle utilisateur dérive de la `UserControl` classe et a une structure similaire à la page. Le balisage des contrôles utilisateur est stocké dans un fichier *. ascx* . Une classe code-behind qui l’accompagne se trouve dans un fichier *. ascx.cs* ou *. ascx. vb* . Les contrôles peuvent également être entièrement générés avec du code, en héritant `WebControl` de `CompositeControl` la classe de base ou.

Les pages ont également un long cycle de vie des événements. Chaque page déclenche des événements pour les événements d’initialisation, de chargement, de prérendu et de déchargement qui se produisent lorsque le runtime ASP.NET exécute le code de la page pour chaque requête.

Les contrôles sur une page sont généralement renvoyés à la même page que celle qui a présenté le contrôle et envoient une charge utile à partir d' `ViewState`un champ de formulaire masqué appelé. Le `ViewState` champ contient des informations sur l’état des contrôles au moment où ils ont été rendus et présentés sur la page, ce qui permet au runtime ASP.net de comparer et d’identifier les modifications apportées au contenu soumis au serveur.

## <a name="blazor"></a>Blazor

Éblouissant est une infrastructure d’interface utilisateur Web côté client similaire à celle des infrastructures frontales JavaScript comme l’angulaire ou la réaction. Éblouissant gère les interactions de l’utilisateur et restitue les mises à jour nécessaires de l’interface utilisateur. Éblouissant *n’est pas* basé sur un modèle de demande-réponse. Les interactions de l’utilisateur sont gérées en tant qu’événements qui ne sont pas dans le contexte d’une requête HTTP particulière.

Les applications éblouissantes se composent d’un ou plusieurs composants racine qui sont rendus sur une page HTML.

![Composants éblouissants en HTML](./media/architecture-comparison/blazor-components-in-html.png)

Comment l’utilisateur spécifie l’emplacement où les composants doivent être rendus et comment les composants sont ensuite associés pour que les interactions de l’utilisateur [hébergent un modèle](hosting-models.md) spécifique.

Les [composants](components.md) éblouissants sont des classes .net qui représentent un élément réutilisable de l’interface utilisateur. Chaque composant gère son propre État et spécifie sa propre logique de rendu, qui peut inclure le rendu d’autres composants. Les composants spécifient des gestionnaires d’événements pour les interactions utilisateur spécifiques afin de mettre à jour l’état du composant.

Une fois qu’un composant gère un événement, éblouissant affiche le composant et effectue le suivi des modifications apportées à la sortie rendue. Les composants ne sont pas rendus directement dans le Document Object Model (DOM). Elles s’affichent à la place dans une représentation en mémoire du DOM `RenderTree` appelée, ce qui permet à éblouissant de suivre les modifications. Éblouissant compare la sortie qui vient d’être rendue avec la sortie précédente pour calculer une différence entre l’interface utilisateur et s’applique ensuite efficacement au DOM.

![Interaction avec le DOM éblouissant](./media/architecture-comparison/blazor-dom-interaction.png)

Les composants peuvent également indiquer manuellement qu’ils doivent être rendus si leur état change en dehors d’un événement d’interface utilisateur normal. Éblouissant utilise un `SynchronizationContext` pour appliquer un seul thread logique d’exécution. Les méthodes de cycle de vie d’un composant et les rappels d’événements déclenchés par éblouissant sont `SynchronizationContext`exécutés sur ce.

>[!div class="step-by-step"]
>[Précédent](introduction.md)
>[Suivant](hosting-models.md)
