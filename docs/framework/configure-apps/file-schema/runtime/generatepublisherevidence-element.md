---
title: Élément <generatePublisherEvidence>
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: 11592b055641c0fa2d2b968547dcc5aa40c94600
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541782"
---
# <a name="generatepublisherevidence-element"></a>Élément \<generatePublisherEvidence>
Spécifie si le runtime crée une <xref:System.Security.Policy.Publisher> preuve pour la sécurité d’accès du code (cas).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<generatePublisherEvidence
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si le runtime crée une <xref:System.Security.Policy.Publisher> preuve.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Value|Description|  
|-----------|-----------------|  
|`false`|Ne crée pas de <xref:System.Security.Policy.Publisher> preuve.|  
|`true`|Crée une <xref:System.Security.Policy.Publisher> preuve. Il s’agit de la valeur par défaut.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Dans le .NET Framework 4 et versions ultérieures, cet élément n’a aucun effet sur les temps de chargement des assemblys. Pour plus d’informations, consultez la section « simplification de la stratégie de sécurité » dans [modifications de sécurité](/previous-versions/dotnet/framework/security/security-changes).  
  
 Le common language runtime (CLR) tente de vérifier la signature Authenticode au moment du chargement pour créer <xref:System.Security.Policy.Publisher> la preuve de l’assembly. Toutefois, par défaut, la plupart des applications n’ont pas besoin de <xref:System.Security.Policy.Publisher> preuve. La stratégie CAS standard ne repose pas sur <xref:System.Security.Policy.PublisherMembershipCondition> . Vous devez éviter les coûts de démarrage inutiles associés à la vérification de la signature de l’éditeur, sauf si votre application s’exécute sur un ordinateur doté d’une stratégie CAS, ou s’il a l’intention de satisfaire les demandes de <xref:System.Security.Permissions.PublisherIdentityPermission> dans un environnement de confiance partielle. (Les demandes d’autorisations d’identité fonctionnent toujours dans un environnement de confiance totale.)  
  
> [!NOTE]
> Nous recommandons que les services utilisent l' `<generatePublisherEvidence>` élément pour améliorer les performances de démarrage.  L’utilisation de cet élément peut également aider à éviter des retards qui peuvent entraîner un délai d’attente et l’annulation du démarrage du service.  
  
## <a name="configuration-file"></a>Fichier de configuration  
 Cet élément peut être utilisé uniquement dans le fichier de configuration de l’application.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment utiliser l' `<generatePublisherEvidence>` élément pour désactiver la vérification de la stratégie d’éditeur cas pour une application.  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma du fichier de configuration](../index.md)
