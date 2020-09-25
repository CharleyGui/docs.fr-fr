---
title: Détails relatifs à l'implémentation du protocole WCF Data Services
ms.date: 03/30/2017
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
ms.openlocfilehash: 0723d5a473bb87b8bd464a944a5c68f1a8d3f5da
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202160"
---
# <a name="wcf-data-services-protocol-implementation-details"></a>Détails relatifs à l'implémentation du protocole WCF Data Services

## <a name="odata-protocol-implementation-details"></a>Détails de l'implémentation du protocole OData  

Le Open Data Protocol (OData) requiert qu’un service de données qui implémente le protocole fournisse un ensemble minimal de fonctionnalités. Ces fonctionnalités sont décrites dans les documents de protocole en termes de « doit » et « doit ». D’autres fonctionnalités facultatives sont décrites en termes de « mai ». Cet article décrit ces fonctionnalités facultatives qui ne sont pas implémentées actuellement par WCF Data Services.
  
### <a name="support-for-the-format-query-option"></a>Prise en charge de l'option de requête $format  

 Le protocole OData prend en charge les flux de notation JavaScript (JSON) et Atom, et OData fournit l' `$format` option de requête système pour permettre à un client de demander le format du flux de réponse. Cette option de requête du système (si prise en charge par le service de données) doit substituer la valeur de l'en-tête Accept de la requête. WCF Data Services prend en charge le retour des flux JSON et Atom. Toutefois, l'implémentation par défaut ne prend pas en charge l'option de requête `$format` et utilise uniquement la valeur de l'en-tête Accept pour déterminer le format de la réponse. Il y a des cas où votre service de données doit prendre en charge l'option de requête `$format`, par exemple lorsque les clients ne peuvent pas définir l'en-tête Accept. Pour prendre en charge ces scénarios, vous devez étendre votre service de données pour gérer cette option dans l'URI. Vous pouvez ajouter cette fonctionnalité à votre service de données en [téléchargeant la prise en charge de JSONP et de format contrôlé par URL pour ADO.NET Data Services](https://go.microsoft.com/fwlink/?LinkId=208228) exemple de projet à partir du site Web MSDN Code Gallery et en l’ajoutant à votre projet de service de données. Cet exemple supprime l'option de requête `$format` et remplace l'en-tête Accept par `application/json`. Lorsque vous incluez l'exemple de projet et ajoutez `JSONPSupportBehaviorAttribute` à votre classe de service de données, le service peut gérer l'option de requête `$format``$format=json`. Une personnalisation plus poussée de cet exemple de projet est requise pour gérer également `$format=atom` ou d'autres formats personnalisés.  
  
## <a name="wcf-data-services-behaviors"></a>Comportements des services de données WCF  

 Les comportements de WCF Data Services suivants ne sont pas définis explicitement par le protocole OData :  
  
### <a name="default-sorting-behavior"></a>Comportement de tri par défaut  

 Lorsqu'une demande de requête envoyée au service de données inclut une option de requête système `$top` ou `$skip` et n'inclut pas d'option de requête système `$orderby`, le flux retourné est trié par les propriétés de clé, dans l'ordre croissant. Cela est dû au fait que le dimensionnement est requis pour garantir la pagination correcte des résultats. Pour cela, le service de données ajoute une expression de classement à la requête. Ce comportement se produit également lorsque la pagination orientée serveur est vérifiée dans le service de données. Pour plus d’informations, consultez [configuration du service de données](configuring-the-data-service-wcf-data-services.md). Pour contrôler l’ordre du flux retourné, vous devez inclure `$orderby` dans l’URI de la requête.  
  
## <a name="see-also"></a>Voir aussi

- [Définition des services de données WCF](defining-wcf-data-services.md)
- [Bibliothèque client services de données WCF](wcf-data-services-client-library.md)
