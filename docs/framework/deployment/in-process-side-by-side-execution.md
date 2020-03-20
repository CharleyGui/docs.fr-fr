---
title: Exécution côte à côte in-process
ms.date: 03/30/2017
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
ms.openlocfilehash: 5ca2f03576946a23b3133bbe7532d46c4ad758ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181662"
---
# <a name="in-process-side-by-side-execution"></a><span data-ttu-id="36be4-102">Exécution côte à côte in-process</span><span class="sxs-lookup"><span data-stu-id="36be4-102">In-Process Side-by-Side Execution</span></span>
<span data-ttu-id="36be4-103">À compter de .NET Framework 4, vous pouvez utiliser l’hébergement côte à côte in-process pour exécuter plusieurs versions du CLR (Common Language Runtime) dans un processus unique.</span><span class="sxs-lookup"><span data-stu-id="36be4-103">Starting with the .NET Framework 4, you can use in-process side-by-side hosting to run multiple versions of the common language runtime (CLR) in a single process.</span></span> <span data-ttu-id="36be4-104">Par défaut, les composants COM managés s’exécutent avec la version du .NET Framework avec laquelle ils ont été générés, indépendamment de la version du .NET Framework chargée pour le processus.</span><span class="sxs-lookup"><span data-stu-id="36be4-104">By default, managed COM components run with the .NET Framework version they were built with, regardless of the .NET Framework version that is loaded for the process.</span></span>  
  
## <a name="background"></a><span data-ttu-id="36be4-105">Arrière-plan</span><span class="sxs-lookup"><span data-stu-id="36be4-105">Background</span></span>  
 <span data-ttu-id="36be4-106">Le .NET Framework a toujours fourni un hébergement côte à côte pour les applications de code managé, mais avant .NET Framework 4, il ne fournissait pas cette fonctionnalité pour les composants COM managés.</span><span class="sxs-lookup"><span data-stu-id="36be4-106">The .NET Framework has always provided side-by-side hosting for managed code applications, but before the .NET Framework 4, it did not provide that functionality for managed COM components.</span></span> <span data-ttu-id="36be4-107">Dans le passé, les composants COM managés chargés dans un processus étaient exécutés avec la version du runtime déjà chargée ou avec la version installée la plus récente du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="36be4-107">In the past, managed COM components that were loaded into a process ran either with the version of the runtime that was already loaded or with the latest installed version of the .NET Framework.</span></span> <span data-ttu-id="36be4-108">Si cette version n’était pas compatible avec le composant COM, le composant échouait.</span><span class="sxs-lookup"><span data-stu-id="36be4-108">If this version was not compatible with the COM component, the component would fail.</span></span>  
  
 <span data-ttu-id="36be4-109">.NET Framework 4 fournit une nouvelle approche de l’hébergement côte à côte qui s’assure des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="36be4-109">The .NET Framework 4 provides a new approach to side-by-side hosting that ensures the following:</span></span>  
  
- <span data-ttu-id="36be4-110">L’installation d’une nouvelle version du .NET Framework n’a aucun effet sur les applications existantes.</span><span class="sxs-lookup"><span data-stu-id="36be4-110">Installing a new version of the .NET Framework has no effect on existing applications.</span></span>  
  
- <span data-ttu-id="36be4-111">Les applications sont exécutées avec la version du .NET Framework avec laquelle elles ont été générées.</span><span class="sxs-lookup"><span data-stu-id="36be4-111">Applications run against the version of the .NET Framework that they were built with.</span></span> <span data-ttu-id="36be4-112">Elles n’utilisent pas la nouvelle version du .NET Framework, à moins que cela ne leur soit expressément demandé.</span><span class="sxs-lookup"><span data-stu-id="36be4-112">They do not use the new version of the .NET Framework unless expressly directed to do so.</span></span> <span data-ttu-id="36be4-113">Il est toutefois plus facile pour les applications de passer à une nouvelle version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="36be4-113">However, it is easier for applications to transition to using a new version of the .NET Framework.</span></span>  
  
## <a name="effects-on-users-and-developers"></a><span data-ttu-id="36be4-114">Effets sur les utilisateurs et les développeurs</span><span class="sxs-lookup"><span data-stu-id="36be4-114">Effects on Users and Developers</span></span>  
  
- <span data-ttu-id="36be4-115">**Utilisateurs finaux et administrateurs système**.</span><span class="sxs-lookup"><span data-stu-id="36be4-115">**End users and system administrators**.</span></span> <span data-ttu-id="36be4-116">Ces utilisateurs savent désormais que, quand ils installent une nouvelle version du runtime, soit indépendamment soit avec une application, cela n’aura aucun impact sur leurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="36be4-116">These users can now have greater confidence that when they install a new version of the runtime, either independently or with an application, it will have no impact on their computers.</span></span> <span data-ttu-id="36be4-117">Les applications existantes continueront de fonctionner comme auparavant.</span><span class="sxs-lookup"><span data-stu-id="36be4-117">Existing applications will continue to run as they did before.</span></span>  
  
- <span data-ttu-id="36be4-118">**Développeurs d’applications**.</span><span class="sxs-lookup"><span data-stu-id="36be4-118">**Application developers**.</span></span> <span data-ttu-id="36be4-119">L’hébergement côte à côte n’a presque aucun effet sur les développeurs d’applications.</span><span class="sxs-lookup"><span data-stu-id="36be4-119">Side-by-side hosting has almost no effect on application developers.</span></span> <span data-ttu-id="36be4-120">Par défaut, les applications sont toujours exécutées avec la version du .NET Framework avec laquelle elles ont été créées. Cela n’a pas changé.</span><span class="sxs-lookup"><span data-stu-id="36be4-120">By default, applications always run against the version of the .NET Framework they were built on; this has not changed.</span></span> <span data-ttu-id="36be4-121">Toutefois, les développeurs peuvent substituer ce comportement et demander à l’application de s’exécuter sous une version plus récente du .NET Framework (consultez le [scénario 2](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="36be4-121">However, developers can override this behavior and direct the application to run under a newer version of the .NET Framework (see [scenario 2](#scenarios)).</span></span>  
  
- <span data-ttu-id="36be4-122">**Consommateurs et développeurs de bibliothèques**.</span><span class="sxs-lookup"><span data-stu-id="36be4-122">**Library developers and consumers**.</span></span> <span data-ttu-id="36be4-123">L’hébergement côte à côte ne résout pas les problèmes de compatibilité rencontrés par les développeurs de bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="36be4-123">Side-by-side hosting does not solve the compatibility problems that library developers face.</span></span> <span data-ttu-id="36be4-124">Une bibliothèque chargée directement par une application, soit via une référence directe soit via un appel <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, continue d’utiliser le runtime du <xref:System.AppDomain> dans lequel elle est chargée.</span><span class="sxs-lookup"><span data-stu-id="36be4-124">A library that is directly loaded by an application -- either through a direct reference or through an <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> call -- continues to use the runtime of the <xref:System.AppDomain> it is loaded into.</span></span> <span data-ttu-id="36be4-125">Vous devez tester vos bibliothèques sur toutes les versions du .NET Framework que vous souhaitez prendre en charge.</span><span class="sxs-lookup"><span data-stu-id="36be4-125">You should test your libraries against all versions of the .NET Framework that you want to support.</span></span> <span data-ttu-id="36be4-126">Si une application est compilée à l’aide du runtime .NET Framework 4 mais inclut une bibliothèque créée à l’aide d’un runtime antérieur, cette bibliothèque utilisera également le runtime .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36be4-126">If an application is compiled using the .NET Framework 4 runtime but includes a library that was built using an earlier runtime, that library will use the .NET Framework 4 runtime as well.</span></span> <span data-ttu-id="36be4-127">Toutefois, si vous possédez une application générée à l’aide d’un runtime antérieur et une bibliothèque créée à l’aide de .NET Framework 4, vous devez forcer votre application à utiliser également .NET Framework 4 (consultez le [scénario 3](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="36be4-127">However, if you have an application that was built using an earlier runtime and a library that was built using the .NET Framework 4, you must force your application to also use the .NET Framework 4 (see [scenario 3](#scenarios)).</span></span>  
  
- <span data-ttu-id="36be4-128">**Développeurs de composants COM managés**.</span><span class="sxs-lookup"><span data-stu-id="36be4-128">**Managed COM component developers**.</span></span> <span data-ttu-id="36be4-129">Dans le passé, les composants COM managés étaient automatiquement exécutés à l’aide de la version la plus récente du runtime installée sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="36be4-129">In the past, managed COM components automatically ran using the latest version of the runtime installed on the computer.</span></span> <span data-ttu-id="36be4-130">Vous pouvez maintenant exécuter les composants COM avec la version du runtime avec laquelle ils ont été créés.</span><span class="sxs-lookup"><span data-stu-id="36be4-130">You can now execute COM components against the version of the runtime they were built with.</span></span>  
  
     <span data-ttu-id="36be4-131">Comme indiqué dans le tableau suivant, les composants générés avec .NET Framework version 1.1 peuvent s’exécuter côte à côte avec les composants de la version 4, mais ils ne peuvent pas s’exécuter avec les composants de la version 2.0, 3.0 ni 3.5, car l’hébergement côte à côte n’est pas disponible pour ces versions.</span><span class="sxs-lookup"><span data-stu-id="36be4-131">As shown by the following table, components that were built with the .NET Framework version 1.1 can run side by side with version 4 components, but they cannot run with version 2.0, 3.0, or 3.5 components, because side-by-side hosting is not available for those versions.</span></span>  
  
    |<span data-ttu-id="36be4-132">Version du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="36be4-132">.NET Framework version</span></span>|<span data-ttu-id="36be4-133">1.1</span><span class="sxs-lookup"><span data-stu-id="36be4-133">1.1</span></span>|<span data-ttu-id="36be4-134">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="36be4-134">2.0 - 3.5</span></span>|<span data-ttu-id="36be4-135">4</span><span class="sxs-lookup"><span data-stu-id="36be4-135">4</span></span>|  
    |----------------------------|---------|----------------|-------|  
    |<span data-ttu-id="36be4-136">1.1</span><span class="sxs-lookup"><span data-stu-id="36be4-136">1.1</span></span>|<span data-ttu-id="36be4-137">Non applicable</span><span class="sxs-lookup"><span data-stu-id="36be4-137">Not applicable</span></span>|<span data-ttu-id="36be4-138">Non </span><span class="sxs-lookup"><span data-stu-id="36be4-138">No</span></span>|<span data-ttu-id="36be4-139">Oui</span><span class="sxs-lookup"><span data-stu-id="36be4-139">Yes</span></span>|  
    |<span data-ttu-id="36be4-140">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="36be4-140">2.0 - 3.5</span></span>|<span data-ttu-id="36be4-141">Non </span><span class="sxs-lookup"><span data-stu-id="36be4-141">No</span></span>|<span data-ttu-id="36be4-142">Non applicable</span><span class="sxs-lookup"><span data-stu-id="36be4-142">Not applicable</span></span>|<span data-ttu-id="36be4-143">Oui</span><span class="sxs-lookup"><span data-stu-id="36be4-143">Yes</span></span>|  
    |<span data-ttu-id="36be4-144">4</span><span class="sxs-lookup"><span data-stu-id="36be4-144">4</span></span>|<span data-ttu-id="36be4-145">Oui</span><span class="sxs-lookup"><span data-stu-id="36be4-145">Yes</span></span>|<span data-ttu-id="36be4-146">Oui</span><span class="sxs-lookup"><span data-stu-id="36be4-146">Yes</span></span>|<span data-ttu-id="36be4-147">Non applicable</span><span class="sxs-lookup"><span data-stu-id="36be4-147">Not applicable</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="36be4-148">Les versions 3.0 et 3.5 du .NET Framework sont générées de façon incrémentielle sur la version 2.0 et n’ont pas besoin de fonctionner côte à côte.</span><span class="sxs-lookup"><span data-stu-id="36be4-148">.NET Framework versions 3.0 and 3.5 are built incrementally on version 2.0, and do not need to run side by side.</span></span> <span data-ttu-id="36be4-149">Il s’agit fondamentalement de la même version.</span><span class="sxs-lookup"><span data-stu-id="36be4-149">These are inherently the same version.</span></span>  
  
<a name="scenarios"></a>
## <a name="common-side-by-side-hosting-scenarios"></a><span data-ttu-id="36be4-150">Scénarios d’hébergement côte à côte courants</span><span class="sxs-lookup"><span data-stu-id="36be4-150">Common Side-by-Side Hosting Scenarios</span></span>  
  
- <span data-ttu-id="36be4-151">**Scénario 1 :** application native qui utilise des composants COM créés avec des versions antérieures du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="36be4-151">**Scenario 1:** Native application that uses COM components built with earlier versions of the .NET Framework.</span></span>  
  
     <span data-ttu-id="36be4-152">.NET Versions-cadre installées: Le cadre .NET 4 et toutes les autres versions du cadre .NET utilisés par les composants COM.</span><span class="sxs-lookup"><span data-stu-id="36be4-152">.NET Framework versions installed: The .NET Framework 4 and all other versions of the .NET Framework used by the COM components.</span></span>  
  
     <span data-ttu-id="36be4-153">Que faire : dans ce scénario, ne faites rien.</span><span class="sxs-lookup"><span data-stu-id="36be4-153">What to do: In this scenario, do nothing.</span></span> <span data-ttu-id="36be4-154">Les composants COM s’exécuteront avec la version du .NET Framework avec laquelle ils ont été inscrits.</span><span class="sxs-lookup"><span data-stu-id="36be4-154">The COM components will run with the version of the .NET Framework they were registered with.</span></span>  
  
- <span data-ttu-id="36be4-155">**Scénario 2**: Application gérée construite avec le .NET Framework 2.0 SP1 que vous préféreriez exécuter avec le cadre .NET 2.0, mais sont prêts à fonctionner sur le cadre .NET 4 si la version 2.0 n’est pas présente.</span><span class="sxs-lookup"><span data-stu-id="36be4-155">**Scenario 2**: Managed application built with the .NET Framework 2.0 SP1 that you would prefer to run with the .NET Framework 2.0, but are willing to run on the .NET Framework 4 if version 2.0 is not present.</span></span>  
  
     <span data-ttu-id="36be4-156">.NET Versions-cadre installées : Une version antérieure du cadre .NET et du cadre .NET 4.</span><span class="sxs-lookup"><span data-stu-id="36be4-156">.NET Framework versions installed: An earlier version of the .NET Framework and the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="36be4-157">Que faire : dans le [fichier de configuration de l’application](../configure-apps/index.md) dans le répertoire de l’application, utilisez l’[élément \<startup>](../configure-apps/file-schema/startup/startup-element.md) et l’[élément \<supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) défini comme suit :</span><span class="sxs-lookup"><span data-stu-id="36be4-157">What to do: In the [application configuration file](../configure-apps/index.md) in the application directory, use the [\<startup> element](../configure-apps/file-schema/startup/startup-element.md) and the [\<supportedRuntime> element](../configure-apps/file-schema/startup/supportedruntime-element.md) set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
- <span data-ttu-id="36be4-158">**Scénario 3 :** Application native qui utilise des composants COM construits avec des versions antérieures du cadre .NET que vous souhaitez exécuter avec le cadre .NET 4.</span><span class="sxs-lookup"><span data-stu-id="36be4-158">**Scenario 3:** Native application that uses COM components built with earlier versions of the .NET Framework that you want to run with the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="36be4-159">.NET Versions-cadre installées : Le cadre .NET 4.</span><span class="sxs-lookup"><span data-stu-id="36be4-159">.NET Framework versions installed: The .NET Framework 4.</span></span>  
  
     <span data-ttu-id="36be4-160">Que faire : dans le fichier de configuration de l’application dans le répertoire de l’application, utilisez l’élément `<startup>` avec l’attribut `useLegacyV2RuntimeActivationPolicy` défini sur `true` et l’élément `<supportedRuntime>` défini comme suit :</span><span class="sxs-lookup"><span data-stu-id="36be4-160">What to do: In the application configuration file in the application directory, use the `<startup>` element with the `useLegacyV2RuntimeActivationPolicy` attribute set to `true` and the `<supportedRuntime>` element set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a><span data-ttu-id="36be4-161"> Exemple</span><span class="sxs-lookup"><span data-stu-id="36be4-161">Example</span></span>  
 <span data-ttu-id="36be4-162">L’exemple suivant montre un hôte COM non managé qui exécute un composant COM managé à l’aide de la version du .NET Framework dans laquelle le composant a été compilé.</span><span class="sxs-lookup"><span data-stu-id="36be4-162">The following example demonstrates an unmanaged COM host that is running a managed COM component by using the version of the .NET Framework that the component was compiled to use.</span></span>  
  
 <span data-ttu-id="36be4-163">Pour exécuter l’exemple suivant, compilez et inscrivez le composant COM managé suivant avec .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="36be4-163">To run the following example, compile and register the following managed COM component using the .NET Framework 3.5.</span></span> <span data-ttu-id="36be4-164">Pour inscrire le composant, dans le menu **Projet**, cliquez sur **Propriétés**, sur l’onglet **Générer**, puis cochez la case **Inscrire pour COM Interop**.</span><span class="sxs-lookup"><span data-stu-id="36be4-164">To register the component, on the **Project** menu, click **Properties**, click the **Build** tab, and then select the **Register for COM interop** check box.</span></span>  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Runtime.InteropServices;  
  
namespace BasicComObject  
{  
    [ComVisible(true), Guid("9C99C4B5-CA54-4c58-8988-49B6811BA53B")]  
    public class MyObject : SimpleObjectModel.IPrintInfo  
    {  
        public MyObject()  
        {  
        }  
        public void PrintInfo()  
        {  
            Console.WriteLine("MyObject was activated in {0} runtime in:\n\tAppDomain {1}:{2}", System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion(), AppDomain.CurrentDomain.Id, AppDomain.CurrentDomain.FriendlyName);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="36be4-165">Compilez l’application C++ non managée suivante, ce qui active l’objet COM créé par l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="36be4-165">Compile the following unmanaged C++ application, which activates the COM object that is created by the previous example.</span></span>  
  
```cpp
#include "stdafx.h"  
#include <string>  
#include <iostream>  
#include <objbase.h>  
#include <string.h>  
#include <process.h>  
  
using namespace std;  
  
int _tmain(int argc, _TCHAR* argv[])  
{  
    char input;  
    CoInitialize(NULL) ;  
    CLSID clsid;  
    HRESULT hr;  
    HRESULT clsidhr = CLSIDFromString(L"{9C99C4B5-CA54-4c58-8988-49B6811BA53B}",&clsid);  
    hr = -1;  
    if (FAILED(clsidhr))  
    {  
        printf("Failed to construct CLSID from String\n");  
    }  
    UUID id = __uuidof(IUnknown);  
    IUnknown * pUnk = NULL;  
    hr = ::CoCreateInstance(clsid,NULL,CLSCTX_INPROC_SERVER,id,(void **) &pUnk);  
    if (FAILED(hr))  
    {  
        printf("Failed CoCreateInstance\n");  
    }else  
    {  
        pUnk->AddRef();  
        printf("Succeeded\n");  
    }  
  
    DISPID dispid;  
    IDispatch* pPrintInfo;  
    pUnk->QueryInterface(IID_IDispatch, (void**)&pPrintInfo);  
    OLECHAR FAR* szMethod[1];  
    szMethod[0]=OLESTR("PrintInfo");
    hr = pPrintInfo->GetIDsOfNames(IID_NULL,szMethod, 1, LOCALE_SYSTEM_DEFAULT, &dispid);  
    DISPPARAMS dispparams;  
    dispparams.cNamedArgs = 0;  
    dispparams.cArgs = 0;  
    VARIANTARG* pvarg = NULL;  
    EXCEPINFO * pexcepinfo = NULL;  
    WORD wFlags = DISPATCH_METHOD ;  
;  
    LPVARIANT pvRet = NULL;  
    UINT * pnArgErr = NULL;  
    hr = pPrintInfo->Invoke(dispid,IID_NULL, LOCALE_USER_DEFAULT, wFlags,  
        &dispparams, pvRet, pexcepinfo, pnArgErr);  
    printf("Press Enter to exit");  
    scanf_s("%c",&input);  
    CoUninitialize();  
    return 0;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="36be4-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36be4-166">See also</span></span>

- [<span data-ttu-id="36be4-167">\<start-up> Element</span><span class="sxs-lookup"><span data-stu-id="36be4-167">\<startup> Element</span></span>](../configure-apps/file-schema/startup/startup-element.md)
- [<span data-ttu-id="36be4-168">\<supportedRuntime> Element</span><span class="sxs-lookup"><span data-stu-id="36be4-168">\<supportedRuntime> Element</span></span>](../configure-apps/file-schema/startup/supportedruntime-element.md)
