---
title: Création, évolution et version des contrats et des API de microservices
description: Créez des API et des contrats de microservices en tenant compte de l’évolution et de la gestion de versions, car les besoins changent.
ms.date: 09/20/2018
ms.openlocfilehash: 1972d02d8bf7935c71bfd383707ae19ea2baded9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "68672896"
---
# <a name="creating-evolving-and-versioning-microservice-apis-and-contracts"></a>Création, évolution et version des contrats et des API de microservices

Une API de microservice est un contrat entre le service et ses clients. Vous ne pouvez pas faire évoluer indépendamment un microservice si son contrat d’API est rompu. C’est pourquoi le contrat est si important. Tout changement apporté au contrat impacte vos applications clientes ou votre passerelle API.

La nature de la définition de l’API dépend du protocole que vous utilisez. Par exemple, si vous utilisez une messagerie telle qu’[AMQP](https://www.amqp.org/), l’API comprend les types de message. Si vous utilisez des services HTTP et RESTful, l’API comprend les URL et les formats JSON de requête et de réponse.

Toutefois, même si votre contrat initial est l’aboutissement d’une réflexion, une API de service doit changer au fil du temps. Quand cela se produit, vous ne pouvez généralement pas forcer tous les clients à effectuer une mise à niveau vers votre nouveau contrat d’API, surtout s’il s’agit d’une API publique consommée par plusieurs applications clientes. Dans la plupart des cas, vous devez déployer par incrément les nouvelles versions d’un service en faisant en sorte que les anciennes et les nouvelles versions du contrat de service s’exécutent simultanément. Il est donc important de disposer d’une stratégie pour la gestion de versions de votre service.

Si vous apportez des changements minimes à l’API, comme l’ajout d’attributs ou de paramètres, il est recommandé que les clients qui utilisent une API antérieure passent à la nouvelle version du service. Il est possible que vous puissiez fournir des valeurs par défaut pour tous les attributs obligatoires manquants et que les clients ignorent les attributs de réponse en trop.

Toutefois, vous pouvez parfois être amené à apporter des changements majeurs à une API de service qui débouchent sur des incompatibilités. Dans l’éventualité où vous ne pourriez pas forcer les applications ou services clients à passer tout de suite à la nouvelle version, un service doit prendre en charge les anciennes versions de l’API pendant un certain temps. Si vous utilisez un mécanisme HTTP, par exemple REST, il existe une approche qui consiste à incorporer le numéro de version de l’API dans l’URL ou dans un en-tête HTTP. Vous pouvez ensuite soit implémenter simultanément les deux versions du service dans la même instance de service, soit déployer des instances distinctes gérant des versions différentes de l’API. Une bonne approche consiste à utiliser le [modèle Médiateur](https://en.wikipedia.org/wiki/Mediator_pattern) (par exemple, la [bibliothèque MediatR](https://github.com/jbogard/MediatR)) pour découpler les versions de l’implémentation en gestionnaires indépendants.

Enfin, si vous utilisez une architecture REST, [Hypermedia](https://www.infoq.com/articles/mark-baker-hypermedia) constitue la meilleure solution pour la gestion de versions de vos services et la prise en charge d’API évolutives.

## <a name="additional-resources"></a>Ressources supplémentaires

- **Scott Hanselman. ASP.NET version WEB API RESTful de base facilitée** \
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- **Version d’une API Web RESTful** \
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- **Roy Fielding. Version, Hypermedia, et REST** \
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

>[!div class="step-by-step"]
>[Suivant précédent](asynchronous-message-based-communication.md)
>[Next](microservices-addressability-service-registry.md)
