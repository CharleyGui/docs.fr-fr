---
title: Élément <generatePublisherEvidence>
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: 24a5ea02992a5bce681b5bab4fb7f75505bd225d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154112"
---
# <a name="generatepublisherevidence-element"></a>\<generatePublisherEvidence> Element
Précise si le temps <xref:System.Security.Policy.Publisher> d’exécution crée des preuves pour la sécurité d’accès au code (CAS).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<générerPublisherEvidence>**  
  
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
|`enabled`|Attribut requis.<br /><br /> Précise si le temps <xref:System.Security.Policy.Publisher> d’exécution crée des preuves.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|Ne crée <xref:System.Security.Policy.Publisher> pas de preuves.|  
|`true`|Crée <xref:System.Security.Policy.Publisher> des preuves. Il s’agit de la valeur par défaut.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## <a name="remarks"></a>Notes   
  
> [!NOTE]
> Dans le cadre .NET 4 et plus tard, cet élément n’a aucun effet sur les temps de chargement d’assemblage. Pour plus d’informations, consultez la section « Simplification de la politique de sécurité » dans [les changements de sécurité](../../../security/security-changes.md).  
  
 Le temps courant de course de langue (CLR) essaye <xref:System.Security.Policy.Publisher> de vérifier la signature Authenticode au moment de la charge pour créer des preuves pour l’assemblage. Toutefois, par défaut, la <xref:System.Security.Policy.Publisher> plupart des applications n’ont pas besoin de preuves. La politique standard de <xref:System.Security.Policy.PublisherMembershipCondition>la SAE ne repose pas sur le . Vous devez éviter les coûts inutiles de démarrage associés à la vérification de la signature de l’éditeur <xref:System.Security.Permissions.PublisherIdentityPermission> à moins que votre application ne s’exécute sur un ordinateur avec la politique de CAS personnalisée, ou a l’intention de satisfaire les demandes dans un environnement de confiance partielle. (Les demandes d’autorisations d’identité réussissent toujours dans un environnement de confiance.)  
  
> [!NOTE]
> Nous recommandons que `<generatePublisherEvidence>` les services utilisent cet élément pour améliorer les performances des startups.  L’utilisation de cet élément peut également aider à éviter les retards qui peuvent entraîner un délai d’utilisation et l’annulation de la start-up de service.  
  
## <a name="configuration-file"></a>Fichier de configuration  
 Cet élément ne peut être utilisé que dans le fichier de configuration d’application.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre `<generatePublisherEvidence>` comment utiliser l’élément pour désactiver la vérification de la politique d’éditeur de la SAE pour une demande.  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d'exécution](index.md)
- [Configuration Fichier Schema](../index.md)
