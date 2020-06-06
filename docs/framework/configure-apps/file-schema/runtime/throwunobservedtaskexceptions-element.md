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
ms.openlocfilehash: de5a686bcbd88fc52173b488103f033575623d62
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153813"
---
# <a name="throwunobservedtaskexceptions-element"></a>Élément \<ThrowUnobservedTaskExceptions>
Indique si les exceptions de tâches non gérées doivent arrêter un processus en cours d’exécution.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**  
  
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
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|N’arrête pas le processus en cours d’exécution pour une exception de tâche non gérée. Il s'agit de la valeur par défaut.|  
|`true`|Met fin au processus en cours d’exécution pour une exception de tâche non gérée.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
|||  
  
## <a name="remarks"></a>Remarques  
 Si une exception associée à un n' <xref:System.Threading.Tasks.Task> a pas été observée, il n’y a aucune <xref:System.Threading.Tasks.Task.Wait%2A> opération, le parent n’est pas attaché et la <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> propriété n’a pas été lue. l’exception de tâche est considérée comme non prise en compte.  
  
 Dans le .NET Framework 4, par défaut, si un <xref:System.Threading.Tasks.Task> qui a une exception non prise en compte est récupéré par le garbage collector, le finaliseur lève une exception et met fin au processus. L’arrêt du processus est déterminé par le minutage de la garbage collection et de la finalisation.  
  
 Pour permettre aux développeurs d’écrire plus facilement du code asynchrone basé sur des tâches, le .NET Framework 4,5 modifie ce comportement par défaut pour les exceptions non prises en compte. Les exceptions non prises en même temps entraînent le <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> déclenchement de l’événement, mais par défaut, le processus ne se termine pas. Au lieu de cela, l’exception est ignorée une fois que l’événement est déclenché, qu’un gestionnaire d’événements observe l’exception ou non.  
  
 Dans le .NET Framework 4,5, vous pouvez utiliser l' [ \<ThrowUnobservedTaskExceptions> élément](throwunobservedtaskexceptions-element.md) dans un fichier de configuration de l’application pour permettre au comportement .NET Framework 4 de lever une exception.  
  
 Vous pouvez également spécifier le comportement de l’exception de l’une des manières suivantes :  
  
- En définissant la variable d’environnement `COMPlus_ThrowUnobservedTaskExceptions` ( `set COMPlus_ThrowUnobservedTaskExceptions=1` ).  
  
- En définissant la valeur de Registre DWORD ThrowUnobservedTaskExceptions = 1 dans le HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft \\ . Clé NETFramework.  
  
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
- [Schéma du fichier de configuration](../index.md)
