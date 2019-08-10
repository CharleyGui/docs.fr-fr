---
title: Sérialisation
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: bebb27ac-9712-4196-9931-de19fc04dbac
author: KrzysztofCwalina
ms.openlocfilehash: 0259bf82e74cbca7df8da246ca2e6ba7ef4542b3
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868523"
---
# <a name="serialization"></a>Sérialisation
La sérialisation est le processus de conversion d’un objet en un format qui peut être facilement rendu persistant ou transporté. Par exemple, vous pouvez sérialiser un objet, le transporter sur Internet à l’aide de HTTP et le désérialiser sur l’ordinateur de destination.  
  
 Le .NET Framework offre trois technologies de sérialisation principales, optimisées pour différents scénarios de sérialisation. Le tableau suivant répertorie ces technologies et les principaux types Framework qui leur sont associés.  
  
|**Nom de la technologie**|**Types principaux**|**Scénario**|  
|-------------------------|--------------------|-------------------|  
|**Sérialisation du contrat de données**|<xref:System.Runtime.Serialization.DataContractAttribute> <br /> <xref:System.Runtime.Serialization.DataMemberAttribute> <br /> <xref:System.Runtime.Serialization.DataContractSerializer> <br /> <xref:System.Runtime.Serialization.NetDataContractSerializer> <br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <br /> <xref:System.Runtime.Serialization.ISerializable>|Persistance générale<br />Services Web<br />JSON|  
|**Sérialisation XML**|<xref:System.Xml.Serialization.XmlSerializer>|Format XML avec contrôle total sur la forme du code XML|  
|**Sérialisation du Runtime (binaire et SOAP)**|<xref:System.SerializableAttribute> <br /> <xref:System.Runtime.Serialization.ISerializable> <br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|.NET Remoting|  
  
 **✓ DO** réflexion sur la sérialisation lors de la création de nouveaux types.  
  
## <a name="choosing-the-right-serialization-technology-to-support"></a>Sélection de la technologie de sérialisation appropriée à prendre en charge  
 **✓ CONSIDER** prenant en charge la sérialisation de contrat de données si les instances de votre type peuvent doivent être rendues persistantes ou sont utilisés dans les Services Web.  
  
 **✓ CONSIDER** prenant en charge la sérialisation XML à la place ou en plus de la sérialisation de contrat de données si vous avez besoin de davantage de contrôle sur le format XML qui se produit quand le type est sérialisé.  
  
 Cela peut être nécessaire dans certains scénarios d’interopérabilité dans lesquels vous devez utiliser une construction XML qui n’est pas prise en charge par la sérialisation de contrat de données, par exemple pour produire des attributs XML.  
  
 **✓ CONSIDER** prenant en charge la sérialisation de l’exécution si les instances de ce type doivent circuler dans les limites de .NET Remoting.  
  
 **X AVOID** prenant en charge la sérialisation du Runtime ou la sérialisation XML uniquement pour des raisons de persistance générales. Préférez la sérialisation du contrat de données à la place.  
  
## <a name="supporting-data-contract-serialization"></a>Prise en charge de la sérialisation du contrat de données  
 Les types peuvent prendre en charge la <xref:System.Runtime.Serialization.DataContractAttribute> sérialisation de contrat de données en appliquant au type <xref:System.Runtime.Serialization.DataMemberAttribute> et aux membres (champs et propriétés) du type.  
  
 **✓ CONSIDER** marquant les membres de données de votre type public si le type peut être utilisé avec une confiance partielle.  
  
 En mode de confiance totale, les sérialiseurs de contrat de données peuvent sérialiser et désérialiser des membres et des types non publics, mais seuls les membres publics peuvent être sérialisés et désérialisés en confiance partielle.  
  
 **✓ DO** implémenter un accesseur Get et un accesseur Set pour toutes les propriétés qui ont <xref:System.Runtime.Serialization.DataMemberAttribute>. Les sérialiseurs de contrat de données requièrent que l’accesseur get et l’accesseur Set pour le type soient considérés comme sérialisables. (Dans .NET Framework 3,5 SP1, certaines propriétés de collection peuvent être accessibles en tout lieu.) Si le type n'est pas utilisé en mode de confiance partielle, un des accesseurs de propriété, ou les deux, peuvent être non publics.  
  
 **✓ CONSIDER** à l’aide de l’initialisation d’instances désérialisées les rappels de sérialisation.  
  
 Les constructeurs ne sont pas appelés lorsque les objets sont désérialisés. (Il existe des exceptions à la règle. Les constructeurs de collections marqués avec <xref:System.Runtime.Serialization.CollectionDataContractAttribute> sont appelés pendant la désérialisation.) Par conséquent, toute logique qui s’exécute pendant une construction normale doit être implémentée comme l’un des rappels de sérialisation.  
  
 `OnDeserializedAttribute`est l’attribut de rappel le plus couramment utilisé. Les autres attributs de la famille sont <xref:System.Runtime.Serialization.OnDeserializingAttribute>,  <xref:System.Runtime.Serialization.OnSerializingAttribute> et <xref:System.Runtime.Serialization.OnSerializedAttribute>. Ils peuvent être utilisés pour marquer les rappels exécutés avant la désérialisation, avant la sérialisation et enfin, après la sérialisation, respectivement.  
  
 **✓ CONSIDER** à l’aide de la <xref:System.Runtime.Serialization.KnownTypeAttribute> pour indiquer les types concrets qui doivent être utilisées lors de la désérialisation d’un graphique d’objets complexes.  
  
 **✓ DO** prendre en compte la compatibilité ascendante et descendante lors de la création ou la modification des types sérialisables.  
  
 Gardez à l'esprit que les flux sérialisés de futures versions de votre type peuvent être désérialisés dans la version actuelle du type, et inversement.  
  
 Assurez-vous que vous comprenez que les membres de données, même privés et internes, ne peuvent pas modifier leurs noms, types ou même leur ordre dans les versions futures du type, sauf si une attention particulière est prise pour préserver le contrat à l’aide de paramètres explicites pour les attributs de contrat de données. .  
  
 Testez la compatibilité de la sérialisation lorsque vous apportez des modifications aux types sérialisables. Essayez de désérialiser la nouvelle version dans une ancienne version, et inversement.  
  
 **✓ CONSIDER** implémentation <xref:System.Runtime.Serialization.IExtensibleDataObject> pour permettre l’aller-retour entre les différentes versions du type.  
  
 L'interface permet au sérialiseur de garantir qu'aucune donnée n'est perdue lors de l'aller-retour. La <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=nameWithType> propriété est utilisée pour stocker toutes les données de la version future du type qui est inconnu de la version actuelle et ne peut donc pas la stocker dans ses membres de données. Lorsque la version actuelle est par la suite sérialisée et désérialisée dans une version future, les données supplémentaires sont disponibles dans le flux sérialisé.  
  
## <a name="supporting-xml-serialization"></a>Prise en charge de la sérialisation XML  
 La sérialisation de contrat de données est la technologie de sérialisation principale (par défaut) dans le .NET Framework, mais il existe des scénarios de sérialisation que la sérialisation de contrat de données ne prend pas en charge. Par exemple, vous n'avez pas le contrôle total sur la forme du XML généré ou consommé par le sérialiseur. Si ce contrôle précis est requis, la sérialisation XML doit être utilisée, et vous devez concevoir vos types pour prendre en charge cette technologie de sérialisation.  
  
 **X AVOID** vous concevez vos types spécifiquement pour la sérialisation XML, sauf si vous avez une raison très forte pour contrôler la forme du code XML généré. Cette technologie de sérialisation a été remplacée par la sérialisation du contrat de données présentée dans la section précédente.  
  
 **✓ CONSIDER** implémentant le <xref:System.Xml.Serialization.IXmlSerializable> interface si vous souhaitez contrôler davantage la forme du code XML sérialisé que celle fournie en appliquant les attributs de sérialisation XML. Deux méthodes de l’interface, <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> et <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>, vous permettent de contrôler entièrement le flux XML sérialisé. Vous pouvez également contrôler le schéma XML qui est généré pour le type en appliquant `XmlSchemaProviderAttribute`.  
  
## <a name="supporting-runtime-serialization"></a>Prise en charge de la sérialisation du runtime  
 La sérialisation du runtime est une technologie utilisée par .NET Remoting. Si vous pensez que vos types seront transportés à l’aide de .NET Remoting, vous devez vous assurer qu’ils prennent en charge la sérialisation du Runtime.  
  
 La prise en charge de base de la sérialisation du runtime peut être <xref:System.SerializableAttribute>fournie en appliquant, et des scénarios plus avancés impliquent l’implémentation d' <xref:System.Runtime.Serialization.ISerializable> un modèle sérialisable simple du Runtime (implémenter et fournir un constructeur de sérialisation).  
  
 **✓ CONSIDER** prenant en charge la sérialisation du Runtime si vos types seront utilisées avec la communication à distance .NET. Par exemple, l' <xref:System.AddIn?displayProperty=nameWithType> espace de noms utilise .NET Remoting, de sorte que tous `System.AddIn` les types échangés entre les compléments doivent prendre en charge la sérialisation du Runtime.  
  
 **✓ CONSIDER** implémentant le modèle sérialisable Runtime si vous souhaitez contrôler le processus de sérialisation. Par exemple, si vous souhaitez transformer des données à mesure qu'elles sont sérialisées ou désérialisées.  
  
 Le modèle est très simple. Il suffit d'implémenter l'interface <xref:System.Runtime.Serialization.ISerializable> et de fournir un constructeur spécial qui est utilisé lorsque l'objet est désérialisé.  
  
 **✓ DO** Protégez le constructeur de sérialisation et de fournir les deux paramètres typés et nommés exactement comme indiqué dans l’exemple ici.  
  
```csharp
[Serializable]  
public class Person : ISerializable
{  
    protected Person(SerializationInfo info, StreamingContext context)
    {  
        // ...  
    }  
}  
```
  
 **✓ DO** implémenter le <xref:System.Runtime.Serialization.ISerializable> membres explicitement.  
  
 **✓ DO** s’appliquent à une demande de liaison <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> implémentation. Cela garantit que seuls les cœurs entièrement fiables et le sérialiseur de Runtime ont accès au membre.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé par l’autorisation de Pearson Education, Inc. à [partir des instructions de conception d’infrastructure: Conventions, idiomes et modèles pour les bibliothèques .net réutilisables, 2nd](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Edition de Krzysztof Cwalina et Brad Abrams, publié le 22 octobre, 2008 de Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi

- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Indications relatives à l’utilisation](../../../docs/standard/design-guidelines/usage-guidelines.md)
