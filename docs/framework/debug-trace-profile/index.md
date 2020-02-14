---
title: Débogage, traçage et profilage
ms.date: 03/30/2017
helpviewer_keywords:
- debugging [.NET Framework]
- .NET Framework application configuration, debugging
- debugging [.NET Framework], .NET Framework application debugging
- troubleshooting applications [.NET Framework], profiling
- application development [.NET Framework], debugging
- .NET Framework application configuration, profiling
- profiling applications
- troubleshooting applications [.NET Framework], debugging
- troubleshooting applications [.NET Framework]
- application development [.NET Framework], profiling
ms.assetid: 4a04863e-2475-46f4-bc3f-3c11510c2a4b
ms.openlocfilehash: 1a43c7fbcb810b22ff9bc409c233d2b1da67370e
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217407"
---
# <a name="debugging-tracing-and-profiling"></a><span data-ttu-id="28f75-102">Débogage, traçage et profilage</span><span class="sxs-lookup"><span data-stu-id="28f75-102">Debugging, Tracing, and Profiling</span></span>
<span data-ttu-id="28f75-103">Pour déboguer une application .NET Framework, le compilateur et l'environnement d'exécution doivent être configurés pour permettre l'attachement d'un débogueur à l'application et la génération de cartes à la fois de symboles et de lignes, si possible, pour l'application et son langage MSIL (Microsoft Intermediate Language) correspondant.</span><span class="sxs-lookup"><span data-stu-id="28f75-103">To debug a .NET Framework application, the compiler and runtime environment must be configured to enable a debugger to attach to the application and to produce both symbols and line maps, if possible, for the application and its corresponding Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="28f75-104">Une fois déboguée, une application managée peut être profilée en vue d'améliorer ses performances.</span><span class="sxs-lookup"><span data-stu-id="28f75-104">After a managed application has been debugged, it can be profiled to boost performance.</span></span> <span data-ttu-id="28f75-105">Le profilage évalue et décrit les lignes de code source qui génèrent le code le plus fréquemment exécuté, et le temps que demande leur exécution.</span><span class="sxs-lookup"><span data-stu-id="28f75-105">Profiling evaluates and describes the lines of source code that generate the most frequently executed code, and how much time it takes to execute them.</span></span>  
  
 <span data-ttu-id="28f75-106">Les applications .NET Framework sont facilement déboguées à l'aide de Visual Studio, qui gère de nombreux détails de la configuration.</span><span class="sxs-lookup"><span data-stu-id="28f75-106">.NET Framework applications are easily debugged by using Visual Studio, which handles many of the configuration details.</span></span> <span data-ttu-id="28f75-107">Si Visual Studio n'est pas installé, vous pouvez analyser et améliorer les performances des applications .NET Framework à l'aide des classes de débogage de l'espace de noms <xref:System.Diagnostics> du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="28f75-107">If Visual Studio is not installed, you can examine and improve the performance of .NET Framework applications by using the debugging classes in the .NET Framework <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="28f75-108">Cet espace de noms comprend les classes <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug> et <xref:System.Diagnostics.TraceSource> pour tracer le flux d'exécution, ainsi que les classes <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog> et <xref:System.Diagnostics.PerformanceCounter> pour profiler le code.</span><span class="sxs-lookup"><span data-stu-id="28f75-108">This namespace includes the <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, and <xref:System.Diagnostics.TraceSource> classes for tracing execution flow, and the <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, and <xref:System.Diagnostics.PerformanceCounter> classes for profiling code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="28f75-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="28f75-109">In This Section</span></span>  
 [<span data-ttu-id="28f75-110">Activation du débogage juste-à-temps</span><span class="sxs-lookup"><span data-stu-id="28f75-110">Enabling JIT-Attach Debugging</span></span>](enabling-jit-attach-debugging.md)  
 <span data-ttu-id="28f75-111">Montre comment configurer le Registre de manière à attacher via le JIT un moteur de débogage à une application .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="28f75-111">Shows how to configure the registry to JIT-attach a debug engine to a .NET Framework application.</span></span>  
  
 [<span data-ttu-id="28f75-112">Simplification du débogage d’une image</span><span class="sxs-lookup"><span data-stu-id="28f75-112">Making an Image Easier to Debug</span></span>](making-an-image-easier-to-debug.md)  
 <span data-ttu-id="28f75-113">Montre comment activer le suivi JIT et désactiver l'optimisation pour faciliter le débogage d'un assembly.</span><span class="sxs-lookup"><span data-stu-id="28f75-113">Shows how to turn JIT tracking on and optimization off to make an assembly easier to debug.</span></span>  
  
 [<span data-ttu-id="28f75-114">Suivi et instrumentation d’applications</span><span class="sxs-lookup"><span data-stu-id="28f75-114">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)  
 <span data-ttu-id="28f75-115">Explique comment surveiller l'exécution de votre application et comment l'instrumenter pour afficher la progression ou au contraire les problèmes survenus.</span><span class="sxs-lookup"><span data-stu-id="28f75-115">Describes how to monitor the execution of your application while it is running, and how to instrument it to display how well it is performing or whether something has gone wrong.</span></span>  
  
 [<span data-ttu-id="28f75-116">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="28f75-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)  
 <span data-ttu-id="28f75-117">Décrit les Assistants Débogage managé (MDA), des outils de débogage qui fonctionnent conjointement au common language runtime (CLR) pour fournir des informations sur l'état d'exécution.</span><span class="sxs-lookup"><span data-stu-id="28f75-117">Describes managed debugging assistants (MDAs), which are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span>  
  
 [<span data-ttu-id="28f75-118">Amélioration du débogage avec les attributs d’affichage de débogueur</span><span class="sxs-lookup"><span data-stu-id="28f75-118">Enhancing Debugging with the Debugger Display Attributes</span></span>](enhancing-debugging-with-the-debugger-display-attributes.md)  
 <span data-ttu-id="28f75-119">Explique comment le développeur d'un type peut contrôler la façon dont ce type s'affiche dans un débogueur.</span><span class="sxs-lookup"><span data-stu-id="28f75-119">Describes how the developer of a type can specify what that type will look like when it is displayed in a debugger.</span></span>  
  
 [<span data-ttu-id="28f75-120">Compteurs de performance</span><span class="sxs-lookup"><span data-stu-id="28f75-120">Performance Counters</span></span>](performance-counters.md)  
 <span data-ttu-id="28f75-121">Décrit les compteurs que vous pouvez utiliser pour suivre les performances d'une application.</span><span class="sxs-lookup"><span data-stu-id="28f75-121">Describes the counters that you can use to track the performance of an application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="28f75-122">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="28f75-122">Related Sections</span></span>  
 [<span data-ttu-id="28f75-123">Déboguer des applications ASP.NET ou ASP.NET Core dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="28f75-123">Debug ASP.NET or ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications)  
 <span data-ttu-id="28f75-124">Indique la configuration requise et fournit des instructions pour déboguer une application ASP.NET pendant le développement ou après le déploiement.</span><span class="sxs-lookup"><span data-stu-id="28f75-124">Provides prerequisites and instructions for how to debug an ASP.NET application during development or after deployment.</span></span>  
  
 [<span data-ttu-id="28f75-125">Guide de développement</span><span class="sxs-lookup"><span data-stu-id="28f75-125">Development Guide</span></span>](../development-guide.md)  
 <span data-ttu-id="28f75-126">Fournit un guide sur tous les domaines technologiques clés et les tâches relatives au développement d’applications, notamment la création, la configuration, le débogage, la sécurisation et le déploiement de votre application, ainsi que des informations sur la programmation dynamique, l’interopérabilité, l’extensibilité, la gestion de mémoire et les threads.</span><span class="sxs-lookup"><span data-stu-id="28f75-126">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
