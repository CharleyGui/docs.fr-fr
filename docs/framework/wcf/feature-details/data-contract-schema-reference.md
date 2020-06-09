---
title: Référence des schémas de contrats de données
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
ms.openlocfilehash: 04d1f753e5788460404942a21a29e1612f674e90
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593566"
---
# <a name="data-contract-schema-reference"></a>Référence des schémas de contrats de données

Cette rubrique décrit le sous-ensemble du schéma XML (XSD) utilisé par <xref:System.Runtime.Serialization.DataContractSerializer> pour décrire les types CLR (Common Language Run-time) pour la sérialisation XML.

## <a name="datacontractserializer-mappings"></a>Mappages DataContractSerializer

Le `DataContractSerializer` mappe des types CLR à XSD lorsque les métadonnées sont exportées à partir d’un service Windows Communication Foundation (WCF) à l’aide d’un point de terminaison de métadonnées ou de l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Pour plus d’informations, consultez [sérialiseur de contrat de données](data-contract-serializer.md).

`DataContractSerializer` mappe également XSD aux types CLR lorsque Svcutil.exe est utilisé pour accéder à Web Services Description Language (WSDL) ou aux documents XSD et génère des contrats de données pour les services ou les clients.

Uniquement les instances de schéma XML conformes aux spécifications déclarées dans ce document peuvent être mappées aux types CLR à l'aide de `DataContractSerializer`.

### <a name="support-levels"></a>Niveaux pris en charge

`DataContractSerializer` fournit les niveaux de prise en charge suivants pour une fonctionnalité de schéma XML donnée :

- **Pris en charge**. Il y a mappage explicite de cette fonctionnalité aux types ou aux attributs CLR (ou les deux à la fois) via `DataContractSerializer`.

- **Ignoré**. La fonctionnalité est autorisée dans les schémas importés par `DataContractSerializer`, mais n'a aucun effet sur la génération du code.

- **Interdit**. `DataContractSerializer` ne prend pas en charge l'importation d'un schéma à l'aide de la fonctionnalité. Par exemple, Svcutil.exe, lors de l'accès à un WSDL avec un schéma qui utilise une telle fonctionnalité, revient à la place à l'utilisation de <xref:System.Xml.Serialization.XmlSerializer> . Il s’agit du comportement par défaut.

## <a name="general-information"></a>Informations générales

- L’espace de noms du schéma est décrit sur la page [XML Schema](https://www.w3.org/2001/XMLSchema)(Schéma XML). Le préfixe "xs" est utilisé dans ce document.

- Les attributs avec un espace de noms qui n'est pas un schéma sont ignorés.

- Les annotations (sauf celles décrites dans ce document) sont ignorées.

### <a name="xsschema-attributes"></a>\<xs:schema>: attributs

|Attribut|DataContract|
|---------------|------------------|
|`attributeFormDefault`|Ignoré.|
|`blockDefault`|Ignoré.|
|`elementFormDefault`|Doit être qualifié. Tous les éléments doivent être qualifiés pour qu'un schéma soit pris en charge par `DataContractSerializer`. Pour ce faire, vous pouvez soit définir sur xs:schema/@elementFormDefault « Qualified », soit définir sur xs:element/@form « Qualified » pour chaque déclaration d’élément.|
|`finalDefault`|Ignoré.|
|`Id`|Ignoré.|
|`targetNamespace`|Pris en charge et mappé à l'espace de noms du contrat de données. Si cet attribut n'est pas spécifié, l'espace de noms vierge est utilisé. Ne peut pas être l’espace de noms réservé `http://schemas.microsoft.com/2003/10/Serialization/` .|
|`version`|Ignoré.|

### <a name="xsschema-contents"></a>\<xs:schema>: contenu

|Contents|schéma|
|--------------|------------|
|`include`|Pris en charge. `DataContractSerializer` prend en charge xs:include et xs:import. Toutefois, Svcutil.exe restreint le suivi des références `xs:include/@schemaLocation` et `xs:import/@location` lorsque les métadonnées sont chargées à partir d'un fichier local. La liste des fichiers de schéma doit passer par un mécanisme hors bande et non par `include` dans ce cas ; les documents de schéma `include`sont ignorés.|
|`redefine`|Interdit. L'utilisation de `xs:redefine` est interdite par `DataContractSerializer` pour des raisons de sécurité : `x:redefine` requiert que `schemaLocation` soit suivi. Dans certaines circonstances, Svcutil.exe restreint l'utilisation de `schemaLocation`à l'aide de DataContract.|
|`import`|Pris en charge. `DataContractSerializer` prend en charge `xs:include` et `xs:import`. Toutefois, Svcutil.exe restreint le suivi des références `xs:include/@schemaLocation` et `xs:import/@location` lorsque les métadonnées sont chargées à partir d'un fichier local. La liste des fichiers de schéma doit passer par un mécanisme hors bande et non par `include` dans ce cas ; les documents de schéma `include`sont ignorés.|
|`simpleType`|Pris en charge. Consultez la section `xs:simpleType` .|
|`complexType`|Pris en charge, mappe aux contrats de données. Consultez la section `xs:complexType` .|
|`group`|Ignoré. `DataContractSerializer` ne prend pas en charge l'utilisation de `xs:group`, `xs:attributeGroup`et `xs:attribute`. Ces déclarations sont ignorées en tant qu'enfants de `xs:schema`, mais ne peuvent pas être référencées à partir de `complexType` ou d'autres constructions prises en charge.|
|`attributeGroup`|Ignoré. `DataContractSerializer` ne prend pas en charge l'utilisation de `xs:group`, `xs:attributeGroup`et `xs:attribute`. Ces déclarations sont ignorées en tant qu'enfants de `xs:schema`, mais ne peuvent pas être référencées à partir de `complexType` ou d'autres constructions prises en charge.|
|`element`|Pris en charge. Consultez la déclaration d'élément globale (GED).|
|`attribute`|Ignoré. `DataContractSerializer` ne prend pas en charge l'utilisation de `xs:group`, `xs:attributeGroup`et `xs:attribute`. Ces déclarations sont ignorées en tant qu'enfants de `xs:schema`, mais ne peuvent pas être référencées à partir de `complexType` ou d'autres constructions prises en charge.|
|`notation`|Ignoré.|

## <a name="complex-types--xscomplextype"></a>Types complexes :\<xs:complexType>

### <a name="general-information"></a>Informations générales

Chaque type complexe est \<xs:complexType> mappé à un contrat de données.

### <a name="xscomplextype-attributes"></a>\<xs:complexType>: attributs

|Attribut|schéma|
|---------------|------------|
|`abstract`|Doit être faux (valeur par défaut).|
|`block`|Interdit.|
|`final`|Ignoré.|
|`id`|Ignoré.|
|`mixed`|Doit être faux (valeur par défaut).|
|`name`|Pris en charge et mappé au nom du contrat de données. Si le nom inclut des points, une tentative est faite pour mapper le type à un type interne. Par exemple, un type complexe nommé `A.B` mappe à un type de contrat de données qui est un type interne d'un type portant le nom du contrat de données `A`, mais uniquement si un tel type de contrat de données existe. Plusieurs niveaux d'imbrication sont possibles : par exemple, `A.B.C` peut être un type interne, mais uniquement si à la fois `A` et `A.B` existent.|

### <a name="xscomplextype-contents"></a>\<xs:complexType>: contenu

|Contents|schéma|
|--------------|------------|
|`simpleContent`|Les extensions sont interdites.<br /><br /> La restriction est autorisée uniquement depuis `anySimpleType`.|
|`complexContent`|Pris en charge. Consultez « Héritage ».|
|`group`|Interdit.|
|`all`|Interdit.|
|`choice`|Interdit|
|`sequence`|Pris en charge, mappe aux membres de données d'un contrat de données.|
|`attribute`|Interdit, même si l'utilisation = "prohibited" (avec une exception). Uniquement les attributs facultatifs de l'espace de noms du schéma de sérialisation standard sont pris en charge. Ils ne mappent pas aux membres de données dans le modèle de programmation du contrat de données. Actuellement, un seul de ces attributs est significatif et est discuté dans la section ISerializable. Tous les autres sont ignorés.|
|`attributeGroup`|Interdit. Dans la version V1 de WCF, `DataContractSerializer` ignore la présence de `attributeGroup` à l’intérieur de `xs:complexType` .|
|`anyAttribute`|Interdit.|
|(empty)|Mappe à un contrat de données sans membres de données.|

### <a name="xssequence-in-a-complex-type-attributes"></a>\<xs:sequence>dans un type complexe : attributs

|Attribut|schéma|
|---------------|------------|
|`id`|Ignoré.|
|`maxOccurs`|Doit être 1 (valeur par défaut).|
|`minOccurs`|Doit être 1 (valeur par défaut).|

### <a name="xssequence-in-a-complex-type-contents"></a>\<xs:sequence>dans un type complexe : contenu

|Contents|schéma|
|--------------|------------|
|`element`|Chaque instance mappe à un membre de données.|
|`group`|Interdit.|
|`choice`|Interdit.|
|`sequence`|Interdit.|
|`any`|Interdit.|
|(empty)|Mappe à un contrat de données sans membres de données.|

## <a name="elements--xselement"></a>Html\<xs:element>

### <a name="general-information"></a>Informations générales

`<xs:element>` peut se produire dans les contextes suivants :

- Il peut se produire dans un `<xs:sequence>`, qui décrit un membre de données d'un contrat de données normal (qui n'est pas une collection). Dans ce cas, l'attribut `maxOccurs` doit avoir la valeur 1. (Une valeur de 0 n'est pas autorisée).

- Il peut se produire dans un `<xs:sequence>`, qui décrit un membre de données d'un contrat de données de collection. Dans ce cas, l'attribut `maxOccurs` doit être supérieur à 1 ou « unbounded ».

- Il peut se produire dans un `<xs:schema>` en tant que déclaration d'élément globale (GED).

### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a>\<xs:element>avec maxOccurs = 1 dans un \<xs:sequence> (données membres)

|Attribut|schéma|
|---------------|------------|
|`ref`|Interdit.|
|`name`|Pris en charge, mappe au nom du membre de données.|
|`type`|Pris en charge, mappe au type du membre de données. Pour plus d'informations, consultez le mappage de type/primitif. Si non spécifié (et l'élément ne contient pas de type anonyme), `xs:anyType` est pris en compte.|
|`block`|Ignoré.|
|`default`|Interdit.|
|`fixed`|Interdit.|
|`form`|Doit être qualifié. Cet attribut peut également être défini via `elementFormDefault` sur `xs:schema`.|
|`id`|Ignoré.|
|`maxOccurs`|1|
|`minOccurs`|Mappe à la propriété <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> d'un membre de données (`IsRequired` a la valeur true lorsque `minOccurs` a la valeur 1).|
|`nillable`|Affecte le mappage de type. Consultez le mappage de type/primitif.|

### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a>\<xs:element>avec maxOccurs>1 dans un \<xs:sequence> (regroupements)

- Mappe à un <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.

- Dans les types collection, un seul xs:element est autorisé dans un xs:sequence.

 Les collections peuvent appartenir aux types suivants :

- Collections normales (par exemple, tableaux).

- Collections de dictionnaires (mappage d'une valeur à une autre; par exemple, un <xref:System.Collections.Hashtable>).

- La seule différence entre un dictionnaire et un tableau pour un type de paire clé/valeur réside dans le modèle de programmation généré. Il existe un mécanisme d'annotation de schéma qui peut être utilisé pour indiquer qu'un type donné est une collection de dictionnaires.

Les règles appliquées aux attributs `ref`, `block`, `default`, `fixed`, `form`et `id` sont les mêmes que pour le type qui n'est pas une collection. Les autres attributs sont inclus dans le tableau suivant.

|Attribut|schéma|
|---------------|------------|
|`name`|Pris en charge, mappe à la propriété <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> dans l'attribut `CollectionDataContractAttribute` .|
|`type`|Pris en charge, mappe au type stocké dans la collection.|
|`maxOccurs`|Supérieur à 1 ou "unbounded". Le schéma DC doit utiliser "unbounded".|
|`minOccurs`|Ignoré.|
|`nillable`|Affecte le mappage de type. Cet attribut est ignoré pour les collections de dictionnaires.|

### <a name="xselement-within-an-xsschema-global-element-declaration"></a>\<xs:element>dans une \<xs:schema> déclaration d’élément globale

- Une déclaration d'élément globale (GED) qui a les mêmes nom et espace de noms qu'un type dans le schéma, ou qui définit un type anonyme à l'intérieur d'elle-même, est considérée comme associée au type.

- Exportation de schéma : les GED associées sont générées pour chaque type généré, simple et complexe.

- Désérialisation/sérialisation : les GED associées sont utilisées comme éléments racine pour le type.

- Importation de schéma : les GED associées ne sont pas requises et sont ignorées si elles suivent les règles suivantes (à moins qu'elles définissent des types).

|Attribut|schéma|
|---------------|------------|
|`abstract`|Doit être faux pour les GED associées.|
|`block`|Interdit dans les GED associées.|
|`default`|Interdit dans les GED associées.|
|`final`|Doit être faux pour les GED associées.|
|`fixed`|Interdit dans les GED associées.|
|`id`|Ignoré.|
|`name`|Pris en charge. Consultez la définition des GED associées.|
|`nillable`|Doit être vrai pour les GED associées.|
|`substitutionGroup`|Interdit dans les GED associées.|
|`type`|Pris en charge, doit correspondre au type associé pour les GED associées (à moins que l'élément contienne un type anonyme).|

### <a name="xselement-contents"></a>\<xs:element>: contenu

|Contents|schéma|
|--------------|------------|
|`simpleType`|Pris en charge.*|
|`complexType`|Pris en charge.*|
|`unique`|Ignoré.|
|`key`|Ignoré.|
|`keyref`|Ignoré.|
|(vide)|Pris en charge.|

\*Lors de l’utilisation du `simpleType` `complexType,` mappage et pour les types anonymes est le même que pour les types non anonymes, à ceci près qu’il n’y a pas de contrats de données anonymes. par conséquent, un contrat de données nommé est créé avec un nom généré dérivé du nom de l’élément. Les règles pour les types anonymes sont les suivantes :

- Détails de l’implémentation WCF : si le `xs:element` nom ne contient pas de points, le type anonyme est mappé à un type interne du type de contrat de données externe. Si le nom contient des points, le type de contrat de données résultant est indépendant (n'est pas un type interne).

- Le nom de contrat de données généré du type interne est le nom de contrat de données du type externe suivi par un point, le nom de l'élément et la chaîne "Type".

- Si un contrat de données avec un tel nom existe déjà, le nom est rendu unique en ajoutant "1", "2", "3" et ainsi de suite jusqu'à ce qu'un nom unique soit créé.

## <a name="simple-types---xssimpletype"></a>Types simples-\<xs:simpleType>

### <a name="xssimpletype-attributes"></a>\<xs:simpleType>: attributs

|Attribut|schéma|
|---------------|------------|
|`final`|Ignoré.|
|`id`|Ignoré.|
|`name`|Pris en charge, mappe au nom du contrat de données.|

### <a name="xssimpletype-contents"></a>\<xs:simpleType>: contenu

|Contents|schéma|
|--------------|------------|
|`restriction`|Pris en charge. Mappe aux contrats de données d'énumération. Cet attribut est ignoré s'il ne correspond pas au modèle d'énumération. Consultez la section des restrictions `xs:simpleType` .|
|`list`|Pris en charge. Mappe aux contrats de données d'énumération d'indicateur. Consultez la section répertoriant `xs:simpleType` .|
|`union`|Interdit.|

### \<xs:restriction>

- Les restrictions de type complexe sont prises en charge uniquement pour la base = "`xs:anyType`".

- Les restrictions de type simple de `xs:string` qui n'ont pas de facettes de restriction autres que `xs:enumeration` sont mappées aux contrats de données d'énumération.

- Toutes les autres restrictions de type simple sont mappées aux types qu'elles restreignent. Par exemple, une restriction de `xs:int` mappe à un entier, tout comme `xs:int` lui-même. Pour plus d’informations sur le mappage de type primitif, consultez mappage de type/primitif.

### <a name="xsrestriction-attributes"></a>\<xs:restriction>: attributs

|Attribut|schéma|
|---------------|------------|
|`base`|Doit être un type simple pris en charge ou `xs:anyType`.|
|`id`|Ignoré.|

### <a name="xsrestriction-for-all-other-cases-contents"></a>\<xs:restriction>pour tous les autres cas : contenu

|Contents|schéma|
|--------------|------------|
|`simpleType`|Si présent, doit être dérivé d'un type primitif pris en charge.|
|`minExclusive`|Ignoré.|
|`minInclusive`|Ignoré.|
|`maxExclusive`|Ignoré.|
|`maxInclusive`|Ignoré.|
|`totalDigits`|Ignoré.|
|`fractionDigits`|Ignoré.|
|`length`|Ignoré.|
|`minLength`|Ignoré.|
|`maxLength`|Ignoré.|
|`enumeration`|Ignoré.|
|`whiteSpace`|Ignoré.|
|`pattern`|Ignoré.|
|(vide)|Pris en charge.|

## <a name="enumeration"></a>Énumération

### <a name="xsrestriction-for-enumerations-attributes"></a>\<xs:restriction>pour les énumérations : attributs

|Attribut|schéma|
|---------------|------------|
|`base`|Si présent, doit être `xs:string`.|
|`id`|Ignoré.|

### <a name="xsrestriction-for-enumerations-contents"></a>\<xs:restriction>pour les énumérations : contenu

|Contents|schéma|
|--------------|------------|
|`simpleType`|Si présent, doit être une restriction d'énumération prise en charge par le contrat de données (cette section).|
|`minExclusive`|Ignoré.|
|`minInclusive`|Ignoré.|
|`maxExclusive`|Ignoré.|
|`maxInclusive`|Ignoré.|
|`totalDigits`|Ignoré.|
|`fractionDigits`|Ignoré.|
|`length`|Interdit.|
|`minLength`|Interdit.|
|`maxLength`|Interdit.|
|`enumeration`|Pris en charge. Le "id" d'énumération est ignoré, et "value" mappe au nom de la valeur dans le contrat de données d'énumération.|
|`whiteSpace`|Interdit.|
|`pattern`|Interdit.|
|(empty)|Pris en charge, mappe au type énumération vide.|

 Le code suivant montre une classe d'énumération C#.

```csharp
public enum MyEnum
{
  first = 3,
  second = 4,
  third =5
}
```

Cette classe mappe au schéma suivant par `DataContractSerializer`. Si les valeurs d'énumération démarrent à partir de 1, les blocs `xs:annotation` ne sont pas générés.

```xml
<xs:simpleType name="MyEnum">
  <xs:restriction base="xs:string">
    <xs:enumeration value="first">
      <xs:annotation>
        <xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
          3
          </EnumerationValue>
        </xs:appinfo>
      </xs:annotation>
    </xs:enumeration>
    <xs:enumeration value="second">
      <xs:annotation>
        <xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
          4
          </EnumerationValue>
        </xs:appinfo>
      </xs:annotation>
    </xs:enumeration>
  </xs:restriction>
</xs:simpleType>
```

### \<xs:list>

`DataContractSerializer` mappe des types énumération marqués avec `System.FlagsAttribute` à `xs:list` dérivé de `xs:string`. Aucune autre variation `xs:list` n'est prise en charge.

### <a name="xslist-attributes"></a>\<xs:list>: attributs

|Attribut|schéma|
|---------------|------------|
|`itemType`|Interdit.|
|`id`|Ignoré.|

### <a name="xslist-contents"></a>\<xs:list>: contenu

|Contents|schéma|
|--------------|------------|
|`simpleType`|Doit être une restriction de `xs:string` utilisant la facette `xs:enumeration` .|

Si la valeur d'énumération ne suit pas une progression de puissance de 2 (valeur par défaut pour les indicateurs), la valeur est stockée dans l'élément `xs:annotation/xs:appInfo/ser:EnumerationValue` .

Par exemple, le code suivant marque un type énumération.

```csharp
[Flags]
public enum AuthFlags
{
  AuthAnonymous = 1,
  AuthBasic = 2,
  AuthNTLM = 4,
  AuthMD5 = 16,
  AuthWindowsLiveID = 64,
}
```

Ce type mappe au schéma suivant.

```xml
<xs:simpleType name="AuthFlags">
    <xs:list>
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:enumeration value="AuthAnonymous" />
          <xs:enumeration value="AuthBasic" />
          <xs:enumeration value="AuthNTLM" />
          <xs:enumeration value="AuthMD5">
            <xs:annotation>
              <xs:appinfo>
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">16</EnumerationValue>
              </xs:appinfo>
            </xs:annotation>
          </xs:enumeration>
          <xs:enumeration value="AuthWindowsLiveID">
            <xs:annotation>
              <xs:appinfo>
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">64</EnumerationValue>
              </xs:appinfo>
            </xs:annotation>
          </xs:enumeration>
        </xs:restriction>
      </xs:simpleType>
    </xs:list>
  </xs:simpleType>
```

## <a name="inheritance"></a>Héritage

### <a name="general-rules"></a>Règles Générales

Un contrat de données peut hériter d'un autre contrat de données. De tels contrats de données mappent à une base et sont dérivés des types d'extension à l'aide de la construction de schéma XML `<xs:extension>` .

Un contrat de données ne peut pas hériter d'un contrat de données de collection.

Le code ci-dessous montre un exemple de contrat de données.

```csharp
[DataContract]
public class Person
{
  [DataMember]
  public string Name;
}
[DataContract]
public class Employee : Person
{
  [DataMember]
  public int ID;
}
```

Ce contrat de données mappe à la déclaration de type de schéma XML suivante.

```xml
<xs:complexType name="Employee">
 <xs:complexContent mixed="false">
  <xs:extension base="tns:Person">
   <xs:sequence>
    <xs:element minOccurs="0" name="ID" type="xs:int"/>
   </xs:sequence>
  </xs:extension>
 </xs:complexContent>
</xs:complexType>
<xs:complexType name="Person">
 <xs:sequence>
  <xs:element minOccurs="0" name="Name"
    nillable="true" type="xs:string"/>
 </xs:sequence>
</xs:complexType>
```

### <a name="xscomplexcontent-attributes"></a>\<xs:complexContent>: attributs

|Attribut|schéma|
|---------------|------------|
|`id`|Ignoré.|
|`mixed`|Doit être faux.|

### <a name="xscomplexcontent-contents"></a>\<xs:complexContent>: contenu

|Contents|schéma|
|--------------|------------|
|`restriction`|Interdit, sauf lorsque la base = "`xs:anyType`". Ce qui précède équivaut à placer directement le contenu de `xs:restriction` sous le conteneur de `xs:complexContent`.|
|`extension`|Pris en charge. Mappe à l'héritage de contrat de données.|

### <a name="xsextension-in-xscomplexcontent-attributes"></a>\<xs:extension>dans \<xs:complexContent> : attributs

|Attribut|schéma|
|---------------|------------|
|`id`|Ignoré.|
|`base`|Pris en charge. Mappe au type de contrat de données de base de qui ce type hérite.|

### <a name="xsextension-in-xscomplexcontent-contents"></a>\<xs:extension>dans \<xs:complexContent> : contenu

Les règles sont les mêmes que pour le contenu `<xs:complexType>` .

Si un `<xs:sequence>` est fourni, ses éléments membres mappent aux membres de données supplémentaires qui sont présents dans le contrat de données dérivé.

Si un type dérivé contient un élément portant le même nom qu'un élément dans un type de base, la déclaration d'élément en double mappe à un membre de données avec un nom généré pour être unique. Des entiers positifs sont ajoutés au nom du membre de données ("member1", "member2" et ainsi de suite) jusqu'à ce qu'un nom unique soit trouvé. Inversement :

- Si un contrat de données dérivé a un membre de données portant le même nom et type qu'un membre de données dans un contrat de données de base, `DataContractSerializer` génère cet élément correspondant dans le type dérivé.

- Si un contrat de données dérivé a un membre de données portant le même nom qu'un membre de données dans un contrat de données de base mais ayant un type différent, `DataContractSerializer` importe un schéma avec un élément de type `xs:anyType` à la fois dans le type de base et dans les déclarations de type dérivé. Le nom du type d'origine est conservé dans `xs:annotations/xs:appInfo/ser:ActualType/@Name`.

Les deux variations peuvent aboutir à schéma ayant un modèle de contenu ambigu, qui dépend de l'ordre des membres de données respectifs.

## <a name="typeprimitive-mapping"></a>Mappage de type/primitif

`DataContractSerializer` utilise le mappage suivant pour les types primitifs de schéma XML.

|Type XSD|Type .NET|
|--------------|---------------|
|`anyType`|<xref:System.Object>.|
|`anySimpleType`|<xref:System.String>.|
|`duration`|<xref:System.TimeSpan>.|
|`dateTime`|<xref:System.DateTime>.|
|`dateTimeOffset`|Objets<xref:System.DateTime> et <xref:System.TimeSpan> pour l'offset. Consultez Sérialisation DateTimeOffset ci-dessous.|
|`time`|<xref:System.String>.|
|`date`|<xref:System.String>.|
|`gYearMonth`|<xref:System.String>.|
|`gYear`|<xref:System.String>.|
|`gMonthDay`|<xref:System.String>.|
|`gDay`|<xref:System.String>.|
|`gMonth`|<xref:System.String>.|
|`boolean`|<xref:System.Boolean>|
|`base64Binary`|Tableau<xref:System.Byte> .|
|`hexBinary`|<xref:System.String>.|
|`float`|<xref:System.Single>.|
|`double`|<xref:System.Double>.|
|`anyURI`|<xref:System.Uri>.|
|`QName`|<xref:System.Xml.XmlQualifiedName>.|
|`string`|<xref:System.String>.|
|`normalizedString`|<xref:System.String>.|
|`token`|<xref:System.String>.|
|`language`|<xref:System.String>.|
|`Name`|<xref:System.String>.|
|`NCName`|<xref:System.String>.|
|`ID`|<xref:System.String>.|
|`IDREF`|<xref:System.String>.|
|`IDREFS`|<xref:System.String>.|
|`ENTITY`|<xref:System.String>.|
|`ENTITIES`|<xref:System.String>.|
|`NMTOKEN`|<xref:System.String>.|
|`NMTOKENS`|<xref:System.String>.|
|`decimal`|<xref:System.Decimal>.|
|`integer`|<xref:System.Int64>.|
|`nonPositiveInteger`|<xref:System.Int64>.|
|`negativeInteger`|<xref:System.Int64>.|
|`long`|<xref:System.Int64>.|
|`int`|<xref:System.Int32>.|
|`short`|<xref:System.Int16>.|
|`Byte`|<xref:System.SByte>.|
|`nonNegativeInteger`|<xref:System.Int64>.|
|`unsignedLong`|<xref:System.UInt64>.|
|`unsignedInt`|<xref:System.UInt32>.|
|`unsignedShort`|<xref:System.UInt16>.|
|`unsignedByte`|<xref:System.Byte>.|
|`positiveInteger`|<xref:System.Int64>.|

## <a name="iserializable-types-mapping"></a>Mappage de types ISerializable

Dans .NET Framework version 1,0, <xref:System.Runtime.Serialization.ISerializable> a été introduit comme mécanisme général pour sérialiser des objets à des fins de persistance ou de transfert de données. Il existe de nombreux types de .NET Framework qui implémentent `ISerializable` et qui peuvent être passés entre les applications. <xref:System.Runtime.Serialization.DataContractSerializer> fournit naturellement le support pour les classes `ISerializable` . `DataContractSerializer` mappe des types de schéma d'implémentation `ISerializable` qui diffèrent uniquement par le QName (nom qualifié) du type et sont des collections de propriétés. Par exemple, le `DataContractSerializer` mappe <xref:System.Exception> au type xsd suivant dans l' `http://schemas.datacontract.org/2004/07/System` espace de noms.

```xml
<xs:complexType name="Exception">
 <xs:sequence>
  <xs:any minOccurs="0" maxOccurs="unbounded"
      namespace="##local" processContents="skip"/>
 </xs:sequence>
 <xs:attribute ref="ser:FactoryType"/>
</xs:complexType>
```

L'attribut facultatif `ser:FactoryType` déclaré dans le schéma de sérialisation du contrat de données référence une classe de fabrique qui peut désérialiser le type. La classe de fabrique doit faire partie de la collection de types connus de l'instance `DataContractSerializer` qui est utilisée. Pour plus d’informations sur les types connus, consultez [types connus de contrat de données](data-contract-known-types.md).

## <a name="datacontract-serialization-schema"></a>Schéma de sérialisation DataContract

Plusieurs schémas exportés par `DataContractSerializer` , utilisent des types, des éléments et des attributs d'un espace de noms spécial de la sérialisation du contrat de données :

`http://schemas.microsoft.com/2003/10/Serialization`

Voici une déclaration de schéma de sérialisation du contrat de données complète.

```xml
<xs:schema attributeFormDefault="qualified"
   elementFormDefault="qualified"
   targetNamespace =
    "http://schemas.microsoft.com/2003/10/Serialization/"
   xmlns:xs="http://www.w3.org/2001/XMLSchema"
   xmlns:tns="http://schemas.microsoft.com/2003/10/Serialization/">

 <!-- Top-level elements for primitive types. -->
 <xs:element name="anyType" nillable="true" type="xs:anyType"/>
 <xs:element name="anyURI" nillable="true" type="xs:anyURI"/>
 <xs:element name="base64Binary"
       nillable="true" type="xs:base64Binary"/>
 <xs:element name="boolean" nillable="true" type="xs:boolean"/>
 <xs:element name="byte" nillable="true" type="xs:byte"/>
 <xs:element name="dateTime" nillable="true" type="xs:dateTime"/>
 <xs:element name="decimal" nillable="true" type="xs:decimal"/>
 <xs:element name="double" nillable="true" type="xs:double"/>
 <xs:element name="float" nillable="true" type="xs:float"/>
 <xs:element name="int" nillable="true" type="xs:int"/>
 <xs:element name="long" nillable="true" type="xs:long"/>
 <xs:element name="QName" nillable="true" type="xs:QName"/>
 <xs:element name="short" nillable="true" type="xs:short"/>
 <xs:element name="string" nillable="true" type="xs:string"/>
 <xs:element name="unsignedByte"
       nillable="true" type="xs:unsignedByte"/>
 <xs:element name="unsignedInt"
       nillable="true" type="xs:unsignedInt"/>
 <xs:element name="unsignedLong"
       nillable="true" type="xs:unsignedLong"/>
 <xs:element name="unsignedShort"
       nillable="true" type="xs:unsignedShort"/>

 <!-- Primitive types introduced for certain .NET simple types. -->
 <xs:element name="char" nillable="true" type="tns:char"/>
 <xs:simpleType name="char">
  <xs:restriction base="xs:int"/>
 </xs:simpleType>

 <!-- xs:duration is restricted to an ordered value space,
    to map to System.TimeSpan -->
 <xs:element name="duration" nillable="true" type="tns:duration"/>
 <xs:simpleType name="duration">
  <xs:restriction base="xs:duration">
   <xs:pattern
     value="\-?P(\d*D)?(T(\d*H)?(\d*M)?(\d*(\.\d*)?S)?)?"/>
   <xs:minInclusive value="-P10675199DT2H48M5.4775808S"/>
   <xs:maxInclusive value="P10675199DT2H48M5.4775807S"/>
  </xs:restriction>
 </xs:simpleType>

 <xs:element name="guid" nillable="true" type="tns:guid"/>
 <xs:simpleType name="guid">
  <xs:restriction base="xs:string">
   <xs:pattern value="[\da-fA-F]{8}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{12}"/>
  </xs:restriction>
 </xs:simpleType>

 <!-- This is used for schemas exported from ISerializable type. -->
 <xs:attribute name="FactoryType" type="xs:QName"/>
</xs:schema>
```

Il convient de remarquer les points suivants :

- `ser:char` est introduit pour représenter des caractères Unicode de type <xref:System.Char>.

- Le `valuespace` de `xs:duration` est réduit à un jeu ordonné afin qu'il puisse être mappé à un <xref:System.TimeSpan>.

- `FactoryType` est utilisé dans les schémas exportés des types dérivés de <xref:System.Runtime.Serialization.ISerializable>.

## <a name="importing-non-datacontract-schemas"></a>Importation de schémas qui ne sont pas DataContract

`DataContractSerializer` dispose de l'option `ImportXmlTypes` pour autoriser l'importation des schémas non conformes au profil XSD `DataContractSerializer` (consultez la propriété <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> ). Affecter à cette option la valeur `true` active l'acceptation des types de schémas non conformes et les mappe à l'implémentation suivante, <xref:System.Xml.Serialization.IXmlSerializable> qui encapsule un tableau de <xref:System.Xml.XmlNode> (seul le nom de la classe diffère).

```csharp
[GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]
[System.Xml.Serialization.XmlSchemaProviderAttribute("ExportSchema")]
[System.Xml.Serialization.XmlRootAttribute(IsNullable=false)]
public partial class Person : object, IXmlSerializable
{
  private XmlNode[] nodesField;
  private static XmlQualifiedName typeName =
new XmlQualifiedName("Person","http://Microsoft.ServiceModel.Samples");
  public XmlNode[] Nodes
  {
    get {return this.nodesField;}
    set {this.nodesField = value;}
  }
  public void ReadXml(XmlReader reader)
  {
    this.nodesField = XmlSerializableServices.ReadNodes(reader);
  }
  public void WriteXml(XmlWriter writer)
  {
    XmlSerializableServices.WriteNodes(writer, this.Nodes);
  }
  public System.Xml.Schema.XmlSchema GetSchema()
  {
    return null;
  }
  public static XmlQualifiedName ExportSchema(XmlSchemaSet schemas)
  {
    XmlSerializableServices.AddDefaultSchema(schemas, typeName);
    return typeName;
  }
}
```

## <a name="datetimeoffset-serialization"></a>Sérialisation DateTimeOffset

<xref:System.DateTimeOffset> n'est pas traité comme un type primitif. À la place, il est sérialisé comme un élément complexe comportant deux parties. La première partie représente la date et l'heure et la deuxième partie représente l'offset de la date et de l'heure. Un exemple d'une valeur DateTimeOffset sérialisée est illustré dans le code suivant.

```xml
<OffSet xmlns:a="http://schemas.datacontract.org/2004/07/System">
  <DateTime i:type="b:dateTime" xmlns=""
    xmlns:b="http://www.w3.org/2001/XMLSchema">2008-08-28T08:00:00
  </DateTime>
  <OffsetMinutes i:type="b:short" xmlns=""
   xmlns:b="http://www.w3.org/2001/XMLSchema">-480
   </OffsetMinutes>
</OffSet>
```

Le schéma se présente comme suit :

```xml
<xs:schema targetNamespace="http://schemas.datacontract.org/2004/07/System">
   <xs:complexType name="DateTimeOffset">
      <xs:sequence minOccurs="1" maxOccurs="1">
         <xs:element name="DateTime" type="xs:dateTime"
         minOccurs="1" maxOccurs="1" />
         <xs:element name="OffsetMinutes" type="xs:short"
         minOccurs="1" maxOccurs="1" />
      </xs:sequence>
   </xs:complexType>
</xs:schema>
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- [Using Data Contracts](using-data-contracts.md)
