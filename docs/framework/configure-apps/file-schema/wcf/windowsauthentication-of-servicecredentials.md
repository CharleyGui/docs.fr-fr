---
title: <windowsAuthentication> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: 81793b0d58a95166bc23f98d46ce94a5f1e1d018
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940288"
---
# <a name="windowsauthentication-of-servicecredentials"></a>\<> WindowsAuthentication du \<> ServiceCredentials
Spécifie les paramètres d'une information d'identification de service Windows.  
  
 \<system.ServiceModel>  
\<behaviors>  
\<serviceBehaviors>  
\<> de comportement  
\<serviceCredentials>  
\<windowsAuthentication>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`includeWindowsGroups`|Attribut à valeur booléenne facultatif qui spécifie si le système inclut des groupes Windows dans le contexte de sécurité. Par défaut, il s’agit de `true`.<br /><br /> L'affectation de la valeur `true` à cet attribut a un impact sur les performances du fait qu'elle provoque une expansion complète du groupe. Affectez la valeur `false` à cet attribut s'il n'est pas nécessaire d'établir la liste des groupes auxquels appartient un utilisateur.|  
|`allowAnonymousLogons`|Attribut à valeur booléenne facultatif qui spécifie si les appelants anonymes et non authentifiés sont autorisés. Par défaut, il s’agit de `false`.<br /><br /> Lorsque l’attribut `clientCredentialType` d’une liaison a la valeur `Windows`, le système n’autorise pas d’appelants anonymes. Cela signifie que seuls les appelants authentifiés du domaine ou du groupe de travail sont autorisés à accéder au système. Vous pouvez substituer ce comportement en utilisant cet attribut.<br /><br /> N'utilisez ce paramètre qu'avec beaucoup de précaution.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Spécifie les informations d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d’identification du client.|  
  
## <a name="remarks"></a>Notes  
 Utilisez cet élément pour autoriser l'accès d'utilisateurs Windows anonymes en définissant l'attribut `allowAnonymousLogons`. Vous pouvez également indiquer s'il faut inclure des informations sur les groupes auxquels les utilisateurs appartiennent dans AuthorizationContext en définissant l'attribut `includeWindowsGroups`. Si ce dernier a la valeur `true` (paramètre par défaut), le service peut déterminer les groupes Windows auxquels le client appartient.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
