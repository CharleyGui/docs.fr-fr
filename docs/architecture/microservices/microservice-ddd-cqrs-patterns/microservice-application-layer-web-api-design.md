---
title: Conception de la couche Application de microservices et de l’API web
description: Architecture de microservices .NET pour les applications .NET conteneurisées | Brève explication des principes SOLID pour la conception de la couche Application.
ms.date: 10/08/2018
ms.openlocfilehash: 491aa7bd90910c7f6c1d0ab56edfe0ae057ca006
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988451"
---
# <a name="design-the-microservice-application-layer-and-web-api"></a>Concevoir la couche Application de microservices et l’API web

## <a name="use-solid-principles-and-dependency-injection"></a>Utiliser les principes SOLID et l’injection de dépendances

Les principes SOLID sont des techniques essentielles à utiliser dans les applications modernes et stratégiques, notamment dans le développement d’un microservice avec des modèles DDD. SOLID est un acronyme qui regroupe cinq principes fondamentaux :

- Principe de responsabilité unique (Single responsibility)

- Principe ouvert/fermé (Open/closed)

- Principe de substitution de Liskov (Liskov substitution)

- Principe de ségrégation des interfaces (Interface segregation)

- Principe d’inversion de dépendances (Dependency inversion)

SOLID a plus trait à la façon dont vous concevez votre application ou vos couches internes de microservices et au découplage des dépendances entre elles. Il n’est pas lié au domaine, mais à la conception technique de l’application. Le dernier principe, celui de l’inversion de dépendances, vous permet de découpler la couche d’infrastructure du reste des couches, ce qui permet une implémentation mieux découplée des couches DDD.

L’inversion de dépendances est une façon d’implémenter le principe éponyme. Il s’agit d’une technique de couplage faible entre des objets et leurs dépendances. Au lieu d’instancier directement des collaborateurs ou d’utiliser des références statiques (comme is, using new…), les objets dont a besoin une classe pour effectuer ses opérations sont fournis à la classe (ou injectés dans la classe). Le plus souvent, les classes déclarent leurs dépendances par le biais de leur constructeur, ce qui leur permet de suivre le principe des dépendances explicites. L’injection de dépendances se base généralement sur des conteneurs d’inversion de contrôle (IoC) spécifiques. ASP.NET Core fournit un simple conteneur IoC intégré, mais vous pouvez également utiliser votre conteneur IoC favori, comme Autofac ou Ninject.

En suivant les principes SOLID, vos classes ont naturellement tendance à être petites, bien factorisées et facilement testées. Mais comment savoir si trop de dépendances sont injectées dans vos classes ? Si vous utilisez l’inversion de dépendances par le biais du constructeur, vous pouvez facilement le détecter rien qu’en examinant le nombre de paramètres pour votre constructeur. S’il y a trop de dépendances, c’est généralement le signe (un [code smell](https://deviq.com/code-smells/)) que votre classe essaie d’en faire trop et qu’elle enfreint probablement le principe de responsabilité unique.

Un autre guide serait nécessaire pour couvrir les principes SOLID de façon approfondie. C’est pourquoi le présent guide exige que vous ayez un minimum de connaissances à ce sujet.

#### <a name="additional-resources"></a>Ressources supplémentaires

- **SOLID: Principes fondamentaux OOP** \
  <https://deviq.com/solid/>

- **Inversion des conteneurs de contrôle et le modèle d’injection de dépendance** \
  <https://martinfowler.com/articles/injection.html>

- **Steve Smith. Nouveau est Glue** \
  <https://ardalis.com/new-is-glue>

> [!div class="step-by-step"]
> [Suivant précédent](nosql-database-persistence-infrastructure.md)
> [Next](microservice-application-layer-implementation-web-api.md)
