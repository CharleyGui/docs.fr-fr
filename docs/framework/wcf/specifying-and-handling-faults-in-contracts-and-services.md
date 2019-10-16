---
title: Spécification et gestion des erreurs dans les contrats et les services
ms.date: 03/30/2017
helpviewer_keywords:
- handling faults [WCF]
ms.assetid: a9696563-d404-4905-942d-1e0834c26dea
ms.openlocfilehash: bbc1ca97c8887ebdfbe30f7dd76549572367efbe
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321111"
---
# <a name="specifying-and-handling-faults-in-contracts-and-services"></a>Spécification et gestion des erreurs dans les contrats et les services

Les applications Windows Communication Foundation (WCF) gèrent les situations d’erreur en mappant les objets d’exception managée aux objets d’erreur SOAP et aux objets d’erreur SOAP aux objets d’exception managés. Les rubriques de cette section expliquent comment concevoir des contrats pour exposer des conditions d'erreur en tant qu'erreurs SOAP personnalisées, comment retourner de telles erreurs dans le cadre de l'implémentation du service et comment les clients interceptent de telles erreurs.

## <a name="error-handling-overview"></a>Vue d'ensemble de la gestion des erreurs

Dans toutes les applications managées, les erreurs de traitement sont représentées par des objets <xref:System.Exception>. Dans les applications basées sur SOAP telles que les applications WCF, les méthodes de service communiquent les informations d’erreur à l’aide de messages d’erreur SOAP. Les erreurs SOAP sont des types de messages inclus dans les métadonnées d'une opération de service et créent, par conséquent, un contrat d'erreur permettant aux clients d'améliorer la fiabilité ou l'interactivité de leur opération. En outre, étant donné que les erreurs SOAP sont exprimées en clients au format XML, il s’agit d’un système de type très interopérable que les clients sur n’importe quelle plateforme SOAP peuvent utiliser, ce qui a pour effet d’améliorer la portée de votre application WCF.

Étant donné que les applications WCF s’exécutent sous les deux types de systèmes d’erreur, toutes les informations sur les exceptions managées envoyées au client doivent être converties des exceptions en erreurs SOAP sur le service, envoyées et converties des erreurs SOAP en exceptions d’erreur dans les clients WCF. Dans le cas de clients duplex, les contrats clients peuvent aussi renvoyer des erreurs SOAP à un service. Dans les deux cas, vous pouvez utiliser les comportements d'exception de service par défaut ou vous pouvez contrôler explicitement si (et comment) les exceptions sont mappées aux messages d'erreur.

Deux types d’erreurs SOAP peuvent être envoyées : *déclarées* et non *déclarées*. Les erreurs SOAP déclarées sont celles dans lesquelles une opération contient un attribut <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> qui spécifie un type d'erreur SOAP personnalisé. Non *déclaré* Les erreurs SOAP ne sont pas spécifiées dans le contrat d’une opération.

Il est vivement recommandé que les opérations de service déclarent leurs erreurs en utilisant l'attribut <xref:System.ServiceModel.FaultContractAttribute> pour spécifier de manière formelle toutes les erreurs SOAP qu'un client peut s'attendre à recevoir dans le cours normal de l'opération. Il est également recommandé de retourner dans une erreur SOAP uniquement les informations qu'un client doit connaître pour réduire la divulgation d'informations.

En général, les services (et les clients duplex) exécutent les étapes suivantes pour intégrer la gestion des erreurs dans leurs applications :

- Mappage des conditions d'exception aux erreurs SOAP personnalisées.

- Les clients et les services envoient et reçoivent des erreurs SOAP comme exceptions.

En outre, les clients et les services WCF peuvent utiliser des erreurs SOAP non déclarées à des fins de débogage et peuvent étendre le comportement d’erreur par défaut. Les sections suivantes traitent de ces tâches et de ces concepts.

## <a name="map-exceptions-to-soap-faults"></a>Mappage d'exceptions aux erreurs SOAP

La première étape pour créer une opération qui gère des conditions d'erreur consiste à décider à quelles conditions une application cliente doit être informée des erreurs. Certaines opérations ont des conditions d'erreur spécifiques à leurs fonctionnalités. Par exemple, une opération `PurchaseOrder` peut retourner des informations spécifiques aux clients qui ne sont plus autorisés à initialiser une commande fournisseur. Dans d'autres cas, comme pour un service `Calculator`, une erreur SOAP `MathFault` plus générale peut-être en mesure de décrire toutes les conditions d'erreur à travers un service entier. Une fois les conditions d'erreur des clients de votre service identifiées, une erreur SOAP personnalisée peut être construite et l'opération peut être marquée comme retournant cette erreur SOAP lorsque la condition d'erreur correspondante se produit.

Pour plus d’informations sur cette étape de développement de votre service ou client, consultez [définition et spécification des erreurs](defining-and-specifying-faults.md).

## <a name="clients-and-services-handle-soap-faults-as-exceptions"></a>Clients et services gérant les erreurs SOAP en tant qu'exceptions

L’identification des conditions d’erreur d’opération, la définition des erreurs SOAP personnalisées et le marquage de ces opérations comme retour de ces erreurs sont les premières étapes de la réussite de la gestion des erreurs dans les applications WCF. L'étape suivante consiste à implémenter correctement l'émission et la réception de ces erreurs. En général les services envoient des erreurs pour signaler aux applications clientes des conditions d'erreur, mais les clients duplex peuvent également envoyer des erreurs SOAP aux services.

Pour plus d’informations, consultez [envoi et réception d’erreurs](sending-and-receiving-faults.md).

## <a name="undeclared-soap-faults-and-debugging"></a>Erreurs SOAP non déclarées et débogage

Les erreurs SOAP déclarées sont extrêmement utiles pour construire des applications fiables, interopérables et distribuées. Toutefois, il est parfois utile pour un service (ou un client duplex) d'envoyer une erreur SOAP non déclarée, c'est-à-dire une erreur qui n'est pas mentionnée dans WSDL (Web Services Description Language) pour une opération. Par exemple, lors du développement d'un service, des situations inattendues peuvent se produire et il peut s'avérer utile de renvoyer des informations au client à des fins de débogage. En outre, vous pouvez définir la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> ou la propriété <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> sur `true` pour permettre aux clients WCF d’obtenir des informations sur les exceptions d’opération de service interne. L’envoi d’erreurs individuelles et la définition des propriétés de comportement de débogage sont décrits dans [envoi et réception d’erreurs](sending-and-receiving-faults.md).

> [!IMPORTANT]
> Étant donné que les exceptions managées peuvent exposer des informations d’application internes, la définition de <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> à `true` peut permettre aux clients WCF d’obtenir des informations sur les exceptions d’opération de service interne, y compris l’identification personnelle ou d’autres éléments sensibles informations.
>
> Par conséquent, affecter à <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> ou à <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> la valeur `true` est recommandé uniquement pour déboguer temporairement une application de service. De plus, le WSDL pour une méthode qui retourne des exceptions managées non prises en charge de cette façon ne contient pas le contrat pour le <xref:System.ServiceModel.FaultException%601> de type <xref:System.ServiceModel.ExceptionDetail>. Les clients doivent attendre une erreur SOAP inconnue (retournée aux clients WCF en tant qu’objets <xref:System.ServiceModel.FaultException?displayProperty=nameWithType>) pour obtenir correctement les informations de débogage.

## <a name="customizing-error-handling-with-ierrorhandler"></a>Personnalisation de la gestion des erreurs avec IErrorHandler

Si vous avez des spécifications spéciales pour personnaliser le message de réponse au client lorsqu'une exception au niveau de l'application se produit ou pour effectuer un traitement personnalisé après avoir retourné le message de réponse, implémentez l'interface <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType>.

## <a name="fault-serialization-issues"></a>Problèmes de sérialisation d'erreur

Lors de la désérialisation d'un contrat d'erreur, WCF essaie d'abord de faire correspondre le nom du contrat d'erreur figurant dans le message SOAP avec le type de contrat d'erreur. S'il ne trouve pas de correspondance exacte, il recherche ensuite un type compatible dans la liste des contrats d'erreur disponibles, par ordre alphabétique. Si deux contrats d'erreur sont des types compatibles (l'un étant une sous-classe de l'autre, par exemple), il est possible que le mauvais soit utilisé pour désérialiser l'erreur. Cela ne se produit que lorsque le contrat  d'erreur ne spécifie pas de nom, d'espace de noms et d'action. Pour éviter la survenue de ce problème, qualifiez toujours les contrats d'erreur en spécifiant les attributs de nom, d'espace de noms et d'action. En outre, si vous avez défini un certain nombre de contrats d'erreur connexes dérivés d'une classe de base partagée, veillez à marquer tout nouveau membre avec `[DataMember(IsRequired=true)]`. Pour plus d'informations sur cet attribut `IsRequired`, consultez <xref:System.Runtime.Serialization.DataMemberAttribute>. Cela empêchera une classe de base d'être un type compatible et forcera la désérialisation de l'erreur vers le type dérivé approprié.

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.FaultException>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.FaultException>
- <xref:System.Xml.Serialization.XmlSerializer>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.CommunicationException>
- <xref:System.ServiceModel.FaultContractAttribute.Action%2A>
- <xref:System.ServiceModel.FaultException.Code%2A>
- <xref:System.ServiceModel.FaultException.Reason%2A>
- <xref:System.ServiceModel.FaultCode.SubCode%2A>
- <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>
- [Définition et spécification des erreurs](defining-and-specifying-faults.md)
