---
title: Assistant Débogage managé bindingFailure
ms.date: 03/30/2017
helpviewer_keywords:
- binding failure
- binding, failures
- MDAs (managed debugging assistants), binding failures
- assemblies [.NET Framework], binding failures
- managed debugging assistants (MDAs), binding failures
- BindingFailure MDA
ms.assetid: 26ada5af-175c-4576-931a-9f07fa1723e9
ms.openlocfilehash: e3a9a915d25cbe5f052f039055167cf3ae4bf424
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216919"
---
# <a name="bindingfailure-mda"></a><span data-ttu-id="ccc30-102">Assistant Débogage managé bindingFailure</span><span class="sxs-lookup"><span data-stu-id="ccc30-102">bindingFailure MDA</span></span>

<span data-ttu-id="ccc30-103">L’Assistant débogage managé (MDA) `bindingFailure` est activé quand le chargement d’un assembly échoue.</span><span class="sxs-lookup"><span data-stu-id="ccc30-103">The `bindingFailure` managed debugging assistant (MDA) is activated when an assembly fails to load.</span></span>

## <a name="symptoms"></a><span data-ttu-id="ccc30-104">Symptômes</span><span class="sxs-lookup"><span data-stu-id="ccc30-104">Symptoms</span></span>

<span data-ttu-id="ccc30-105">Le code a tenté de charger un assembly à l’aide d’une référence statique ou de l’une des méthodes de chargeur, telles que <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> ou <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ccc30-105">Code has attempted to load an assembly using a static reference or one of the loader methods, such as <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ccc30-106">L’assembly n’est pas chargé et une exception <xref:System.IO.FileNotFoundException> ou <xref:System.IO.FileLoadException> est levée.</span><span class="sxs-lookup"><span data-stu-id="ccc30-106">The assembly is not loaded and a <xref:System.IO.FileNotFoundException> or <xref:System.IO.FileLoadException> exception is thrown.</span></span>

## <a name="cause"></a><span data-ttu-id="ccc30-107">Cause :</span><span class="sxs-lookup"><span data-stu-id="ccc30-107">Cause</span></span>

<span data-ttu-id="ccc30-108">Un échec de liaison se produit quand le runtime ne peut pas charger un assembly.</span><span class="sxs-lookup"><span data-stu-id="ccc30-108">A binding failure occurs when the runtime is unable to load an assembly.</span></span> <span data-ttu-id="ccc30-109">Un échec de liaison peut être dû à l’une des situations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ccc30-109">A binding failure might be the result of one of the following situations:</span></span>

- <span data-ttu-id="ccc30-110">Le Common Language Runtime (CLR) ne trouve pas l’assembly demandé.</span><span class="sxs-lookup"><span data-stu-id="ccc30-110">The common language runtime (CLR) cannot find the requested assembly.</span></span> <span data-ttu-id="ccc30-111">Cela peut se produire par exemple si l’assembly n’est pas installé ou si l’application n’est pas configurée correctement pour trouver l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ccc30-111">There are many reasons this can occur, such as the assembly not being installed or the application not being correctly configured to find the assembly.</span></span>

- <span data-ttu-id="ccc30-112">Un scénario à problème courant est le passage d’un type à un autre domaine d’application. Dans ce cas, le CLR doit charger l’assembly contenant ce type dans l’autre domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="ccc30-112">A common problem scenario is passing a type to another application domain, which requires the CLR to load the assembly containing that type in the other application domain.</span></span> <span data-ttu-id="ccc30-113">Il est possible que le runtime ne puisse pas charger l’assembly si l’autre domaine d’application est configuré différemment du domaine d’application d’origine.</span><span class="sxs-lookup"><span data-stu-id="ccc30-113">It may not be possible for the runtime to load the assembly if the other application domain is configured differently from the original application domain.</span></span> <span data-ttu-id="ccc30-114">Les deux domaines d’application peuvent par exemple avoir différentes valeurs de propriété <xref:System.AppDomain.BaseDirectory%2A>.</span><span class="sxs-lookup"><span data-stu-id="ccc30-114">For example, the two application domains might have different <xref:System.AppDomain.BaseDirectory%2A> property values.</span></span>

- <span data-ttu-id="ccc30-115">L’assembly demandé est endommagé ou n’est pas un assembly.</span><span class="sxs-lookup"><span data-stu-id="ccc30-115">The requested assembly is corrupted or is not an assembly.</span></span>

- <span data-ttu-id="ccc30-116">Le code qui tente de charger l’assembly ne dispose pas des autorisations de sécurité d’accès du code correctes pour charger des assemblys.</span><span class="sxs-lookup"><span data-stu-id="ccc30-116">The code attempting to load the assembly does not have the correct code access security permissions to load assemblies.</span></span>

- <span data-ttu-id="ccc30-117">Les informations d’identification de l’utilisateur ne fournissent pas les autorisations requises pour lire le fichier.</span><span class="sxs-lookup"><span data-stu-id="ccc30-117">The user credentials do not provide the required permissions to read the file.</span></span>

## <a name="resolution"></a><span data-ttu-id="ccc30-118">Résolution</span><span class="sxs-lookup"><span data-stu-id="ccc30-118">Resolution</span></span>

<span data-ttu-id="ccc30-119">La première étape consiste à déterminer pourquoi le CLR n’a pas pu établir de liaison avec l’assembly demandé.</span><span class="sxs-lookup"><span data-stu-id="ccc30-119">The first step is to determine why the CLR could not bind to the requested assembly.</span></span> <span data-ttu-id="ccc30-120">Il existe de nombreuses raisons pour lesquelles le runtime est susceptible de ne pas avoir trouvé ou chargé l’assembly demandé, parmi lesquelles les scénarios répertoriés dans la section Cause.</span><span class="sxs-lookup"><span data-stu-id="ccc30-120">There are many reasons why the runtime might not have found or been able load the requested assembly, such as the scenarios listed in the Cause section.</span></span> <span data-ttu-id="ccc30-121">Nous vous recommandons d’effectuer les actions suivantes pour éliminer la cause de l’échec de liaison :</span><span class="sxs-lookup"><span data-stu-id="ccc30-121">The following actions are recommended to eliminate the cause of the binding failure:</span></span>

- <span data-ttu-id="ccc30-122">Déterminez la cause à l’aide des données fournies par l’Assistant Débogage managé `bindingFailure` :</span><span class="sxs-lookup"><span data-stu-id="ccc30-122">Determine the cause by using the data provided by the `bindingFailure` MDA:</span></span>

  - <span data-ttu-id="ccc30-123">Exécutez [Fuslogvw.exe (Visionneuse du journal de liaison d’assembly)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) pour lire les journaux d’erreur produits par le binder d’assembly.</span><span class="sxs-lookup"><span data-stu-id="ccc30-123">Run the [Fuslogvw.exe (Assembly Binding Log Viewer)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) to read the error logs produced by the assembly binder.</span></span>

  - <span data-ttu-id="ccc30-124">Déterminez si l’assembly se trouve à l’emplacement demandé.</span><span class="sxs-lookup"><span data-stu-id="ccc30-124">Determine if the assembly is at the location requested.</span></span> <span data-ttu-id="ccc30-125">Avec les méthodes <xref:System.Reflection.Assembly.LoadFrom%2A> et <xref:System.Reflection.Assembly.LoadFile%2A>, il est facile de déterminer l’emplacement demandé.</span><span class="sxs-lookup"><span data-stu-id="ccc30-125">In the case of the <xref:System.Reflection.Assembly.LoadFrom%2A> and <xref:System.Reflection.Assembly.LoadFile%2A> methods, the requested location can be easily determined.</span></span> <span data-ttu-id="ccc30-126">Avec la méthode <xref:System.Reflection.Assembly.Load%2A>, qui établit une liaison à l’aide de l’identité d’assembly, vous devez rechercher les assemblys qui correspondent à cette identité dans le chemin de sonde de propriété <xref:System.AppDomain.BaseDirectory%2A> du domaine d’application et le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="ccc30-126">In the case of the <xref:System.Reflection.Assembly.Load%2A> method, which binds using the assembly identity, you must look for assemblies that match that identity in the application domain's <xref:System.AppDomain.BaseDirectory%2A> property probe path and the global assembly cache.</span></span>

- <span data-ttu-id="ccc30-127">Résolvez le problème en fonction de la détermination précédente.</span><span class="sxs-lookup"><span data-stu-id="ccc30-127">Resolve the cause based on the preceding determination.</span></span> <span data-ttu-id="ccc30-128">Les options de résolution possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="ccc30-128">Possible resolution options are the following:</span></span>

  - <span data-ttu-id="ccc30-129">Installez l’assembly demandé dans le global assembly cache et appelez la méthode</span><span class="sxs-lookup"><span data-stu-id="ccc30-129">Install the requested assembly in the global assembly cache and call the.</span></span> <span data-ttu-id="ccc30-130"><xref:System.Reflection.Assembly.Load%2A> pour charger l’assembly par identité.</span><span class="sxs-lookup"><span data-stu-id="ccc30-130"><xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>

  - <span data-ttu-id="ccc30-131">Copiez l’assembly demandé dans le répertoire de l’application et appelez la méthode <xref:System.Reflection.Assembly.Load%2A> pour charger l’assembly par identité.</span><span class="sxs-lookup"><span data-stu-id="ccc30-131">Copy the requested assembly into the application directory and call the <xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>

  - <span data-ttu-id="ccc30-132">Reconfigurez le domaine d’application dans lequel l’échec de liaison s’est produit pour inclure le chemin d’assembly en modifiant la propriété <xref:System.AppDomain.BaseDirectory%2A> ou en ajoutant des chemins de sonde privés.</span><span class="sxs-lookup"><span data-stu-id="ccc30-132">Reconfigure the application domain in which the binding failure occurred to include the assembly path by either changing the <xref:System.AppDomain.BaseDirectory%2A> property or adding private probing paths.</span></span>

  - <span data-ttu-id="ccc30-133">Modifiez la liste de contrôle d’accès pour le fichier afin de permettre à l’utilisateur connecté de lire le fichier.</span><span class="sxs-lookup"><span data-stu-id="ccc30-133">Change the access control list for the file to allow the logged-on user to read the file.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="ccc30-134">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="ccc30-134">Effect on the Runtime</span></span>

<span data-ttu-id="ccc30-135">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="ccc30-135">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="ccc30-136">Il signale uniquement des données relatives aux échecs de liaison.</span><span class="sxs-lookup"><span data-stu-id="ccc30-136">It only reports data about binding failures.</span></span>

## <a name="output"></a><span data-ttu-id="ccc30-137">Output</span><span class="sxs-lookup"><span data-stu-id="ccc30-137">Output</span></span>

<span data-ttu-id="ccc30-138">L’Assistant Débogage managé signale l’assembly dont le chargement a échoué, notamment le chemin demandé et/ou le nom complet, le contexte de liaison, le domaine d’application dans lequel le chargement a été demandé et la raison de l’échec.</span><span class="sxs-lookup"><span data-stu-id="ccc30-138">The MDA reports the assembly that failed to load, including the requested path and/or display name, the binding context, the application domain in which the load was requested, and the reason for the failure.</span></span>

<span data-ttu-id="ccc30-139">Le nom complet ou le chemin demandé peut être vide si ces données n’étaient pas accessibles au CLR.</span><span class="sxs-lookup"><span data-stu-id="ccc30-139">The display name or requested path may be blank if that data was not available to the CLR.</span></span> <span data-ttu-id="ccc30-140">Si l’appel qui a échoué était un appel à la méthode <xref:System.Reflection.Assembly.Load%2A>, il est probable que le runtime n’a pas pu déterminer le nom complet de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ccc30-140">If the call that failed was to the <xref:System.Reflection.Assembly.Load%2A> method, it is likely the runtime could not determine the display name for the assembly.</span></span>

## <a name="configuration"></a><span data-ttu-id="ccc30-141">Configuration</span><span class="sxs-lookup"><span data-stu-id="ccc30-141">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <bindingFailure />
  </assistants>
</mdaConfig>
```

## <a name="example"></a><span data-ttu-id="ccc30-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="ccc30-142">Example</span></span>

<span data-ttu-id="ccc30-143">L’exemple de code suivant montre une situation qui peut activer cet Assistant Débogage managé :</span><span class="sxs-lookup"><span data-stu-id="ccc30-143">The following code example demonstrates a situation that can activate this MDA:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Text;
using System.Reflection;
namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            // This call attempts to load a nonexistent assembly.
            // The call will throw a System.IO.FileNotFound exception
            // and cause the activation of the bindingFailure MDA
            // if it is registered.
            Assembly.Load("NonExistentAssembly");
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="ccc30-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ccc30-144">See also</span></span>

- [<span data-ttu-id="ccc30-145">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="ccc30-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
