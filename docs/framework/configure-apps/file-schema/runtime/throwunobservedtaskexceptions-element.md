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
ms.openlocfilehash: 012c2e70e66015bc317606a7eea07812b5df26e7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183921"
---
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="46e00-102">Élément \<ThrowUnobservedTaskExceptions></span><span class="sxs-lookup"><span data-stu-id="46e00-102">\<ThrowUnobservedTaskExceptions> Element</span></span>

<span data-ttu-id="46e00-103">Indique si les exceptions de tâches non gérées doivent arrêter un processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="46e00-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**  
  
## <a name="syntax"></a><span data-ttu-id="46e00-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46e00-104">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46e00-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="46e00-105">Attributes and Elements</span></span>  

 <span data-ttu-id="46e00-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="46e00-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46e00-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="46e00-107">Attributes</span></span>  
  
|<span data-ttu-id="46e00-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="46e00-108">Attribute</span></span>|<span data-ttu-id="46e00-109">Description</span><span class="sxs-lookup"><span data-stu-id="46e00-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="46e00-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="46e00-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="46e00-111">Spécifie si les exceptions de tâche non gérée doivent mettre fin au processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="46e00-111">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="46e00-112">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="46e00-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="46e00-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="46e00-113">Value</span></span>|<span data-ttu-id="46e00-114">Description</span><span class="sxs-lookup"><span data-stu-id="46e00-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="46e00-115">N’arrête pas le processus en cours d’exécution pour une exception de tâche non gérée.</span><span class="sxs-lookup"><span data-stu-id="46e00-115">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="46e00-116">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="46e00-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="46e00-117">Met fin au processus en cours d’exécution pour une exception de tâche non gérée.</span><span class="sxs-lookup"><span data-stu-id="46e00-117">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="46e00-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="46e00-118">Child Elements</span></span>  

 <span data-ttu-id="46e00-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="46e00-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="46e00-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="46e00-120">Parent Elements</span></span>  
  
|<span data-ttu-id="46e00-121">Élément</span><span class="sxs-lookup"><span data-stu-id="46e00-121">Element</span></span>|<span data-ttu-id="46e00-122">Description</span><span class="sxs-lookup"><span data-stu-id="46e00-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="46e00-123">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="46e00-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="46e00-124">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="46e00-124">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="46e00-125">Notes</span><span class="sxs-lookup"><span data-stu-id="46e00-125">Remarks</span></span>  

 <span data-ttu-id="46e00-126">Si une exception associée à un n' <xref:System.Threading.Tasks.Task> a pas été observée, il n’y a aucune <xref:System.Threading.Tasks.Task.Wait%2A> opération, le parent n’est pas attaché et la <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> propriété n’a pas été lue. l’exception de tâche est considérée comme non prise en compte.</span><span class="sxs-lookup"><span data-stu-id="46e00-126">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="46e00-127">Dans le .NET Framework 4, par défaut, si un <xref:System.Threading.Tasks.Task> qui a une exception non prise en compte est récupéré par le garbage collector, le finaliseur lève une exception et met fin au processus.</span><span class="sxs-lookup"><span data-stu-id="46e00-127">In the .NET Framework 4, by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="46e00-128">L’arrêt du processus est déterminé par le minutage de la garbage collection et de la finalisation.</span><span class="sxs-lookup"><span data-stu-id="46e00-128">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="46e00-129">Pour permettre aux développeurs d’écrire plus facilement du code asynchrone basé sur des tâches, le .NET Framework 4,5 modifie ce comportement par défaut pour les exceptions non prises en compte.</span><span class="sxs-lookup"><span data-stu-id="46e00-129">To make it easier for developers to write asynchronous code based on tasks, the .NET Framework 4.5 changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="46e00-130">Les exceptions non prises en même temps entraînent le <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> déclenchement de l’événement, mais par défaut, le processus ne se termine pas.</span><span class="sxs-lookup"><span data-stu-id="46e00-130">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="46e00-131">Au lieu de cela, l’exception est ignorée une fois que l’événement est déclenché, qu’un gestionnaire d’événements observe l’exception ou non.</span><span class="sxs-lookup"><span data-stu-id="46e00-131">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="46e00-132">Dans le .NET Framework 4,5, vous pouvez utiliser l' [ \<ThrowUnobservedTaskExceptions> élément](throwunobservedtaskexceptions-element.md) dans un fichier de configuration de l’application pour permettre au comportement .NET Framework 4 de lever une exception.</span><span class="sxs-lookup"><span data-stu-id="46e00-132">In the .NET Framework 4.5, you can use the [\<ThrowUnobservedTaskExceptions> element](throwunobservedtaskexceptions-element.md) in an application configuration file to enable the .NET Framework 4 behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="46e00-133">Vous pouvez également spécifier le comportement de l’exception de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="46e00-133">You can also specify the exception behavior in one of the following ways:</span></span>  
  
- <span data-ttu-id="46e00-134">En définissant la variable d’environnement `COMPlus_ThrowUnobservedTaskExceptions` ( `set COMPlus_ThrowUnobservedTaskExceptions=1` ).</span><span class="sxs-lookup"><span data-stu-id="46e00-134">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
- <span data-ttu-id="46e00-135">En définissant la valeur de Registre DWORD ThrowUnobservedTaskExceptions = 1 dans le HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft \\ . Clé NETFramework.</span><span class="sxs-lookup"><span data-stu-id="46e00-135">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46e00-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="46e00-136">Example</span></span>  

 <span data-ttu-id="46e00-137">L’exemple suivant montre comment activer la levée d’exceptions dans des tâches à l’aide d’un fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="46e00-137">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="46e00-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="46e00-138">Example</span></span>  

 <span data-ttu-id="46e00-139">L’exemple suivant montre comment une exception non détectée est levée à partir d’une tâche.</span><span class="sxs-lookup"><span data-stu-id="46e00-139">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="46e00-140">Le code doit être exécuté comme un programme libéré pour fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="46e00-140">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="46e00-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46e00-141">See also</span></span>

- [<span data-ttu-id="46e00-142">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="46e00-142">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="46e00-143">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="46e00-143">Configuration File Schema</span></span>](../index.md)
