---
title: Élément <generatePublisherEvidence>
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: b04ef53d6e9c3d954b0925ea8634b3d220b36af7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116569"
---
# <a name="generatepublisherevidence-element"></a>\<élément generatePublisherEvidence >
Spécifie si le runtime crée <xref:System.Security.Policy.Publisher> preuve pour la sécurité d’accès du code (CAS).  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<generatePublisherEvidence** >  
  
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
|`enabled`|Attribut requis.<br /><br /> Spécifie si le runtime crée <xref:System.Security.Policy.Publisher> preuve.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|valeur|Description|  
|-----------|-----------------|  
|`false`|Ne crée pas <xref:System.Security.Policy.Publisher> preuve.|  
|`true`|Crée <xref:System.Security.Policy.Publisher> preuve. Il s'agit de la valeur par défaut.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun(e).  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Dans le .NET Framework 4 et versions ultérieures, cet élément n’a aucun effet sur les temps de chargement des assemblys. Pour plus d’informations, consultez la section « simplification de la stratégie de sécurité » dans [modifications de sécurité](../../../security/security-changes.md).  
  
 Le common language runtime (CLR) tente de vérifier la signature Authenticode au moment du chargement pour créer <xref:System.Security.Policy.Publisher> preuve pour l’assembly. Toutefois, par défaut, la plupart des applications n’ont pas besoin de <xref:System.Security.Policy.Publisher> preuve. La stratégie CAS standard ne repose pas sur la <xref:System.Security.Policy.PublisherMembershipCondition>. Vous devez éviter les coûts de démarrage inutiles associés à la vérification de la signature de l’éditeur, sauf si votre application s’exécute sur un ordinateur avec une stratégie CAS personnalisée ou s’il a l’intention de satisfaire les demandes de <xref:System.Security.Permissions.PublisherIdentityPermission> dans un environnement de confiance partielle. (Les demandes d’autorisations d’identité fonctionnent toujours dans un environnement de confiance totale.)  
  
> [!NOTE]
> Nous recommandons que les services utilisent l’élément `<generatePublisherEvidence>` pour améliorer les performances de démarrage.  L’utilisation de cet élément peut également aider à éviter des retards qui peuvent entraîner un délai d’attente et l’annulation du démarrage du service.  
  
## <a name="configuration-file"></a>Fichier de configuration  
 Cet élément peut être utilisé uniquement dans le fichier de configuration de l’application.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser l’élément `<generatePublisherEvidence>` pour désactiver la vérification de la stratégie d’éditeur CAS pour une application.  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
