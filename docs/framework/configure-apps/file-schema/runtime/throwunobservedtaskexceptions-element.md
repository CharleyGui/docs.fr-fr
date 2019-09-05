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
ms.openlocfilehash: 3ed1e66c4aadab656455686a7a1e5028b035676a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252263"
---
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="5ff0b-102">\<ThrowUnobservedTaskExceptions >, élément</span><span class="sxs-lookup"><span data-stu-id="5ff0b-102">\<ThrowUnobservedTaskExceptions> Element</span></span>
<span data-ttu-id="5ff0b-103">Indique si les exceptions de tâches non gérées doivent arrêter un processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="5ff0b-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
<span data-ttu-id="5ff0b-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5ff0b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5ff0b-105">&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="5ff0b-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="5ff0b-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<ThrowUnobservedTaskExceptions>**</span><span class="sxs-lookup"><span data-stu-id="5ff0b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ff0b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ff0b-107">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ff0b-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5ff0b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5ff0b-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5ff0b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ff0b-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="5ff0b-110">Attributes</span></span>  
  
|<span data-ttu-id="5ff0b-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="5ff0b-111">Attribute</span></span>|<span data-ttu-id="5ff0b-112">Description</span><span class="sxs-lookup"><span data-stu-id="5ff0b-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="5ff0b-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="5ff0b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="5ff0b-114">Spécifie si les exceptions de tâche non gérée doivent mettre fin au processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="5ff0b-114">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5ff0b-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="5ff0b-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="5ff0b-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="5ff0b-116">Value</span></span>|<span data-ttu-id="5ff0b-117">Description</span><span class="sxs-lookup"><span data-stu-id="5ff0b-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="5ff0b-118">N’arrête pas le processus en cours d’exécution pour une exception de tâche non gérée.</span><span class="sxs-lookup"><span data-stu-id="5ff0b-118">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="5ff0b-119">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="5ff0b-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="5ff0b-120">Met fin au processus en cours d’exécution pour une exception de tâche non gérée.</span><span class="sxs-lookup"><span data-stu-id="5ff0b-120">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ff0b-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5ff0b-121">Child Elements</span></span>  
 <span data-ttu-id="5ff0b-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5ff0b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ff0b-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5ff0b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5ff0b-124">Élément</span><span class="sxs-lookup"><span data-stu-id="5ff0b-124">Element</span></span>|<span data-ttu-id="5ff0b-125">Description</span><span class="sxs-lookup"><span data-stu-id="5ff0b-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5ff0b-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5ff0b-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5ff0b-127">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="5ff0b-127">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="5ff0b-128">Notes</span><span class="sxs-lookup"><span data-stu-id="5ff0b-128">Remarks</span></span>  
 <span data-ttu-id="5ff0b-129">Si une exception associée à un <xref:System.Threading.Tasks.Task> n’a pas été observée, il n’y a aucune <xref:System.Threading.Tasks.Task.Wait%2A> opération, le parent n’est pas attaché <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> et la propriété n’a pas été lue. l’exception de tâche est considérée comme non prise en compte.</span><span class="sxs-lookup"><span data-stu-id="5ff0b-129">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="5ff0b-130">Dans le .NET Framework 4, par défaut, si un <xref:System.Threading.Tasks.Task> qui a une exception non prise en compte est récupéré par le garbage collector, le finaliseur lève une exception et met fin au processus.</span><span class="sxs-lookup"><span data-stu-id="5ff0b-130">In the .NET Framework 4, by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="5ff0b-131">L’arrêt du processus est déterminé par le minutage de la garbage collection et de la finalisation.</span><span class="sxs-lookup"><span data-stu-id="5ff0b-131">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="5ff0b-132">Pour permettre aux développeurs d’écrire plus facilement du code asynchrone basé sur des tâches, le .NET Framework 4,5 modifie ce comportement par défaut pour les exceptions non prises en compte.</span><span class="sxs-lookup"><span data-stu-id="5ff0b-132">To make it easier for developers to write asynchronous code based on tasks, the .NET Framework 4.5 changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="5ff0b-133">Les exceptions non prises en même <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> temps entraînent le déclenchement de l’événement, mais par défaut, le processus ne se termine pas.</span><span class="sxs-lookup"><span data-stu-id="5ff0b-133">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="5ff0b-134">Au lieu de cela, l’exception est ignorée une fois que l’événement est déclenché, qu’un gestionnaire d’événements observe l’exception ou non.</span><span class="sxs-lookup"><span data-stu-id="5ff0b-134">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="5ff0b-135">Dans le .NET Framework 4,5, vous pouvez utiliser l' [ \<élément ThrowUnobservedTaskExceptions >](throwunobservedtaskexceptions-element.md) dans un fichier de configuration de l’application pour permettre au comportement .NET Framework 4 de lever une exception.</span><span class="sxs-lookup"><span data-stu-id="5ff0b-135">In the .NET Framework 4.5, you can use the [\<ThrowUnobservedTaskExceptions> element](throwunobservedtaskexceptions-element.md) in an application configuration file to enable the .NET Framework 4 behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="5ff0b-136">Vous pouvez également spécifier le comportement de l’exception de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="5ff0b-136">You can also specify the exception behavior in one of the following ways:</span></span>  
  
- <span data-ttu-id="5ff0b-137">En définissant la variable `COMPlus_ThrowUnobservedTaskExceptions` d'`set COMPlus_ThrowUnobservedTaskExceptions=1`environnement ().</span><span class="sxs-lookup"><span data-stu-id="5ff0b-137">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
- <span data-ttu-id="5ff0b-138">En définissant la valeur de Registre DWORD ThrowUnobservedTaskExceptions = 1 dans\\le HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft. Clé NETFramework.</span><span class="sxs-lookup"><span data-stu-id="5ff0b-138">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ff0b-139">Exemples</span><span class="sxs-lookup"><span data-stu-id="5ff0b-139">Example</span></span>  
 <span data-ttu-id="5ff0b-140">L’exemple suivant montre comment activer la levée d’exceptions dans des tâches à l’aide d’un fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="5ff0b-140">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="5ff0b-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="5ff0b-141">Example</span></span>  
 <span data-ttu-id="5ff0b-142">L’exemple suivant montre comment une exception non détectée est levée à partir d’une tâche.</span><span class="sxs-lookup"><span data-stu-id="5ff0b-142">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="5ff0b-143">Le code doit être exécuté comme un programme libéré pour fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="5ff0b-143">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5ff0b-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ff0b-144">See also</span></span>

- [<span data-ttu-id="5ff0b-145">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="5ff0b-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5ff0b-146">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="5ff0b-146">Configuration File Schema</span></span>](../index.md)
