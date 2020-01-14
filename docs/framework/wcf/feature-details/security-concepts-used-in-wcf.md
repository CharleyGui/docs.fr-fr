---
title: Concepts de sécurité utilisés dans WCF
ms.date: 03/30/2017
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
ms.openlocfilehash: ce6dc6f5cb8680d6228e21206afdc3aa33085e7d
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938122"
---
# <a name="security-concepts-used-in-wcf"></a>Concepts de sécurité utilisés dans WCF
La sécurité Windows Communication Foundation (WCF) repose sur des concepts déjà utilisés et déployés dans diverses infrastructures de sécurité.  
  
 WCF prend en charge certaines de ces infrastructures, telles que protocole SSL (SSL) sur HTTP (HTTPs). Toutefois, WCF va au-delà de la prise en charge des infrastructures de sécurité existantes en implémentant des normes de sécurité interopérables plus récentes (telles que WS-Security) sur des messages SOAP. Toutefois, qu'il s'agisse de mécanismes existants ou de nouveaux standards interopérables, les concepts de sécurité sous-jacents sont dans ces deux cas les mêmes. Par conséquent, comprendre les concepts qui sous-tendent les infrastructures existantes et les standards plus récents est un atout essentiel à l'implémentation du meilleur modèle de sécurité pour une application.  
  
## <a name="introduction-to-security-for-wcf-web-services"></a>Introduction à la sécurité pour WCF Web Services  
 Le groupe Microsoft Patterns and Practices a rédigé un livre blanc détaillé sur les conseils de sécurité WCF, qui est disponible en téléchargement ici : [Guide de sécurité WCF](https://go.microsoft.com/fwlink/?LinkId=210210). Ce livre blanc décrit les concepts fondamentaux de sécurité liés aux services Web, aux principaux concepts de sécurité WCF, aux scénarios d’application intranet et aux scénarios d’application Internet.  
  
## <a name="industry-wide-security-specifications"></a>Spécifications de sécurité de l'industrie  
  
### <a name="public-key-infrastructure"></a>Infrastructure à clé publique  
 L’infrastructure à clé publique (PKI) est un système de certificats numériques, d’autorités de certification et autres autorités d’immatriculation qui vérifient et authentifient chaque partie impliquée dans une transaction électronique via l’utilisation du chiffrement à clé publique. Pour plus d’informations, consultez [services de certificats Windows Server 2008 R2](https://go.microsoft.com/fwlink/?LinkId=210211).  
  
### <a name="kerberos-protocol"></a>Protocole Kerberos  
 Le *protocole Kerberos* est une spécification pour la création d’un mécanisme de sécurité qui authentifie les utilisateurs sur un domaine Windows. Il permet d'établir un contexte sécurisé avec d'autres entités au sein d'un domaine. Windows 2000 et les plateformes ultérieures utilisent le protocole Kerberos par défaut. La maîtrise des mécanismes du système est utile lors de la création d'un service qui interagira avec les clients intranet. En outre, étant donné que la *liaison kerberos Web Services Security* est largement publiée, vous pouvez utiliser le protocole Kerberos pour communiquer avec les clients Internet (autrement dit, le protocole Kerberos est interopérable). Pour plus d’informations sur l’implémentation du protocole Kerberos dans Windows, consultez [Microsoft Kerberos](https://go.microsoft.com/fwlink/?LinkId=210212).  
  
### <a name="x509-certificates"></a>Certificats X.509  
 Les certificats X.509 constituent un formulaire d'informations d'identification principal utilisé dans les applications de sécurité. Pour plus d’informations sur les certificats X. 509, consultez [certificats de clé publique x. 509](https://go.microsoft.com/fwlink/?LinkId=210213). Les certificats X.509 sont stockés dans un magasin de certificats. Un ordinateur qui exécute Windows a plusieurs types de magasins de certificats, chacun ayant un but différent. Pour plus d’informations sur les différents magasins, consultez [magasins de certificats](https://go.microsoft.com/fwlink/?LinkID=87787).  
  
## <a name="web-services-security-specifications"></a>Spécifications Web Services Security  
 Les liaisons définies par le système prennent en charge plusieurs spécifications de sécurité communément utilisées pour les services Web. Pour obtenir la liste complète des liaisons fournies par le système et les spécifications des services Web qu’elles prennent en charge, consultez [protocoles de services Web pris en charge par les liaisons d’interopérabilité fournies par le système](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md) .  
  
## <a name="access-control-mechanisms"></a>Mécanismes de contrôle d'accès  
 WCF offre plusieurs méthodes pour contrôler l'accès à un service ou à une opération. Parmi celles-ci :  
  
1. <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2. Fournisseur d'appartenances ASP.NET  
  
3. Fournisseur de rôle ASP.NET  
  
4. Gestionnaire d’autorisations  
  
5. Modèle d'identité  
  
 Pour plus d’informations sur ces rubriques, consultez [Access Control mécanismes](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la sécurité](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Modèle de sécurité pour Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
