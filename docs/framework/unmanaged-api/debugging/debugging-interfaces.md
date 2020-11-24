---
title: Interfaces de débogage
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: a3dd81ceaab2ba467d4c8ca091c1c2219040a273
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676294"
---
# <a name="debugging-interfaces"></a><span data-ttu-id="af84b-102">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="af84b-102">Debugging Interfaces</span></span>

<span data-ttu-id="af84b-103">Cette section décrit les interfaces non managées qui gèrent le débogage d'un programme s'exécutant dans le Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="af84b-103">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="af84b-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="af84b-104">In This Section</span></span>  

 <span data-ttu-id="af84b-105">[ICLRDataEnumMemoryRegions, interface](iclrdataenummemoryregions-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-105">[ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)</span></span>\
 <span data-ttu-id="af84b-106">Fournit une méthode pour énumérer les régions de mémoire qui sont spécifiées par les appelants.</span><span class="sxs-lookup"><span data-stu-id="af84b-106">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 <span data-ttu-id="af84b-107">[Interface ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-107">[ICLRDataEnumMemoryRegionsCallback Interface](iclrdataenummemoryregionscallback-interface.md)</span></span>\
 <span data-ttu-id="af84b-108">Fournit une méthode de rappel pour que `EnumMemoryRegions` rapporte au débogueur le résultat d'une tentative d'énumération d'une région spécifiée de mémoire.</span><span class="sxs-lookup"><span data-stu-id="af84b-108">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 <span data-ttu-id="af84b-109">[ICLRDataTarget, interface](iclrdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-109">[ICLRDataTarget Interface](iclrdatatarget-interface.md)</span></span>\
 <span data-ttu-id="af84b-110">Fournit des méthodes pour l'interaction avec un processus CLR cible.</span><span class="sxs-lookup"><span data-stu-id="af84b-110">Provides methods for interaction with a target CLR process.</span></span>  
  
 <span data-ttu-id="af84b-111">[Interface ICLRDataTarget2](iclrdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-111">[ICLRDataTarget2 Interface](iclrdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="af84b-112">Sous-classe de `ICLRDataTarget` qui est utilisée par la couche des services d'accès aux données pour manipuler les régions de la mémoire virtuelle dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="af84b-112">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 <span data-ttu-id="af84b-113">[Interface ICLRDataTarget3](iclrdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-113">[ICLRDataTarget3 Interface](iclrdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="af84b-114">Sous-classe de [ICLRDataTarget2](iclrdatatarget2-interface.md) qui fournit l’accès aux informations sur les exceptions.</span><span class="sxs-lookup"><span data-stu-id="af84b-114">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 <span data-ttu-id="af84b-115">[ICLRDebugging, interface](iclrdebugging-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-115">[ICLRDebugging Interface](iclrdebugging-interface.md)</span></span>\
 <span data-ttu-id="af84b-116">Fournit des méthodes qui gèrent le chargement et le déchargement des modules pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="af84b-116">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 <span data-ttu-id="af84b-117">[Interface ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-117">[ICLRDebuggingLibraryProvider Interface](iclrdebugginglibraryprovider-interface.md)</span></span>\
 <span data-ttu-id="af84b-118">Comprend la méthode de [méthode ProvideLibrary,](iclrdebugginglibraryprovider-providelibrary-method.md) , qui obtient une interface de rappel de fournisseur de bibliothèque qui permet à Common Language Runtime bibliothèques de débogage spécifiques à la version d’être localisées et chargées à la demande.</span><span class="sxs-lookup"><span data-stu-id="af84b-118">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 <span data-ttu-id="af84b-119">[Interface ICLRMetadataLocator](iclrmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-119">[ICLRMetadataLocator Interface](iclrmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="af84b-120">Interface utilisée par la couche des services d'accès aux données pour localiser les métadonnées des assemblys dans un processus cible.</span><span class="sxs-lookup"><span data-stu-id="af84b-120">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 <span data-ttu-id="af84b-121">[ICorDebug, interface](icordebug-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-121">[ICorDebug Interface](icordebug-interface.md)</span></span>\
 <span data-ttu-id="af84b-122">Fournit des méthodes qui permettent aux développeurs de déboguer des applications dans l'environnement du CLR.</span><span class="sxs-lookup"><span data-stu-id="af84b-122">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="af84b-123">[ICorDebugAppDomain, interface](icordebugappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-123">[ICorDebugAppDomain Interface](icordebugappdomain-interface.md)</span></span>\
 <span data-ttu-id="af84b-124">Fournit des méthodes pour le débogage de domaines d'application.</span><span class="sxs-lookup"><span data-stu-id="af84b-124">Provides methods for debugging application domains.</span></span>  
  
 <span data-ttu-id="af84b-125">[Interface ICorDebugAppDomain2](icordebugappdomain2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-125">[ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)</span></span>\
 <span data-ttu-id="af84b-126">Fournit des méthodes destinées au travail avec les tableaux, les pointeurs, les pointeurs fonction et les types ByRef.</span><span class="sxs-lookup"><span data-stu-id="af84b-126">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="af84b-127">Cette interface est une extension de l'interface `ICorDebugAppDomain`.</span><span class="sxs-lookup"><span data-stu-id="af84b-127">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 <span data-ttu-id="af84b-128">[Interface ICorDebugAppDomain3](icordebugappdomain3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-128">[ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)</span></span>\
 <span data-ttu-id="af84b-129">Fournit des méthodes pour utiliser les types de Windows Runtime dans un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="af84b-129">Provides methods to work with the Windows Runtime types in an application domain.</span></span> <span data-ttu-id="af84b-130">Cette interface est une extension des interfaces `ICorDebugAppDomain` et `ICorDebugAppDomain2`.</span><span class="sxs-lookup"><span data-stu-id="af84b-130">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 <span data-ttu-id="af84b-131">[Interface Icordebugappdomain4,](icordebugappdomain4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-131">[ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)</span></span>\
 <span data-ttu-id="af84b-132">Étend logiquement l’interface [ICorDebugAppDomain](icordebugappdomain-interface.md) pour obtenir un objet managé à partir d’un wrapper CCW (COM Callable Wrapper).</span><span class="sxs-lookup"><span data-stu-id="af84b-132">Logically extends the [ICorDebugAppDomain](icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 <span data-ttu-id="af84b-133">[Interface ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-133">[ICorDebugAppDomainEnum Interface](icordebugappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="af84b-134">Fournit une méthode qui retourne un nombre spécifié de valeurs `ICorDebugAppDomain` qui démarrent à l'emplacement suivant dans l'énumération.</span><span class="sxs-lookup"><span data-stu-id="af84b-134">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 <span data-ttu-id="af84b-135">[ICorDebugArrayValue, interface](icordebugarrayvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-135">[ICorDebugArrayValue Interface](icordebugarrayvalue-interface.md)</span></span>\
 <span data-ttu-id="af84b-136">Sous-classe de `ICorDebugHeapValue` qui représente un tableau unidimensionnel ou multidimensionnel.</span><span class="sxs-lookup"><span data-stu-id="af84b-136">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 <span data-ttu-id="af84b-137">[ICorDebugAssembly, interface](icordebugassembly-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-137">[ICorDebugAssembly Interface](icordebugassembly-interface.md)</span></span>\
 <span data-ttu-id="af84b-138">Représente un assembly.</span><span class="sxs-lookup"><span data-stu-id="af84b-138">Represents an assembly.</span></span>  
  
 <span data-ttu-id="af84b-139">[Interface ICorDebugAssembly2](icordebugassembly2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-139">[ICorDebugAssembly2 Interface](icordebugassembly2-interface.md)</span></span>\
 <span data-ttu-id="af84b-140">Représente un assembly.</span><span class="sxs-lookup"><span data-stu-id="af84b-140">Represents an assembly.</span></span> <span data-ttu-id="af84b-141">Cette interface est une extension de l'interface `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="af84b-141">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 <span data-ttu-id="af84b-142">[Interface méthode icordebugassembly3](icordebugassembly3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-142">[ICorDebugAssembly3 Interface](icordebugassembly3-interface.md)</span></span>\
 <span data-ttu-id="af84b-143">Étend logiquement l’interface [ICorDebugAssembly](icordebugassembly-interface.md) pour assurer la prise en charge des assemblys de conteneur et de leurs assemblys contenus.</span><span class="sxs-lookup"><span data-stu-id="af84b-143">Logically extends the [ICorDebugAssembly](icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="af84b-144">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="af84b-144">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="af84b-145">[Interface ICorDebugAssemblyEnum](icordebugassemblyenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-145">[ICorDebugAssemblyEnum Interface](icordebugassemblyenum-interface.md)</span></span>\
 <span data-ttu-id="af84b-146">Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="af84b-146">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 <span data-ttu-id="af84b-147">[Interface ICorDebugBlockingObjectEnum](icordebugblockingobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-147">[ICorDebugBlockingObjectEnum Interface](icordebugblockingobjectenum-interface.md)</span></span>\
 <span data-ttu-id="af84b-148">Fournit un énumérateur pour une liste de structures [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="af84b-148">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
 <span data-ttu-id="af84b-149">[Interface ICorDebugBoxValue](icordebugboxvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-149">[ICorDebugBoxValue Interface](icordebugboxvalue-interface.md)</span></span>\
 <span data-ttu-id="af84b-150">Sous-classe de `ICorDebugHeapValue` qui représente un objet classe de valeur boxed.</span><span class="sxs-lookup"><span data-stu-id="af84b-150">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 <span data-ttu-id="af84b-151">[ICorDebugBreakpoint, interface](icordebugbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-151">[ICorDebugBreakpoint Interface](icordebugbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="af84b-152">Représente un point d'arrêt dans une fonction ou un point de contrôle sur une valeur.</span><span class="sxs-lookup"><span data-stu-id="af84b-152">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 <span data-ttu-id="af84b-153">[Interface ICorDebugBreakpointEnum](icordebugbreakpointenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-153">[ICorDebugBreakpointEnum Interface](icordebugbreakpointenum-interface.md)</span></span>\
 <span data-ttu-id="af84b-154">Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="af84b-154">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 <span data-ttu-id="af84b-155">[ICorDebugChain, interface](icordebugchain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-155">[ICorDebugChain Interface](icordebugchain-interface.md)</span></span>\
 <span data-ttu-id="af84b-156">Représente un segment d'une pile des appels physique ou logique.</span><span class="sxs-lookup"><span data-stu-id="af84b-156">Represents a segment of a physical or logical call stack.</span></span>  
  
 <span data-ttu-id="af84b-157">[ICorDebugChainEnum, interface](icordebugchainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-157">[ICorDebugChainEnum Interface](icordebugchainenum-interface.md)</span></span>\
 <span data-ttu-id="af84b-158">Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugChain`.</span><span class="sxs-lookup"><span data-stu-id="af84b-158">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 <span data-ttu-id="af84b-159">[ICorDebugClass, interface](icordebugclass-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-159">[ICorDebugClass Interface](icordebugclass-interface.md)</span></span>\
 <span data-ttu-id="af84b-160">Représente un type, qui peut être de base ou complexe (c'est-à-dire défini par l'utilisateur).</span><span class="sxs-lookup"><span data-stu-id="af84b-160">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="af84b-161">Si le type est générique, `ICorDebugClass` représente le type générique non instancié.</span><span class="sxs-lookup"><span data-stu-id="af84b-161">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 <span data-ttu-id="af84b-162">[Interface ICorDebugClass2](icordebugclass2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-162">[ICorDebugClass2 Interface](icordebugclass2-interface.md)</span></span>\
 <span data-ttu-id="af84b-163">Représente une classe générique ou une classe avec un paramètre de méthode de type <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="af84b-163">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="af84b-164">Cette interface étend `ICorDebugClass`.</span><span class="sxs-lookup"><span data-stu-id="af84b-164">This interface extends `ICorDebugClass`.</span></span>  
  
 <span data-ttu-id="af84b-165">[ICorDebugCode, interface](icordebugcode-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-165">[ICorDebugCode Interface](icordebugcode-interface1.md)</span></span>\
 <span data-ttu-id="af84b-166">Représente un segment de code MSIL ou de code natif.</span><span class="sxs-lookup"><span data-stu-id="af84b-166">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 <span data-ttu-id="af84b-167">[Interface ICorDebugCode2](icordebugcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-167">[ICorDebugCode2 Interface](icordebugcode2-interface.md)</span></span>\
 <span data-ttu-id="af84b-168">Fournit des méthodes qui étendent les fonctions de `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="af84b-168">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 <span data-ttu-id="af84b-169">[Interface ICorDebugCode3](icordebugcode3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-169">[ICorDebugCode3 Interface](icordebugcode3-interface.md)</span></span>\
 <span data-ttu-id="af84b-170">Fournit une méthode qui étend [ICorDebugCode](icordebugcode-interface1.md) et [ICorDebugCode2](icordebugcode2-interface.md) pour fournir des informations sur une valeur de retour managée.</span><span class="sxs-lookup"><span data-stu-id="af84b-170">Provides a method that extends [ICorDebugCode](icordebugcode-interface1.md) and [ICorDebugCode2](icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 <span data-ttu-id="af84b-171">[Interface ICorDebugCode4](icordebugcode4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-171">[ICorDebugCode4 Interface](icordebugcode4-interface.md)</span></span>\
 <span data-ttu-id="af84b-172">Fournit une méthode qui permet à un débogueur d’énumérer les variables et les arguments locaux dans une fonction.</span><span class="sxs-lookup"><span data-stu-id="af84b-172">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="af84b-173">[Interface ICorDebugCodeEnum](icordebugcodeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-173">[ICorDebugCodeEnum Interface](icordebugcodeenum-interface.md)</span></span>\
 <span data-ttu-id="af84b-174">Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="af84b-174">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 <span data-ttu-id="af84b-175">[Interface ICorDebugComObjectValue](icordebugcomobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-175">[ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="af84b-176">Fournit des méthodes pour récupérer des objets d'interface mis en cache.</span><span class="sxs-lookup"><span data-stu-id="af84b-176">Provides methods to retrieve cached interface objects.</span></span>  
  
 <span data-ttu-id="af84b-177">[Interface ICorDebugContext](icordebugcontext-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-177">[ICorDebugContext Interface](icordebugcontext-interface.md)</span></span>\
 <span data-ttu-id="af84b-178">Représente un objet de contexte.</span><span class="sxs-lookup"><span data-stu-id="af84b-178">Represents a context object.</span></span> <span data-ttu-id="af84b-179">Cette interface n'a pas encore été implémentée.</span><span class="sxs-lookup"><span data-stu-id="af84b-179">This interface has not been implemented yet.</span></span>  
  
 <span data-ttu-id="af84b-180">[ICorDebugController, interface](icordebugcontroller-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-180">[ICorDebugController Interface](icordebugcontroller-interface.md)</span></span>\
 <span data-ttu-id="af84b-181">Représente une portée, un <xref:System.Diagnostics.Process> ou un <xref:System.AppDomain>, où le contexte d'exécution du code peut être contrôlé.</span><span class="sxs-lookup"><span data-stu-id="af84b-181">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 <span data-ttu-id="af84b-182">[ICorDebugDataTarget, interface](icordebugdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-182">[ICorDebugDataTarget Interface](icordebugdatatarget-interface.md)</span></span>\
 <span data-ttu-id="af84b-183">Fournit une interface de rappel qui permet d'accéder à un processus cible particulier.</span><span class="sxs-lookup"><span data-stu-id="af84b-183">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 <span data-ttu-id="af84b-184">[Interface ICorDebugDataTarget2](icordebugdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-184">[ICorDebugDataTarget2 Interface](icordebugdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="af84b-185">Étend logiquement l’interface [ICorDebugDataTarget](icordebugdatatarget-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="af84b-185">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="af84b-186">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="af84b-186">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="af84b-187">[Interface Icordebugdatatarget3,](icordebugdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-187">[ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="af84b-188">Étend logiquement l’interface [ICorDebugDataTarget](icordebugdatatarget-interface.md) pour fournir des informations sur les modules chargés.</span><span class="sxs-lookup"><span data-stu-id="af84b-188">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="af84b-189">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="af84b-189">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="af84b-190">[Interface ICorDebugDebugEvent](icordebugdebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-190">[ICorDebugDebugEvent Interface](icordebugdebugevent-interface.md)</span></span>\
 <span data-ttu-id="af84b-191">Définit l’interface de base de laquelle dérivent tous les événements de débogage `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="af84b-191">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="af84b-192">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="af84b-192">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="af84b-193">[ICorDebugEditAndContinueErrorInfo, interface](icordebugeditandcontinueerrorinfo-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-193">[ICorDebugEditAndContinueErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)</span></span>\
 <span data-ttu-id="af84b-194">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="af84b-194">Obsolete.</span></span> <span data-ttu-id="af84b-195">N'utilisez pas cette interface.</span><span class="sxs-lookup"><span data-stu-id="af84b-195">Do not use this interface.</span></span>  
  
 <span data-ttu-id="af84b-196">[Interface ICorDebugEditAndContinueSnapshot](icordebugeditandcontinuesnapshot-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-196">[ICorDebugEditAndContinueSnapshot Interface](icordebugeditandcontinuesnapshot-interface.md)</span></span>\
 <span data-ttu-id="af84b-197">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="af84b-197">Obsolete.</span></span> <span data-ttu-id="af84b-198">N'utilisez pas cette interface.</span><span class="sxs-lookup"><span data-stu-id="af84b-198">Do not use this interface.</span></span>  
  
 <span data-ttu-id="af84b-199">[ICorDebugEnum, interface](icordebugenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-199">[ICorDebugEnum Interface](icordebugenum-interface1.md)</span></span>\
 <span data-ttu-id="af84b-200">Sert d’interface de base abstraite pour déboguer des énumérateurs.</span><span class="sxs-lookup"><span data-stu-id="af84b-200">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 <span data-ttu-id="af84b-201">[Interface ICorDebugErrorInfoEnum](icordebugerrorinfoenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-201">[ICorDebugErrorInfoEnum Interface](icordebugerrorinfoenum-interface.md)</span></span>\
 <span data-ttu-id="af84b-202">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="af84b-202">Obsolete.</span></span> <span data-ttu-id="af84b-203">N'utilisez pas cette interface.</span><span class="sxs-lookup"><span data-stu-id="af84b-203">Do not use this interface.</span></span>  
  
 <span data-ttu-id="af84b-204">[ICorDebugEval, interface](icordebugeval-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-204">[ICorDebugEval Interface](icordebugeval-interface.md)</span></span>\
 <span data-ttu-id="af84b-205">Fournit des méthodes pour permettre au débogueur d'exécuter le code à l'intérieur du contexte du code en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="af84b-205">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 <span data-ttu-id="af84b-206">[Interface ICorDebugEval2](icordebugeval2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-206">[ICorDebugEval2 Interface](icordebugeval2-interface.md)</span></span>\
 <span data-ttu-id="af84b-207">Étend `ICorDebugEval` pour offrir une prise en charge pour les types génériques.</span><span class="sxs-lookup"><span data-stu-id="af84b-207">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 <span data-ttu-id="af84b-208">[Interface Icordebugexceptiondebugevent,](icordebugexceptiondebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-208">[ICorDebugExceptionDebugEvent Interface](icordebugexceptiondebugevent-interface.md)</span></span>\
 <span data-ttu-id="af84b-209">Étend l’interface [ICorDebugDebugEvent](icordebugdebugevent-interface.md) pour prendre en charge les événements d’exception.</span><span class="sxs-lookup"><span data-stu-id="af84b-209">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="af84b-210">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="af84b-210">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="af84b-211">[Interface Icordebugexceptionobjectcallstackenum,](icordebugexceptionobjectcallstackenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-211">[ICorDebugExceptionObjectCallStackEnum Interface](icordebugexceptionobjectcallstackenum-interface.md)</span></span>\
 <span data-ttu-id="af84b-212">Fournit un énumérateur pour les informations de la pile des appels qui sont incorporées dans un objet exception.</span><span class="sxs-lookup"><span data-stu-id="af84b-212">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 <span data-ttu-id="af84b-213">[Interface Icordebugexceptionobjectvalue,](icordebugexceptionobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-213">[ICorDebugExceptionObjectValue Interface](icordebugexceptionobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="af84b-214">Étend l’interface [ICorDebugObjectValue](icordebugobjectvalue-interface.md) pour fournir des informations de trace de la pile à partir d’un objet exception managée.</span><span class="sxs-lookup"><span data-stu-id="af84b-214">Extends the [ICorDebugObjectValue](icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 <span data-ttu-id="af84b-215">[ICorDebugFrame, interface](icordebugframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-215">[ICorDebugFrame Interface](icordebugframe-interface.md)</span></span>\
 <span data-ttu-id="af84b-216">Représente un frame sur la pile en cours.</span><span class="sxs-lookup"><span data-stu-id="af84b-216">Represents a frame on the current stack.</span></span>  
  
 <span data-ttu-id="af84b-217">[Interface ICorDebugFrameEnum](icordebugframeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-217">[ICorDebugFrameEnum Interface](icordebugframeenum-interface.md)</span></span>\
 <span data-ttu-id="af84b-218">Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="af84b-218">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 <span data-ttu-id="af84b-219">[ICorDebugFunction, interface](icordebugfunction-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-219">[ICorDebugFunction Interface](icordebugfunction-interface1.md)</span></span>\
 <span data-ttu-id="af84b-220">Représente une fonction ou une méthode managée.</span><span class="sxs-lookup"><span data-stu-id="af84b-220">Represents a managed function or method.</span></span>  
  
 <span data-ttu-id="af84b-221">[ICorDebugFunction2, interface](icordebugfunction2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-221">[ICorDebugFunction2 Interface](icordebugfunction2-interface.md)</span></span>\
 <span data-ttu-id="af84b-222">Étend logiquement `ICorDebugFunction` pour prendre en charge le débogage pas à pas pour « Uniquement mon code ».</span><span class="sxs-lookup"><span data-stu-id="af84b-222">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 <span data-ttu-id="af84b-223">[Interface Icordebugfunction3,](icordebugfunction3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-223">[ICorDebugFunction3 Interface](icordebugfunction3-interface.md)</span></span>\
 <span data-ttu-id="af84b-224">Étend logiquement l’interface [ICorDebugFunction](icordebugfunction-interface1.md) pour fournir l’accès au code à partir d’une demande ReJIT.</span><span class="sxs-lookup"><span data-stu-id="af84b-224">Logically extends the [ICorDebugFunction](icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 <span data-ttu-id="af84b-225">[ICorDebugFunctionBreakpoint, interface](icordebugfunctionbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-225">[ICorDebugFunctionBreakpoint Interface](icordebugfunctionbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="af84b-226">Étend `ICorDebugBreakpoint` pour prendre en charge les points d'arrêt au sein de fonctions.</span><span class="sxs-lookup"><span data-stu-id="af84b-226">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 <span data-ttu-id="af84b-227">[Interface Icordebuggcreferenceenum,](icordebuggcreferenceenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-227">[ICorDebugGCReferenceEnum Interface](icordebuggcreferenceenum-interface.md)</span></span>\
 <span data-ttu-id="af84b-228">Fournit un énumérateur pour les objets qui sont récupérés par le récupérateur de mémoire.</span><span class="sxs-lookup"><span data-stu-id="af84b-228">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 <span data-ttu-id="af84b-229">[Interface ICorDebugGenericValue](icordebuggenericvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-229">[ICorDebugGenericValue Interface](icordebuggenericvalue-interface.md)</span></span>\
 <span data-ttu-id="af84b-230">Sous-classe de `ICorDebugValue` qui s'applique à toutes les valeurs.</span><span class="sxs-lookup"><span data-stu-id="af84b-230">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="af84b-231">Cette interface fournit les méthodes Get et Set pour la valeur.</span><span class="sxs-lookup"><span data-stu-id="af84b-231">This interface provides Get and Set methods for the value.</span></span>  
  
 <span data-ttu-id="af84b-232">[Interface Icordebugguidtotypeenum,](icordebugguidtotypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-232">[ICorDebugGuidToTypeEnum Interface](icordebugguidtotypeenum-interface.md)</span></span>\
 <span data-ttu-id="af84b-233">Fournit un énumérateur pour un objet qui mappe les GUID et leurs objets `ICorDebugType` correspondants.</span><span class="sxs-lookup"><span data-stu-id="af84b-233">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 <span data-ttu-id="af84b-234">[ICorDebugHandleValue, interface](icordebughandlevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-234">[ICorDebugHandleValue Interface](icordebughandlevalue-interface.md)</span></span>\
 <span data-ttu-id="af84b-235">Sous-classe de `ICorDebugReferenceValue` qui représente une valeur de référence dans laquelle le débogueur a créé un handle pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="af84b-235">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 <span data-ttu-id="af84b-236">[Interface Icordebugheapenum,](icordebugheapenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-236">[ICorDebugHeapEnum Interface](icordebugheapenum-interface.md)</span></span>\
 <span data-ttu-id="af84b-237">Fournit un énumérateur pour les objets sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="af84b-237">Provides an enumerator for objects on the managed heap.</span></span>  
  
 <span data-ttu-id="af84b-238">[Interface Icordebugheapsegmentenum,](icordebugheapsegmentenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-238">[ICorDebugHeapSegmentEnum Interface](icordebugheapsegmentenum-interface.md)</span></span>\
 <span data-ttu-id="af84b-239">Fournit un énumérateur pour les régions de mémoire du tas managé.</span><span class="sxs-lookup"><span data-stu-id="af84b-239">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 <span data-ttu-id="af84b-240">[ICorDebugHeapValue, interface](icordebugheapvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-240">[ICorDebugHeapValue Interface](icordebugheapvalue-interface.md)</span></span>\
 <span data-ttu-id="af84b-241">Sous-classe de `ICorDebugValue` qui représente un objet qui a été collecté par le garbage collector du CLR.</span><span class="sxs-lookup"><span data-stu-id="af84b-241">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 <span data-ttu-id="af84b-242">[Interface ICorDebugHeapValue2](icordebugheapvalue2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-242">[ICorDebugHeapValue2 Interface](icordebugheapvalue2-interface1.md)</span></span>\
 <span data-ttu-id="af84b-243">Extension de `ICorDebugHeapValue` qui fournit la prise en charge des handles d’exécution.</span><span class="sxs-lookup"><span data-stu-id="af84b-243">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 <span data-ttu-id="af84b-244">[Interface ICorDebugHeapValue3](icordebugheapvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-244">[ICorDebugHeapValue3 Interface](icordebugheapvalue3-interface.md)</span></span>\
 <span data-ttu-id="af84b-245">Expose les propriétés du verrou du moniteur d'objets.</span><span class="sxs-lookup"><span data-stu-id="af84b-245">Exposes the monitor lock properties of objects.</span></span>  
  
 <span data-ttu-id="af84b-246">[Interface ICorDebugILCode](icordebugilcode-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-246">[ICorDebugILCode Interface](icordebugilcode-interface.md)</span></span>\
 <span data-ttu-id="af84b-247">Représente un segment du code en langage intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="af84b-247">Represents a segment of intermediate language (IL) code.</span></span>  
  
 <span data-ttu-id="af84b-248">[Interface ICorDebugILCode2](icordebugilcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-248">[ICorDebugILCode2 Interface](icordebugilcode2-interface.md)</span></span>\
 <span data-ttu-id="af84b-249">Étend logiquement l’interface [ICorDebugILCode](icordebugilcode-interface.md) pour fournir des méthodes qui retournent le jeton pour la signature de variable locale d’une fonction et qui mappent les offsets du langage intermédiaire instrumenté d’un profileur aux DÉCALAGEs il de la méthode d’origine.</span><span class="sxs-lookup"><span data-stu-id="af84b-249">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 <span data-ttu-id="af84b-250">[ICorDebugILFrame, interface](icordebugilframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-250">[ICorDebugILFrame Interface](icordebugilframe-interface.md)</span></span>\
 <span data-ttu-id="af84b-251">Représente un frame de pile de code MSIL.</span><span class="sxs-lookup"><span data-stu-id="af84b-251">Represents a stack frame of MSIL code.</span></span>  
  
 <span data-ttu-id="af84b-252">[Interface ICorDebugILFrame2](icordebugilframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-252">[ICorDebugILFrame2 Interface](icordebugilframe2-interface.md)</span></span>\
 <span data-ttu-id="af84b-253">Extension logique de `ICorDebugILFrame`.</span><span class="sxs-lookup"><span data-stu-id="af84b-253">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 <span data-ttu-id="af84b-254">[Interface ICorDebugILFrame3](icordebugilframe3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-254">[ICorDebugILFrame3 Interface](icordebugilframe3-interface.md)</span></span>\
 <span data-ttu-id="af84b-255">Fournit une méthode qui encapsule la valeur de retour d'une fonction.</span><span class="sxs-lookup"><span data-stu-id="af84b-255">Provides a method that encapsulates the return value of a function.</span></span>  
  
 <span data-ttu-id="af84b-256">[Interface ICorDebugILFrame4](icordebugilframe4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-256">[ICorDebugILFrame4 Interface](icordebugilframe4-interface.md)</span></span>\
 <span data-ttu-id="af84b-257">Fournit des méthodes qui vous permettent d'accéder aux variables locales et au code dans un frame de pile de code de langage intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="af84b-257">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="af84b-258">Un paramètre spécifie si le débogueur a accès aux variables et au code ajoutés dans l'instrumentation ReJIT du profileur.</span><span class="sxs-lookup"><span data-stu-id="af84b-258">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 <span data-ttu-id="af84b-259">[Interface Icordebuginstancefieldsymbol,](icordebuginstancefieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-259">[ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="af84b-260">Représente les informations sur les symboles de débogage pour un champ d’instance.</span><span class="sxs-lookup"><span data-stu-id="af84b-260">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="af84b-261">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="af84b-261">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="af84b-262">[Interface ICorDebugInternalFrame](icordebuginternalframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-262">[ICorDebugInternalFrame Interface](icordebuginternalframe-interface.md)</span></span>\
 <span data-ttu-id="af84b-263">Identifie les types de frame pour le débogueur.</span><span class="sxs-lookup"><span data-stu-id="af84b-263">Identifies frame types for the debugger.</span></span>  
  
 <span data-ttu-id="af84b-264">[Interface ICorDebugInternalFrame2](icordebuginternalframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-264">[ICorDebugInternalFrame2 Interface](icordebuginternalframe2-interface.md)</span></span>\
 <span data-ttu-id="af84b-265">Fournit des informations sur les frames internes, y compris l’adresse et la position de la pile par rapport aux objets [ICorDebugFrame](icordebugframe-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="af84b-265">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](icordebugframe-interface.md) objects.</span></span>  
  
 <span data-ttu-id="af84b-266">[Interface ICorDebugLoadedModule](icordebugloadedmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-266">[ICorDebugLoadedModule Interface](icordebugloadedmodule-interface.md)</span></span>\
 <span data-ttu-id="af84b-267">Fournit des informations sur un module chargé.</span><span class="sxs-lookup"><span data-stu-id="af84b-267">Provides information about a loaded module.</span></span> <span data-ttu-id="af84b-268">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="af84b-268">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="af84b-269">[ICorDebugManagedCallback, interface](icordebugmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-269">[ICorDebugManagedCallback Interface](icordebugmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="af84b-270">Fournit des méthodes pour traiter les rappels de débogueur.</span><span class="sxs-lookup"><span data-stu-id="af84b-270">Provides methods to process debugger callbacks.</span></span>  
  
 <span data-ttu-id="af84b-271">[ICorDebugManagedCallback2, interface](icordebugmanagedcallback2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-271">[ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)</span></span>\
 <span data-ttu-id="af84b-272">Fournit des méthodes pour prendre en charge la gestion des exceptions et les Assistants Débogage managé (MDA) du débogueur.</span><span class="sxs-lookup"><span data-stu-id="af84b-272">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="af84b-273">`ICorDebugManagedCallback2` est une extension logique de `ICorDebugManagedCallback`.</span><span class="sxs-lookup"><span data-stu-id="af84b-273">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 <span data-ttu-id="af84b-274">[Interface ICorDebugManagedCallback3](icordebugmanagedcallback3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-274">[ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)</span></span>\
 <span data-ttu-id="af84b-275">Fournit une méthode de rappel indiquant qu'une notification de débogueur personnalisée active a été déclenchée.</span><span class="sxs-lookup"><span data-stu-id="af84b-275">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 <span data-ttu-id="af84b-276">[ICorDebugMDA, interface](icordebugmda-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-276">[ICorDebugMDA Interface](icordebugmda-interface.md)</span></span>\
 <span data-ttu-id="af84b-277">Représente un message d'Assistant Débogage managé (MDA).</span><span class="sxs-lookup"><span data-stu-id="af84b-277">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 <span data-ttu-id="af84b-278">[Interface ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-278">[ICorDebugMemoryBuffer Interface](icordebugmemorybuffer-interface.md)</span></span>\
 <span data-ttu-id="af84b-279">Représente une mémoire tampon en mémoire.</span><span class="sxs-lookup"><span data-stu-id="af84b-279">Represents an in-memory buffer.</span></span> <span data-ttu-id="af84b-280">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="af84b-280">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="af84b-281">[Interface ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-281">[ICorDebugMergedAssemblyRecord Interface](icordebugmergedassemblyrecord-interface.md)</span></span>\
 <span data-ttu-id="af84b-282">Fournit des informations sur un assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="af84b-282">Provides information about a merged assembly.</span></span> <span data-ttu-id="af84b-283">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="af84b-283">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="af84b-284">[Interface ICorDebugMetaDataLocator](icordebugmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-284">[ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="af84b-285">Fournit des informations de métadonnées au débogueur.</span><span class="sxs-lookup"><span data-stu-id="af84b-285">Provides metadata information to the debugger.</span></span>  
  
 <span data-ttu-id="af84b-286">[ICorDebugModule, interface](icordebugmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-286">[ICorDebugModule Interface](icordebugmodule-interface.md)</span></span>\
 <span data-ttu-id="af84b-287">Représente un module CLR qui est un fichier exécutable ou une bibliothèque de liens dynamiques (DLL).</span><span class="sxs-lookup"><span data-stu-id="af84b-287">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 <span data-ttu-id="af84b-288">[Interface ICorDebugModule2](icordebugmodule2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-288">[ICorDebugModule2 Interface](icordebugmodule2-interface.md)</span></span>\
 <span data-ttu-id="af84b-289">Sert d’extension logique de `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="af84b-289">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 <span data-ttu-id="af84b-290">[Interface ICorDebugModule3](icordebugmodule3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-290">[ICorDebugModule3 Interface](icordebugmodule3-interface.md)</span></span>\
 <span data-ttu-id="af84b-291">Crée un lecteur de symboles pour un module dynamique.</span><span class="sxs-lookup"><span data-stu-id="af84b-291">Creates a symbol reader for a dynamic module.</span></span>  
  
 <span data-ttu-id="af84b-292">[Interface ICorDebugModuleBreakpoint](icordebugmodulebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-292">[ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="af84b-293">Étend `ICorDebugBreakpoint` pour fournir l'accès aux modules spécifiques.</span><span class="sxs-lookup"><span data-stu-id="af84b-293">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 <span data-ttu-id="af84b-294">[Interface Icordebugmoduledebugevent,](icordebugmoduledebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-294">[ICorDebugModuleDebugEvent Interface](icordebugmoduledebugevent-interface.md)</span></span>\
 <span data-ttu-id="af84b-295">Étend l’interface [ICorDebugDebugEvent](icordebugdebugevent-interface.md) pour prendre en charge les événements au niveau du module.</span><span class="sxs-lookup"><span data-stu-id="af84b-295">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="af84b-296">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="af84b-296">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="af84b-297">[Interface ICorDebugModuleEnum](icordebugmoduleenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-297">[ICorDebugModuleEnum Interface](icordebugmoduleenum-interface.md)</span></span>\
 <span data-ttu-id="af84b-298">Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="af84b-298">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 <span data-ttu-id="af84b-299">[Interface ICorDebugMutableDataTarget](icordebugmutabledatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-299">[ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)</span></span>\
 <span data-ttu-id="af84b-300">Étend l’interface [ICorDebugDataTarget](icordebugdatatarget-interface.md) pour prendre en charge les cibles de données mutables.</span><span class="sxs-lookup"><span data-stu-id="af84b-300">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 <span data-ttu-id="af84b-301">[ICorDebugNativeFrame, interface](icordebugnativeframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-301">[ICorDebugNativeFrame Interface](icordebugnativeframe-interface.md)</span></span>\
 <span data-ttu-id="af84b-302">Implémentation spécialisée de `ICorDebugFrame` utilisée pour les frames natifs.</span><span class="sxs-lookup"><span data-stu-id="af84b-302">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 <span data-ttu-id="af84b-303">[Interface ICorDebugNativeFrame2](icordebugnativeframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-303">[ICorDebugNativeFrame2 Interface](icordebugnativeframe2-interface.md)</span></span>\
 <span data-ttu-id="af84b-304">Fournit des méthodes qui testent les relations entre frames enfant et parent.</span><span class="sxs-lookup"><span data-stu-id="af84b-304">Provides methods that test for child and parent frame relationships.</span></span>  
  
 <span data-ttu-id="af84b-305">[Interface ICorDebugObjectEnum](icordebugobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-305">[ICorDebugObjectEnum Interface](icordebugobjectenum-interface.md)</span></span>\
 <span data-ttu-id="af84b-306">Implémente les méthodes `ICorDebugEnum` et énumère des tableaux d'objets par leurs adresses virtuelles relatives.</span><span class="sxs-lookup"><span data-stu-id="af84b-306">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 <span data-ttu-id="af84b-307">[ICorDebugObjectValue, interface](icordebugobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-307">[ICorDebugObjectValue Interface](icordebugobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="af84b-308">Sous-classe de `ICorDebugValue` qui représente une valeur contenant un objet.</span><span class="sxs-lookup"><span data-stu-id="af84b-308">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 <span data-ttu-id="af84b-309">[Interface ICorDebugObjectValue2](icordebugobjectvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-309">[ICorDebugObjectValue2 Interface](icordebugobjectvalue2-interface.md)</span></span>\
 <span data-ttu-id="af84b-310">Étend `ICorDebugObjectValue` pour prendre en charge l'héritage et les substitutions.</span><span class="sxs-lookup"><span data-stu-id="af84b-310">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 <span data-ttu-id="af84b-311">[ICorDebugProcess, interface](icordebugprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-311">[ICorDebugProcess Interface](icordebugprocess-interface.md)</span></span>\
 <span data-ttu-id="af84b-312">Représente un processus qui exécute le code managé.</span><span class="sxs-lookup"><span data-stu-id="af84b-312">Represents a process that is executing managed code.</span></span>  
  
 <span data-ttu-id="af84b-313">[Interface ICorDebugProcess2](icordebugprocess2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-313">[ICorDebugProcess2 Interface](icordebugprocess2-interface1.md)</span></span>\
 <span data-ttu-id="af84b-314">Extension logique de `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="af84b-314">A logical extension of `ICorDebugProcess`.</span></span>  
  
 <span data-ttu-id="af84b-315">[Interface ICorDebugProcess3](icordebugprocess3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-315">[ICorDebugProcess3 Interface](icordebugprocess3-interface.md)</span></span>\
 <span data-ttu-id="af84b-316">Contrôle les notifications de débogueur personnalisées.</span><span class="sxs-lookup"><span data-stu-id="af84b-316">Controls custom debugger notifications.</span></span>

 <span data-ttu-id="af84b-317">[Interface ICorDebugProcess4](icordebugprocess4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-317">[ICorDebugProcess4 Interface](icordebugprocess4-interface.md)</span></span>\
 <span data-ttu-id="af84b-318">Prend en charge le contrôle de l’exécution hors processus.</span><span class="sxs-lookup"><span data-stu-id="af84b-318">Provides support for out of process execution control.</span></span>
  
 <span data-ttu-id="af84b-319">[Interface ICorDebugProcess5](icordebugprocess5-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-319">[ICorDebugProcess5 Interface](icordebugprocess5-interface.md)</span></span>\
 <span data-ttu-id="af84b-320">Étend l’interface [ICorDebugProcess](icordebugprocess-interface.md) pour prendre en charge l’accès au tas managé, pour fournir des informations sur garbage collection d’objets managés et pour déterminer si un débogueur charge des images à partir du cache des images natives locales de l’application.</span><span class="sxs-lookup"><span data-stu-id="af84b-320">Extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 <span data-ttu-id="af84b-321">[Interface ICorDebugProcess6](icordebugprocess6-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-321">[ICorDebugProcess6 Interface](icordebugprocess6-interface.md)</span></span>\
 <span data-ttu-id="af84b-322">Étend logiquement l’interface [ICorDebugProcess](icordebugprocess-interface.md) pour activer des fonctionnalités telles que le décodage des événements de débogage managés qui sont encodés dans des événements de débogage d’exception native et le fractionnement de module virtuel.</span><span class="sxs-lookup"><span data-stu-id="af84b-322">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="af84b-323">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="af84b-323">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="af84b-324">[Interface Icordebugprocess7,](icordebugprocess7-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-324">[ICorDebugProcess7 Interface](icordebugprocess7-interface.md)</span></span>\
 <span data-ttu-id="af84b-325">Fournit une méthode qui configure le débogueur afin de gérer les mises à jour de métadonnées en mémoire dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="af84b-325">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 <span data-ttu-id="af84b-326">[Interface Icordebugprocess8,](icordebugprocess8-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-326">[ICorDebugProcess8 Interface](icordebugprocess8-interface.md)</span></span>\
 <span data-ttu-id="af84b-327">Étend logiquement l’interface [ICorDebugProcess](icordebugprocess-interface.md) pour activer ou désactiver certains types de rappels d’exception [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="af84b-327">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 <span data-ttu-id="af84b-328">[Interface ICorDebugProcessEnum](icordebugprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-328">[ICorDebugProcessEnum Interface](icordebugprocessenum-interface.md)</span></span>\
 <span data-ttu-id="af84b-329">Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="af84b-329">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 <span data-ttu-id="af84b-330">[ICorDebugReferenceValue (interface)](icordebugreferencevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-330">[ICorDebugReferenceValue Interface](icordebugreferencevalue-interface.md)</span></span>\
 <span data-ttu-id="af84b-331">Sous-classe de `ICorDebugValue` qui prend en charge les types référence.</span><span class="sxs-lookup"><span data-stu-id="af84b-331">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 <span data-ttu-id="af84b-332">[ICorDebugRegisterSet, interface](icordebugregisterset-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-332">[ICorDebugRegisterSet Interface](icordebugregisterset-interface.md)</span></span>\
 <span data-ttu-id="af84b-333">Représente le jeu de registres disponible sur l'ordinateur qui exécute actuellement le code.</span><span class="sxs-lookup"><span data-stu-id="af84b-333">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 <span data-ttu-id="af84b-334">[Interface ICorDebugRegisterSet2](icordebugregisterset2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-334">[ICorDebugRegisterSet2 Interface](icordebugregisterset2-interface.md)</span></span>\
 <span data-ttu-id="af84b-335">Étend les fonctionnalités de `ICorDebugRegisterSet` pour les plateformes matérielles qui possèdent plus de 64 registres.</span><span class="sxs-lookup"><span data-stu-id="af84b-335">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 <span data-ttu-id="af84b-336">[Interface ICorDebugRemote](icordebugremote-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-336">[ICorDebugRemote Interface](icordebugremote-interface.md)</span></span>\
 <span data-ttu-id="af84b-337">Fournit la possibilité de lancer ou de joindre un débogueur managé à un processus distant cible.</span><span class="sxs-lookup"><span data-stu-id="af84b-337">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 <span data-ttu-id="af84b-338">[Interface ICorDebugRemoteTarget](icordebugremotetarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-338">[ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md)</span></span>\
 <span data-ttu-id="af84b-339">Fournit des méthodes qui vous permettent de déboguer les applications Silverlight dans l'environnement du CLR.</span><span class="sxs-lookup"><span data-stu-id="af84b-339">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="af84b-340">[Interface ICorDebugRuntimeUnwindableFrame,](icordebugruntimeunwindableframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-340">[ICorDebugRuntimeUnwindableFrame Interface](icordebugruntimeunwindableframe-interface.md)</span></span>\
 <span data-ttu-id="af84b-341">Fournit un support technique pour les méthodes non managées qui requièrent que le Common Language Runtime (CLR) déroule un frame.</span><span class="sxs-lookup"><span data-stu-id="af84b-341">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 <span data-ttu-id="af84b-342">[ICorDebugStackWalk, interface](icordebugstackwalk-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-342">[ICorDebugStackWalk Interface](icordebugstackwalk-interface.md)</span></span>\
 <span data-ttu-id="af84b-343">Fournit des méthodes pour obtenir les méthodes managées, ou frames, sur la pile d'un thread.</span><span class="sxs-lookup"><span data-stu-id="af84b-343">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 <span data-ttu-id="af84b-344">[Interface ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-344">[ICorDebugStaticFieldSymbol Interface](icordebugstaticfieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="af84b-345">Représente les informations sur les symboles de débogage pour un champ static.</span><span class="sxs-lookup"><span data-stu-id="af84b-345">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="af84b-346">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="af84b-346">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="af84b-347">[ICorDebugStepper (interface)](icordebugstepper-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-347">[ICorDebugStepper Interface](icordebugstepper-interface.md)</span></span>\
 <span data-ttu-id="af84b-348">Représente dans l'exécution du code une étape qui est effectuée par un débogueur, et qui sert d'identificateur entre l'émission et l'achèvement d'une commande tout en offrant un moyen d'annuler une étape.</span><span class="sxs-lookup"><span data-stu-id="af84b-348">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 <span data-ttu-id="af84b-349">[Interface ICorDebugStepper2](icordebugstepper2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-349">[ICorDebugStepper2 Interface](icordebugstepper2-interface1.md)</span></span>\
 <span data-ttu-id="af84b-350">Prend en charge le débogage « Uniquement mon code ».</span><span class="sxs-lookup"><span data-stu-id="af84b-350">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 <span data-ttu-id="af84b-351">[Interface ICorDebugStepperEnum](icordebugstepperenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-351">[ICorDebugStepperEnum Interface](icordebugstepperenum-interface.md)</span></span>\
 <span data-ttu-id="af84b-352">Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugStepper`.</span><span class="sxs-lookup"><span data-stu-id="af84b-352">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 <span data-ttu-id="af84b-353">[ICorDebugStringValue, interface](icordebugstringvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-353">[ICorDebugStringValue Interface](icordebugstringvalue-interface.md)</span></span>\
 <span data-ttu-id="af84b-354">Sous-classe de `ICorDebugHeapValue` qui s'applique aux valeurs de chaîne.</span><span class="sxs-lookup"><span data-stu-id="af84b-354">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 <span data-ttu-id="af84b-355">[Interface ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-355">[ICorDebugSymbolProvider Interface](icordebugsymbolprovider-interface.md)</span></span>\
 <span data-ttu-id="af84b-356">Fournit des méthodes pouvant être utilisées pour récupérer des informations sur les symboles de débogage.</span><span class="sxs-lookup"><span data-stu-id="af84b-356">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="af84b-357">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="af84b-357">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="af84b-358">[Interface Icordebugsymbolprovider2,](icordebugsymbolprovider2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-358">[ICorDebugSymbolProvider2 Interface](icordebugsymbolprovider2-interface.md)</span></span>\
 <span data-ttu-id="af84b-359">Étend logiquement l’interface [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) pour récupérer des informations supplémentaires sur les symboles de débogage.</span><span class="sxs-lookup"><span data-stu-id="af84b-359">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="af84b-360">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="af84b-360">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="af84b-361">[ICorDebugThread, interface](icordebugthread-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-361">[ICorDebugThread Interface](icordebugthread-interface.md)</span></span>\
 <span data-ttu-id="af84b-362">Représente un thread de processus.</span><span class="sxs-lookup"><span data-stu-id="af84b-362">Represents a thread in a process.</span></span> <span data-ttu-id="af84b-363">La durée de vie d'une instance `ICorDebugThread` est la même que la durée de vie du thread qu'elle représente.</span><span class="sxs-lookup"><span data-stu-id="af84b-363">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 <span data-ttu-id="af84b-364">[ICorDebugThread2, interface](icordebugthread2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-364">[ICorDebugThread2 Interface](icordebugthread2-interface.md)</span></span>\
 <span data-ttu-id="af84b-365">Sert d’extension logique de `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="af84b-365">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 <span data-ttu-id="af84b-366">[Interface ICorDebugThread3](icordebugthread3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-366">[ICorDebugThread3 Interface](icordebugthread3-interface.md)</span></span>\
 <span data-ttu-id="af84b-367">Fournit le point d’entrée pour [ICorDebugStackWalk](icordebugstackwalk-interface.md) et les interfaces correspondantes.</span><span class="sxs-lookup"><span data-stu-id="af84b-367">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 <span data-ttu-id="af84b-368">[Interface ICorDebugThread4](icordebugthread4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-368">[ICorDebugThread4 Interface](icordebugthread4-interface.md)</span></span>\
 <span data-ttu-id="af84b-369">Fournit des informations sur le blocage des threads.</span><span class="sxs-lookup"><span data-stu-id="af84b-369">Provides thread blocking information.</span></span>  
  
 <span data-ttu-id="af84b-370">[Interface ICorDebugThreadEnum](icordebugthreadenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-370">[ICorDebugThreadEnum Interface](icordebugthreadenum-interface1.md)</span></span>\
 <span data-ttu-id="af84b-371">Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="af84b-371">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 <span data-ttu-id="af84b-372">[ICorDebugType, interface](icordebugtype-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-372">[ICorDebugType Interface](icordebugtype-interface.md)</span></span>\
 <span data-ttu-id="af84b-373">Représente un type, qui peut être de base ou complexe (c'est-à-dire défini par l'utilisateur).</span><span class="sxs-lookup"><span data-stu-id="af84b-373">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="af84b-374">Si le type est générique, `ICorDebugType` représente le type générique instancié.</span><span class="sxs-lookup"><span data-stu-id="af84b-374">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 <span data-ttu-id="af84b-375">[Interface méthode icordebugtype2](icordebugtype2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-375">[ICorDebugType2 Interface](icordebugtype2-interface.md)</span></span>\
 <span data-ttu-id="af84b-376">Étend l’interface [ICorDebugType](icordebugtype-interface.md) pour récupérer l’identificateur de type d’un type de base ou un type complexe (défini par l’utilisateur).</span><span class="sxs-lookup"><span data-stu-id="af84b-376">Extends the [ICorDebugType](icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 <span data-ttu-id="af84b-377">[ICorDebugTypeEnum, interface](icordebugtypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-377">[ICorDebugTypeEnum Interface](icordebugtypeenum-interface.md)</span></span>\
 <span data-ttu-id="af84b-378">Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="af84b-378">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 <span data-ttu-id="af84b-379">[Interface ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-379">[ICorDebugUnmanagedCallback Interface](icordebugunmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="af84b-380">Fournit une notification des événements natifs qui ne sont pas mis directement en rapport avec le CLR.</span><span class="sxs-lookup"><span data-stu-id="af84b-380">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="af84b-381">[ICorDebugValue](icordebugvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-381">[ICorDebugValue](icordebugvalue-interface.md)</span></span>\
 <span data-ttu-id="af84b-382">Représente une valeur de lecture ou d'écriture dans le processus en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="af84b-382">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="af84b-383">[ICorDebugValue2](icordebugvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-383">[ICorDebugValue2](icordebugvalue2-interface.md)</span></span>\
 <span data-ttu-id="af84b-384">Étend `ICorDebugValue` pour prendre en charge `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="af84b-384">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="af84b-385">[Interface Icordebugvalue3,](icordebugvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-385">[ICorDebugValue3 Interface](icordebugvalue3-interface.md)</span></span>\
 <span data-ttu-id="af84b-386">Étend les interfaces « ICorDebugValue » et « ICorDebugValue2 » pour assurer la prise en charge des tableaux d’une taille supérieure à 2 Go.</span><span class="sxs-lookup"><span data-stu-id="af84b-386">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="af84b-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="af84b-388">Étend `ICorDebugBreakpoint` pour fournir l'accès aux valeurs spécifiques.</span><span class="sxs-lookup"><span data-stu-id="af84b-388">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="af84b-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span></span>\
 <span data-ttu-id="af84b-390">Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugValue`.</span><span class="sxs-lookup"><span data-stu-id="af84b-390">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 <span data-ttu-id="af84b-391">[Interface ICorDebugVariableHome](icordebugvariablehome-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-391">[ICorDebugVariableHome Interface](icordebugvariablehome-interface.md)</span></span>\
 <span data-ttu-id="af84b-392">Représente une variable locale ou un argument d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="af84b-392">Represents a local variable or argument of a function.</span></span>  
  
 <span data-ttu-id="af84b-393">[Interface ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-393">[ICorDebugVariableHomeEnum Interface](icordebugvariablehomeenum-interface.md)</span></span>\
 <span data-ttu-id="af84b-394">Fournit un énumérateur aux variables locales et aux arguments dans une fonction.</span><span class="sxs-lookup"><span data-stu-id="af84b-394">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="af84b-395">[Interface méthode icordebugvariablesymbol](icordebugvariablesymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-395">[ICorDebugVariableSymbol Interface](icordebugvariablesymbol-interface.md)</span></span>\
 <span data-ttu-id="af84b-396">Récupère les informations sur les symboles de débogage pour une variable.</span><span class="sxs-lookup"><span data-stu-id="af84b-396">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="af84b-397">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="af84b-397">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="af84b-398">[Interface ICorDebugVirtualUnwinder](icordebugvirtualunwinder-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-398">[ICorDebugVirtualUnwinder Interface](icordebugvirtualunwinder-interface.md)</span></span>\
 <span data-ttu-id="af84b-399">Fournit des méthodes pour faciliter le déroulement de la pile.</span><span class="sxs-lookup"><span data-stu-id="af84b-399">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="af84b-400">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="af84b-400">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="af84b-401">[ICorPublish, interface](icorpublish-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-401">[ICorPublish Interface](icorpublish-interface.md)</span></span>\
 <span data-ttu-id="af84b-402">Sert d'interface générale pour les processus de publication.</span><span class="sxs-lookup"><span data-stu-id="af84b-402">Serves as the general interface for the publishing processes.</span></span>  
  
 <span data-ttu-id="af84b-403">[ICorPublishAppDomain, interface](icorpublishappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-403">[ICorPublishAppDomain Interface](icorpublishappdomain-interface.md)</span></span>\
 <span data-ttu-id="af84b-404">Représente et fournit des informations à propos d'un domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="af84b-404">Represents and provides information about an application domain.</span></span>  
  
 <span data-ttu-id="af84b-405">[ICorPublishAppDomainEnum, interface](icorpublishappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-405">[ICorPublishAppDomainEnum Interface](icorpublishappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="af84b-406">Fournit des méthodes qui parcourent une collection d’objets `ICorPublishAppDomain` qui existent actuellement dans un processus.</span><span class="sxs-lookup"><span data-stu-id="af84b-406">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 <span data-ttu-id="af84b-407">[ICorPublishEnum, interface](icorpublishenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-407">[ICorPublishEnum Interface](icorpublishenum-interface.md)</span></span>\
 <span data-ttu-id="af84b-408">Sert comme base abstraite pour la publication des énumérateurs.</span><span class="sxs-lookup"><span data-stu-id="af84b-408">Serves as the abstract base for publishing enumerators.</span></span>  
  
 <span data-ttu-id="af84b-409">[ICorPublishProcess, interface](icorpublishprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-409">[ICorPublishProcess Interface](icorpublishprocess-interface.md)</span></span>\
 <span data-ttu-id="af84b-410">Fournit des méthodes qui permettent d'accéder aux informations sur un processus.</span><span class="sxs-lookup"><span data-stu-id="af84b-410">Provides methods that access information about a process.</span></span>  
  
 <span data-ttu-id="af84b-411">[Interface ICorPublishProcessEnum](icorpublishprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-411">[ICorPublishProcessEnum Interface](icorpublishprocessenum-interface.md)</span></span>\
 <span data-ttu-id="af84b-412">Fournit des méthodes qui parcourent une collection d’objets `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="af84b-412">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  

 <span data-ttu-id="af84b-413">[Interface ISOSDacInterface](isosdacinterface-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-413">[ISOSDacInterface Interface](isosdacinterface-interface.md)</span></span>\
 <span data-ttu-id="af84b-414">Fournit des méthodes d’assistance pour accéder aux données à partir de `SOS` .</span><span class="sxs-lookup"><span data-stu-id="af84b-414">Provides helper methods to access data from `SOS`.</span></span>

 <span data-ttu-id="af84b-415">[Interface IXCLRDataMethodDefinition](ixclrdatamethoddefinition-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-415">[IXCLRDataMethodDefinition Interface](ixclrdatamethoddefinition-interface.md)</span></span>\
 <span data-ttu-id="af84b-416">Fournit des méthodes pour interroger des informations sur une définition de méthode.</span><span class="sxs-lookup"><span data-stu-id="af84b-416">Provides methods for querying information about a method definition.</span></span>

 <span data-ttu-id="af84b-417">[Interface IXCLRDataMethodInstance](ixclrdatamethodinstance-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-417">[IXCLRDataMethodInstance Interface](ixclrdatamethodinstance-interface.md)</span></span>\
 <span data-ttu-id="af84b-418">Fournit des méthodes pour interroger les informations relatives à une instance de méthode.</span><span class="sxs-lookup"><span data-stu-id="af84b-418">Provides methods for querying information about a method instance.</span></span>

 <span data-ttu-id="af84b-419">[Interface IXCLRDataModule](ixclrdatamodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-419">[IXCLRDataModule Interface](ixclrdatamodule-interface.md)</span></span>\
 <span data-ttu-id="af84b-420">Fournit des méthodes pour interroger des informations sur un module chargé.</span><span class="sxs-lookup"><span data-stu-id="af84b-420">Provides methods for querying information about a loaded module.</span></span>

 <span data-ttu-id="af84b-421">[Interface IXCLRDataProcess](ixclrdataprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-421">[IXCLRDataProcess Interface](ixclrdataprocess-interface.md)</span></span>\
 <span data-ttu-id="af84b-422">Fournit des méthodes pour interroger les informations relatives à un processus.</span><span class="sxs-lookup"><span data-stu-id="af84b-422">Provides methods for querying information about a process.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="af84b-423">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="af84b-423">Related Sections</span></span>  

 <span data-ttu-id="af84b-424">[Débogage des coclasses](debugging-coclasses.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-424">[Debugging Coclasses](debugging-coclasses.md)</span></span>\
 <span data-ttu-id="af84b-425">[Fonctions statiques globales de débogage](debugging-global-static-functions.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-425">[Debugging Global Static Functions](debugging-global-static-functions.md)</span></span>\
 <span data-ttu-id="af84b-426">[Énumérations de débogage](debugging-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-426">[Debugging Enumerations](debugging-enumerations.md)</span></span>\
 <span data-ttu-id="af84b-427">[Structures de débogage](debugging-structures.md)</span><span class="sxs-lookup"><span data-stu-id="af84b-427">[Debugging Structures](debugging-structures.md)</span></span>\
