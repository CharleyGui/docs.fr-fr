---
title: Contrats
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], contracts
- contracts [WCF]
- Windows Communication Foundation [WCF], contracts
ms.assetid: c8364183-4ac1-480b-804a-c5e6c59a5d7d
ms.openlocfilehash: 1cd7e54d50e7116c71c040df1965674a4fdaff13
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595594"
---
# <a name="contracts"></a>Contrats
Cette section vous montre comment définir et implémenter des contrats Windows Communication Foundation (WCF). Un contrat de service spécifie ce qu'un point de terminaison communique au monde extérieur. À un niveau plus concret, il s'agit d'une instruction à propos d'un ensemble de messages spécifiques organisé en modèles d'échange de messages de base, tels que les messages demande/réponse, unidirectionnels et duplex. Si un contrat de service est un ensemble d'échanges de messages liés de manière logique, une opération de service est un échange de messages unique. Par exemple, une opération `Hello` doit évidemment accepter un message (de sorte que l'appelant puisse annoncer la salutation) et peut ou non retourner un message (en fonction du niveau de courtoisie de l'opération).  
  
 Pour plus d’informations sur les contrats et les autres concepts principaux de WCF, consultez [concepts fondamentaux du Windows Communication Foundation](../fundamental-concepts.md). Cette rubrique est consacrée au fonctionnement des contrats de service. Pour plus d’informations sur la façon de créer des clients qui utilisent des contrats de service pour se connecter à des services, consultez [vue d’ensemble du client WCF](../wcf-client-overview.md). Pour plus d’informations sur les canaux clients, l’architecture client et les autres problèmes liés aux clients, consultez [clients](clients.md).  
  
## <a name="overview"></a>Vue d’ensemble  
 Cette rubrique fournit une orientation conceptuelle de haut niveau pour la conception et l’implémentation des services WCF. Les sous-rubriques fournissent des informations plus détaillées sur les aspects spécifiques à la conception et à l'implémentation. Avant de concevoir et d’implémenter votre application WCF, il est recommandé d’exécuter les tâches suivantes :  
  
- comprendre ce qu'est un contrat de service, comment il fonctionne et comment en créer un ;  
  
- comprendre que les contrats définissent des exigences minimales que la configuration à l’exécution ou l’environnement d’hébergement peuvent ne pas prendre en charge.  
  
## <a name="service-contracts"></a>Contrats de service  
 Un contrat de service est une instruction qui fournit des informations sur :  
  
- le groupement d'opérations dans un service ;  
  
- la signature des opérations en termes de messages échangés ;  
  
- les types de données de ces messages ;  
  
- l'emplacement des opérations ;  
  
- les protocoles et formats de sérialisation spécifiques utilisés pour prendre en charge la communication avec le service.  
  
 Par exemple, un contrat de commande fournisseur peut avoir une opération `CreateOrder` qui accepte une entrée de types d'informations de commande et retourne des information de succès ou d'échec, y compris un identificateur de commande. Il peut également avoir une opération `GetOrderStatus` qui accepte un identificateur de commande et retourne des informations d'état de commande. Un tel contrat de service spécifie alors :  
  
- que le contrat de commande fournisseur serait composé d'opérations `CreateOrder` et `GetOrderStatus` ;  
  
- que les opérations auraient des messages d'entrée et des messages de sortie spécifiés ;  
  
- les données que ces messages pourraient transporter ;  
  
- des instructions catégoriques à propos de l'infrastructure de communication nécessaire pour traiter les messages avec succès. Par exemple, ces détails incluent les éventuelles formes de sécurité requises pour établir la communication.  
  
 Pour communiquer ce type d’informations aux applications sur d’autres plateformes (y compris les plateformes non-Microsoft), les contrats de service XML sont exprimés publiquement dans des formats XML standard, tels que [Web Services Description Language (WSDL)](https://www.w3.org/TR/2001/NOTE-wsdl-20010315) et [XML Schema (XSD)](https://www.w3.org/XML/Schema), entre autres. Les développeurs qui travaillent avec un grand nombre de plateformes différentes peuvent utiliser ces informations de contrat publiques pour créer des applications capables de communiquer avec le service, ces applications comprenant le langage des spécifications, d'une part, et ce langage assurant l'interopérabilité grâce à sa description de formes, formats et protocoles publics pris en charge par ce service, d'autre part. Pour plus d’informations sur la façon dont WCF gère ce type d’informations, consultez [métadonnées](metadata.md).  
  
 Les contrats peuvent toutefois être exprimés de nombreuses manières, et bien que WSDL et XSD constituent d'excellents langages pour décrire des services d'une manière accessible, ce sont des langages difficiles à utiliser directement ; en tous les cas, ils constituent simplement des descriptions d'un service, et non des implémentations de contrat de service. Par conséquent, les applications WCF utilisent des attributs, des interfaces et des classes managés pour définir la structure de et pour implémenter un service.  
  
 Le contrat résultant défini dans les types managés peut être converti (également appelé *exporté*) en tant que métadonnées (WSDL et XSD) quand cela est nécessaire pour les clients ou d’autres implémenteurs de service, en particulier sur d’autres plateformes. Le résultat est un modèle de programmation simple qui peut être décrit à l'aide de métadonnées publiques à toute application cliente. Les détails des messages SOAP sous-jacents, tels que les informations relatives au transport et à la sécurité, peuvent être laissés à WCF, ce qui effectue automatiquement les conversions nécessaires vers et depuis le système de type de contrat de service vers le système de type XML.  
  
 Pour plus d’informations sur la conception de contrats, consultez [conception de contrats de service](../designing-service-contracts.md). Pour plus d’informations sur l’implémentation de contrats, consultez [implémentation de contrats de service](../implementing-service-contracts.md).  
  
 En outre, WCF offre également la possibilité de développer entièrement des contrats de service au niveau du message. Pour plus d’informations sur le développement de contrats de service au niveau du message, consultez [utilisation de contrats de message](using-message-contracts.md). Pour plus d’informations sur le développement de services en XML non-SOAP, consultez [interopérabilité avec les applications POX](interoperability-with-pox-applications.md).  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>Présentation de la hiérarchie des exigences  
 Un contrat de service groupe les opérations, spécifie les modèles d'échange de messages, les types de messages et les types de données que ces messages transportent, et indique les catégories de comportement à l'exécution qu'une implémentation doit avoir pour prendre en charge le contrat (par exemple, il peut exiger que les messages soient chiffrés et signés). Toutefois, le contrat de service lui-même ne spécifie pas précisément comment ces exigences sont satisfaites, mais uniquement qu’elles doivent l’être. Le type de chiffrement utilisé ou la façon dont un message est signé incombe à l'implémentation et à la configuration d'un service conforme.  
  
 Remarquez la façon dont le contrat requiert certaines choses de l'implémentation de contrat de service et de la configuration à l'exécution pour ajouter un comportement. L’ensemble d’exigences qui doivent être satisfaites pour exposer un service pour une utilisation repose sur l’ensemble d’exigences précédent. Si un contrat spécifie des exigences concernant l'implémentation, une implémentation peut requérir une plus grande partie de la configuration et des liaisons qui autorisent l'exécution du service. Pour finir, l’application hôte doit également prendre en charge les exigences ajoutées par la configuration du service et les liaisons.  
  
 Ce processus d’exigence supplémentaire est important à garder à l’esprit lors de la conception, de l’implémentation, de la configuration et de l’hébergement de votre application de service Windows Communication Foundation (WCF). Par exemple, le contrat peut spécifier qu'il doit prendre en charge une session. Dans ce cas, vous devez configurer la liaison de façon à prendre en charge cette spécification contractuelle, sinon l’implémentation de service ne fonctionnera pas. Si votre service requiert l'authentification intégrée de Windows et qu'il est hébergé par les services IIS, l'option Authentification intégrée de Windows de l'application Web dans laquelle se trouve le service doit être activée et l'option de prise en charge anonyme doit être désactivée. Pour plus d’informations sur les fonctionnalités et l’impact des différents types d’application hôte de service, consultez [hébergement](hosting.md).  
  
## <a name="see-also"></a>Voir aussi

- [Points de terminaison : adresses, liaisons et contrats](endpoints-addresses-bindings-and-contracts.md)
- [Conception de contrats de service](../designing-service-contracts.md)
- [Implémentation de contrats de service](../implementing-service-contracts.md)
