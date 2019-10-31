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
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="5269a-102">\<élément ThrowUnobservedTaskExceptions ></span><span class="sxs-lookup"><span data-stu-id="5269a-102">\<ThrowUnobservedTaskExceptions> Element</span></span>
<span data-ttu-id="5269a-103">Indique si les exceptions de tâches non gérées doivent arrêter un processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="5269a-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
<span data-ttu-id="5269a-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5269a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5269a-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="5269a-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="5269a-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<ThrowUnobservedTaskExceptions** ></span><span class="sxs-lookup"><span data-stu-id="5269a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5269a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5269a-107">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5269a-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5269a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5269a-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5269a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5269a-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="5269a-110">Attributes</span></span>  
  
|<span data-ttu-id="5269a-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="5269a-111">Attribute</span></span>|<span data-ttu-id="5269a-112">Description</span><span class="sxs-lookup"><span data-stu-id="5269a-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="5269a-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="5269a-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="5269a-114">Spécifie si les exceptions de tâche non gérée doivent mettre fin au processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="5269a-114">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5269a-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="5269a-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="5269a-116">valeur</span><span class="sxs-lookup"><span data-stu-id="5269a-116">Value</span></span>|<span data-ttu-id="5269a-117">Description</span><span class="sxs-lookup"><span data-stu-id="5269a-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="5269a-118">N’arrête pas le processus en cours d’exécution pour une exception de tâche non gérée.</span><span class="sxs-lookup"><span data-stu-id="5269a-118">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="5269a-119">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="5269a-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="5269a-120">Met fin au processus en cours d’exécution pour une exception de tâche non gérée.</span><span class="sxs-lookup"><span data-stu-id="5269a-120">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5269a-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5269a-121">Child Elements</span></span>  
 <span data-ttu-id="5269a-122">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="5269a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5269a-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5269a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5269a-124">Élément</span><span class="sxs-lookup"><span data-stu-id="5269a-124">Element</span></span>|<span data-ttu-id="5269a-125">Description</span><span class="sxs-lookup"><span data-stu-id="5269a-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5269a-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5269a-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5269a-127">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="5269a-127">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="5269a-128">Notes</span><span class="sxs-lookup"><span data-stu-id="5269a-128">Remarks</span></span>  
 <span data-ttu-id="5269a-129">Si une exception associée à un <xref:System.Threading.Tasks.Task> n’a pas été observée, il n’y a aucune opération <xref:System.Threading.Tasks.Task.Wait%2A>, le parent n’est pas attaché et la propriété <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> n’a pas été lue. l’exception de tâche est considérée comme non prise en compte.</span><span class="sxs-lookup"><span data-stu-id="5269a-129">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="5269a-130">Dans le .NET Framework 4, par défaut, si une <xref:System.Threading.Tasks.Task> qui a une exception non prise en compte est récupérée par le garbage collector, le finaliseur lève une exception et met fin au processus.</span><span class="sxs-lookup"><span data-stu-id="5269a-130">In the .NET Framework 4, by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="5269a-131">L’arrêt du processus est déterminé par le minutage de la garbage collection et de la finalisation.</span><span class="sxs-lookup"><span data-stu-id="5269a-131">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="5269a-132">Pour permettre aux développeurs d’écrire plus facilement du code asynchrone basé sur des tâches, le .NET Framework 4,5 modifie ce comportement par défaut pour les exceptions non prises en compte.</span><span class="sxs-lookup"><span data-stu-id="5269a-132">To make it easier for developers to write asynchronous code based on tasks, the .NET Framework 4.5 changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="5269a-133">Les exceptions non prises en même temps entraînent le déclenchement de l’événement <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException>, mais par défaut, le processus ne se termine pas.</span><span class="sxs-lookup"><span data-stu-id="5269a-133">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="5269a-134">Au lieu de cela, l’exception est ignorée une fois que l’événement est déclenché, qu’un gestionnaire d’événements observe l’exception ou non.</span><span class="sxs-lookup"><span data-stu-id="5269a-134">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="5269a-135">Dans le .NET Framework 4,5, vous pouvez utiliser l' [élément\<ThrowUnobservedTaskExceptions >](throwunobservedtaskexceptions-element.md) dans un fichier de configuration de l’application pour permettre au comportement .NET Framework 4 de lever une exception.</span><span class="sxs-lookup"><span data-stu-id="5269a-135">In the .NET Framework 4.5, you can use the [\<ThrowUnobservedTaskExceptions> element](throwunobservedtaskexceptions-element.md) in an application configuration file to enable the .NET Framework 4 behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="5269a-136">Vous pouvez également spécifier le comportement de l’exception de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="5269a-136">You can also specify the exception behavior in one of the following ways:</span></span>  
  
- <span data-ttu-id="5269a-137">En définissant la variable d’environnement `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span><span class="sxs-lookup"><span data-stu-id="5269a-137">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
- <span data-ttu-id="5269a-138">En définissant la valeur de Registre DWORD ThrowUnobservedTaskExceptions = 1 dans le\\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft. Clé NETFramework.</span><span class="sxs-lookup"><span data-stu-id="5269a-138">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5269a-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="5269a-139">Example</span></span>  
 <span data-ttu-id="5269a-140">L’exemple suivant montre comment activer la levée d’exceptions dans des tâches à l’aide d’un fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="5269a-140">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="5269a-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="5269a-141">Example</span></span>  
 <span data-ttu-id="5269a-142">L’exemple suivant montre comment une exception non détectée est levée à partir d’une tâche.</span><span class="sxs-lookup"><span data-stu-id="5269a-142">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="5269a-143">Le code doit être exécuté comme un programme libéré pour fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="5269a-143">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5269a-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5269a-144">See also</span></span>

- [<span data-ttu-id="5269a-145">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="5269a-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5269a-146">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="5269a-146">Configuration File Schema</span></span>](../index.md)
