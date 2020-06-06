---
title: Réflexion et .NET Native
ms.date: 03/30/2017
ms.assetid: 91c9eae4-c641-476c-a06e-d7ce39709763
ms.openlocfilehash: 65921377be9b8bf1c2d147b384c85cbd037d15f2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128184"
---
# <a name="reflection-and-net-native"></a>Réflexion et .NET Native
Dans le .NET Framework, le développement managé prend en charge la métaprogrammation par le biais de l'API de réflexion. La réflexion vous permet d'inspecter les objets dans une application, d'appeler des méthodes sur les objets découverts au cours de l'inspection et de générer de nouveaux types au moment de l'exécution. Elle prend également en charge de nombreux autres scénarios de code dynamique, comme la sérialisation et la désérialisation, qui permettent de rendre persistantes les valeurs de champ d’un objet et de les restaurer ultérieurement. Ces scénarios nécessitent tous le compilateur juste-à-temps (JIT) du .NET Framework pour générer du code natif basé sur les métadonnées disponibles.  
  
 Le Runtime .NET Native n’inclut pas de compilateur JIT. Tout le code natif nécessaire doit donc être généré à l'avance. Un ensemble d'heuristiques permet de déterminer le code à générer, mais ces heuristiques ne peuvent pas couvrir tous les scénarios de métaprogrammation possibles.  Vous devez donc fournir des indications pour ces scénarios de métaprogrammation à l’aide de [directives runtime](runtime-directives-rd-xml-configuration-file-reference.md). Si les métadonnées ou le code d’implémentation nécessaires ne sont pas disponibles lors de l’exécution, votre application lève une exception [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) ou [MissingInteropDataException](missinginteropdataexception-class-net-native.md). Deux utilitaires de résolution des problèmes sont disponibles, qui vont génèrer l'entrée appropriée pour votre fichier de directives de runtime qui élimine l'exception :  
  
- l’ [utilitaire de résolution des problèmes MissingMetadataException](https://dotnet.github.io/native/troubleshooter/type.html) pour les types ;  
  
- l’ [utilitaire de résolution des problèmes MissingMetadataException](https://dotnet.github.io/native/troubleshooter/method.html) pour les méthodes.  
  
> [!NOTE]
> Pour une vue d'ensemble du processus de compilation .NET Native apportant des informations générales sur la nécessité d'un fichier de directives de runtime, voir [.NET Native et compilation](net-native-and-compilation.md).  
  
 En outre, .NET Native ne vous permet pas de réfléchir à des membres privés de la bibliothèque de classes .NET Framework. Par exemple, un appel de la propriété <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=nameWithType> pour récupérer les champs d'un type de bibliothèque de classes du .NET Framework retourne uniquement des champs publics ou protégés.  
  
 Les rubriques suivantes fournissent la documentation conceptuelle et de référence qui vous permet de prendre en charge la réflexion et la sérialisation dans vos applications :  
  
- [API qui s'appuient sur la réflexion](apis-that-rely-on-reflection.md)  
  
- [Informations de référence sur les API de réflexion](net-native-reflection-api-reference.md)  
  
- [Guide de référence du fichier de configuration des directives runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)  
  
## <a name="see-also"></a>Voir aussi

- [Compilation d'applications avec .NET Native](index.md)
- [Compilation et .NET natif](net-native-and-compilation.md)
