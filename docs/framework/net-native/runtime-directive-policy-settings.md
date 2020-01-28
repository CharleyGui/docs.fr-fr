---
title: Paramètres de stratégie de directive runtime
ms.date: 03/30/2017
ms.assetid: cb52b1ef-47fd-4609-b69d-0586c818ac9e
ms.openlocfilehash: 7a8933decaec45e8000f3f3d1717847f333deddd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738495"
---
# <a name="runtime-directive-policy-settings"></a>Paramètres de stratégie de directive runtime

> [!NOTE]
> Cette rubrique fait référence à .NET Native Developer Preview, qui correspond à la version préliminaire du logiciel. Vous pouvez télécharger la préversion sur le [site web Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (inscription nécessaire).

Les paramètres de stratégie des directives runtime pour .NET Native déterminent la disponibilité des métadonnées pour les types et les membres de type au moment de l'exécution. Sans les métadonnées nécessaires, les opérations qui reposent sur la réflexion, la sérialisation, la désérialisation ou le marshaling de types .NET Framework vers COM ou Windows Runtime peuvent échouer et lever une exception. Les exceptions les plus courantes sont [MissingMetadataException](missingmetadataexception-class-net-native.md) et, dans le cas de l’interopérabilité, [MissingInteropDataException](missinginteropdataexception-class-net-native.md).

Les paramètres de stratégie runtime sont contrôlés par un fichier de directives runtime (.rd.xml). Chaque directive runtime définit la stratégie pour un élément de programme particulier, par exemple un assembly (élément [\<Assembly>](assembly-element-net-native.md)), un type (élément [\<Type>](type-element-net-native.md)) ou une méthode (élément [\<Method>](method-element-net-native.md)). La directive inclut un ou plusieurs attributs qui définissent les types de stratégie de réflexion, les types de stratégie de sérialisation et les types de stratégie d'interopérabilité décrits dans la section suivante. La valeur de l'attribut définit le paramètre de stratégie.

## <a name="policy-types"></a>Types de stratégie

Les fichiers de directives runtime reconnaissent trois catégories de types de stratégie : réflexion, sérialisation et interopérabilité.

- Les types de stratégie de réflexion déterminent les métadonnées mises à disposition au moment de l'exécution pour la réflexion :

  - `Activate` contrôle l'accès aux constructeurs, pour permettre l'activation d'instances au moment de l'exécution.

  - `Browse` contrôle la demande d'informations sur les éléments de programme.

  - `Dynamic` contrôle l'accès à tous les types et membres au moment de l'exécution pour autoriser la programmation dynamique.

  Le tableau suivant répertorie les types de stratégie de réflexion et les éléments de programme avec lesquels ils peuvent être utilisés.

  |Élément|Activate|Parcourir|Dynamic|
  |-------------|--------------|------------|-------------|
  |[\<Application>](application-element-net-native.md)|✔️|✔️|✔️|
  |[\<Assembly>](assembly-element-net-native.md)|✔️|✔️|✔️|
  |[\<AttributeImplies>](attributeimplies-element-net-native.md)|✔️|✔️|✔️|
  |[\<Event>](event-element-net-native.md)||✔️|✔️|
  |[\<Field>](field-element-net-native.md)||✔️|✔️|
  |[\<GenericParameter>](genericparameter-element-net-native.md)|✔️|✔️|✔️|
  |[\<ImpliesType>](impliestype-element-net-native.md)|✔️|✔️|✔️|
  |[\<Method>](method-element-net-native.md)||✔️|✔️|
  |[\<MethodInstantiation>](methodinstantiation-element-net-native.md)||✔️|✔️|
  |[\<Namespace>](namespace-element-net-native.md)|✔️|✔️|✔️|
  |[\<Parameter>](parameter-element-net-native.md)|✔️|✔️|✔️|
  |[\<Property>](property-element-net-native.md)||✔️|✔️|
  |[\<Subtypes>](subtypes-element-net-native.md)|✔️|✔️|✔️|
  |[\<Type>](type-element-net-native.md)|✔️|✔️|✔️|
  |[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|✔️|✔️|✔️|
  |[\<TypeParameter>](typeparameter-element-net-native.md)|✔️|✔️|✔️|

- Les types de stratégie de sérialisation déterminent les métadonnées mises à disposition au moment de l’exécution pour la sérialisation et la désérialisation :

  - `Serialize` contrôle l'accès au moment de l'exécution aux constructeurs, champs et propriétés, pour permettre la sérialisation des instances de types par des bibliothèques tierces comme le sérialiseur JSON Newtonsoft.

  - `DataContractSerializer` contrôle l'accès aux constructeurs, aux champs et aux propriétés au moment de l'exécution, pour permettre aux instances de type d'être sérialisées par la classe <xref:System.Runtime.Serialization.DataContractSerializer>.

  - `DataContractJsonSerializer` contrôle l'accès aux constructeurs, aux champs et aux propriétés au moment de l'exécution, pour permettre aux instances de type d'être sérialisées par la classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.

  - `XmlSerializer` contrôle l'accès aux constructeurs, aux champs et aux propriétés au moment de l'exécution, pour permettre aux instances de type d'être sérialisées par la classe <xref:System.Xml.Serialization.XmlSerializer>.

  Le tableau suivant répertorie les types de stratégie de sérialisation et les éléments de programme avec lesquels ils peuvent être utilisés.

  |Élément|Sérialiser|DataContractSerializer|DataContractJsonSerializer|XmlSerializer|
  |-------------|---------------|----------------------------|--------------------------------|-------------------|
  |[\<Application>](application-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<Assembly>](assembly-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<AttributeImplies>](attributeimplies-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<Event>](event-element-net-native.md)|||||
  |[\<Field>](field-element-net-native.md)|✔️||||
  |[\<GenericParameter>](genericparameter-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<ImpliesType>](impliestype-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<Method>](method-element-net-native.md)|||||
  |[\<MethodInstantiation>](methodinstantiation-element-net-native.md)|||||
  |[\<Namespace>](namespace-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<Parameter>](parameter-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<Property>](property-element-net-native.md)|✔️||||
  |[\<Subtypes>](subtypes-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<Type>](type-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<TypeParameter>](typeparameter-element-net-native.md)|✔️|✔️|✔️|✔️|

- Les types de stratégie d'interopérabilité déterminent les métadonnées mises à disposition au moment de l'exécution pour passer des types de référence, des types de valeur et des pointeurs de fonction à COM et Windows Runtime :

  - `MarshalObject` contrôle le marshaling natif vers COM et Windows Runtime pour les types de référence.

  - `MarshalDelegate` contrôle le marshaling natif de types de délégué en tant que pointeurs de fonction.

  - `MarshalStructure` contrôle le marshaling natif vers COM et Windows Runtime pour les types de valeur.

  Le tableau suivant répertorie les types de stratégie d'interopérabilité et les éléments de programme avec lesquels ils peuvent être utilisés.

  |Élément|MarshalObject|MarshalDelegate|MarshalStructure|
  |-------------|-------------------|---------------------|----------------------|
  |[\<Application>](application-element-net-native.md)|✔️|✔️|✔️|
  |[\<Assembly>](assembly-element-net-native.md)|✔️|✔️|✔️|
  |[\<AttributeImplies>](attributeimplies-element-net-native.md)|✔️|✔️|✔️|
  |[\<Event>](event-element-net-native.md)||||
  |[\<Field>](field-element-net-native.md)||||
  |[\<GenericParameter>](genericparameter-element-net-native.md)|✔️|✔️|✔️|
  |[\<ImpliesType>](impliestype-element-net-native.md)|✔️|✔️|✔️|
  |[\<Method>](method-element-net-native.md)||||
  |[\<MethodInstantiation>](methodinstantiation-element-net-native.md)||||
  |[\<Namespace>](namespace-element-net-native.md)|✔️|✔️|✔️|
  |[\<Parameter>](parameter-element-net-native.md)|✔️|✔️|✔️|
  |[\<Property>](property-element-net-native.md)||||
  |[\<Subtypes>](subtypes-element-net-native.md)|✔️|✔️|✔️|
  |[\<Type>](type-element-net-native.md)|✔️|✔️|✔️|
  |[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|✔️|✔️|✔️|
  |[\<TypeParameter>](typeparameter-element-net-native.md)|✔️|✔️|✔️|

## <a name="policy-settings"></a>Paramètres de stratégie

Chaque type de stratégie peut être défini sur l'une des valeurs répertoriées dans le tableau suivant. Notez que les éléments qui représentent les membres de type ne prennent pas en charge le même jeu de paramètres de stratégie que les autres éléments.

|Paramètre de stratégie|Description|Éléments `Assembly`, `Namespace`, `Type` et `TypeInstantiation`|Éléments `Event`, `Field`, `Method`, `MethodInstantiation` et `Property`|
|--------------------|-----------------|-----------------------------------------------------------------------|--------------------------------------------------------------------------------|
|`All`|Active la stratégie pour tous les types et membres non supprimés par la chaîne d'outils .NET Native.|✔️||
|`Auto`|Spécifie que la stratégie par défaut doit être utilisée pour le type de stratégie pour cet élément de programme. Cela revient à omettre une stratégie pour ce type de stratégie. `Auto` sert généralement à indiquer que la stratégie est héritée d'un élément parent.|✔️|✔️|
|`Excluded`|Spécifie que la stratégie est désactivée pour un élément de programme particulier. Par exemple, la directive runtime :<br /><br /> `<Type Name="BusinessClasses.Person" Browse="Excluded" Dynamic="Excluded" />`<br /><br /> indique que les métadonnées pour la classe `BusinessClasses.Person` ne sont pas disponibles soit pour parcourir des objets `Person`, soit pour les instancier et modifier dynamiquement.|✔️|✔️|
|`Included`|Active une stratégie si les métadonnées pour le type parent sont disponibles.||✔️|
|`Public`|Active la stratégie pour les types ou membres publics, sauf si la chaîne d'outils détermine que le type ou membre n'est pas nécessaire et donc le supprime. Ce paramètre est différent de `Required Public`, qui garantit que les métadonnées pour les membres et types publics sont toujours disponibles, même si la chaîne d'outils détermine qu'elles sont superflues.|✔️||
|`PublicAndInternal`|Active la stratégie pour les types ou membres publics et internes, sauf si la chaîne d'outils détermine que le type ou membre n'est pas nécessaire et donc le supprime. Ce paramètre est différent de `Required PublicAndInternal`, qui garantit que les métadonnées pour les membres et types publics et internes sont toujours disponibles, même si la chaîne d'outils détermine qu'elles sont superflues.|✔️||
|`Required`|Spécifie que la stratégie pour un membre est activée et que les métadonnées seront disponibles même si le membre semble utilisé.||✔️|
|`Required Public`|Active la stratégie pour les types ou membres publics et garantit que les métadonnées pour les types et membres publics sont toujours disponibles. Ce paramètre est différent de `Public`, qui ne garantit la disponibilité des métadonnées pour les types et membres publics que si la chaîne d'outils détermine qu'elles sont nécessaires.|✔️||
|`Required PublicAndInternal`|Active la stratégie pour les types ou membres publics et internes et garantit que les métadonnées pour les types et membres publics et internes sont toujours disponibles. Ce paramètre est différent de `PublicAndInternal`, qui ne garantit la disponibilité des métadonnées pour les types et membres publics et internes que si la chaîne d'outils détermine qu'elles sont nécessaires.|✔️||
|`Required All`|Oblige la chaîne d'outils à conserver tous les types et membres, qu'ils soient utilisés ou non, et active la stratégie pour eux.|✔️||

## <a name="see-also"></a>Voir aussi

- [Guide de référence du fichier de configuration des directives runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Éléments de directive runtime](runtime-directive-elements.md)
