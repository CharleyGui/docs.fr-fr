---
title: MissingMetadataException, classe (.NET Native)
ms.date: 03/30/2017
ms.assetid: 408f25c4-6d60-475c-92b1-7b52b777c6db
ms.openlocfilehash: d73d66529bc30358c946eb0a7072f0cb8910b19a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128286"
---
# <a name="missingmetadataexception-class-net-native"></a>MissingMetadataException, classe (.NET Native)

**.NET pour les applications Windows pour Windows 10, .NET Native uniquement**

Exception levée quand la réflexion est utilisée pour récupérer des métadonnées qui ne sont pas présentes.

**Espace de noms :** System.Reflection

> [!IMPORTANT]
> La `MissingMetadataException` classe est destinée exclusivement à un usage interne par la chaîne d’outils .net native. Elle n'est pas destinée à être utilisée dans du code tiers ni à traiter l'exception dans le code de votre application. Au lieu de cela, éliminez l’exception en ajoutant des entrées à votre [fichier de directives runtime](runtime-directives-rd-xml-configuration-file-reference.md). Pour plus d'informations, consultez la section Notes.

## <a name="syntax"></a>Syntaxe

[!code-csharp[ProjectN#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingmetadataexception_syntax1.cs#4)]

Notez que la classe `MissingMetadataException` est dérivée de <xref:System.TypeAccessException>.

La classe `MissingMetadataException` possède les membres suivants :

## <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-----------------|-----------------|
|`public MissingMetadataException()`|Initialise une nouvelle instance de la classe `MissingMetadataException` à l'aide d'un message système qui décrit l'erreur.<br /><br /> Ce constructeur est destiné à un usage interne par la chaîne d’outils .NET Native uniquement.|
|`public MissingMetadataException(String message)`|Initialise une nouvelle instance de la classe `MissingMetadataException` avec un message d'erreur spécifié.<br /><br /> Ce constructeur est destiné à un usage interne par la chaîne d’outils .NET Native uniquement.|

## <a name="properties"></a>Propriétés

|Propriété|Description|
|--------------|-----------------|
|`public IDictionary Data { get; }`|Obtient une collection de paires clé/valeur qui fournissent des informations définies par l'utilisateur supplémentaires sur l'exception. (Hérité de <xref:System.Exception?displayProperty=nameWithType>.)|
|`public string HelpLink { get; set; }`|Obtient ou définit un lien vers le fichier d'aide associé à cette exception. (Hérité de <xref:System.Exception?displayProperty=nameWithType>.)|
|`public int HResult { get; protected set; }`|Obtient ou définit la valeur `HRESULT`, valeur numérique codée qui est assignée à une exception spécifique. (Hérité de <xref:System.Exception?displayProperty=nameWithType>.)|
|`public Exception InnerException { get; }`|Obtient l'exception à l'origine de l'exception actuelle. (Hérité de <xref:System.Exception?displayProperty=nameWithType>.)|
|`public string Message { get; }`|Obtient un message qui décrit l'exception active. (Hérité de <xref:System.TypeLoadException>.)|
|`public string Source { get; set; }`|Obtient ou définit le nom de l'application ou de l'objet à l'origine de l'erreur. (Hérité de <xref:System.Exception?displayProperty=nameWithType>.)|
|`public string StackTrace { get; }`|Obtient une représentation sous forme de chaîne des frames immédiats sur la pile des appels. (Hérité de <xref:System.Exception?displayProperty=nameWithType>.)|
|`public MethodBase TargetSite { get; }`|Obtient la méthode qui a levé l'exception actuelle. (Hérité de <xref:System.Exception?displayProperty=nameWithType>.)|
|`public string TypeName { get; ]`|Obtient le nom qualifié complet du type dont les métadonnées sont manquantes. (Hérité de <xref:System.TypeLoadException>.)|

## <a name="methods"></a>Méthodes

|Méthode|Description|
|------------|-----------------|
|`public bool Equals(Object obj)`|Détermine si l'objet spécifié est égal à l'objet actuel.  (Hérité de <xref:System.Exception?displayProperty=nameWithType>.)|
|`protected void Finalize()`|Autorise un objet à tenter de libérer des ressources et à exécuter d'autres opérations de nettoyage avant qu'il ne soit récupéré par une opération garbage collection. (Hérité de <xref:System.Object>.)|
|`public Exception GetBaseException()`|Retourne l’exception qui est la cause racine d’une ou plusieurs exceptions ultérieures. (Hérité de <xref:System.Exception?displayProperty=nameWithType>.)|
|`public int GetHashCode()`|Retourne un code de hachage pour une instance `MissingMetadataException`.   (Hérité de <xref:System.Object>.)|
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Définit un objet <xref:System.Runtime.Serialization.SerializationInfo> avec des informations relatives à l'exception.  (Hérité de <xref:System.TypeLoadException>.)|
|`public Type GetType()`|Obtient le type au moment de l'exécution de l'instance actuelle. (Hérité de <xref:System.Exception?displayProperty=nameWithType>.)|
|`protected Object MemberwiseClone()`|Crée une copie superficielle de l'objet actuel. (Hérité de <xref:System.Object>.)|
|`public string ToString()`|Retourne la représentation sous forme de chaîne de l'exception actuelle. (Hérité de <xref:System.Exception?displayProperty=nameWithType>.)|

## <a name="events"></a>Événements

|Événement|Description|
|-----------|-----------------|
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Se produit quand une exception est sérialisée pour créer un objet d'état d'exception qui contient des données sérialisées concernant l'exception. (Hérité de <xref:System.Exception?displayProperty=nameWithType>.)|

## <a name="usage-details"></a>Usage Details

L'exception `MissingMetadataException` est levée quand la réflexion est utilisée pour accéder à des métadonnées qui ne sont pas disponibles dans un assembly.

Les métadonnées disponibles pour une application au moment de l’exécution sont définies par le fichier de directives Runtime (configuration XML), \* . rd. Xml. Pour empêcher votre application de lever cette exception, vous devez modifier le fichier \*.rd.xml de manière à définir les métadonnées qui doivent être présentes au moment de l’exécution. Pour plus d’informations sur le format du fichier \*.rd.xml, consultez [Guide de référence du fichier de configuration des directives runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md).

> [!IMPORTANT]
> Comme cette exception indique que les métadonnées nécessaires à votre application ne sont pas disponibles au moment de l’exécution, vous ne devez pas gérer cette exception dans un bloc `try`/`catch`. Au lieu de cela, vous devez diagnostiquer la cause de l'exception et l'éliminer à l'aide d'un fichier de directives runtime. Pour obtenir l'entrée que vous pouvez ajouter à votre fichier de directives de runtime qui élimine l'exception, vous pouvez utiliser un des deux utilitaires de résolution des problèmes :
>
> - l’ [utilitaire de résolution des problèmes MissingMetadataException](https://dotnet.github.io/native/troubleshooter/type.html) pour les types ;
> - l’ [utilitaire de résolution des problèmes MissingMetadataException](https://dotnet.github.io/native/troubleshooter/method.html) pour les méthodes.

La classe `MissingMetadataException` ne contient pas de membres uniques ; tous ses membres sont hérités de sa classe de base, <xref:System.TypeAccessException>.

## <a name="see-also"></a>Voir aussi

- <xref:System.Exception?displayProperty=nameWithType>
- <xref:System.TypeAccessException>
- [MissingInteropDataException, classe](missinginteropdataexception-class-net-native.md)
- [MissingRuntimeArtifactException, classe](missingruntimeartifactexception-class-net-native.md)
- [Guide de référence du fichier de configuration des directives runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
