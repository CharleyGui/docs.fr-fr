---
title: WCF et API Web ASP.NET
description: Découvrez si WCF ou le API Web ASP.NET est mieux adapté à vos besoins en comparant les principales fonctionnalités de chaque technologie.
ms.date: 03/30/2017
ms.assetid: 08ceded3-fd9a-4467-9715-c4cbd9c7228e
ms.openlocfilehash: b3a905f890b4dfa9f60c906c3a242be60921e5c8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273592"
---
# <a name="wcf-and-aspnet-web-api"></a>WCF et API Web ASP.NET

WCF est le modèle de programmation unifié de Microsoft permettant de générer des applications orientées service. Il permet aux développeurs de générer des solutions transactionnelles sécurisées et fiables qui s'intègrent à plusieurs plateformes et interagissent avec les investissements existants. [API Web ASP.net](https://www.asp.net/web-api) est une infrastructure qui facilite la création de services http qui atteignent un large éventail de clients, y compris des navigateurs et des appareils mobiles. L'API Web ASP.NET est une plate-forme idéale pour générer des applications RESTful sur le .NET Framework. Cette rubrique vous aider à déterminer quelle technologie est la plus adaptée vos besoins.  
  
## <a name="choosing-which-technology-to-use"></a>Choix de la technologie à utiliser  

 Le tableau suivant décrit les principales fonctionnalités de chaque technologie.  
  
|WCF|API web ASP.NET|  
|---------|---------------------|  
|Active les services de génération qui prennent en charge plusieurs fournisseurs de transport (HTTP, TCP, UDP et transports personnalisés) et permet le basculement entre eux.|HTTP uniquement. Modèle de programmation de premier ordre pour HTTP. Plus adapté à l’accès à partir de différents navigateurs, appareils mobiles, etc.|  
|Active les services de génération qui prennent en charge plusieurs encodages (texte, MTOM et binaire) du même type de message et permet la commutation entre eux.|Active les API Web de génération qui prennent en charge une large gamme de types de média y compris XML, JSON, etc.|  
|Prend en charge les services de génération avec les normes WS-*, tels que messagerie fiable, transactions et sécurité des messages.|Utilise le protocole de base et les formats tels que HTTP, WebSocket, SSL, JSON et XML. Il n'existe aucune prise en charge des protocoles de niveau supérieur, tels que Messagerie fiable ou Transactions.|  
|Prend en charge les modèles d’échange de messages duplex, demande-réponse et unidirectionnels.|HTTP est requête/réponse, mais des modèles supplémentaires peuvent être pris en charge via l’intégration de [signalr](https://github.com/SignalR/SignalR) et WebSocket.|  
|Les services SOAP WCF peuvent être décrits en WSDL, ce qui permet aux outils automatisés de générer des proxys clients même pour les services ayant des schémas complexes.|Il existe plusieurs façons de décrire une API Web, allant d'une page HTML générée automatiquement décrivant les extraits de code aux métadonnées structurées pour les API intégrées OData.|  
|Est fourni avec le .NET Framework.|Est fourni avec .NET Framework mais est open source et est également disponible hors bande en téléchargement indépendant.|  
  
 Utilisez WCF pour créer des services Web fiables et sécurisés qui sont accessibles sur un grand nombre de transports. Utilisez l'API Web ASP.NET pour créer des services HTTP qui sont accessibles à partir d'une large gamme de clients. Utilisez l'API Web ASP.NET si vous créez et concevez de nouveaux services REST. Bien que WCF prenne en charge l'écriture de services REST, la prise en charge de REST dans l'API Web ASP.NET est plus complète et toutes les futures améliorations des fonctionnalités REST seront apportées dans l'API Web ASP.NET. Si vous disposez d'un service WCF et souhaitez exposer des points de terminaison REST supplémentaires, utilisez WCF et <xref:System.ServiceModel.WebHttpBinding>.  
  
## <a name="see-also"></a>Voir aussi

- [Présentation de Windows Communication Foundation](whats-wcf.md)
- [Concepts fondamentaux concernant Windows Communication Foundation](fundamental-concepts.md)
