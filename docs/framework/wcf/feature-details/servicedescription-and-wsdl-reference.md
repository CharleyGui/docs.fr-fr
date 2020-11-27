---
title: Référence pour ServiceDescription et WSDL
ms.date: 03/30/2017
ms.assetid: eedc025d-abd9-46b1-bf3b-61d2d5c95fd6
ms.openlocfilehash: 11a5d65026d13db56d1d349c130861094c3e123b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253880"
---
# <a name="servicedescription-and-wsdl-reference"></a>Référence pour ServiceDescription et WSDL

Cette rubrique décrit comment Windows Communication Foundation (WCF) mappe des documents Web Services Description Language (WSDL) à et à partir d' <xref:System.ServiceModel.Description.ServiceDescription> instances.  
  
## <a name="how-servicedescription-maps-to-wsdl-11"></a>Comment ServiceDescription mappe à WSDL 1.1  

 Vous pouvez utiliser WCF pour exporter des documents WSDL à partir d’une <xref:System.ServiceModel.Description.ServiceDescription> instance de pour votre service. Des documents WSDL sont automatiquement générés pour votre service lorsque vous publiez des points de terminaison de métadonnées.  
  
 Vous pouvez également importer des instances <xref:System.ServiceModel.Description.ServiceEndpoint>, des instances <xref:System.ServiceModel.Description.ContractDescription> et des instances <xref:System.ServiceModel.Channels.Binding> à partir de documents WSDL en utilisant le type `WsdlImporter`.  
  
 Les documents WSDL, exportés par WCF, importent les définitions de schéma XML utilisées à partir de documents de schéma XML externes. Un document de schéma XML distinct est exporté pour chaque espace de noms cible utilisé par les types de données dans le service. De même, un document WSDL distinct est exporté pour chaque espace de noms cible utilisé par les contrats de service.  
  
### <a name="servicedescription"></a>ServiceDescription  

 Une instance <xref:System.ServiceModel.Description.ServiceDescription> correspond à un élément `wsdl:service`. Une instance <xref:System.ServiceModel.Description.ServiceDescription> contient une collection d’instances <xref:System.ServiceModel.Description.ServiceEndpoint> qui correspondent chacune à des éléments `wsdl:port` individuels.  
  
|Propriétés|Mappage WSDL|  
|----------------|------------------|  
|`Name`|`wsdl:service` /@name Valeur du service.|  
|`Namespace`|TargetNamespace de la définition `wsdl:service` du service.|  
|`Endpoints`|Définitions `wsdl:port` du service.|  
  
### <a name="serviceendpoint"></a>ServiceEndpoint  

 Une instance <xref:System.ServiceModel.Description.ServiceEndpoint> correspond à un élément `wsdl:port`. Une instance <xref:System.ServiceModel.Description.ServiceEndpoint> contient une adresse, une liaison et un contrat.  
  
 Les comportements de point de terminaison qui implémentent l'interface <xref:System.ServiceModel.Description.IWsdlExportExtension> peuvent modifier l'élément `wsdl:port` du point de terminaison auquel ils sont attachés.  
  
|Propriétés|Mappage WSDL|  
|----------------|------------------|  
|`Name`|La `wsdl:port` /@name valeur du point de terminaison et la `wsdl:binding` /@name valeur de la liaison de point de terminaison.|  
|`Address`|Adresse de la définition `wsdl:port` du point de terminaison.<br /><br /> Le transport du point de terminaison détermine le format de l'adresse. Par exemple, pour les transports pris en charge par WCF, il peut s’agir d’une adresse SOAP ou d’une référence de point de terminaison.|  
|`Binding`|Définition `wsdl:binding` du point de terminaison.<br /><br /> Contrairement aux `wsdl:binding` définitions, les liaisons dans WCF ne sont pas liées à un contrat.|  
|`Contract`|Définition `wsdl:portType` du point de terminaison.|  
|`Behaviors`|Les comportements de point de terminaison qui implémentent l'interface <xref:System.ServiceModel.Description.IWsdlExportExtension> peuvent modifier l'élément `wsdl:port` du point de terminaison.|  
  
### <a name="bindings"></a>Liaisons  

 L'instance de liaison d'une instance `ServiceEndpoint` correspond à une définition `wsdl:binding`. Contrairement aux `wsdl:binding` définitions, qui doivent être associées à une `wsdl:portType` définition spécifique, les liaisons WCF sont indépendantes des contrats.  
  
 Une liaison est composée d’une collection d’éléments de liaison. Chaque élément décrit un aspect de la façon dont le point de terminaison communique avec les clients. En outre, une liaison a un <xref:System.ServiceModel.Channels.MessageVersion> qui indique le <xref:System.ServiceModel.EnvelopeVersion> et le <xref:System.ServiceModel.Channels.AddressingVersion> du point de terminaison.  
  
|Propriétés|Mappage WSDL|  
|----------------|------------------|  
|`Name`|Utilisé dans le nom par défaut d'un point de terminaison, qui est le nom de liaison auquel est ajouté le nom du contrat séparé par un trait de soulignement.|  
|`Namespace`|`targetNamespace` de la définition `wsdl:binding`.<br /><br /> Lors de l’importation, si une stratégie est jointe au port WSDL, l’espace de noms de liaison importé correspond à l’`targetNamespace` de la définition `wsdl:port`.|  
|`BindingElementCollection`, telle que retournée par la méthode `CreateBindingElements`()|Différentes extensions propres au domaine de la définition `wsdl:binding`, généralement des assertions de stratégie.|  
|`MessageVersion`|`EnvelopeVersion` et `AddressingVersion` du point de terminaison.<br /><br /> Lorsque `MessageVersion.None` est spécifié, la liaison WSDL ne contient pas de liaison SOAP et le port WSDL n'a pas de contenu WS-Addressing. Ce paramètre est généralement utilisé pour les points de terminaison POX (Plain Old XML).|  
  
#### <a name="bindingelements"></a>BindingElement  

 Les éléments de liaison d'un point de terminaison de liaison correspondent à différentes extensions WSDL dans la définition `wsdl:binding`, comme des assertions de stratégie.  
  
 Le <xref:System.ServiceModel.Channels.TransportBindingElement> de la liaison détermine l’URI (Uniform Resource Identifier) de transport d’une liaison SOAP.  
  
#### <a name="addressingversion"></a>AddressingVersion  

 `AddressingVersion` d'une liaison correspond à la version d'adressage utilisée dans la définition `wsd:port`. WCF prend en charge les adresses SOAP 1,1 et SOAP 1,2, ainsi que les références de point de terminaison WS-Addressing 08/2004 et WS-Addressing 1,0.  
  
#### <a name="envelopeversion"></a>EnvelopeVersion  

 `EnvelopeVersion` d'une liaison correspond à la version de SOAP utilisée dans la définition `wsdl:binding`. WCF prend en charge les liaisons SOAP 1,1 et SOAP 1,2.  
  
### <a name="contracts"></a>Contrats  

 L'instance <xref:System.ServiceModel.Description.ContractDescription> d'une instance `ServiceEndpoint` correspond à un `wsdl:portType`. Une instance `ContractDescription` décrit toutes les opérations d'un contrat donné.  
  
|Propriétés|Mappage WSDL|  
|----------------|------------------|  
|`Name`|`wsdl:portType` /@name Valeur du contrat.|  
|`Namespace`|TargetNamespace de la définition `wsdl:portType`.|  
|`SessionMode`|`wsdl:portType` /@msc:usingSession Valeur du contrat. Cet attribut est une extension WCF pour WSDL 1,1.|  
|`Operations`|Définitions `wsdl:operation` du contrat.|  
  
### <a name="operations"></a>Opérations  

 Une <xref:System.ServiceModel.Description.OperationDescription> instance est mappée à un `wsdl:portType` / `wsdl:operation` . Une `OperationDescription` contient une collection d’instances `MessageDescription` qui décrivent les messages de l’opération.  
  
 Deux comportements d'opération participent largement à la manière dont une `OperationDescription` est mappé à un document WSDL : `DataContractSerializerOperationBehavior` et `XmlSerializerOperationBehavior`.  
  
|Propriétés|Mappage WSDL|  
|----------------|------------------|  
|`Name`|`wsdl:portType` / `wsdl:operation` /@name Valeur de l’opération.|  
|`ProtectionLevel`|Assertions de protection dans la stratégie de sécurité jointe aux messages `wsdl:binding/wsdl:operation` de cette opération.|  
|`IsInitiating`|`wsdl:portType` / `wsdl:operation` /@msc:isInitiating Valeur de l’opération. Cet attribut est une extension WCF pour WSDL 1,1.|  
|`IsTerminating`|`wsdl:portType` / `wsdl:operation` /@msc:isTerminating Valeur de l’opération. Cet attribut est une extension WCF pour WSDL 1,1.|  
|`Messages`|Les `wsdl:portType` / `wsdl:operation` / `wsdl:input` `wsdl:portType` / `wsdl:operation` / `wsdl:output` messages et pour l’opération.|  
|`Faults`|`wsdl:portType` / `wsdl:operation` / `wsdl:fault` Définitions pour l’opération.|  
|`Behaviors`|Les comportements `DataContractSerializerOperationBehavior` et `XmlSerializerOperationBehavior` gèrent la liaison d’opération et les messages d’opération.|  
  
#### <a name="the-datacontractserializeroperationbehavior"></a>DataContractSerializerOperationBehavior  

 Le comportement `DataContractSerializerOperationBehavior` d’une opération est une implémentation de l’`IWsdlExportExtension` qui exporte les messages WSDL et la liaison de cette opération. Les types de schémas XML sont exportés à l'aide de l'`XsdDataContractExporter`. Le comportement `DataContractSerializerOperationBehavior` détermine également l'utilisation, le style, ainsi que l'exportateur et importateur de schéma à utiliser pour cette opération.  
  
|Propriétés|Mappage WSDL|  
|----------------|------------------|  
|`DataContractFormatAttribute`|La `Style` propriété de cet attribut est mappée à la `wsdl:binding` / `wsdl:operation` / `soap:operation` /@style valeur de l’opération.<br /><br /> Le comportement `DataContractSerializerOperationBehavior` prend uniquement en charge l'utilisation littérale des types de schémas dans WSDL.|  
  
#### <a name="the-xmlserializeroperationbehavior"></a>XmlSerializerOperationBehavior  

 Le comportement `XmlSerializerOperationBehavior` d’une opération est une implémentation de l’`IWsdlExportExtension` qui exporte les messages WSDL et la liaison de cette opération. Les types de schémas XML sont exportés à l'aide de l'`XmlSchemaExporter`. Le comportement `XmlSerializerOperationBehavior` détermine également l'utilisation, le style, ainsi que l'exportateur et importateur de schéma à utiliser pour cette opération.  
  
|Propriétés|Mappage WSDL|  
|----------------|------------------|  
|`XmlSerializerFormatAttribute`|La `Style` propriété de cet attribut est mappée à la `wsdl:binding` / `wsdl:operation` / `soap:operation` /@style valeur de l’opération.<br /><br /> La `Use` propriété de cet attribut est mappée aux `wsdl:binding` / `wsdl:operation` / `soap:operation` valeurs/* /@use pour tous les messages de l’opération.|  
  
### <a name="messages"></a>Messages  

 Une `MessageDescription` instance est mappée à un `wsdl:message` qui est référencé par un `wsdl:portType` / `wsdl:operation` / `wsdl:input` ou un `wsdl:portType` / `wsdl:operation` / `wsdl:output` message dans une opération. Une `MessageDescription` possède un corps et des en-têtes.  
  
|Propriétés|Mappage WSDL|  
|----------------|------------------|  
|`Action`|Action SOAP ou WS-Addressing du message.<br /><br /> Notez que les opérations qui utilisent la chaîne d'action "*" ne sont pas représentées dans WSDL.|  
|`Direction`|`MessageDirection.Input` correspond à `wsdl:input`.<br /><br /> `MessageDirection.Output` correspond à `wsdl:output`.|  
|`ProtectionLevel`|Assertions de protection dans la stratégie de sécurité jointe à la définition `wsdl:message` de ce message.|  
|`Body`|Corps du message.|  
|`Headers`|En-têtes du message.|  
|`ContractDescription.Name`, `OperationContract.Name`|Lors de l’exportation, utilisé pour dériver la `wsdl:message` /@name valeur.|  
  
#### <a name="message-body"></a>Corps du message  

 Une `MessageBodyDescription` instance est mappée aux `wsdl:message` / `wsdl:part` définitions pour le corps d’un message. Le corps du message peut être encapsulé ou nu.  
  
|Propriétés|Mappage WSDL|  
|----------------|------------------|  
|`WrapperName`|Si le style n’est pas RPC, le est `WrapperName` mappé au nom d’élément référencé par `wsdl:message` / `wsdl:part` avec ayant la @name valeur « Parameters ».|  
|`WrapperNamespace`|Si le style n’est pas RPC, le `WrapperNamespace` mappe à l’espace de noms de l’élément pour `wsdl:message` / `wsdl:part` avec @name défini sur « Parameters ».|  
|`Parts`|Parties du message pour ce corps du message.|  
|`ReturnValue`|Élément enfant de l’élément wrapper s’il existe un élément wrapper (style de document encapsulé ou style RPC), sinon le premier `wsdl:message` / `wsdl:part` dans le message.|  
  
#### <a name="message-parts"></a>Parties du message  

 Une `MessagePartDescription` instance est mappée à un `wsdl:message` / `wsdl:part` et au type de schéma XML ou à l’élément vers lequel la partie du message pointe.  
  
|Propriétés|Mappage WSDL|  
|----------------|------------------|  
|`Name`|`wsd:message` / `wsdl:part` /@name Valeur de la partie de message et nom de l’élément vers lequel la partie du message pointe.|  
|`Namespace`|Espace de noms de l'élément vers lequel la partie de message pointe.|  
|`Index`|Index du `wsdl:message` / `wsdl:part` pour le message.|  
|`ProtectionLevel`|Assertions de protection dans la stratégie de sécurité jointe à la définition `wsdl:message` de cette partie du message. La stratégie est paramétrée pour pointer vers la partie spécifique du message.|  
|`MessageType`|Type de schéma XML de l'élément vers lequel la partie du message pointe.|  
  
#### <a name="message-headers"></a>En-têtes de message  

 Une instance `MessageHeaderDescription` est une partie de message qui correspond également à une liaison `soap:header` de la partie du message.  
  
### <a name="faults"></a>Pannes  

 Une `FaultDescription` instance est mappée à une `wsdl:portType` / `wsdl:operation` / `wsdl:fault` définition et à sa `wsdl:message` définition associée. La définition `wsdl:message` est ajoutée au même espace de noms cible que son type de port WSDL associé. La définition `wsdl:message` possède une seule partie de message nommée « détail » qui pointe vers l'élément du schéma XML qui correspond à la valeur de propriété `DefaultType` de l'instance `FaultDescription`.  
  
|Propriétés|Mappage WSDL|  
|----------------|------------------|  
|`Name`|`wsdl:portType` / `wsdl:operation` / `wsdl:fault` /@name Valeur de l’erreur.|  
|`Namespace`|Espace de noms de l'élément du schéma XML vers lequel la partie « détail » du message d'erreur pointe.|  
|`Action`|Action SOAP ou WS-Addressing de l'erreur.|  
|`ProtectionLevel`|Assertions de protection dans la stratégie de sécurité jointe à la définition `wsdl:message` de cette erreur.|  
|`DetailType`|Type de schéma XML de l'élément vers lequel la partie « détail » du message pointe.|  
|`Name, ContractDescription.Name, OperationDescription.Name,`|Utilisé pour dériver la `wsdl:message` /@name valeur du message d’erreur.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Description>
