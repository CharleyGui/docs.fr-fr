---
title: <wsFederation>
ms.date: 03/30/2017
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
author: BrucePerlerMS
ms.openlocfilehash: 53f3943524c45a43ddb60553b8ff45f19df66b14
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152461"
---
# <a name="wsfederation"></a>\<wsFederation>
Fournit la <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> configuration pour le (WSFAM).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<fédérationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsFederation>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
<system.identityModel.services>  
  <federationConfiguration>  
    <wsFederation authenticationType=xs:string (URI)  
                  freshness=xs:decimal  
                  homerealm=xs:string (URI)  
                  issuer=xs:string (URI)  
                  persistentCookiesOnPassiveRedirects=xs:boolean  
                  passiveRedirectEnabled=xs:boolean  
                  policy=xs:string (URI)  
                  realm=xs:string (URI)  
                  reply=xs:string (URI)  
                  request=xs:string (URI)  
                  requestPtr=xs:string (URI)  
                  requireHttps=xs:boolean  
                  resource=xs:string (URI)  
                  signInQueryString=xs:string  
                  signOutQueryString=xs:string  
                  signOutReply=xs:string (URL)  
    </wsFederation>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|authenticationType|URI qui spécifie le type d'authentification. Définit le paramètre WS-Federation demande d’inscription wauth. facultatif. La valeur par défaut est une chaîne vide, qui précise que le paramètre wauth n’est pas inclus dans la demande.|  
|Fraîcheur|Âge maximal souhaité des demandes d'authentification, en minutes. Définit le paramètre wfresh de demande de connexion WS-Federation. facultatif. La valeur par défaut est 0. facultatif. **Avertissement:**  Dans la prochaine version de .NET Framework `freshness` 4.5, l’attribut sera de type `xs:string` et sa valeur par défaut sera `null`.|  
|homeRealm|Le domaine de la maison du fournisseur d’identité (IdP) à utiliser pour l’authentification. Définit le paramètre whr de demande de connexion WS-Federation. facultatif. La valeur par défaut est une chaîne vide, qui précise que le paramètre whr n’est pas inclus dans la demande.|  
|émetteur|L’URI de l’émetteur de jetons prévu. Définit l’URL de base des demandes d’inscription WS-Federation et les demandes d’inscription requises.|  
|persistantCookiesOnPassiveRedirects|Précise si les cookies persistants sont émis sur l’authentification. facultatif. La valeur par défaut est "fausse", les cookies ne sont pas émis.|  
|passiveRedirectEnabled|Précise si le WSFAM est activé pour rediriger automatiquement les demandes non autorisées vers un STS. facultatif. La valeur par défaut est "vraie", les demandes non autorisées sont automatiquement redirigées.|  
|policy|Une URL qui spécifie l’emplacement de la stratégie pertinente à utiliser sur les demandes d’inscription. La valeur par défaut est une chaîne vide. Définit le paramètre wp de demande de connexion WS-Federation. facultatif. La valeur par défaut est une chaîne vide, qui précise que le paramètre wp n’est pas inclus dans la demande.|  
|realm|L’URI du royaume demandé. (Un URI qui identifie la partie qui compte (RP) au service de jetons de sécurité (STS).) Définit le paramètre de demande wtrealm WS-Federation. Obligatoire.|  
|Réponse|URL qui identifie l'adresse de préférence de l'application de partie de confiance (RP) pour recevoir des réponses du service d'émission de jeton de sécurité (Security Token Service STS). Définit le paramètre WS-Federation de la demande de connexion. facultatif. La valeur par défaut est une chaîne vide, qui précise que le paramètre wreply n’est pas inclus dans la demande.|  
|request|La demande d’émission de jetons. Définit le paramètre wreq de demande de connexion WS-Federation. facultatif. La valeur par défaut est une chaîne vide, qui précise que le paramètre wreq n’est pas inclus dans la demande. L’inclusion du wreq ou du paramètre wreqptr dans la demande implique que la STS sait quel genre de jeton émettre.|  
|requestPtr|URL qui spécifie l'emplacement de la demande d'émission de jeton. Définit le paramètre wreqptr de demande. facultatif. La valeur par défaut est une chaîne vide, qui précise que le paramètre wreqptr n’est pas inclus dans la demande. L’inclusion du wreq ou du paramètre wreqptr dans la demande implique que la STS sait quel genre de jeton émettre.|  
|besoinHttps|Précise si la communication avec le service de jetons de sécurité (STS) doit utiliser le protocole HTTPS. facultatif. La valeur par défaut est "vraie", HTTPS doit être utilisé.|  
|resource|URI qui identifie la ressource faisant l'objet d'une tentative d'accès, de la partie de confiance (RP) au service d'émission de jeton de sécurité (STS). facultatif. Définit le paramètre de demande de connexion WS-Federation wres. facultatif. La valeur par défaut est une chaîne vide, qui précise que le paramètre wres n’est pas inclus dans la demande. **Remarque :** les wres sont un paramètre hérité. Spécifiez l’attribut `realm` pour utiliser le paramètre wtrealm à la place.|  
|signInQueryString|Fournit un point d’extensibility pour spécifier les paramètres de requête définis par l’application dans l’URL de demande de connexion WS-Federation. facultatif. La valeur par défaut est une chaîne vide, qui précise qu’aucun paramètre supplémentaire ne doit être inclus dans la demande. Les paramètres sont spécifiés comme un fragment de `"param1=value1&param2=value2&param3=value3"` chaîne de requête en utilisant la forme suivante: et ainsi de suite. **Note:**  Dans un fichier de configuration, le caractère « & » de la `&`chaîne de requête doit être spécifié à l’aide de sa référence d’entité.|  
|signOutQueryString|Fournit un point d’extensibility pour spécifier les paramètres de requête définis par l’application dans l’URL de demande de connexion WS-Federation. facultatif. La valeur par défaut est une chaîne vide, qui précise qu’aucun paramètre supplémentaire ne doit être inclus dans la demande. Les paramètres sont spécifiés comme un fragment de `"param1=value1&param2=value2&param3=value3"` chaîne de requête en utilisant la forme suivante: et ainsi de suite. **Note:**  Dans un fichier de configuration, le caractère « & » de la `&`chaîne de requête doit être spécifié à l’aide de sa référence d’entité.|  
|signOutReply|Spécifie l’URL vers laquelle le client doit être redirigé par le service de jetons de sécurité (STS) lors d’une connexion passive par le protocole WS-Federation. Définit le paramètre wreply sur une demande de signature WS-Federation. facultatif. La valeur par défaut est une chaîne vide, qui précise qu’aucun paramètre supplémentaire ne doit être inclus dans la demande.|  
  
### <a name="child-elements"></a>Éléments enfants  
 None  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<fédérationConfiguration>](federationconfiguration.md)|Contient les paramètres <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> qui configurent le <xref:System.IdentityModel.Services.SessionAuthenticationModule> (WSFAM) et le (SAM).|  
  
## <a name="remarks"></a>Notes   
 Vous pouvez `<wsFederation>` utiliser l’élément pour configurer les paramètres par défaut de la WS-Federation et le comportement par défaut pour le WSFAM. Paramètres de paramètres WS-Federation définis sous `<wsFederation>` <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> l’élément définis propriétés équivalentes exposées par la classe. Ces propriétés restent les mêmes pour chaque demande émise par le WSFAM. Vous pouvez modifier dynamiquement les paramètres de la WS-Federation pendant le traitement des demandes en ajoutant des gestionnaires d’événements pour les événements exposés par WSFAM; par exemple, <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> l’événement. Pour plus d’informations, <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> consultez la documentation de la classe.  
  
 L’élément `<wsFederation>` est représenté <xref:System.IdentityModel.Services.Configuration.WSFederationElement> par la classe. L’objet de configuration lui-même est représenté par la <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> classe. Une <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> seule instance est <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> réglée sur l’objet qui est accessible par la <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> propriété et fournit la configuration pour le WSFAM.  
  
## <a name="example"></a> Exemple  
 Le XML suivant `<wsFederation>` montre un élément qui spécifie les paramètres pour le WSFAM.  
  
> [!WARNING]
> Dans cet exemple, le WSFAM n’est pas tenu d’utiliser HTTPS. C’est `requireHttps` parce que `<wsFederation>` l’attribut sur l’élément est défini `false`. Ce paramètre n’est pas recommandé pour la plupart des environnements de production car il peut présenter un risque pour la sécurité.  
  
```xml
<wsFederation passiveRedirectEnabled="true"
              issuer="http://localhost:15839/wsFederationSTS/Issue"
              realm="http://localhost:50969/"
              reply="http://localhost:50969/"
              requireHttps="false"
              signOutReply="http://localhost:50969/SignedOutPage.html"
              signOutQueryString="Param1=value2&Param2=value2"
              persistentCookiesOnPassiveRedirects="true" />
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
