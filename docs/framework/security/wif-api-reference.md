---
title: Référence de l’API WIF
ms.date: 03/30/2017
ms.assetid: a027d902-9314-4bfd-b172-4e81847b1d68
author: BrucePerlerMS
ms.openlocfilehash: fd7f34e619626ddca63074a89ec7253fd818ab55
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045147"
---
# <a name="wif-api-reference"></a>Référence de l’API WIF
Les classes WIF (Windows Identity Foundation) sont réparties dans les assemblys suivants : `mscorlib` (mscorlib.dll), `System.IdentityModel` (System.IdentityModel.dll), `System.IdentityModel.Services` (System.IdentityModel.Services.dll) et `System.ServiceModel` (System.ServiceModel.dll). Cette rubrique fournit des liens vers les espaces de noms WIF et une brève explication des classes contenues dans chaque espace de noms.  
  
> [!IMPORTANT]
> Les espaces de noms `System.IdentityModel` suivants contiennent des classes qui implémentent le modèle d’identité basé sur des revendications WCF : <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType> et <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. À compter de .NET Framework 4.5, le modèle d’identité basée sur les revendications WCF est remplacé par WIF. Vous ne devez pas utiliser les classes de ces trois espaces de noms quand vous créez des solutions basées sur WIF.  
  
 <xref:System.IdentityModel?displayProperty=nameWithType>  
 Contient des classes qui représentent des transformations de cookies, des services d’émission de jeton de sécurité et des lecteurs de dictionnaires XML spécifiques.  
  
 <xref:System.IdentityModel.Configuration?displayProperty=nameWithType>  
 Contient des classes qui spécifient la configuration pour les applications et services créés à l’aide de WIF. Les classes de cet espace de noms représentent les paramètres sous l’élément [\<identityConfiguration>](../configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md).  
  
 <xref:System.IdentityModel.Metadata?displayProperty=nameWithType>  
 Contient des classes qui représentent des éléments dans un document de métadonnées de fédération.  
  
 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>  
 Contient des classes qui représentent des artefacts WS-Trust.  
  
 <xref:System.IdentityModel.Services?displayProperty=nameWithType>  
 Contient des classes utilisées dans des scénarios passifs (WS-Federation). Contient également des classes qui représentent les paramètres sous l’élément [\<system.identityModel.services>](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md). Les paramètres sous cet élément configurent WS-Federation pour les applications. L’espace de noms `System.IdentityModel.Services.Configuration` contient la plupart des classes utilisées pour configurer WS-Federation.  
  
 <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>  
 Contient des classes qui spécifient la configuration pour les applications WIF utilisant le protocole WS-Federation. Les classes de cet espace de noms représentent les paramètres sous l’élément [\<system.identityModel.services>](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md). L’espace de noms `System.IdentityModel.Services` contient aussi des classes qui sont utilisées pour configurer WS-Federation.  
  
 <xref:System.IdentityModel.Services.Tokens?displayProperty=nameWithType>  
 Contient des gestionnaires de jetons de sécurité spécifiques pour les scénarios avec batterie de serveurs web.  
  
 <xref:System.IdentityModel.Tokens?displayProperty=nameWithType>  
 Contient des classes qui représentent des jetons de sécurité, des gestionnaires de jetons de sécurité et d’autres artefacts de jetons de sécurité.  
  
 <xref:System.Security.Claims?displayProperty=nameWithType>  
 Contient des classes qui représentent des revendications, des identités basées sur les revendications, des principaux basés sur les revendications et d’autres artefacts de modèles d’identité basée sur les revendications.  
  
 <xref:System.ServiceModel.Security?displayProperty=nameWithType>  
 Contient des classes qui représentent des contrats, canaux et hôtes de service WCF, ainsi que d’autres artefacts utilisés dans des scénarios actifs (WS-Trust). Cet espace de noms contient également des classes propres à WCF qui ne sont pas utilisées par WIF.  
  
## <a name="see-also"></a>Voir aussi

- [Référence de configuration de WIF](wif-configuration-reference.md)
- [Mappage des espaces de noms entre WIF 3.5 et WIF 4.5](namespace-mapping-between-wif-3-5-and-wif-4-5.md)
