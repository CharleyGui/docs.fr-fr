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
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="d1bc5-102">\<ThrowUnobservedTaskExceptions> Element</span><span class="sxs-lookup"><span data-stu-id="d1bc5-102">\<ThrowUnobservedTaskExceptions> Element</span></span>
<span data-ttu-id="d1bc5-103">Indique si les exceptions de tâches non gérées doivent arrêter un processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="d1bc5-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
<span data-ttu-id="d1bc5-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d1bc5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d1bc5-105">&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="d1bc5-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="d1bc5-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**</span><span class="sxs-lookup"><span data-stu-id="d1bc5-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1bc5-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1bc5-107">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1bc5-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d1bc5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d1bc5-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d1bc5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1bc5-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="d1bc5-110">Attributes</span></span>  
  
|<span data-ttu-id="d1bc5-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="d1bc5-111">Attribute</span></span>|<span data-ttu-id="d1bc5-112">Description</span><span class="sxs-lookup"><span data-stu-id="d1bc5-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d1bc5-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="d1bc5-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d1bc5-114">Précise si les exceptions de tâches non gérées devraient mettre fin au processus de fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="d1bc5-114">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d1bc5-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="d1bc5-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="d1bc5-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="d1bc5-116">Value</span></span>|<span data-ttu-id="d1bc5-117">Description</span><span class="sxs-lookup"><span data-stu-id="d1bc5-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="d1bc5-118">Ne met pas fin au processus de fonctionnement pour une exception de tâche non gérée.</span><span class="sxs-lookup"><span data-stu-id="d1bc5-118">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="d1bc5-119">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="d1bc5-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="d1bc5-120">Termine le processus de fonctionnement pour une exception de tâche non gérée.</span><span class="sxs-lookup"><span data-stu-id="d1bc5-120">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1bc5-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d1bc5-121">Child Elements</span></span>  
 <span data-ttu-id="d1bc5-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d1bc5-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d1bc5-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d1bc5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d1bc5-124">Élément</span><span class="sxs-lookup"><span data-stu-id="d1bc5-124">Element</span></span>|<span data-ttu-id="d1bc5-125">Description</span><span class="sxs-lookup"><span data-stu-id="d1bc5-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d1bc5-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d1bc5-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d1bc5-127">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="d1bc5-127">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="d1bc5-128">Notes </span><span class="sxs-lookup"><span data-stu-id="d1bc5-128">Remarks</span></span>  
 <span data-ttu-id="d1bc5-129">Si une exception associée <xref:System.Threading.Tasks.Task> à un n’a <xref:System.Threading.Tasks.Task.Wait%2A> pas été observée, il n’y a pas d’opération, le parent n’est pas attaché, et le <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> bien n’a pas lu l’exception de tâche est considérée comme non observée.</span><span class="sxs-lookup"><span data-stu-id="d1bc5-129">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="d1bc5-130">Dans le cadre .NET 4, <xref:System.Threading.Tasks.Task> par défaut, si une exception non observée est les ordures collectées, le finalisateur jette une exception et met fin au processus.</span><span class="sxs-lookup"><span data-stu-id="d1bc5-130">In the .NET Framework 4, by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="d1bc5-131">La fin du processus est déterminée par le moment de la collecte et de la finalisation des ordures.</span><span class="sxs-lookup"><span data-stu-id="d1bc5-131">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="d1bc5-132">Pour faciliter l’écriture de code asynchrone pour les développeurs en fonction des tâches, le cadre .NET 4.5 modifie ce comportement par défaut pour des exceptions non observées.</span><span class="sxs-lookup"><span data-stu-id="d1bc5-132">To make it easier for developers to write asynchronous code based on tasks, the .NET Framework 4.5 changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="d1bc5-133">Les exceptions non observées font toujours augmenter l’événement, <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> mais par défaut, le processus ne prend pas fin.</span><span class="sxs-lookup"><span data-stu-id="d1bc5-133">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="d1bc5-134">Au lieu de cela, l’exception est ignorée après que l’événement est soulevé, peu importe si un gestionnaire d’événement observe l’exception.</span><span class="sxs-lookup"><span data-stu-id="d1bc5-134">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="d1bc5-135">Dans le cadre .NET 4.5, vous pouvez utiliser le [ \<ThrowUnobservedTaskExceptions> élément](throwunobservedtaskexceptions-element.md) dans un fichier de configuration d’application pour activer le comportement .NET Framework 4 de jeter une exception.</span><span class="sxs-lookup"><span data-stu-id="d1bc5-135">In the .NET Framework 4.5, you can use the [\<ThrowUnobservedTaskExceptions> element](throwunobservedtaskexceptions-element.md) in an application configuration file to enable the .NET Framework 4 behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="d1bc5-136">Vous pouvez également spécifier le comportement d’exception de l’une des façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="d1bc5-136">You can also specify the exception behavior in one of the following ways:</span></span>  
  
- <span data-ttu-id="d1bc5-137">En fixant `COMPlus_ThrowUnobservedTaskExceptions` la`set COMPlus_ThrowUnobservedTaskExceptions=1`variable de l’environnement ( ).</span><span class="sxs-lookup"><span data-stu-id="d1bc5-137">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
- <span data-ttu-id="d1bc5-138">En définissant le registre DWORD valeur ThrowUnobservedTaskExceptions 1 dans\\le HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft . Clé NETFramework.</span><span class="sxs-lookup"><span data-stu-id="d1bc5-138">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1bc5-139"> Exemple</span><span class="sxs-lookup"><span data-stu-id="d1bc5-139">Example</span></span>  
 <span data-ttu-id="d1bc5-140">L’exemple suivant montre comment activer le lancement d’exceptions dans les tâches à l’aide d’un fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="d1bc5-140">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="d1bc5-141"> Exemple</span><span class="sxs-lookup"><span data-stu-id="d1bc5-141">Example</span></span>  
 <span data-ttu-id="d1bc5-142">L’exemple suivant montre comment une exception non observée est écartée d’une tâche.</span><span class="sxs-lookup"><span data-stu-id="d1bc5-142">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="d1bc5-143">Le code doit être exécuté comme un programme publié pour fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="d1bc5-143">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d1bc5-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1bc5-144">See also</span></span>

- [<span data-ttu-id="d1bc5-145">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="d1bc5-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d1bc5-146">Configuration Fichier Schema</span><span class="sxs-lookup"><span data-stu-id="d1bc5-146">Configuration File Schema</span></span>](../index.md)
