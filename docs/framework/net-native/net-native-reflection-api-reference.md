---
title: Guide de référence de l'API de réflexion .NET Native
ms.date: 03/30/2017
ms.assetid: 0429c049-22a3-4ba1-9cc8-f6ee91e31d9c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69a4addbd00c119af4336faae2cd0f8fc31f8852
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941618"
---
# <a name="net-native-reflection-api-reference"></a>Guide de référence de l'API de réflexion .NET Native
.NET Native comprend trois nouveaux types d’exception: [System. Runtime. CompilerServices. MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), [System. Reflection. MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)et [System. Reflection. MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md). Notez les éléments suivants concernant ces trois types d'exception :  
  
 Ces types sont destinés à une utilisation interne uniquement.  
 Ces trois types d’exception sont destinés à l’utilisation de la chaîne d’outils .NET Native uniquement. Les exceptions sont levées lorsque la chaîne d’outils .NET Native détecte des données manquantes qui n’autorisent pas l’exécution du programme à continuer.  
  
 Ne gérez pas ces exceptions dans votre code.  
 Ces exceptions indiquent que des métadonnées requises par votre application sont absentes (exceptions [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) et [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) ) ou que le code d'implémentation requis par votre application est manquant (exception [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) ). Vous pouvez corriger ces conditions d'exception en modifiant un fichier de directives runtime (.rd.xml) pour rendre disponibles les métadonnées ou le code d'implémentation nécessaires au moment de l'exécution. Pour plus d'informations, consultez [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Deux utilitaires de résolution des problèmes sont disponibles. Ils fournissent les entrées appropriées pour votre fichier de directives runtime qui vont éliminer les exceptions [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) et [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) :  
  
- l’ [utilitaire de résolution des problèmes MissingMetadataException](https://dotnet.github.io/native/troubleshooter/type.html) pour les types ;  
  
- l’ [utilitaire de résolution des problèmes MissingMetadataException](https://dotnet.github.io/native/troubleshooter/method.html) pour les méthodes.  
  
> [!NOTE]
> Cette référence décrit trois types d’exception propres à .NET Native. Pour obtenir une documentation de référence sur l’API de réflexion .NET Framework <xref:System.Reflection>Core <xref:System.Reflection.Context> , <xref:System.Reflection.Emit> consultez les espaces de noms et. Pour la documentation de référence sur l'API d'interopérabilité principale du .NET Framework, consultez <xref:System.Runtime.InteropServices>.  
  
## <a name="systemreflection-namespace"></a>Espace de noms System.Reflection  
 L'espace de noms <xref:System.Reflection> contient les types principaux utilisés pour la réflexion dans le .NET Framework. Par .NET Native, il comprend également deux nouveaux types d’exception:  
  
|Classe|Description|  
|-----------|-----------------|  
|[MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)|Exception levée quand la réflexion est utilisée pour récupérer des métadonnées qui ne sont pas présentes.|  
|[MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)|Exception levée quand les métadonnées d'un type ou d'un membre de type sont disponibles, mais que leur implémentation a été supprimée.|  
  
 Pour plus d'informations sur les autres types de cet espace de noms, consultez les pages de référence de <xref:System.Reflection> dans l'ensemble de la documentation du .NET Framework.  
  
## <a name="systemruntimecompilerservices-namespace"></a>Espace de noms System.Runtime.CompilerServices  
 L'espace de noms <xref:System.Runtime.CompilerServices> comprend des types qui ont été conçus pour être utilisés par des compilateurs de langage. Par .NET Native, il comprend également un nouveau type d’exception:  
  
|Classe|Description|  
|-----------|-----------------|  
|[MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)|Exception levée quand une méthode de marshaling manuel est appelée, mais que les métadonnées d'un type sont introuvables par analyse statique ou dans un fichier de directives runtime.|  
  
 Pour plus d'informations sur les autres types de cet espace de noms, consultez les pages de référence de <xref:System.Runtime.CompilerServices> dans l'ensemble de la documentation du .NET Framework.  
  
## <a name="see-also"></a>Voir aussi

- [MissingInteropDataException, classe](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)
- [MissingMetadataException, classe](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)
- [MissingRuntimeArtifactException, classe](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)
- [Prise en main](../../../docs/framework/net-native/getting-started-with-net-native.md)
