---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: 678e5c705181c55257b1ddb853690ada60ecd17a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942457"
---
# <a name="securitytokenhandlers"></a>\<securityTokenHandlers>
Spécifie une collection de gestionnaires de jetons de sécurité inscrits auprès du point de terminaison.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|name|Spécifie le nom d’une collection de gestionnaires de jetons. Les seules valeurs reconnues par l’infrastructure sont «ActAs» et «OnBehalfOf». Si les collections de gestionnaires de jetons sont spécifiées avec l’un de ces noms, la collection sera utilisée lors du traitement des jetons ActAs ou OnBehalfOf, respectivement.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add>](add.md)|Ajoute un gestionnaire de jetons de sécurité à la collection de gestionnaires de jetons.|  
|[\<clear>](clear.md)|Efface tous les gestionnaires de jetons de sécurité de la collection de gestionnaires de jetons.|  
|[\<remove>](remove.md)|Supprime un gestionnaire de jetons de sécurité de la collection de gestionnaires de jetons.|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Fournit la configuration pour la collection de gestionnaires de jetons.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Spécifie les paramètres d’identité au niveau du service.|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez spécifier une ou plusieurs collections nommées de gestionnaires de jetons de sécurité dans une configuration de service. Vous pouvez spécifier un nom pour une collection à l’aide `name` de l’attribut. Les seuls noms que le Framework gère sont «ActAs» et «OnBehalfOf». Si des gestionnaires existent dans ces collections, ils sont utilisés par un service d’émission de jeton de sécurité (STS) à la place des `ActAs` gestionnaires `OnBehalfOf` par défaut lors du traitement et des jetons.  
  
 Par défaut, la collection est remplie avec les types de gestionnaires suivants <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>: <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, et <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>. Vous pouvez modifier la collection à l’aide `<add>`des `<remove>`éléments, `<clear>` et. Vous devez vous assurer qu’il n’existe qu’un seul gestionnaire d’un type particulier dans la collection. Par exemple, si vous dérivez un gestionnaire <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> de la classe, votre gestionnaire ou <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> le peut être configuré dans une seule collection, mais pas les deux.  
  
 Utilisez l' `<securityTokenHandlerConfiguration>` élément pour spécifier les paramètres de configuration des gestionnaires dans la collection. Les paramètres spécifiés par le biais de cet élément remplacent ceux spécifiés sur le service par le biais de l' [ \<élément identityConfiguration >](identityconfiguration.md) . Certains gestionnaires (y compris plusieurs des types de gestionnaires intégrés) peuvent prendre en charge une configuration supplémentaire via un élément enfant de `<add>` l’élément. Les paramètres spécifiés sur un gestionnaire substituent les paramètres équivalents spécifiés dans la collection ou le service.
