---
title: Assistant Débogage managé loadFromContext
description: Comprendre l’Assistant Débogage managé loadFromContext (MDA) dans .NET, qui est activé si un assembly est chargé dans le contexte LoadFrom.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
ms.openlocfilehash: 8d55268f2b2106dde4e488a6f0271fd3b17349da
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051647"
---
# <a name="loadfromcontext-mda"></a><span data-ttu-id="d96bf-103">Assistant Débogage managé loadFromContext</span><span class="sxs-lookup"><span data-stu-id="d96bf-103">loadFromContext MDA</span></span>
<span data-ttu-id="d96bf-104">L’Assistant Débogage managé `loadFromContext` est activé si un assembly est chargé dans le contexte `LoadFrom`.</span><span class="sxs-lookup"><span data-stu-id="d96bf-104">The `loadFromContext` managed debugging assistant (MDA) is activated if an assembly is loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="d96bf-105">Cette situation peut se produire suite à l’appel <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> ou d’autres méthodes similaires.</span><span class="sxs-lookup"><span data-stu-id="d96bf-105">This situation can occur as a result of calling <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or other similar methods.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="d96bf-106">Symptômes</span><span class="sxs-lookup"><span data-stu-id="d96bf-106">Symptoms</span></span>  
 <span data-ttu-id="d96bf-107">L’utilisation de certaines méthodes de chargeur peut aboutir au chargement des assemblys dans le contexte `LoadFrom`.</span><span class="sxs-lookup"><span data-stu-id="d96bf-107">The use of some loader methods can result in assemblies being loaded in the `LoadFrom` context.</span></span> <span data-ttu-id="d96bf-108">L’utilisation de ce contexte peut entraîner un comportement inattendu de la sérialisation, des opérations de cast et de la résolution des dépendances.</span><span class="sxs-lookup"><span data-stu-id="d96bf-108">The use of this context can result in unexpected behavior for serialization, casting, and dependency resolution.</span></span> <span data-ttu-id="d96bf-109">En règle générale, il est recommandé de charger les assemblys dans le contexte `Load` pour éviter ces problèmes.</span><span class="sxs-lookup"><span data-stu-id="d96bf-109">In general, it is recommended that assemblies be loaded into the `Load` context to avoid these problems.</span></span> <span data-ttu-id="d96bf-110">Il est difficile de déterminer le contexte dans lequel un assembly a été chargé sans cet Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="d96bf-110">It is difficult to determine which context an assembly has been loaded into without this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="d96bf-111">Cause</span><span class="sxs-lookup"><span data-stu-id="d96bf-111">Cause</span></span>  
 <span data-ttu-id="d96bf-112">En règle générale, un assembly a été chargé dans le contexte `LoadFrom` s’il a été chargé à partir d’un chemin en dehors du contexte `Load`, comme le Global Assembly Cache ou la propriété <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d96bf-112">Generally, an assembly was loaded into the `LoadFrom` context if it was loaded from a path outside the `Load` context, such as the global assembly cache or the <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="d96bf-113">Résolution</span><span class="sxs-lookup"><span data-stu-id="d96bf-113">Resolution</span></span>  
 <span data-ttu-id="d96bf-114">Configurez les applications pour que les appels de <xref:System.Reflection.Assembly.LoadFrom%2A> ne soient plus nécessaires.</span><span class="sxs-lookup"><span data-stu-id="d96bf-114">Configure applications such that <xref:System.Reflection.Assembly.LoadFrom%2A> calls are no longer needed.</span></span> <span data-ttu-id="d96bf-115">Vous pouvez pour cela utiliser les techniques suivantes :</span><span class="sxs-lookup"><span data-stu-id="d96bf-115">You can use the following techniques for doing so:</span></span>  
  
- <span data-ttu-id="d96bf-116">Installez les assemblys dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="d96bf-116">Install assemblies in the global assembly cache.</span></span>  
  
- <span data-ttu-id="d96bf-117">Placez les assemblys dans le répertoire <xref:System.AppDomainSetup.ApplicationBase%2A> pour <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="d96bf-117">Place assemblies in the <xref:System.AppDomainSetup.ApplicationBase%2A> directory for the <xref:System.AppDomain>.</span></span> <span data-ttu-id="d96bf-118">Dans le cas le domaine par défaut, le répertoire <xref:System.AppDomainSetup.ApplicationBase%2A> est celui qui contient le fichier exécutable qui a démarré le processus.</span><span class="sxs-lookup"><span data-stu-id="d96bf-118">In the case of the default domain, the <xref:System.AppDomainSetup.ApplicationBase%2A> directory is the one that contains the executable file that started the process.</span></span> <span data-ttu-id="d96bf-119">Ceci peut également nécessiter la création d’un <xref:System.AppDomain> s’il n’est pas pratique de déplacer l’assembly.</span><span class="sxs-lookup"><span data-stu-id="d96bf-119">This might also require creating a new <xref:System.AppDomain> if it is not convenient to move the assembly.</span></span>  
  
- <span data-ttu-id="d96bf-120">Ajoutez un chemin de détection au fichier de configuration (.config) de votre application ou aux domaines d’application secondaires si les assemblys dépendants se trouvent dans des répertoires enfants par rapport à l’exécutable.</span><span class="sxs-lookup"><span data-stu-id="d96bf-120">Add a probing path to your application configuration (.config) file or to secondary  application domains if dependent assemblies are in child directories relative to the executable.</span></span>  
  
 <span data-ttu-id="d96bf-121">Dans chaque cas, le code peut être changé de façon à utiliser la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d96bf-121">In each case, the code can be changed to use the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d96bf-122">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="d96bf-122">Effect on the Runtime</span></span>  
 <span data-ttu-id="d96bf-123">L’Assistant Débogage managé n’a pas d’effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="d96bf-123">The MDA does not have any effect on the CLR.</span></span> <span data-ttu-id="d96bf-124">Il indique le contexte qui a été utilisé à la suite d’une demande de chargement.</span><span class="sxs-lookup"><span data-stu-id="d96bf-124">It reports the context that was used as a result of a load request.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d96bf-125">Sortie</span><span class="sxs-lookup"><span data-stu-id="d96bf-125">Output</span></span>  
 <span data-ttu-id="d96bf-126">L’Assistant Débogage managé signale que l’assembly a été chargé dans le contexte `LoadFrom`.</span><span class="sxs-lookup"><span data-stu-id="d96bf-126">The MDA reports that the assembly was loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="d96bf-127">Il spécifie le nom simple de l’assembly et le chemin.</span><span class="sxs-lookup"><span data-stu-id="d96bf-127">It specifies the simple name of the assembly and the path.</span></span> <span data-ttu-id="d96bf-128">Il suggère également des mesures de limitation des risques pour éviter d’utiliser le contexte `LoadFrom`.</span><span class="sxs-lookup"><span data-stu-id="d96bf-128">It also suggests mitigations to avoid using the `LoadFrom` context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="d96bf-129">Configuration</span><span class="sxs-lookup"><span data-stu-id="d96bf-129">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="d96bf-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="d96bf-130">Example</span></span>  
 <span data-ttu-id="d96bf-131">L’exemple de code suivant illustre une situation qui peut activer cet Assistant Débogage managé :</span><span class="sxs-lookup"><span data-stu-id="d96bf-131">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
```csharp
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // The following call caused the LoadFrom context to be used  
            // because the assembly is loaded using LoadFrom and the path is
            // located outside of the Load context probing path.
            Assembly.LoadFrom(@"C:\Text\Test.dll");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d96bf-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d96bf-132">See also</span></span>

- [<span data-ttu-id="d96bf-133">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="d96bf-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
