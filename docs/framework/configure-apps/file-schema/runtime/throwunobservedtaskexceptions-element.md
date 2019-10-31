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
ms.openlocfilehash: 99eef6b8c264e21df7f4ecf9fc79dc607d484a0a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115421"
---
# <a name="throwunobservedtaskexceptions-element"></a>\<élément ThrowUnobservedTaskExceptions >
Indique si les exceptions de tâches non gérées doivent arrêter un processus en cours d’exécution.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<ThrowUnobservedTaskExceptions** >  
  
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
|`enabled`|Attribut requis.<br /><br /> Spécifie si les exceptions de tâche non gérée doivent mettre fin au processus en cours d’exécution.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|valeur|Description|  
|-----------|-----------------|  
|`false`|N’arrête pas le processus en cours d’exécution pour une exception de tâche non gérée. Il s'agit de la valeur par défaut.|  
|`true`|Met fin au processus en cours d’exécution pour une exception de tâche non gérée.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun(e).  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
|||  
  
## <a name="remarks"></a>Notes  
 Si une exception associée à un <xref:System.Threading.Tasks.Task> n’a pas été observée, il n’y a aucune opération <xref:System.Threading.Tasks.Task.Wait%2A>, le parent n’est pas attaché et la propriété <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> n’a pas été lue. l’exception de tâche est considérée comme non prise en compte.  
  
 Dans le .NET Framework 4, par défaut, si une <xref:System.Threading.Tasks.Task> qui a une exception non prise en compte est récupérée par le garbage collector, le finaliseur lève une exception et met fin au processus. L’arrêt du processus est déterminé par le minutage de la garbage collection et de la finalisation.  
  
 Pour permettre aux développeurs d’écrire plus facilement du code asynchrone basé sur des tâches, le .NET Framework 4,5 modifie ce comportement par défaut pour les exceptions non prises en compte. Les exceptions non prises en même temps entraînent le déclenchement de l’événement <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException>, mais par défaut, le processus ne se termine pas. Au lieu de cela, l’exception est ignorée une fois que l’événement est déclenché, qu’un gestionnaire d’événements observe l’exception ou non.  
  
 Dans le .NET Framework 4,5, vous pouvez utiliser l' [élément\<ThrowUnobservedTaskExceptions >](throwunobservedtaskexceptions-element.md) dans un fichier de configuration de l’application pour permettre au comportement .NET Framework 4 de lever une exception.  
  
 Vous pouvez également spécifier le comportement de l’exception de l’une des manières suivantes :  
  
- En définissant la variable d’environnement `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).  
  
- En définissant la valeur de Registre DWORD ThrowUnobservedTaskExceptions = 1 dans le\\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft. Clé NETFramework.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment activer la levée d’exceptions dans des tâches à l’aide d’un fichier de configuration de l’application.  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment une exception non détectée est levée à partir d’une tâche. Le code doit être exécuté comme un programme libéré pour fonctionner correctement.  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
