---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: 9991430f09cb6a63d0a3cdde24a4ff03d3dd746d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165050"
---
# \<issuerNameRegistry>

Configure le registre des noms d’émetteurs qui est utilisé par les gestionnaires dans la collection de gestionnaires de jetons.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerNameRegistry>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry type=xs:string>  
          <optionalCustomConfigurationElements />  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|type|Type qui dérive de la <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe. Pour plus d’informations sur la façon de spécifier un personnalisé `type` , consultez [références de types personnalisés].|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<trustedIssuers>](trustedissuers.md)|Lorsque l' `type` attribut spécifie le registre des noms d’émetteurs basés sur la configuration (la <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe), l' [\<trustedIssuers>](trustedissuers.md) élément doit être spécifié. L' [\<trustedIssuers>](trustedissuers.md) élément peut prendre `<add>` des `<clear>` éléments, ou `<remove>` en tant qu’éléments enfants.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.|  
  
## <a name="remarks"></a>Notes  

 Tous les jetons d’émetteur sont validés à l’aide d’un registre de noms d’émetteurs. Il s’agit d’un objet qui dérive de la <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe. Le registre des noms d’émetteurs est utilisé pour associer un nom mnémonique aux documents de chiffrement nécessaires à la vérification des signatures des jetons produits par l’émetteur correspondant. Le registre des noms d’émetteurs gère une liste des émetteurs qui sont approuvés par l’application de partie de confiance (RP). Le type du registre des noms d’émetteurs est spécifié à l’aide de l' `type` attribut. L' `<issuerNameRegistry>` élément peut avoir un ou plusieurs éléments enfants qui fournissent la configuration pour le type spécifié. Vous fournissez la logique qui traite ces éléments enfants en substituant la <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> méthode.  
  
 WIF fournit un type de registre de nom d’émetteur unique, la <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe. Cette classe utilise un ensemble de certificats d’émetteurs approuvés spécifiés dans la configuration. Il nécessite un élément de configuration enfant, `<trustedIssuers>` , sous lequel la collection de certificats d’émetteurs approuvés est configurée. Les certificats approuvés sont spécifiés à l’aide de la forme encodée ASN. 1 de l’empreinte numérique du certificat et sont ajoutés ou supprimés de la collection à l’aide des `<add>` `<clear>` éléments, ou `<remove>` .  
  
 L' `<issuerNameRegistry>` élément est représenté par la <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> classe.  
  
> [!NOTE]
> La spécification de l' `<issuerNameRegistry>` élément en tant qu’élément enfant de l' [\<identityConfiguration>](identityconfiguration.md) élément a été dépréciée, mais est toujours prise en charge pour la compatibilité descendante. Les paramètres de l' `<securityTokenHandlerConfiguration>` élément remplacent ceux de l' `<identityConfiguration>` élément.  
  
## <a name="example"></a>Exemple  

 Le code XML suivant montre comment spécifier le registre des noms d’émetteurs basés sur la configuration.  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
