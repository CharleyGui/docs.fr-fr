---
title: <wsFederation>
ms.date: 03/30/2017
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
author: BrucePerlerMS
ms.openlocfilehash: 53f3943524c45a43ddb60553b8ff45f19df66b14
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152461"
---
# \<wsFederation>
Fournit la configuration pour le <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
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
|authenticationType|URI qui spécifie le type d'authentification. Définit le paramètre wauth de demande de connexion WS-Federation. facultatif. La valeur par défaut est une chaîne vide, qui spécifie que le paramètre wauth n’est pas inclus dans la demande.|  
|actualisation|Âge maximal souhaité des demandes d'authentification, en minutes. Définit le paramètre wfresh de demande de connexion WS-Federation. facultatif. La valeur par défaut est 0. facultatif. **Avertissement :**  Dans la prochaine version de .NET Framework 4,5, l' `freshness` attribut sera de type `xs:string` et sa valeur par défaut sera `null` .|  
|homeRealm|Domaine d’hébergement du fournisseur d’identité (IdP) à utiliser pour l’authentification. Définit le paramètre whr de demande de connexion WS-Federation. facultatif. La valeur par défaut est une chaîne vide, qui spécifie que le paramètre WHR n’est pas inclus dans la demande.|  
|émetteur|URI de l’émetteur de jeton prévu. Définit l’URL de base des demandes de connexion WS-Federation et des demandes de déconnexion requises.|  
|persistentCookiesOnPassiveRedirects|Spécifie si les cookies persistants sont émis lors de l’authentification. facultatif. La valeur par défaut est « false », les cookies ne sont pas émis.|  
|passiveRedirectEnabled|Spécifie si le WSFAM est activé pour rediriger automatiquement les demandes non autorisées vers un STS. facultatif. La valeur par défaut est « true », les demandes non autorisées sont automatiquement redirigées.|  
|policy|URL qui spécifie l’emplacement de la stratégie appropriée à utiliser lors des demandes de connexion. La valeur par défaut est une chaîne vide. Définit le paramètre wp de demande de connexion WS-Federation. facultatif. La valeur par défaut est une chaîne vide, qui spécifie que le paramètre WP n’est pas inclus dans la demande.|  
|realm|URI du domaine demandeur. (URI qui identifie la partie de confiance (RP) au service d’émission de jeton de sécurité (STS).) Définit le paramètre de demande de connexion WS-Federation de la demande wtrealm. Obligatoire.|  
|réponse|URL qui identifie l'adresse de préférence de l'application de partie de confiance (RP) pour recevoir des réponses du service d'émission de jeton de sécurité (Security Token Service STS). Définit le paramètre wreply de demande de connexion WS-Federation. facultatif. La valeur par défaut est une chaîne vide, qui spécifie que le paramètre wreply n’est pas inclus dans la demande.|  
|request|Demande d’émission de jeton. Définit le paramètre wreq de demande de connexion WS-Federation. facultatif. La valeur par défaut est une chaîne vide, qui spécifie que le paramètre wreq n’est pas inclus dans la demande. Si vous n’incluez pas le paramètre wreq ou wreqptr dans la demande, le STS sait quel type de jeton doit être émis.|  
|requestPtr|URL qui spécifie l'emplacement de la demande d'émission de jeton. Définit le paramètre wreqptr de la requête. facultatif. La valeur par défaut est une chaîne vide, qui spécifie que le paramètre wreqptr n’est pas inclus dans la demande. Si vous n’incluez pas le paramètre wreq ou wreqptr dans la demande, le STS sait quel type de jeton doit être émis.|  
|requireHttps|Spécifie si la communication avec le service d’émission de jeton de sécurité (STS) doit utiliser le protocole HTTPs. facultatif. La valeur par défaut est « true ». HTTPs doit être utilisé.|  
|resource|URI qui identifie la ressource faisant l'objet d'une tentative d'accès, de la partie de confiance (RP) au service d'émission de jeton de sécurité (STS). facultatif. Définit le paramètre wres de demande de connexion WS-Federation. facultatif. La valeur par défaut est une chaîne vide, qui spécifie que le paramètre wres n’est pas inclus dans la demande. **Remarque :** wres est un paramètre hérité. Spécifiez l' `realm` attribut pour utiliser le paramètre wtrealm à la place.|  
|signInQueryString|Fournit un point d’extensibilité pour spécifier les paramètres de requête définis par l’application dans l’URL de demande de connexion WS-Federation. facultatif. La valeur par défaut est une chaîne vide, qui spécifie qu’aucun paramètre supplémentaire ne doit être inclus dans la demande. Les paramètres sont spécifiés en tant que fragments de chaîne de requête en utilisant la forme suivante : `"param1=value1&param2=value2&param3=value3"` et ainsi de suite. **Remarque :**  Dans un fichier de configuration, le caractère « & » dans la chaîne de requête doit être spécifié à l’aide de sa référence d’entité, `&` .|  
|signOutQueryString|Fournit un point d’extensibilité pour spécifier les paramètres de requête définis par l’application dans l’URL de demande de connexion WS-Federation. facultatif. La valeur par défaut est une chaîne vide, qui spécifie qu’aucun paramètre supplémentaire ne doit être inclus dans la demande. Les paramètres sont spécifiés en tant que fragments de chaîne de requête en utilisant la forme suivante : `"param1=value1&param2=value2&param3=value3"` et ainsi de suite. **Remarque :**  Dans un fichier de configuration, le caractère « & » dans la chaîne de requête doit être spécifié à l’aide de sa référence d’entité, `&` .|  
|signOutReply|Spécifie l’URL vers laquelle le client doit être redirigé par le service d’émission de jeton de sécurité (STS) lors de la déconnexion passive via le protocole WS-Federation. Définit le paramètre wreply sur une demande de déconnexion WS-Federation. facultatif. La valeur par défaut est une chaîne vide, qui spécifie qu’aucun paramètre supplémentaire ne doit être inclus dans la demande.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucune  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|Contient les paramètres qui configurent le <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) et le <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam).|  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez utiliser l' `<wsFederation>` élément pour configurer les paramètres par défaut des paramètres WS-Federation et le comportement par défaut pour le WSFAM. Les paramètres de paramètre WS-Federation définis sous l' `<wsFederation>` élément définissent les propriétés équivalentes exposées par la <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> classe. Ces propriétés restent les mêmes pour chaque requête émise par WSFAM. Vous pouvez modifier dynamiquement les paramètres WS-Federation lors du traitement de la demande en ajoutant des gestionnaires d’événements pour les événements exposés par WSFAM. par exemple, l' <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> événement. Pour plus d’informations, consultez la documentation de la <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> classe.  
  
 L' `<wsFederation>` élément est représenté par la <xref:System.IdentityModel.Services.Configuration.WSFederationElement> classe. L’objet de configuration lui-même est représenté par la <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> classe. Une seule <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> instance est définie sur l' <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> objet accessible via la <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> propriété et fournit la configuration pour WSFAM.  
  
## <a name="example"></a>Exemple  
 Le code XML suivant montre un `<wsFederation>` élément qui spécifie les paramètres de WSFAM.  
  
> [!WARNING]
> Dans cet exemple, le WSFAM n’est pas requis pour utiliser HTTPs. Cela est dû au fait que l' `requireHttps` attribut de l' `<wsFederation>` élément est défini `false` . Ce paramètre n’est pas recommandé pour la plupart des environnements de production, car il peut présenter un risque pour la sécurité.  
  
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
