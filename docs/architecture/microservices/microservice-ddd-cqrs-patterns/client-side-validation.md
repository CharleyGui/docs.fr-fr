---
title: Validation côté client (validation dans les couches de présentation)
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Explorer les concepts clés de la validation côté client.
ms.date: 10/08/2018
ms.openlocfilehash: 4e72dcafafc3144a75afe1fd23a4a779f5667459
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "68674356"
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a>Validation côté client (validation dans les couches de présentation)

Même quand la source fiable est le modèle de domaine et que vous devez obtenir au final une validation à ce niveau, la validation peut toujours être gérée au niveau du modèle de domaine (côté serveur) et au niveau de l’interface utilisateur (côté client).

La validation côté client est très pratique pour les utilisateurs. Elle leur épargne le temps d’attente nécessaire à un aller-retour avec le serveur qui pourrait retourner des erreurs de validation. En termes d’activité de l’entreprise, même quelques fractions de secondes multipliées des centaines de fois par jour finissent par représenter un temps considérable, auquel s’ajoutent un coût et de la frustration. Une validation directe et immédiate permet aux utilisateurs de travailler plus efficacement, et de produire une meilleure qualité des entrées et des sorties.

Alors que le modèle d’affichage et le modèle de domaine sont différents, leur validation peut être semblable, mais avec un objectif différent. Si vous vous souciez du principe DRY (Don’t Repeat Yourself), considérez que dans ce cas la réutilisation du code peut également impliquer un couplage et, dans les applications d’entreprise, il est plus important de ne pas associer le côté serveur au côté client que de respecter le principe DRY.

Même quand vous utilisez la validation côté client, vous devez toujours valider vos commandes ou DTO d’entrée dans le code serveur, car les API serveur représentent un vecteur d’attaque possible. En règle générale, il vaut mieux effectuer les deux opérations car, si vous avez une application cliente, il est recommandé du point de vue de l’expérience utilisateur d’être proactif et de ne pas autoriser l’utilisateur à entrer des informations non valides.

Par conséquent, dans le code côté client, vous validez généralement les ViewModels. Vous pouvez également valider les commandes ou DTO de sortie clients avant de les envoyer aux services.

L’implémentation de la validation côté client dépend du type d’application cliente que vous créez. Elle sera différente si vous validez des données dans une application web MVC avec la plupart du code en .NET, une application web SPA avec cette validation codée en JavaScript ou TypeScript, ou une application mobile codée avec Xamarin et C#.

## <a name="additional-resources"></a>Ressources supplémentaires

### <a name="validation-in-xamarin-mobile-apps"></a>Validation dans les applications mobiles Xamarin

- **Valider l’entrée de texte et afficher les erreurs** \
  [https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

- **Rappel de validation** \
  <https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/>

### <a name="validation-in-aspnet-core-apps"></a>Validation dans les applications ASP.NET Core

- **Rick Anderson. Ajout de validation** \
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a>Validation dans les applications web SPA (Angular 2, TypeScript, JavaScript)

- **Ado Kukic. Validation de formulaire angulaire 2** \
  <https://scotch.io/tutorials/angular-2-form-validation>

- **Validation du formulaire** \
  <https://angular.io/guide/form-validation>

- **Validation.** Documentation Breeze. \
  <https://breeze.github.io/doc-js/validation.html>

En résumé, voici les concepts les plus importants en ce qui concerne la validation :

- Les entités et les agrégats doivent appliquer leur propre cohérence et être « toujours valides ». Les racines d’agrégat sont responsables de la cohérence de plusieurs entités dans le même agrégat.

- Si vous pensez qu’une entité doit entrer dans un état non valide, envisagez d’utiliser un modèle d’objet différent, par exemple un DTO temporaire jusqu’à ce que l’entité de domaine finale soit créée.

- Si vous devez créer plusieurs objets associés, comme un agrégat, et qu’ils ne sont valides qu’une fois que tous ont été créés, envisagez d’utiliser le modèle de fabrique.

- Dans la plupart des cas, une validation redondante côté client est appropriée, car l’application peut être proactive.

>[!div class="step-by-step"]
>[Suivant précédent](domain-model-layer-validations.md)
>[Next](domain-events-design-implementation.md)
