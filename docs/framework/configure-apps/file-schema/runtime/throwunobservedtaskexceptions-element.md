---
title: Élément <ThrowUnobservedTaskExceptions>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb6cfc8e1c3f0409d99d31efa0a645476b47e45e
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456254"
---
# <a name="throwunobservedtaskexceptions-element"></a>\<ThrowUnobservedTaskExceptions > élément
Indique si les exceptions de tâches non gérées doivent arrêter un processus en cours d’exécution.  
  
 \<configuration>  
\<runtime>  
\<ThrowUnobservedTaskExceptions>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si les exceptions de tâche non gérée doivent s’arrêter le processus en cours d’exécution.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Value|Description|  
|-----------|-----------------|  
|`false`|N’arrête pas le processus en cours d’exécution pour une exception de tâche non prise en charge. Il s'agit de la valeur par défaut.|  
|`true`|Met fin au processus en cours d’exécution pour une exception de tâche non prise en charge.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
|||  
  
## <a name="remarks"></a>Notes  
 Si une exception qui est associée à un <xref:System.Threading.Tasks.Task> n’a pas été observée, il existe aucune <xref:System.Threading.Tasks.Task.Wait%2A> opération, le parent n’est pas attachée et le <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> propriété Impossible de lire l’exception de la tâche est considérée comme défaillante.  
  
 Dans le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], par défaut, si un <xref:System.Threading.Tasks.Task> qui a une prise en charge exception collecté, le finaliseur lève une exception et met fin au processus. L’arrêt du processus est déterminée par le minutage du garbage collection et la finalisation.  
  
 Pour le rendre plus facile pour les développeurs d’écrire du code asynchrone basé sur les tâches, le .NET Framework 4.5 modifie ce comportement par défaut pour les exceptions non prise en charge. Non prises en charge les exceptions d’entraîner la <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> événement est déclenché, mais par défaut, le processus s’arrête. Au lieu de cela, l’exception est ignorée une fois que l’événement est déclenché, indépendamment de si un gestionnaire d’événements observe l’exception.  
  
 Dans le .NET Framework 4.5, vous pouvez utiliser la [ \<ThrowUnobservedTaskExceptions > élément](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) dans un fichier de configuration d’application pour activer le comportement de .NET Framework 4 de lever une exception.  
  
 Vous pouvez également spécifier le comportement d’exception dans une des manières suivantes :  
  
- En définissant la variable d’environnement `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).  
  
- En définissant le Registre DWORD, valeur ThrowUnobservedTaskExceptions = 1 dans les clés HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework clé.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment activer la levée d’exceptions des tâches à l’aide d’un fichier de configuration d’application.  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment une propagation de l’exception est levée à partir d’une tâche. Le code doit être exécuté comme un programme lancé fonctionne correctement.  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)
