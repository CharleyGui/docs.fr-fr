---
title: MissingInteropDataException, classe (.NET Native)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eab4bcf8-9f5f-4731-87d8-842748a6062a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 803709c97309f9766b6a441f5521cdcd7504862f
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052501"
---
# <a name="missinginteropdataexception-class-net-native"></a>MissingInteropDataException, classe (.NET Native)
**.NET pour les applications Windows pour Windows 10, .NET natif uniquement**  
  
 Exception levée quand une méthode de marshaling manuel est appelée, mais que les métadonnées d'un type sont introuvables par analyse statique ou dans un fichier de directives runtime.  
  
 **Espace de noms :** System.Runtime.CompilerServices  
  
> [!IMPORTANT]
>  Le `MissingInteropDataException` classe est destinée exclusivement à un usage interne par la chaîne d’outils .NET Native. Elle n'est pas destinée à être utilisée dans du code tiers ni à traiter l'exception dans le code de votre application. Au lieu de cela, éliminez l’exception en ajoutant des entrées à votre [fichier de directives runtime](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Pour plus d'informations, consultez la section Remarques.  
  
## <a name="syntax"></a>Syntaxe  
 [!code-csharp[ProjectN#21](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missinginteropdataexception_syntax1.cs#21)]
 [!code-vb[ProjectN#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/projectn/vb/missinginteropdataexception_syntax1.vb#21)]  
  
 La classe `MissingInteropDataException` possède les membres suivants :  
  
## <a name="constructors"></a>Constructeurs  
  
|Constructeur|Description|  
|-----------------|-----------------|  
|`public MissingInteropDataException(String resourceId, Type pertinentType)`|Initialise une nouvelle instance de la classe `MissingInteropDataException` en utilisant l'ID d'un message système qui décrit l'erreur et le type dont les données sont manquantes. Ce constructeur est pour une utilisation interne par la chaîne d’outils .NET Native uniquement.|  
  
## <a name="properties"></a>Properties  
  
|Propriété|Description|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Obtient une collection de paires clé/valeur qui fournissent des informations supplémentaires définies par l’utilisateur sur l’exception. (Hérité de <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string HelpLink { get; set; }`|Obtient ou définit un lien vers le fichier d'aide associé à cette exception. (Hérité de <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int HResult { get; protected set; }`|Obtient ou définit la valeur `HRESULT`, valeur numérique codée qui est assignée à une exception spécifique. (Hérité de <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Exception InnerException { get; }`|Obtient l'exception à l'origine de l'exception actuelle. (Hérité de <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Message { get; }`|Obtient un message qui décrit l'exception actuelle. (Hérité de <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Type MissingType { get; private set; }`|Obtient ou définit le type dont les données sont manquantes.|  
|`public string Source { get; set; }`|Obtient ou définit le nom de l'application ou de l'objet à l'origine de l'erreur. (Hérité de <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string StackTrace { get; }`|Obtient une représentation sous forme de chaîne des frames immédiats sur la pile des appels. (Hérité de <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public MethodBase TargetSite { get; }`|Obtient la méthode qui a levé l'exception actuelle. (Hérité de <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Détermine si l'objet spécifié est identique à l'objet actuel.  (Hérité de <xref:System.Object>.)|  
|`protected void Finalize()`|Autorise un objet à tenter de libérer des ressources et à exécuter d'autres opérations de nettoyage avant qu'il ne soit récupéré par une opération garbage collection. (Hérité de <xref:System.Object>.)|  
|`public Exception GetBaseException()`|Retourne l’exception qui est la cause racine d’une ou plusieurs exceptions ultérieures. (Hérité de <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int GetHashCode()`|Retourne un code de hachage pour une instance `MissingInteropDataException`.   (Hérité de <xref:System.Object>.)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Définit un objet <xref:System.Runtime.Serialization.SerializationInfo> avec des informations relatives à l'exception.  (Hérité de <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Type GetType()`|Obtient le type au moment de l'exécution de l'instance actuelle. (Hérité de <xref:System.Exception?displayProperty=nameWithType>.)|  
|`protected Object MemberwiseClone()`|Crée une copie superficielle de l'objet actuel. (Hérité de <xref:System.Object>.)|  
|`public string ToString()`|Retourne la représentation sous forme de chaîne de l'exception actuelle. (Hérité de <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="events"></a>Événements  
  
|Événement|Description|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Se produit quand une exception est sérialisée pour créer un objet d'état d'exception qui contient des données sérialisées concernant l'exception. (Hérité de <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="usage-details"></a>Détails de l'utilisation  
 L'exception `MissingInteropDataException` est levée quand un appel de méthode à destination d'un composant COM ou Windows Runtime ne peut pas aboutir car les informations de type ne sont pas disponibles.  
  
 Les métadonnées qui sont disponibles pour une application au moment de l'exécution sont définies par le fichier (configuration XML) de directives runtime, *.rd.xml. Pour empêcher votre application de lever cette exception, vous devez modifier ce fichier de manière à définir les métadonnées qui doivent être présentes au moment de l'exécution. Le plus souvent, vous corrigez cette erreur en ajoutant un attribut `MarshalObject`, `MarshalDelegate` ou `MarshalStructure` à un élément de programme approprié dans le fichier de directives runtime. Pour plus d’informations sur le format de ce fichier, consultez [Guide de référence du fichier de configuration des directives runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
>  Comme cette exception indique que les métadonnées nécessaires à votre application ne sont pas disponibles au moment de l’exécution, vous ne devez pas gérer cette exception dans un bloc `try`/`catch`. Au lieu de cela, vous devez diagnostiquer la cause de l'exception et l'éliminer en ajoutant l'entrée appropriée à un fichier de directives runtime.  
  
 La classe `MissingInteropDataException` contient un seul membre, la propriété `MissingType`, qui indique le type dont les métadonnées sont nécessaires à un appel de méthode. Tous les autres membres sont hérités de la classe de base, <xref:System.Exception?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Exception?displayProperty=nameWithType>
- [MissingMetadataException, classe](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)
- [Guide de référence du fichier de configuration des directives runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
