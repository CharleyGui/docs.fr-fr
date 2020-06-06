---
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: dc5c00a2204646863ae2570bb97b8d70e22a72d4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399186"
---
# \<userNameAuthentication>
Spécifie les informations d'identification d'un service selon le nom d'utilisateur et le mot de passe.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameAuthentication>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<xref:System.TimeSpan> qui spécifie la durée maximale de mise en cache d'un jeton. La valeur par défaut est 00:15:00.|  
|`cacheLogonTokens`|Valeur booléenne qui spécifie si les jetons d'ouverture de session sont mis en cache. Par défaut, il s’agit de `false`.|  
|`customUserNamePasswordValidatorType`|Chaîne qui spécifie le type de validateur de mot de passe de nom d'utilisateur personnalisé à utiliser. La valeur par défaut est une chaîne vide.|  
|`includeWindowsGroups`|Valeur booléenne qui spécifie si les groupes Windows sont inclus au contexte de sécurité. Par défaut, il s’agit de `true`.<br /><br /> L'affectation de la valeur `true` à cet attribut a un impact sur les performances du fait qu'elle provoque une expansion complète du groupe. Affectez la valeur `false` à cette propriété s'il n'est pas nécessaire d'établir la liste des groupes auxquels appartient un utilisateur.|  
|`maxCacheLogonTokens`|Entier qui spécifie le nombre maximal de jetons d'ouverture de session à mettre en cache. Cette valeur doit être supérieure à zéro. La valeur par défaut est 128.|  
|`membershipProviderName`|Lorsque l’attribut `clientCredentialType` d’une liaison a la valeur `username`, le nom d’utilisateur est mappé aux comptes Windows. Vous pouvez substituer ce comportement à l’aide de cet attribut, qui est une chaîne contenant le nom de la valeur <xref:System.Web.Security.MembershipProvider> qui fournit le mécanisme de validation du mot de passe pertinent.|  
|`userNamePasswordValidationMode`|Spécifie la manière dont le mot de passe de nom d'utilisateur est validé. Les valeurs autorisées sont :<br /><br /> -Windows<br />-MembershipProvider<br />-Personnalisé<br /><br /> Le paramètre par défaut est Windows. Cet attribut est de type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Spécifie l’information d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation de l’information d’identification du client.|  
  
## <a name="remarks"></a>Remarques  
 Si aucune des liaisons utilisées par un service n'est configurée pour l'authentification par nom d'utilisateur/mot de passe, les attributs de cet élément sont ignorés. Il s'agit notamment de `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName` et `userNamePasswordValidationMode`.  
  
 Si aucun des liaisons utilisées par un service n’est configurée pour utiliser l’authentification Windows par nom d’utilisateur/mot de passe, les paramètres en rapport avec la mise en cache des jetons d’ouverture de session sont ignorés. Il s'agit notamment de `cacheLogonTokenLifetime`, `cacheLogonTokens` et `maxCacheLogonTokens`.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
