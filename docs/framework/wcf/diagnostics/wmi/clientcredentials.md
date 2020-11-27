---
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: c63e1b3de464b306f46e2f0935b1208d7262925a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274190"
---
# <a name="clientcredentials"></a>ClientCredentials

ClientCredentials  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class ClientCredentials : Behavior  
{  
  string ClientCertificate;  
  string HttpDigest;  
  string IssuedToken;  
  string Peer;  
  string ServiceCertificate;  
  boolean SupportInteractive;  
  string UserName;  
  string Windows;  
};  
```  
  
## <a name="methods"></a>Méthodes  

 La classe ClientCredentials ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  

 La classe ClientCredentials a les propriétés suivantes :  
  
### <a name="clientcertificate"></a>ClientCertificate  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Certificat X.509 que le client utilise pour s'authentifier auprès du service.  
  
### <a name="httpdigest"></a>HttpDigest  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Informations d’identification HTTP Digest actuelles.  
  
### <a name="issuedtoken"></a>IssuedToken  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Adresse de point de terminaison et liaison utilisées pour contacter le service de jetons de sécurité local.  
  
### <a name="peer"></a>Homologue  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Informations d'identification que le nœud d'homologue utilise pour s'authentifier auprès d'autres nœuds dans la maille.  
  
### <a name="servicecertificate"></a>ServiceCertificate  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Certificat X.509 du service.  
  
### <a name="supportinteractive"></a>SupportInteractive  

 Type de données : booléen  
  
 Type d'accès : Lecture seule  
  
 Valeur booléenne qui spécifie si les informations d'identification prennent en charge la négociation interactive.  
  
### <a name="username"></a>UserName  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Nom d'utilisateur et mot de passe que le client utilise pour s'authentifier auprès du service.  
  
### <a name="windows"></a>Windows  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Informations d'identification que le client utilise pour s'authentifier auprès du service.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Description.ClientCredentials>
