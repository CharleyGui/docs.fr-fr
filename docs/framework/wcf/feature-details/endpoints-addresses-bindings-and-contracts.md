---
title: 'Points de terminaison : adresses, liaisons et contrats'
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: 3ac7f0b165b99a1ed3702628958f7d4c7702f5b1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593514"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a>Points de terminaison : adresses, liaisons et contrats

Toutes les communications avec un service Windows Communication Foundation (WCF) se produisent via les *points de terminaison* du service. Les points de terminaison fournissent aux clients l’accès aux fonctionnalités offertes par un service WCF.

Chaque point de terminaison se compose de quatre propriétés :

- Une adresse qui indique où rechercher le point de terminaison.

- Une liaison qui spécifie comment un client peut communiquer avec le point de terminaison.

- Un contrat qui identifie les opérations disponibles.

- L'ensemble des comportements qui spécifient les détails d'implémentation locaux du point de terminaison.

Cette rubrique traite de cette structure de point de terminaison et explique comment elle est représentée dans le modèle d’objet WCF.

## <a name="the-structure-of-an-endpoint"></a>Structure d'un point de terminaison

Chaque point de terminaison comprend les éléments suivants :

- Adresse : l'adresse identifie le point de terminaison de manière unique et indique aux consommateurs potentiels l'emplacement du service. Elle est représentée dans le modèle d’objet WCF par la <xref:System.ServiceModel.EndpointAddress> classe. Une classe <xref:System.ServiceModel.EndpointAddress> contient :

  - Une propriété <xref:System.ServiceModel.EndpointAddress.Uri%2A>, qui représente l'adresse du service.

  - Une propriété <xref:System.ServiceModel.EndpointAddress.Identity%2A> qui représente l’identité de sécurité du service et une collection d’en-tête de message facultatifs. Les en-têtes de message facultatifs sont utilisés pour fournir des informations d'adressage supplémentaires et plus détaillées afin d'identifier le point de terminaison ou d'interagir avec lui.

  Pour plus d’informations, consultez [spécification d’une adresse de point de terminaison](../specifying-an-endpoint-address.md).

- Liaison : la liaison spécifie le mode de communication avec le point de terminaison. notamment :

  - Le protocole de transport à utiliser (par exemple, TCP ou HTTP).

  - L'encodage à utiliser pour les messages (par exemple, texte ou binaire).

  - Les exigences de sécurité nécessaires (par exemple, SSL ou la sécurité des messages SOAP).

  Pour plus d’informations, consultez [vue d’ensemble des liaisons WCF](../bindings-overview.md). Une liaison est représentée dans le modèle objet WCF par la classe de base abstraite <xref:System.ServiceModel.Channels.Binding> . Pour la plupart des scénarios, les utilisateurs peuvent utiliser l'une des liaisons fournies par le système. Pour plus d’informations, consultez [liaisons fournies par le système](../system-provided-bindings.md).

- Contrats : le contrat de service définit les fonctionnalités que le point de terminaison expose au client. Un contrat spécifie :

  - Quelles opérations peuvent être appelées par un client.

  - Le format du message.

  - Le type de paramètres d'entrée ou les données requis pour appeler l'opération.

  - Le type de traitement ou le message de réponse que le client peut attendre.

  Pour plus d’informations sur la définition d’un contrat, consultez [conception de contrats de service](../designing-service-contracts.md).

- Comportements : vous pouvez utiliser des comportements de point de terminaison pour personnaliser le comportement local du point de terminaison du service. Pour y parvenir, les comportements de point de terminaison participent au processus de création d’un Runtime WCF. Un exemple de comportement de point de terminaison est la propriété <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> qui vous permet de spécifier une adresse d'écoute différente de l'adresse SOAP ou WSDL (Web Services Description Language). Pour plus d’informations, consultez [ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md).

## <a name="defining-endpoints"></a>Définition des points de terminaison

L'adresse du point de terminaison pour un service peut être spécifiée de manière impérative en utilisant le code ou de façon déclarative par la configuration. Pour plus d’informations, consultez [Comment : créer un point de terminaison de service dans la configuration](how-to-create-a-service-endpoint-in-configuration.md) et [Comment : créer un point de terminaison de service dans le code](how-to-create-a-service-endpoint-in-code.md).

## <a name="in-this-section"></a>Dans cette section

Cette section explique à quoi servent les liaisons, les points de terminaison et les adresses, indique comment configurer une liaison et un point de terminaison et montre comment utiliser le comportement `ClientVia` et la propriété `ListenUri`.

[Résoudre](endpoint-addresses.md)\
Décrit comment les points de terminaison sont traités dans WCF.

[Liaisons](bindings.md)\
Décrit comment les liaisons sont utilisées pour spécifier le transport, l’encodage et les détails de protocole requis pour que les clients et les services puissent communiquer l’un l’autre.

[Contrats](contracts.md)\
Décrit comment les contrats définissent les méthodes d'un service.

[Comment : créer un point de terminaison de service dans la configuration](how-to-create-a-service-endpoint-in-configuration.md)\
Décrit comment créer un point de terminaison de service dans la configuration.

[Comment : créer un point de terminaison de service dans le code](how-to-create-a-service-endpoint-in-code.md)\
Décrit comment créer un point de terminaison de service dans le code.

[Comment : utiliser Svcutil. exe pour valider le code de service compilé](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)\
Décrit comment détecter les erreurs dans les implémentations et les configurations de service sans héberger le service à l’aide de l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).

## <a name="see-also"></a>Voir aussi

- [Configuration des services](../configuring-services.md)
- [Extension de liaisons](../extending/extending-bindings.md)
