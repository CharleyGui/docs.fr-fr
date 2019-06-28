---
title: 'Points de terminaison : Adresses, liaisons et contrats'
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: d224535bb266d0a3673359388c6c211103df7374
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424848"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a>Points de terminaison : Adresses, liaisons et contrats
Toutes les communications avec un service Windows Communication Foundation (WCF) s’effectue via le *points de terminaison* du service. Points de terminaison fournissent les clients l’accès à la fonctionnalité offerte par un service WCF.  
  
 Chaque point de terminaison se compose de quatre propriétés :  
  
- Une adresse qui indique où rechercher le point de terminaison.  
  
- Une liaison qui spécifie comment un client peut communiquer avec le point de terminaison.  
  
- Un contrat qui identifie les opérations disponibles.  
  
- L'ensemble des comportements qui spécifient les détails d'implémentation locaux du point de terminaison.  
  
 Cette rubrique traite de cette structure de point de terminaison et explique comment elle est représentée dans le modèle d’objet WCF.  
  
## <a name="the-structure-of-an-endpoint"></a>Structure d'un point de terminaison  
 Chaque point de terminaison comprend les éléments suivants :  
  
- Adresse : L’adresse identifie le point de terminaison et indique le potentiel de manière unique les consommateurs du service dans lequel il se trouve. Elle est représentée dans le modèle d’objet WCF par le <xref:System.ServiceModel.EndpointAddress> classe. Une classe <xref:System.ServiceModel.EndpointAddress> contient :  
  
    - Une propriété <xref:System.ServiceModel.EndpointAddress.Uri%2A>, qui représente l'adresse du service.  
  
    - Une propriété <xref:System.ServiceModel.EndpointAddress.Identity%2A> qui représente l’identité de sécurité du service et une collection d’en-tête de message facultatifs. Les en-têtes de message facultatifs sont utilisés pour fournir des informations d'adressage supplémentaires et plus détaillées afin d'identifier le point de terminaison ou d'interagir avec lui.  
  
     Pour plus d’informations, consultez [spécification d’une adresse de point de terminaison](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
- Liaison : La liaison spécifie le mode de communication avec le point de terminaison. Cela concerne :  
  
    - Le protocole de transport à utiliser (par exemple, TCP ou HTTP).  
  
    - L'encodage à utiliser pour les messages (par exemple, texte ou binaire).  
  
    - Les exigences de sécurité nécessaires (par exemple, SSL ou la sécurité des messages SOAP).  
  
     Pour plus d’informations, consultez [vue d’ensemble des liaisons WCF](../../../../docs/framework/wcf/bindings-overview.md). Une liaison est représentée dans le modèle objet WCF par la classe de base abstraite <xref:System.ServiceModel.Channels.Binding>. Pour la plupart des scénarios, les utilisateurs peuvent utiliser l'une des liaisons fournies par le système. Pour plus d’informations, consultez [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
- Contrats : Le contrat définit les fonctionnalités que le point de terminaison expose au client. Un contrat spécifie :  
  
    - Quelles opérations peuvent être appelées par un client.  
  
    - Le format du message.  
  
    - Le type de paramètres d'entrée ou les données requis pour appeler l'opération.  
  
    - Le type de traitement ou le message de réponse que le client peut attendre.  
  
     Pour plus d’informations sur la définition d’un contrat, consultez [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
- Comportements : Vous pouvez utiliser des comportements de point de terminaison pour personnaliser le comportement du point de terminaison de service local. Pour cela, les comportements de point de terminaison participant au processus de création d’un service d’exécution WCF. Un exemple de comportement de point de terminaison est la propriété <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> qui vous permet de spécifier une adresse d'écoute différente de l'adresse SOAP ou WSDL (Web Services Description Language). Pour plus d’informations, consultez [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).  
  
## <a name="defining-endpoints"></a>Définition des points de terminaison  
 L'adresse du point de terminaison pour un service peut être spécifiée de manière impérative en utilisant le code ou de façon déclarative par la configuration. Pour plus d'informations, voir [Procédure : Créer un point de terminaison de Service dans la Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) et [Comment : Créer un point de terminaison de Service dans le Code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 Cette section explique à quoi servent les liaisons, les points de terminaison et les adresses, indique comment configurer une liaison et un point de terminaison et montre comment utiliser le comportement `ClientVia` et la propriété `ListenUri`.  
  
 [Adresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 Décrit la façon dont les points de terminaison sont adressés dans WCF.  
  
 [Liaisons](../../../../docs/framework/wcf/feature-details/bindings.md)  
 Décrit comment les liaisons sont utilisées pour spécifier le transport, l’encodage et les détails de protocole requis pour que les clients et les services puissent communiquer l’un l’autre.  
  
 [Contrats](../../../../docs/framework/wcf/feature-details/contracts.md)  
 Décrit comment les contrats définissent les méthodes d'un service.  
  
 [Guide pratique pour Créer un point de terminaison de Service dans la Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 Décrit comment créer un point de terminaison de service dans la configuration.  
  
 [Guide pratique pour Créer un point de terminaison de Service dans le Code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 Décrit comment créer un point de terminaison de service dans le code.  
  
 [Guide pratique pour Utiliser Svcutil.exe pour valider le Code de Service compilé](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 Décrit comment détecter les erreurs dans les configurations et les implémentations de service sans héberger le service en utilisant le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="see-also"></a>Voir aussi

- [Configuration des services](../../../../docs/framework/wcf/configuring-services.md)
- [Extension de liaisons](../../../../docs/framework/wcf/extending/extending-bindings.md)
