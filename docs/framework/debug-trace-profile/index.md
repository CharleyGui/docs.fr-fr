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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 43927be83b8b2a9163656f8d6d54c2cf83a23e28
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052653"
---
# <a name="debugging-tracing-and-profiling"></a>Débogage, traçage et profilage
Pour déboguer une application .NET Framework, le compilateur et l'environnement d'exécution doivent être configurés pour permettre l'attachement d'un débogueur à l'application et la génération de cartes à la fois de symboles et de lignes, si possible, pour l'application et son langage MSIL (Microsoft Intermediate Language) correspondant. Une fois déboguée, une application managée peut être profilée en vue d'améliorer ses performances. Le profilage évalue et décrit les lignes de code source qui génèrent le code le plus fréquemment exécuté, et le temps que demande leur exécution.  
  
 Les applications .NET Framework sont facilement déboguées à l'aide de Visual Studio, qui gère de nombreux détails de la configuration. Si Visual Studio n'est pas installé, vous pouvez analyser et améliorer les performances des applications .NET Framework à l'aide des classes de débogage de l'espace de noms <xref:System.Diagnostics> du .NET Framework. Cet espace de noms comprend les classes <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug> et <xref:System.Diagnostics.TraceSource> pour tracer le flux d'exécution, ainsi que les classes <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog> et <xref:System.Diagnostics.PerformanceCounter> pour profiler le code.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Activation du débogage juste-à-temps](enabling-jit-attach-debugging.md)  
 Montre comment configurer le Registre de manière à attacher via le JIT un moteur de débogage à une application .NET Framework.  
  
 [Simplification du débogage d’une image](making-an-image-easier-to-debug.md)  
 Montre comment activer le suivi JIT et désactiver l'optimisation pour faciliter le débogage d'un assembly.  
  
 [Suivi et instrumentation d’applications](tracing-and-instrumenting-applications.md)  
 Explique comment surveiller l'exécution de votre application et comment l'instrumenter pour afficher la progression ou au contraire les problèmes survenus.  
  
 [Diagnostic d’erreurs avec les Assistants Débogage managé](diagnosing-errors-with-managed-debugging-assistants.md)  
 Décrit les Assistants Débogage managé (MDA), des outils de débogage qui fonctionnent conjointement au common language runtime (CLR) pour fournir des informations sur l'état d'exécution.  
  
 [Amélioration du débogage avec les attributs d’affichage de débogueur](enhancing-debugging-with-the-debugger-display-attributes.md)  
 Explique comment le développeur d'un type peut contrôler la façon dont ce type s'affiche dans un débogueur.  
  
 [Compteurs de performance](performance-counters.md)  
 Décrit les compteurs que vous pouvez utiliser pour suivre les performances d'une application.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Déboguer des applications ASP.NET ou ASP.NET Core dans Visual Studio](/visualstudio/debugger/debugging-aspnet-and-ajax-applications)  
 Indique la configuration requise et fournit des instructions pour déboguer une application ASP.NET pendant le développement ou après le déploiement.  
  
 [Guide de développement](../development-guide.md)  
 Fournit un guide sur tous les domaines technologiques clés et les tâches relatives au développement d’applications, notamment la création, la configuration, le débogage, la sécurisation et le déploiement de votre application, ainsi que des informations sur la programmation dynamique, l’interopérabilité, l’extensibilité, la gestion de mémoire et les threads.
