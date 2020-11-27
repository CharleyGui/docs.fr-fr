---
title: Liaisons et éléments de liaison
ms.date: 03/30/2017
helpviewer_keywords:
- binding elements [WCF]
ms.assetid: 765ff77b-7682-4ea3-90eb-e4d751e37379
ms.openlocfilehash: 16e1b7840be6a3ec247033fa3a2eada9e5799bdb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262136"
---
# <a name="bindings-and-binding-elements"></a>Liaisons et éléments de liaison

Les liaisons sont des collections d’éléments de configuration spéciaux, appelés *éléments de liaison*, qui sont évalués par le runtime de service chaque fois qu’un client ou point de terminaison de service est construit. Le type et l'ordre des éléments de liaison dans une liaison déterminent la sélection et l'ordre d'empilement des protocoles et des canaux de transport dans la pile de canaux d'un point de terminaison.  
  
 Les liaisons, surtout les liaisons fournies par le système, possèdent en général plusieurs propriétés de configuration qui reflètent les propriétés le plus couramment modifiées des éléments de liaison encapsulés.  
  
 Une liaison doit contenir exactement un élément de liaison de transport. Chaque élément de liaison de transport implique un élément de liaison d’encodage de message par défaut, qui peut être substitué en ajoutant au plus un élément de liaison d’encodage de message à la liaison. En plus des éléments de liaison de transport et d’encodeur, la liaison peut contenir un nombre quelconque d’éléments de liaison de protocole qui, ensemble, implémentent la fonctionnalité nécessaire pour servir et envoyer un message SOAP d’un point de terminaison à un autre. Pour plus d’informations, consultez [utilisation de liaisons pour configurer des services et des clients](../using-bindings-to-configure-services-and-clients.md).  
  
## <a name="extending-bindings-and-binding-elements"></a>Extension de liaisons et d’éléments de liaisons  

 Windows Communication Foundation (WCF) comprend des liaisons fournies par le système qui couvrent un large éventail de scénarios. (Pour plus d’informations, consultez [liaisons fournies par le système](../system-provided-bindings.md).) Toutefois, il peut arriver que vous deviez créer et utiliser une liaison qui n’est pas incluse dans WCF. Les scénarios suivants requièrent la création d’une nouvelle liaison.  
  
- Pour utiliser un nouvel élément de liaison (tel qu'un nouvel élément de liaison de transport, d'encodage ou de protocole), vous devez créer une nouvelle liaison qui inclut cet élément de liaison. Par exemple, si vous avez ajouté un `UdpTransportBindingElement` personnalisé pour le transport UDP, vous devez créer une liaison pour l’utiliser. Pour plus d’informations sur l’exécution de ce comportement à l’aide du <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> type, consultez [liaisons personnalisées](custom-bindings.md).  
  
- Pour configurer des éléments de liaison existantes de sorte que les liaisons fournies par le système ne soient pas exposées sur les propriétés publiques. Par exemple, vous devez créer une liaison pour modifier l'ordre dans lequel les opérations de signature et de chiffrement sont exécutées. Pour plus d’informations sur l’exécution de ce comportement, consultez [How to : Customize a System-Provided Binding](how-to-customize-a-system-provided-binding.md).  
  
- Pour établir des liaisons d’entreprise standard qui exposent uniquement des options de configuration spécifiques. Par exemple, pour créer pour votre société une variante du <xref:System.ServiceModel.WSHttpBinding> dans laquelle la sécurité ne peut pas être désactivée, créez une nouvelle liaison qui se comporte comme le <xref:System.ServiceModel.WSHttpBinding>, mais avec la sécurité toujours activée. Pour plus d’informations, consultez [création de liaisons de User-Defined](creating-user-defined-bindings.md).  
  
- Pour effectuer une personnalisation des métadonnées, en général (mais pas nécessairement) pour configurer ou utiliser un élément de liaison personnalisé. Pour plus d’informations sur la prise en charge des métadonnées pour les liaisons et les éléments de liaison, consultez [prise en charge de la configuration et des métadonnées](configuration-and-metadata-support.md).  

## <a name="channels-bindings-and-binding-elements"></a>Canaux, liaisons et éléments de liaison  

 Les liaisons et éléments de liaison sont la connexion entre le modèle de programmation d'applications, qui inclut les attributs et comportements, et le modèle de canal, qui inclut les fabrications et écouteurs, les encodeurs de message et les implémentations de transport et de protocole. En général, les éléments de liaison et les liaisons sont implémentés pour permettre aux canaux d'être utilisés par la couche Application.  
  
 La couche de canal fournit ou reçoit des messages vers ou en provenance de la couche de service et transporte ces messages entre des points de terminaison. Sur un client, la couche de canal est une pile de fabrications de canaux qui créent des canaux à un point de terminaison réseau. Sur un service, la couche de canal est une pile d'écouteurs de canal qui acceptent les canaux reçus à un point de terminaison réseau.  
  
 Il existe deux types généraux de canaux : les canaux de protocole et les canaux de transport. Les canaux de transport sont responsables de la transmission d'un message d'un point de terminaison réseau à un autre. Les canaux de transport doivent avoir un encodeur de message par défaut et doivent être capables d’utiliser un autre encodeur de message fourni par le biais d’un élément de liaison d’encodeur de message. Un encodeur de message est chargé de la conversion d'un <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> en une représentation sur le câble, et inversement. Les canaux de protocole sont chargés d'implémenter des protocoles de niveau SOAP (par exemple, WS-Security ou WS-ReliableMessaging).  
  
 La principale condition relative aux canaux de protocole et de transport concerne leur implémentation des interfaces de canal requises. Pour créer une couche de canal active, ils doivent avoir des fabrications et des écouteurs associés, et ainsi de suite. Pour utiliser les implémentations de canal de WCF, il doit y avoir un élément de liaison associé dérivé de <xref:System.ServiceModel.Channels.BindingElement> pour chaque canal et il doit y avoir un élément d’extension de liaison connexe pour l’inclusion dans des fichiers de configuration qui dérivent de <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> .  
  
 Comme mentionné précédemment, les éléments de liaison pour les implémentations de canal de transport, d'encodeurs de message et de protocole peuvent être empilés pour former une pile de canaux et le mécanisme permettant de les aligner dans un ensemble ordonné est la liaison. Les liaisons et les éléments de liaison connectent le modèle de programmation d'applications au modèle de canal. Vous pouvez utiliser vos implémentations de canal directement à partir du code, mais à moins que les encodeurs, les transports et les protocoles ne soient implémentés comme éléments de liaison, ils ne peuvent pas être utilisés à partir du modèle de programmation de couche de service.  
  
 Pour plus d’informations sur le développement de canaux et leurs éléments de liaison, consultez [extension de la couche de canal](extending-the-channel-layer.md).
