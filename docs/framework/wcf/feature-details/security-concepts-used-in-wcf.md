---
title: Concepts de sécurité utilisés dans WCF
ms.date: 03/30/2017
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
ms.openlocfilehash: 2c7bc01ba45c02be4a1d40c2600fde62e94afe32
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251384"
---
# <a name="security-concepts-used-in-wcf"></a>Concepts de sécurité utilisés dans WCF

La sécurité Windows Communication Foundation (WCF) repose sur des concepts déjà utilisés et déployés dans diverses infrastructures de sécurité.  
  
 WCF prend en charge certaines de ces infrastructures, telles que protocole SSL (SSL) sur HTTP (HTTPs). Toutefois, WCF va au-delà de la prise en charge des infrastructures de sécurité existantes en implémentant des normes de sécurité interopérables plus récentes (telles que WS-Security) sur des messages SOAP. Toutefois, qu'il s'agisse de mécanismes existants ou de nouveaux standards interopérables, les concepts de sécurité sous-jacents sont dans ces deux cas les mêmes. Par conséquent, comprendre les concepts qui sous-tendent les infrastructures existantes et les standards plus récents est un atout essentiel à l'implémentation du meilleur modèle de sécurité pour une application.  
  
## <a name="introduction-to-security-for-wcf-web-services"></a>Introduction à la sécurité pour WCF Web Services  

Le groupe Microsoft Patterns and Practices a rédigé un livre blanc détaillé appelé [Guide de sécurité WCF](https://archive.codeplex.com/?p=wcfsecurityguide). Ce livre blanc décrit les concepts fondamentaux de sécurité liés aux services Web, aux principaux concepts de sécurité WCF, aux scénarios d’application intranet et aux scénarios d’application Internet.  
  
## <a name="industry-wide-security-specifications"></a>Spécifications de sécurité de l'industrie  
  
### <a name="public-key-infrastructure"></a>Infrastructure à clé publique (PKI)  

L’infrastructure à clé publique (PKI) est un système de certificats numériques, d’autorités de certification et d’autres autorités d’enregistrement qui vérifient et authentifient chaque partie impliquée dans une transaction électronique via l’utilisation du chiffrement à clé publique.
  
### <a name="kerberos-protocol"></a>Protocole Kerberos  

 Le *protocole Kerberos* est une spécification pour la création d’un mécanisme de sécurité qui authentifie les utilisateurs sur un domaine Windows. Il permet d'établir un contexte sécurisé avec d'autres entités au sein d'un domaine. Windows 2000 et les plateformes ultérieures utilisent le protocole Kerberos par défaut. La maîtrise des mécanismes du système est utile lors de la création d'un service qui interagira avec les clients intranet. En outre, étant donné que la *liaison kerberos Web Services Security* est largement publiée, vous pouvez utiliser le protocole Kerberos pour communiquer avec les clients Internet (autrement dit, le protocole Kerberos est interopérable). Pour plus d’informations sur l’implémentation du protocole Kerberos dans Windows, consultez  [Microsoft Kerberos](/windows/win32/secauthn/microsoft-kerberos).  
  
### <a name="x509-certificates"></a>Certificats X.509  

 Les certificats X.509 constituent un formulaire d'informations d'identification principal utilisé dans les applications de sécurité. Pour plus d’informations sur les certificats X. 509, consultez [certificats de clé publique x. 509](/windows/win32/seccertenroll/about-x-509-public-key-certificates). Les certificats X.509 sont stockés dans un magasin de certificats. Un ordinateur qui exécute Windows a plusieurs types de magasins de certificats, chacun ayant un but différent. Pour plus d’informations sur les différents magasins, consultez [magasins de certificats](/previous-versions/windows/it-pro/windows-server-2003/cc757138(v=ws.10)).  
  
## <a name="web-services-security-specifications"></a>Spécifications Web Services Security  

 Les liaisons définies par le système prennent en charge plusieurs spécifications de sécurité communément utilisées pour les services Web. Pour obtenir la liste complète des liaisons fournies par le système et des spécifications de services Web qu’ils prennent en charge, consultez : [protocoles de services Web pris en charge par les liaisons de System-Provided interopérabilité](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
  
## <a name="access-control-mechanisms"></a>Mécanismes de contrôle d'accès  

 WCF offre plusieurs méthodes pour contrôler l'accès à un service ou à une opération. Parmi celles-ci :  
  
1. <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2. Fournisseur d'appartenances ASP.NET  
  
3. Fournisseur de rôle ASP.NET  
  
4. Gestionnaire d'autorisations  
  
5. Modèle d'identité  
  
 Pour plus d’informations sur ces rubriques, consultez [Access Control mécanismes](access-control-mechanisms.md)  
  
## <a name="see-also"></a>Voir aussi

- [Présentation de la sécurité](security-overview.md)
- [Modèle de sécurité pour Windows Server AppFabric](/previous-versions/appfabric/ee677202(v=azure.10))
