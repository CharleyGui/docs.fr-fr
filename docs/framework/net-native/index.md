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
ms.openlocfilehash: 1f176e81905fe68c6d740a13240fe814659a7a59
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128373"
---
# <a name="compiling-apps-with-net-native"></a>Compilation d'applications avec .NET Native

.NET Native est une technologie de précompilation pour la création et le déploiement d’applications Windows incluses avec Visual Studio 2015 et versions ultérieures. Elle compile automatiquement la version commerciale des applications écrites en code managé (C# ou Visual Basic) et qui ciblent .NET Framework et Windows 10 en code natif.

En règle générale, les applications qui ciblent .NET Framework sont compilées en langage intermédiaire (IL). Au moment de l'exécution, le compilateur juste-à-temps (JIT) traduit le langage intermédiaire en code natif. En revanche, .NET Native compile les applications Windows directement en code natif. Pour les développeurs, cela signifie les points suivants :

- Vos applications disposent des performances du code natif. En règle générale, les performances seront supérieures au code qui est d’abord compilé en IL, puis compilé en code natif par le compilateur JIT.

- Vous pouvez continuer à programmer en C# ou Visual Basic.

- Vous pouvez continuer à exploiter les ressources fournies par .NET Framework, y compris sa bibliothèque de classes, la gestion automatique de la mémoire, le garbage collection et la gestion des exceptions.

Pour les utilisateurs de vos applications, .NET Native offre les avantages suivants :

- Durée d’exécution plus rapide pour la majorité des applications et des scénarios.

- Des temps de démarrage plus rapides pour la majorité des applications et des scénarios.

- Faibles coûts de déploiement et de mise à jour.

- Utilisation optimisée de la mémoire de l’application.

> [!IMPORTANT]
> Pour la grande majorité des applications et des scénarios, .NET Native offre des temps de démarrage nettement plus rapides et des performances supérieures par rapport à une application compilée en IL ou à une image NGEN. Toutefois, vos résultats peuvent varier. Pour vous assurer que votre application a bénéficié des améliorations des performances de .NET Native, vous devez comparer ses performances à celles de la version native non-.NET de votre application. Pour plus d’informations, consultez [vue d’ensemble des sessions de performance](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).

Mais .NET Native implique plus qu’une compilation en code natif. Il transforme la façon dont les applications .NET Framework sont intégrées et exécutées. En particulier :

- Pendant la précompilation, les parties nécessaires de .NET Framework sont liées statiquement dans votre application. Cela permet à l'application de s'exécuter avec les bibliothèques app-local de .NET Framework et au compilateur d'effectuer une analyse globale pour procurer des gains de performance. Ainsi, les applications se lancent systématiquement plus rapidement même après une mise à jour de .NET Framework.

- Le .NET Native Runtime est optimisé pour la précompilation statique et, dans la plupart des cas, offre des performances supérieures. Dans le même temps, il conserve les fonctionnalités de réflexion principales, si productives au regard des développeurs.

- .NET Native utilise le même back end que le compilateur C++, qui est optimisé pour les scénarios de précompilation statique.

.NET Native est en mesure d’apporter les avantages en termes de performances de C++ aux développeurs de code managé, car il utilise les mêmes outils ou des outils similaires que C++, comme indiqué dans ce tableau.

||.NET Native|C++|
|-|----------------------------------------------------------------|-----------|
|Bibliothèques|.NET Framework + Windows Runtime|Win32 + Windows Runtime|
|Compilateur|Compilateur d'optimisation UTC|Compilateur d'optimisation UTC|
|Déployé|Fichiers binaires prêts à être exécutés|Fichiers binaires prêts à être exécutés (ASM)|
|Runtime|MRT.dll (Runtime CLR minimal)|CRT.dll (Runtime C)|

Pour les applications Windows pour Windows 10, vous devez charger les binaires de compilation de code .NET Native contenus dans les packages d’application (fichiers .aspx) vers le Windows Store.

## <a name="in-this-section"></a>Dans cette section

Pour plus d'informations sur le développement d'applications avec la compilation de code .NET Native, consultez les rubriques suivantes :

- [Prise en main de la compilation de code .NET Native : procédure détaillée pour les développeurs](getting-started-with-net-native.md)

- [.NET Native et compilation :](net-native-and-compilation.md) Comment .NET Native compile votre projet en code natif.

- [Réflexion et .NET Native](reflection-and-net-native.md)

  - [API qui s'appuient sur la réflexion](apis-that-rely-on-reflection.md)

  - [Informations de référence sur les API de réflexion](net-native-reflection-api-reference.md)

  - [Guide de référence du fichier de configuration des directives runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)

- [Sérialisation et métadonnées](serialization-and-metadata.md)

- [Migration de votre application du Windows Store vers .NET Native](migrating-your-windows-store-app-to-net-native.md)

- [Résolution des problèmes généraux liés à .NET Native](net-native-general-troubleshooting.md)
