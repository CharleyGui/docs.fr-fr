---
title: Détails relatifs à l'implémentation du protocole WCF Data Services
ms.date: 03/30/2017
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
ms.openlocfilehash: a9b996671f2d8b57593f80fb13e966c5f03a2801
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190388"
---
# <a name="wcf-data-services-protocol-implementation-details"></a>Détails relatifs à l'implémentation du protocole WCF Data Services

## <a name="odata-protocol-implementation-details"></a>Détails de l'implémentation du protocole OData  

Le Open Data Protocol (OData) requiert qu’un service de données qui implémente le protocole fournisse un ensemble minimal de fonctionnalités. Ces fonctionnalités sont décrites dans les documents de protocole en termes de « doit » et « doit ». D’autres fonctionnalités facultatives sont décrites en termes de « mai ». Cet article décrit ces fonctionnalités facultatives qui ne sont pas implémentées actuellement par WCF Data Services.
  
### <a name="support-for-the-format-query-option"></a>Prise en charge de l'option de requête $format  

 Le protocole OData prend en charge les flux de notation JavaScript (JSON) et Atom, et OData fournit l' `$format` option de requête système pour permettre à un client de demander le format du flux de réponse. Cette option de requête du système (si prise en charge par le service de données) doit substituer la valeur de l'en-tête Accept de la requête. WCF Data Services prend en charge le retour des flux JSON et Atom. Toutefois, l'implémentation par défaut ne prend pas en charge l'option de requête `$format` et utilise uniquement la valeur de l'en-tête Accept pour déterminer le format de la réponse. Il y a des cas où votre service de données doit prendre en charge l'option de requête `$format`, par exemple lorsque les clients ne peuvent pas définir l'en-tête Accept. Pour prendre en charge ces scénarios, vous devez étendre votre service de données pour gérer cette option dans l'URI.
  
## <a name="wcf-data-services-behaviors"></a>Comportements des services de données WCF  

 Les comportements de WCF Data Services suivants ne sont pas définis explicitement par le protocole OData :  
  
### <a name="default-sorting-behavior"></a>Comportement de tri par défaut  

 Lorsqu'une demande de requête envoyée au service de données inclut une option de requête système `$top` ou `$skip` et n'inclut pas d'option de requête système `$orderby`, le flux retourné est trié par les propriétés de clé, dans l'ordre croissant. Cela est dû au fait que le dimensionnement est requis pour garantir la pagination correcte des résultats. Pour cela, le service de données ajoute une expression de classement à la requête. Ce comportement se produit également lorsque la pagination orientée serveur est vérifiée dans le service de données. Pour plus d’informations, consultez [configuration du service de données](configuring-the-data-service-wcf-data-services.md). Pour contrôler l’ordre du flux retourné, vous devez inclure `$orderby` dans l’URI de la requête.  
  
## <a name="see-also"></a>Voir aussi

- [Définition des services de données WCF](defining-wcf-data-services.md)
- [Bibliothèque client services de données WCF](wcf-data-services-client-library.md)
