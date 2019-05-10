---
title: Compilation d'applications avec .NET Native
ms.date: 03/30/2017
helpviewer_keywords:
- native compilation
- .NET and native code
- compilation with .NET Native
- .NET Native
- C# and native compilation
ms.assetid: 47cd5648-9469-4b1d-804c-43cc04384045
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3c845cefad451c608f5c095e4941c3368dc9975
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650549"
---
# <a name="compiling-apps-with-net-native"></a>Compilation d'applications avec .NET Native
[!INCLUDE[net_native](../../../includes/net-native-md.md)] est une technologie de précompilation pour générer et déployer des applications Windows qui est incluse avec Visual Studio 2015 et versions ultérieures. Elle compile automatiquement la version commerciale des applications écrites en code managé (C# ou Visual Basic) et qui ciblent .NET Framework et Windows 10 en code natif.  
  
 En règle générale, les applications qui ciblent .NET Framework sont compilées en langage intermédiaire (IL). Au moment de l'exécution, le compilateur juste-à-temps (JIT) traduit le langage intermédiaire en code natif. En revanche, [!INCLUDE[net_native](../../../includes/net-native-md.md)] compile les applications Windows directement en code natif. Pour les développeurs, cela signifie les points suivants :  
  
- Les performances du code natif de fonctionnalités de vos applications. En règle générale, les performances seront supérieures au code qui est tout d’abord compilée en langage intermédiaire et ensuite compilé en code natif par le compilateur JIT. 
  
- Vous pouvez continuer à programmer en C# ou Visual Basic.  
  
- Vous pouvez continuer à exploiter les ressources fournies par .NET Framework, y compris sa bibliothèque de classes, la gestion automatique de la mémoire, le garbage collection et la gestion des exceptions.  
  
 Pour les utilisateurs de vos applications, [!INCLUDE[net_native](../../../includes/net-native-md.md)] présente les avantages suivants :  
  
- Durées d’exécution pour la majorité des applications et de scénarios.
  
- Démarrage plus rapide pour la majorité des applications et de scénarios. 
  
- Faibles coûts de déploiement et de mise à jour.  
  
- Utilisation de mémoire d’application optimisée.  

> [!IMPORTANT]
> Pour la grande majorité des applications et des scénarios, .NET Native offre des temps de démarrage sensiblement plus rapides et des performances supérieures par rapport à une application compilée en langage intermédiaire ou à une image NGEN. Toutefois, les résultats peuvent varier. Pour vous assurer que votre application a tiré parti de l’amélioration des performances de .NET Native, vous devez comparer ses performances avec celle de la version non - .NET Native de votre application. Pour plus d’informations, consultez [vue d’ensemble de la Session de Performance](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).
 
Toutefois, [!INCLUDE[net_native](../../../includes/net-native-md.md)] va au-delà d'une simple compilation en code natif. Il transforme la façon dont les applications .NET Framework sont intégrées et exécutées. En particulier :  
  
- Pendant la précompilation, les parties nécessaires de .NET Framework sont liées statiquement dans votre application. Cela permet à l'application de s'exécuter avec les bibliothèques app-local de .NET Framework et au compilateur d'effectuer une analyse globale pour procurer des gains de performance. Ainsi, les applications se lancent systématiquement plus rapidement même après une mise à jour de .NET Framework.  
  
- Le [!INCLUDE[net_native](../../../includes/net-native-md.md)] runtime est optimisé pour la précompilation statique et offre de meilleures performances dans la grande majorité des cas. Dans le même temps, il conserve les fonctionnalités de réflexion principales, si productives au regard des développeurs.  
  
- [!INCLUDE[net_native](../../../includes/net-native-md.md)] utilise le même système principal que le compilateur C++, qui est optimisé pour les scénarios de précompilation statique.  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] peut procurer aux développeurs de code managé les performances de C++, car il s'appuie pratiquement sur les mêmes outils que C++, comme indiqué dans le tableau ci-après.  
  
||[!INCLUDE[net_native](../../../includes/net-native-md.md)]|C++|  
|-|----------------------------------------------------------------|-----------|  
|Bibliothèques|.NET Framework + Windows Runtime|Win32 + Windows Runtime|  
|Compilateur|Compilateur d'optimisation UTC|Compilateur d'optimisation UTC|  
|Déployé|Fichiers binaires prêts à être exécutés|Fichiers binaires prêts à être exécutés (ASM)|  
|Runtime|MRT.dll (Runtime CLR minimal)|CRT.dll (Runtime C)|  
  
 Pour les applications Windows pour Windows 10, vous devez charger les binaires de compilation de code .NET Native contenus dans les packages d’application (fichiers .aspx) vers le Windows Store.  
  
## <a name="in-this-section"></a>Dans cette section  
 Pour plus d'informations sur le développement d'applications avec la compilation de code .NET Native, consultez les rubriques suivantes :  
  
- [Mise en route avec la Compilation de Code natif .NET : La procédure détaillée pour développeurs](../../../docs/framework/net-native/getting-started-with-net-native.md)  
  
- [.NET native et Compilation :](../../../docs/framework/net-native/net-native-and-compilation.md) Comment .NET Native compile votre projet en code natif.  
  
- [Réflexion et .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)  
  
    - [API qui s’appuient sur la réflexion](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
    - [Informations de référence sur les API de réflexion](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
    - [Guide de référence du fichier de configuration des directives runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
- [Sérialisation et métadonnées](../../../docs/framework/net-native/serialization-and-metadata.md)  
  
- [Migration de votre application du Windows Store vers .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)  
  
- [Résolution des problèmes généraux liés à .NET Native](../../../docs/framework/net-native/net-native-general-troubleshooting.md)
