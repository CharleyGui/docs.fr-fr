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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153813"
---
# <a name="throwunobservedtaskexceptions-element"></a>\<ThrowUnobservedTaskExceptions> Element
Indique si les exceptions de tâches non gérées doivent arrêter un processus en cours d’exécution.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)\
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
|`enabled`|Attribut requis.<br /><br /> Précise si les exceptions de tâches non gérées devraient mettre fin au processus de fonctionnement.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|Ne met pas fin au processus de fonctionnement pour une exception de tâche non gérée. Il s’agit de la valeur par défaut.|  
|`true`|Termine le processus de fonctionnement pour une exception de tâche non gérée.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
|||  
  
## <a name="remarks"></a>Notes   
 Si une exception associée <xref:System.Threading.Tasks.Task> à un n’a <xref:System.Threading.Tasks.Task.Wait%2A> pas été observée, il n’y a pas d’opération, le parent n’est pas attaché, et le <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> bien n’a pas lu l’exception de tâche est considérée comme non observée.  
  
 Dans le cadre .NET 4, <xref:System.Threading.Tasks.Task> par défaut, si une exception non observée est les ordures collectées, le finalisateur jette une exception et met fin au processus. La fin du processus est déterminée par le moment de la collecte et de la finalisation des ordures.  
  
 Pour faciliter l’écriture de code asynchrone pour les développeurs en fonction des tâches, le cadre .NET 4.5 modifie ce comportement par défaut pour des exceptions non observées. Les exceptions non observées font toujours augmenter l’événement, <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> mais par défaut, le processus ne prend pas fin. Au lieu de cela, l’exception est ignorée après que l’événement est soulevé, peu importe si un gestionnaire d’événement observe l’exception.  
  
 Dans le cadre .NET 4.5, vous pouvez utiliser le [ \<ThrowUnobservedTaskExceptions> élément](throwunobservedtaskexceptions-element.md) dans un fichier de configuration d’application pour activer le comportement .NET Framework 4 de jeter une exception.  
  
 Vous pouvez également spécifier le comportement d’exception de l’une des façons suivantes :  
  
- En fixant `COMPlus_ThrowUnobservedTaskExceptions` la`set COMPlus_ThrowUnobservedTaskExceptions=1`variable de l’environnement ( ).  
  
- En définissant le registre DWORD valeur ThrowUnobservedTaskExceptions 1 dans\\le HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft . Clé NETFramework.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment activer le lancement d’exceptions dans les tâches à l’aide d’un fichier de configuration d’application.  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment une exception non observée est écartée d’une tâche. Le code doit être exécuté comme un programme publié pour fonctionner correctement.  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d'exécution](index.md)
- [Configuration Fichier Schema](../index.md)
