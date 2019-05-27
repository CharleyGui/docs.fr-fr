---
title: Guide de référence de l'API de réflexion .NET Native
ms.date: 03/30/2017
ms.assetid: 0429c049-22a3-4ba1-9cc8-f6ee91e31d9c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 833d31c48220e2d2b5d07ee482325df090714329
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052423"
---
# <a name="net-native-reflection-api-reference"></a>Guide de référence de l'API de réflexion .NET Native
.NET native inclut trois nouveaux types d’exception : [System.Runtime.CompilerServices.MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), [System.Reflection.MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), et [System.Reflection.MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) . Notez les éléments suivants concernant ces trois types d'exception :  
  
 Ces types sont destinés à une utilisation interne uniquement.  
 Ces trois types d’exception sont pour l’utilisation de la chaîne d’outils .NET Native uniquement. Les exceptions sont levées lorsque la chaîne d’outils .NET Native détecte des données manquantes qui n’autorise pas l’exécution du programme continuer.  
  
 Ne gérez pas ces exceptions dans votre code.  
 Ces exceptions indiquent que des métadonnées requises par votre application sont absentes (exceptions [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) et [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) ) ou que le code d'implémentation requis par votre application est manquant (exception [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) ). Vous pouvez corriger ces conditions d'exception en modifiant un fichier de directives runtime (.rd.xml) pour rendre disponibles les métadonnées ou le code d'implémentation nécessaires au moment de l'exécution. Pour plus d'informations, consultez [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Deux utilitaires de résolution des problèmes sont disponibles. Ils fournissent les entrées appropriées pour votre fichier de directives runtime qui vont éliminer les exceptions [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) et [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) :  
  
- l’ [utilitaire de résolution des problèmes MissingMetadataException](https://dotnet.github.io/native/troubleshooter/type.html) pour les types ;  
  
- l’ [utilitaire de résolution des problèmes MissingMetadataException](https://dotnet.github.io/native/troubleshooter/method.html) pour les méthodes.  
  
> [!NOTE]
>  Cette référence décrit trois types d’exceptions qui sont propres à .NET Native. Pour la documentation de référence pour l’API de réflexion .NET Framework core, consultez le <xref:System.Reflection>, <xref:System.Reflection.Context> et <xref:System.Reflection.Emit> espaces de noms. Pour la documentation de référence sur l'API d'interopérabilité principale du .NET Framework, consultez <xref:System.Runtime.InteropServices>.  
  
## <a name="systemreflection-namespace"></a>Espace de noms System.Reflection  
 L'espace de noms <xref:System.Reflection> contient les types principaux utilisés pour la réflexion dans le .NET Framework. Pour .NET Native, il inclut également deux nouveaux types d’exception :  
  
|Classe|Description|  
|-----------|-----------------|  
|[MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)|Exception levée quand la réflexion est utilisée pour récupérer des métadonnées qui ne sont pas présentes.|  
|[MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)|Exception levée quand les métadonnées d'un type ou d'un membre de type sont disponibles, mais que leur implémentation a été supprimée.|  
  
 Pour plus d'informations sur les autres types de cet espace de noms, consultez les pages de référence de <xref:System.Reflection> dans l'ensemble de la documentation du .NET Framework.  
  
## <a name="systemruntimecompilerservices-namespace"></a>Espace de noms System.Runtime.CompilerServices  
 L'espace de noms <xref:System.Runtime.CompilerServices> comprend des types qui ont été conçus pour être utilisés par des compilateurs de langage. Pour .NET Native, il inclut également un nouveau type d’exception :  
  
|Classe|Description|  
|-----------|-----------------|  
|[MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)|Exception levée quand une méthode de marshaling manuel est appelée, mais que les métadonnées d'un type sont introuvables par analyse statique ou dans un fichier de directives runtime.|  
  
 Pour plus d'informations sur les autres types de cet espace de noms, consultez les pages de référence de <xref:System.Runtime.CompilerServices> dans l'ensemble de la documentation du .NET Framework.  
  
## <a name="see-also"></a>Voir aussi

- [MissingInteropDataException, classe](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)
- [MissingMetadataException, classe](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)
- [MissingRuntimeArtifactException, classe](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)
- [Prise en main](../../../docs/framework/net-native/getting-started-with-net-native.md)
