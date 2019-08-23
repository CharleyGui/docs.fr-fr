---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: d0a1f8dd0c29aaee56c2ca1162cc70cc1e5ed106
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942666"
---
# <a name="issuernameregistry"></a>\<issuerNameRegistry>
Configure le registre des noms d’émetteurs qui est utilisé par les gestionnaires dans la collection de gestionnaires de jetons.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration>  
\<issuerNameRegistry>  
  
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
|type|Type qui dérive de la <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe. Pour plus d’informations sur la façon de spécifier `type`un personnalisé, consultez [références de types personnalisés].|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<trustedIssuers>](trustedissuers.md)|Lorsque l' `type` attribut spécifie le registre des noms d’émetteurs basés sur la <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> configuration (la classe), l' [ \<élément trustedIssuers >](trustedissuers.md) doit être spécifié. L' `<add>` `<clear>` [ \<élément trustedIssuers >](trustedissuers.md) peut prendre des éléments, `<remove>` ou en tant qu’éléments enfants.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.|  
  
## <a name="remarks"></a>Notes  
 Tous les jetons d’émetteur sont validés à l’aide d’un registre de noms d’émetteurs. Il s’agit d’un objet qui dérive <xref:System.IdentityModel.Tokens.IssuerNameRegistry> de la classe. Le registre des noms d’émetteurs est utilisé pour associer un nom mnémonique aux documents de chiffrement nécessaires à la vérification des signatures des jetons produits par l’émetteur correspondant. Le registre des noms d’émetteurs gère une liste des émetteurs qui sont approuvés par l’application de partie de confiance (RP). Le type du registre des noms d’émetteurs est spécifié à l' `type` aide de l’attribut. L' `<issuerNameRegistry>` élément peut avoir un ou plusieurs éléments enfants qui fournissent la configuration pour le type spécifié. Vous fournissez la logique qui traite ces éléments enfants en substituant <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> la méthode.  
  
 WIF fournit un type de registre de nom d’émetteur unique, la <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe. Cette classe utilise un ensemble de certificats d’émetteurs approuvés spécifiés dans la configuration. Il nécessite un élément de configuration enfant `<trustedIssuers>`,, sous lequel la collection de certificats d’émetteurs approuvés est configurée. Les certificats approuvés sont spécifiés à l’aide de la forme encodée ASN. 1 de l’empreinte numérique du certificat et sont ajoutés `<add>`ou `<clear>`supprimés de `<remove>` la collection à l’aide des éléments, ou.  
  
 L' `<issuerNameRegistry>` élément est représenté par la <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> classe.  
  
> [!NOTE]
> La spécification `<issuerNameRegistry>` de l’élément en tant qu’élément enfant de l' [ \<élément identityConfiguration >](identityconfiguration.md) a été dépréciée, mais est toujours prise en charge pour la compatibilité descendante. Les paramètres de `<securityTokenHandlerConfiguration>` l’élément remplacent ceux de `<identityConfiguration>` l’élément.  
  
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
