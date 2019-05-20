---
title: Validation côté client (validation dans les couches de présentation)
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Explorer les concepts clés de la validation côté client.
ms.date: 10/08/2018
ms.openlocfilehash: 4e72dcafafc3144a75afe1fd23a4a779f5667459
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644842"
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a><span data-ttu-id="1ab76-103">Validation côté client (validation dans les couches de présentation)</span><span class="sxs-lookup"><span data-stu-id="1ab76-103">Client-side validation (validation in the presentation layers)</span></span>

<span data-ttu-id="1ab76-104">Même quand la source fiable est le modèle de domaine et que vous devez obtenir au final une validation à ce niveau, la validation peut toujours être gérée au niveau du modèle de domaine (côté serveur) et au niveau de l’interface utilisateur (côté client).</span><span class="sxs-lookup"><span data-stu-id="1ab76-104">Even when the source of truth is the domain model and ultimately you must have validation at the domain model level, validation can still be handled at both the domain model level (server side) and the UI (client side).</span></span>

<span data-ttu-id="1ab76-105">La validation côté client est très pratique pour les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="1ab76-105">Client-side validation is a great convenience for users.</span></span> <span data-ttu-id="1ab76-106">Elle leur épargne le temps d’attente nécessaire à un aller-retour avec le serveur qui pourrait retourner des erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="1ab76-106">It saves time they would otherwise spend waiting for a round trip to the server that might return validation errors.</span></span> <span data-ttu-id="1ab76-107">En termes d’activité de l’entreprise, même quelques fractions de secondes multipliées des centaines de fois par jour finissent par représenter un temps considérable, auquel s’ajoutent un coût et de la frustration.</span><span class="sxs-lookup"><span data-stu-id="1ab76-107">In business terms, even a few fractions of seconds multiplied hundreds of times each day adds up to a lot of time, expense, and frustration.</span></span> <span data-ttu-id="1ab76-108">Une validation directe et immédiate permet aux utilisateurs de travailler plus efficacement, et de produire une meilleure qualité des entrées et des sorties.</span><span class="sxs-lookup"><span data-stu-id="1ab76-108">Straightforward and immediate validation enables users to work more efficiently and produce better quality input and output.</span></span>

<span data-ttu-id="1ab76-109">Alors que le modèle d’affichage et le modèle de domaine sont différents, leur validation peut être semblable, mais avec un objectif différent.</span><span class="sxs-lookup"><span data-stu-id="1ab76-109">Just as the view model and the domain model are different, view model validation and domain model validation might be similar but serve a different purpose.</span></span> <span data-ttu-id="1ab76-110">Si vous vous souciez du principe DRY (Don’t Repeat Yourself), considérez que dans ce cas la réutilisation du code peut également impliquer un couplage et, dans les applications d’entreprise, il est plus important de ne pas associer le côté serveur au côté client que de respecter le principe DRY.</span><span class="sxs-lookup"><span data-stu-id="1ab76-110">If you are concerned about DRY (the Don’t Repeat Yourself principle), consider that in this case code reuse might also mean coupling, and in enterprise applications it is more important not to couple the server side to the client side than to follow the DRY principle.</span></span>

<span data-ttu-id="1ab76-111">Même quand vous utilisez la validation côté client, vous devez toujours valider vos commandes ou DTO d’entrée dans le code serveur, car les API serveur représentent un vecteur d’attaque possible.</span><span class="sxs-lookup"><span data-stu-id="1ab76-111">Even when using client-side validation, you should always validate your commands or input DTOs in server code, because the server APIs are a possible attack vector.</span></span> <span data-ttu-id="1ab76-112">En règle générale, il vaut mieux effectuer les deux opérations car, si vous avez une application cliente, il est recommandé du point de vue de l’expérience utilisateur d’être proactif et de ne pas autoriser l’utilisateur à entrer des informations non valides.</span><span class="sxs-lookup"><span data-stu-id="1ab76-112">Usually, doing both is your best bet because if you have a client application, from a UX perspective, it is best to be proactive and not allow the user to enter invalid information.</span></span>

<span data-ttu-id="1ab76-113">Par conséquent, dans le code côté client, vous validez généralement les ViewModels.</span><span class="sxs-lookup"><span data-stu-id="1ab76-113">Therefore, in client-side code you typically validate the ViewModels.</span></span> <span data-ttu-id="1ab76-114">Vous pouvez également valider les commandes ou DTO de sortie clients avant de les envoyer aux services.</span><span class="sxs-lookup"><span data-stu-id="1ab76-114">You could also validate the client output DTOs or commands before you send them to the services.</span></span>

<span data-ttu-id="1ab76-115">L’implémentation de la validation côté client dépend du type d’application cliente que vous créez.</span><span class="sxs-lookup"><span data-stu-id="1ab76-115">The implementation of client-side validation depends on what kind of client application you are building.</span></span> <span data-ttu-id="1ab76-116">Elle sera différente si vous validez des données dans une application web MVC avec la plupart du code en .NET, une application web SPA avec cette validation codée en JavaScript ou TypeScript, ou une application mobile codée avec Xamarin et C#.</span><span class="sxs-lookup"><span data-stu-id="1ab76-116">It will be different if you are validating data in a web MVC web application with most of the code in .NET, a SPA web application with that validation being coded in JavaScript or TypeScript, or a mobile app coded with Xamarin and C#.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="1ab76-117">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="1ab76-117">Additional resources</span></span>

### <a name="validation-in-xamarin-mobile-apps"></a><span data-ttu-id="1ab76-118">Validation dans les applications mobiles Xamarin</span><span class="sxs-lookup"><span data-stu-id="1ab76-118">Validation in Xamarin mobile apps</span></span>

- <span data-ttu-id="1ab76-119">**Valider l’entrée de texte et afficher les erreurs** \\</span><span class="sxs-lookup"><span data-stu-id="1ab76-119">**Validate Text Input and Show Errors** \\</span></span>
  [https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

- <span data-ttu-id="1ab76-120">**Rappel de validation** \\</span><span class="sxs-lookup"><span data-stu-id="1ab76-120">**Validation Callback** \\</span></span>
  <https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/>

### <a name="validation-in-aspnet-core-apps"></a><span data-ttu-id="1ab76-121">Validation dans les applications ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1ab76-121">Validation in ASP.NET Core apps</span></span>

- <span data-ttu-id="1ab76-122">**Rick Anderson. Ajout de la validation** \\</span><span class="sxs-lookup"><span data-stu-id="1ab76-122">**Rick Anderson. Adding validation** \\</span></span>
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a><span data-ttu-id="1ab76-123">Validation dans les applications web SPA (Angular 2, TypeScript, JavaScript)</span><span class="sxs-lookup"><span data-stu-id="1ab76-123">Validation in SPA Web apps (Angular 2, TypeScript, JavaScript)</span></span>

- <span data-ttu-id="1ab76-124">**Ado Kukic. Validation des formulaires Angular 2** \\</span><span class="sxs-lookup"><span data-stu-id="1ab76-124">**Ado Kukic. Angular 2 Form Validation** \\</span></span>
  <https://scotch.io/tutorials/angular-2-form-validation>

- <span data-ttu-id="1ab76-125">**Validation des formulaires** \\</span><span class="sxs-lookup"><span data-stu-id="1ab76-125">**Form Validation** \\</span></span>
  <https://angular.io/guide/form-validation>

- <span data-ttu-id="1ab76-126">**Validation.**</span><span class="sxs-lookup"><span data-stu-id="1ab76-126">**Validation.**</span></span> <span data-ttu-id="1ab76-127">Documentation Breeze.</span><span class="sxs-lookup"><span data-stu-id="1ab76-127">Breeze documentation.</span></span> \
  <https://breeze.github.io/doc-js/validation.html>

<span data-ttu-id="1ab76-128">En résumé, voici les concepts les plus importants en ce qui concerne la validation :</span><span class="sxs-lookup"><span data-stu-id="1ab76-128">In summary, these are the most important concepts in regards to validation:</span></span>

- <span data-ttu-id="1ab76-129">Les entités et les agrégats doivent appliquer leur propre cohérence et être « toujours valides ».</span><span class="sxs-lookup"><span data-stu-id="1ab76-129">Entities and aggregates should enforce their own consistency and be "always valid”.</span></span> <span data-ttu-id="1ab76-130">Les racines d’agrégat sont responsables de la cohérence de plusieurs entités dans le même agrégat.</span><span class="sxs-lookup"><span data-stu-id="1ab76-130">Aggregate roots are responsible for multi-entity consistency within the same aggregate.</span></span>

- <span data-ttu-id="1ab76-131">Si vous pensez qu’une entité doit entrer dans un état non valide, envisagez d’utiliser un modèle d’objet différent, par exemple un DTO temporaire jusqu’à ce que l’entité de domaine finale soit créée.</span><span class="sxs-lookup"><span data-stu-id="1ab76-131">If you think that an entity needs to enter an invalid state, consider using a different object model—for example, using a temporary DTO until you create the final domain entity.</span></span>

- <span data-ttu-id="1ab76-132">Si vous devez créer plusieurs objets associés, comme un agrégat, et qu’ils ne sont valides qu’une fois que tous ont été créés, envisagez d’utiliser le modèle de fabrique.</span><span class="sxs-lookup"><span data-stu-id="1ab76-132">If you need to create several related objects, such as an aggregate, and they are only valid once all of them have been created, consider using the Factory pattern.</span></span>

- <span data-ttu-id="1ab76-133">Dans la plupart des cas, une validation redondante côté client est appropriée, car l’application peut être proactive.</span><span class="sxs-lookup"><span data-stu-id="1ab76-133">In most of the cases, having redundant validation in the client side is good, because the application can be proactive.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1ab76-134">[Précédent](domain-model-layer-validations.md)
>[Suivant](domain-events-design-implementation.md)</span><span class="sxs-lookup"><span data-stu-id="1ab76-134">[Previous](domain-model-layer-validations.md)
[Next](domain-events-design-implementation.md)</span></span>
