---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 32aad3529ded6d0234b1bcb388ecbbc3b0a11c87
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944271"
---
# <a name="trustedissuers"></a>\<trustedIssuers>
Configure la liste des certificats d’émetteurs approuvés utilisés par le registre des noms d’émetteurs basés sur la configuration<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>().  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration>  
\<issuerNameRegistry>  
\<trustedIssuers>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry>  
          <trustedIssuers>  
            <add thumbprint=xs:string name=xs:string>  
            <clear>  
            <remove thumbprint=xs:string>  
          </trustedIssuers>  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|Ajoute un certificat à la collection d’émetteurs approuvés. Le certificat est spécifié avec l' `thumbprint` attribut. Cet attribut est obligatoire et doit contenir la forme encodée ASN. 1 de l’empreinte numérique du certificat. L' `name` attribut est facultatif et peut être utilisé pour spécifier un nom convivial pour le certificat.|  
|`<clear>`|Efface tous les certificats de la collection d’émetteurs approuvés.|  
|`<remove thumbprint=xs:string>`|Supprime un certificat de la collection d’émetteurs approuvés. Le certificat est spécifié avec l' `thumbprint` attribut. Cet attribut est obligatoire.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<issuerNameRegistry>](issuernameregistry.md)|Configure le registre des noms d’émetteurs. **Important :**  L' `type` attribut de l' `<issuerNameRegistry>` élément doit faire référence <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> à la classe `<trustedIssuers>` pour que l’élément soit valide.|  
  
## <a name="remarks"></a>Notes  
 Windows Identity Foundation (WIF) fournit une implémentation unique de <xref:System.IdentityModel.Tokens.IssuerNameRegistry> la classe prête à l’emploi, <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> la classe. Le registre des noms d’émetteurs de configuration gère une liste d’émetteurs approuvés qui est chargée à partir de la configuration. La liste associe chaque nom d’émetteur au certificat X. 509 nécessaire pour vérifier la signature des jetons produits par l’émetteur. La liste des certificats d’émetteurs approuvés est spécifiée sous l' `<trustedIssuers>` élément. Chaque élément de la liste associe un nom d’émetteur mnémonique au certificat X. 509 nécessaire pour vérifier la signature des jetons produits par l’émetteur. Les certificats approuvés sont spécifiés à l’aide de la forme encodée ASN. 1 de l’empreinte numérique du certificat `<add>` et sont ajoutés à la collection à l’aide de l’élément. Vous pouvez effacer ou supprimer les émetteurs (certificats) de la liste à l’aide `<clear>` des `<remove>` éléments et.  
  
 L' `type` attribut de l' `<issuerNameRegistry>` élément doit faire référence <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> à la classe `<trustedIssuers>` pour que l’élément soit valide.  
  
## <a name="example"></a>Exemple  
 Le code XML suivant montre comment spécifier le registre des noms d’émetteurs basés sur la configuration.  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
