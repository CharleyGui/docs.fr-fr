---
title: Assistant Débogage managé memberInfoCacheCreation
description: Comprendre l’Assistant Débogage managé memberInfoCacheCreation (MDA) dans .NET, qui est activé lors de la création d’un cache MemberInfo.
ms.date: 03/30/2017
helpviewer_keywords:
- member info cache creation
- MemberInfoCacheCreation MDA
- reflection, run-time errors
- MDAs (managed debugging assistants), cache
- cache [.NET Framework], reflection
- managed debugging assistants (MDAs), cache
- MemberInfo cache
ms.assetid: 5abdad23-1335-4744-8acb-934002c0b6fe
ms.openlocfilehash: c48be7ac8632b8072981be01e01997ee8c34b6b3
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051140"
---
# <a name="memberinfocachecreation-mda"></a><span data-ttu-id="81db6-103">Assistant Débogage managé memberInfoCacheCreation</span><span class="sxs-lookup"><span data-stu-id="81db6-103">memberInfoCacheCreation MDA</span></span>
<span data-ttu-id="81db6-104">L’Assistant Débogage managé `memberInfoCacheCreation` est activé quand le cache <xref:System.Reflection.MemberInfo> est créé.</span><span class="sxs-lookup"><span data-stu-id="81db6-104">The `memberInfoCacheCreation` managed debugging assistant (MDA) is activated when a <xref:System.Reflection.MemberInfo> cache is created.</span></span> <span data-ttu-id="81db6-105">Il s’agit d’une indication forte d’un programme qui utilise des fonctionnalités de réflexion coûteuses en ressources.</span><span class="sxs-lookup"><span data-stu-id="81db6-105">This is a strong indication of a program that is making use of resource-expensive reflection features.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="81db6-106">Symptômes</span><span class="sxs-lookup"><span data-stu-id="81db6-106">Symptoms</span></span>  
 <span data-ttu-id="81db6-107">La plage de travail d’un programme augmente, car il utilise une réflexion coûteuse en ressources.</span><span class="sxs-lookup"><span data-stu-id="81db6-107">A program's working set increases because the program is using resource-expensive reflection.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="81db6-108">Cause</span><span class="sxs-lookup"><span data-stu-id="81db6-108">Cause</span></span>  
 <span data-ttu-id="81db6-109">Les opérations de réflexion qui impliquent des objets <xref:System.Reflection.MemberInfo> sont considérées comme coûteuses en ressources, car elles doivent lire les métadonnées stockées dans des pages peu consultées et elles indiquent généralement que le programme utilise un type de scénario à liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="81db6-109">Reflection operations that involve <xref:System.Reflection.MemberInfo> objects are considered resource expensive because they must read metadata that is stored in cold pages and in general they indicate the program is using some type of late-bound scenario.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="81db6-110">Résolution</span><span class="sxs-lookup"><span data-stu-id="81db6-110">Resolution</span></span>  
 <span data-ttu-id="81db6-111">Vous pouvez déterminer où la réflexion est utilisée dans votre programme en activant cet Assistant Débogage managé puis en exécutant votre code dans un débogueur, ou en effectuant un attachement avec un débogueur quand l’Assistant Débogage managé est activé.</span><span class="sxs-lookup"><span data-stu-id="81db6-111">You can determine where reflection is being used in your program by enabling this MDA and then running your code in a debugger or attaching with a debugger when the MDA is activated.</span></span> <span data-ttu-id="81db6-112">Avec un débogueur, vous obtenez une arborescence des appels de procédure indiquant où le cache <xref:System.Reflection.MemberInfo> a été créé et, à partir de là, vous pouvez déterminer où votre programme utilise la réflexion.</span><span class="sxs-lookup"><span data-stu-id="81db6-112">Under a debugger you will get a stack trace showing where the <xref:System.Reflection.MemberInfo> cache was created and from there you can determine where your program is using reflection.</span></span>  
  
 <span data-ttu-id="81db6-113">La résolution dépend des objectifs du code.</span><span class="sxs-lookup"><span data-stu-id="81db6-113">The resolution is dependent on the objectives of the code.</span></span> <span data-ttu-id="81db6-114">Cet Assistant Débogage managé vous avertit que votre programme a un scénario à liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="81db6-114">This MDA alerts you that your program has a late-bound scenario.</span></span> <span data-ttu-id="81db6-115">Vous pouvez alors déterminer si vous pouvez substituer un scénario à liaison anticipée ou considérer les performances du scénario à liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="81db6-115">You might want to determine if you can substitute an early-bound scenario or consider the performance of the late bound scenario.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="81db6-116">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="81db6-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="81db6-117">Cet Assistant Débogage managé est activé pour chaque cache <xref:System.Reflection.MemberInfo> créé.</span><span class="sxs-lookup"><span data-stu-id="81db6-117">This MDA is activated for every <xref:System.Reflection.MemberInfo> cache that is created.</span></span> <span data-ttu-id="81db6-118">L’impact sur les performances est négligeable.</span><span class="sxs-lookup"><span data-stu-id="81db6-118">The performance impact is negligible.</span></span>  
  
## <a name="output"></a><span data-ttu-id="81db6-119">Sortie</span><span class="sxs-lookup"><span data-stu-id="81db6-119">Output</span></span>  
 <span data-ttu-id="81db6-120">L’Assistant Débogage managé génère un message indiquant que le cache <xref:System.Reflection.MemberInfo> a été créé.</span><span class="sxs-lookup"><span data-stu-id="81db6-120">The MDA outputs a message indicating the <xref:System.Reflection.MemberInfo> cache was created.</span></span> <span data-ttu-id="81db6-121">Pour obtenir une arborescence des appels de procédure montrant l’endroit où votre programme utilise la réflexion, utilisez un débogueur.</span><span class="sxs-lookup"><span data-stu-id="81db6-121">Use a debugger to get a stack trace showing where your program is using reflection.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="81db6-122">Configuration</span><span class="sxs-lookup"><span data-stu-id="81db6-122">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="81db6-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="81db6-123">Example</span></span>  
 <span data-ttu-id="81db6-124">Cet exemple de code active l’Assistant Débogage managé `memberInfoCacheCreation`.</span><span class="sxs-lookup"><span data-stu-id="81db6-124">This sample code will activate the `memberInfoCacheCreation` MDA.</span></span>  
  
```csharp
using System;  
  
public class Exe  
{  
    public static void Main()  
    {  
        typeof(object).GetMethods();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="81db6-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81db6-125">See also</span></span>

- <xref:System.Reflection.MemberInfo>
- [<span data-ttu-id="81db6-126">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="81db6-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
