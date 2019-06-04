---
title: Élément <generatePublisherEvidence>
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a0861436ca727d63cdae58e3222826bf6414610
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489440"
---
# <a name="generatepublisherevidence-element"></a>\<generatePublisherEvidence > élément
Spécifie si le runtime crée <xref:System.Security.Policy.Publisher> preuve pour la sécurité d’accès de code (CAS).  
  
 \<configuration>  
\<runtime>  
\<generatePublisherEvidence>  
  
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
  
|Value|Description|  
|-----------|-----------------|  
|`false`|Ne crée pas <xref:System.Security.Policy.Publisher> preuve.|  
|`true`|Crée <xref:System.Security.Policy.Publisher> preuve. Il s'agit de la valeur par défaut.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Dans le .NET Framework 4 et versions ultérieures, cet élément n’a aucun effet sur les temps de chargement d’assembly. Pour plus d’informations, consultez la section « Simplification de la stratégie sécurité » dans [modifications de sécurité](../../../../../docs/framework/security/security-changes.md).  
  
 Le common language runtime (CLR) essaie de vérifier la signature Authenticode au moment du chargement pour créer <xref:System.Security.Policy.Publisher> preuve pour l’assembly. Toutefois, par défaut, la plupart des applications ne doivent pas <xref:System.Security.Policy.Publisher> preuve. La stratégie CAS standard ne repose pas sur le <xref:System.Security.Policy.PublisherMembershipCondition>. Vous devez éviter le coût de démarrage inutile associé à la vérification de la signature de serveur de publication, sauf si votre application s’exécute sur un ordinateur avec la stratégie CAS personnalisée ou projette de répondre aux exigences pour <xref:System.Security.Permissions.PublisherIdentityPermission> dans un environnement de confiance partielle. (Demandes d’autorisations d’identité aboutissent toujours dans un environnement de confiance totale.)  
  
> [!NOTE]
>  Nous recommandons que les services utilisent le `<generatePublisherEvidence>` élément pour améliorer les performances de démarrage.  À l’aide de cet élément peut également aider à éviter les retards qui peuvent entraîner un délai d’attente et l’annulation du démarrage du service.  
  
## <a name="configuration-file"></a>Fichier de configuration  
 Cet élément peut être utilisé uniquement dans le fichier de configuration d’application.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `<generatePublisherEvidence>` élément pour désactiver la vérification de la stratégie de serveur de publication d’autorités de certification pour une application.  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)
