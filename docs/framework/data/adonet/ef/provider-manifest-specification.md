---
title: Spécification de manifeste du fournisseur
ms.date: 03/30/2017
ms.assetid: bb450b47-8951-4f99-9350-26f05a4d4e46
ms.openlocfilehash: cc58bbc82f3930f087b5da0c64afb4f9f03e905b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854506"
---
# <a name="provider-manifest-specification"></a>Spécification de manifeste du fournisseur
Cette section explique comment un fournisseur de banques de données peut prendre en charge les types et les fonctions dans la banque de données.  
  
 Les Services d'entités fonctionnent indépendamment d'un fournisseur de banques de données spécifique, mais permettent encore à un fournisseur de données de définir explicitement la manière dont les modèles, les mappages et les requêtes interagissent avec une banque de données sous-jacente. Sans couche d'abstraction, les Services d'entités seraient uniquement destinés à une banque de données ou un fournisseur de données spécifique.  
  
 Les types pris en charge par le fournisseur sont pris en charge directement ou indirectement par la base de données sous-jacente. Ces types ne sont pas nécessairement les types de magasins exacts, mais les types utilisés par le fournisseur pour prendre en charge l’Entity Framework. Les types de fournisseurs/banques sont décrits en termes EDM (Entity Data Model).  
  
 Les types de paramètres et les types de retour pour les fonctions prises en charge par la banque de données sont spécifiés en termes EDM.  
  
## <a name="requirements"></a>Configuration requise  
 Le Entity Framework et le magasin de données doivent être en mesure de transmettre des données dans les types connus sans perte de données ni troncation.  
  
 Le manifeste du fournisseur doit pouvoir être chargé par les outils au moment du design sans devoir ouvrir une connexion à la banque de données.  
  
 La Entity Framework est sensible à la casse, mais le magasin de données sous-jacent peut ne pas l’être. Lorsque les artefacts EDM (identificateurs et noms de type, par exemple) sont définis et utilisés dans le manifeste, ils doivent utiliser le respect de la casse Entity Framework. Si des éléments de la banque de données respectueux de la casse apparaissent dans le manifeste du fournisseur, cette casse doit être conservée dans le manifeste du fournisseur.  
  
 L’Entity Framework nécessite un manifeste du fournisseur pour tous les fournisseurs de données. Si vous essayez d’utiliser un fournisseur qui n’a pas de manifeste de fournisseur avec le Entity Framework, vous obtiendrez une erreur.  
  
 Le tableau suivant décrit les types d’exceptions que le Entity Framework lèvera lorsque des exceptions surviennent lors de l’interaction du fournisseur :  
  
|Problème|Exception|  
|-----------|---------------|  
|Le fournisseur ne prend pas en charge GetProviderManifest dans DbProviderServices.|ProviderIncompatibleException|  
|Manifeste du fournisseur manquant : le fournisseur retourne `null` lors de la tentative de récupération du manifeste du fournisseur.|ProviderIncompatibleException|  
|Manifeste du fournisseur non valide : le fournisseur retourne un code XML non valide lors de la tentative de récupération du manifeste du fournisseur.|ProviderIncompatibleException|  
  
## <a name="scenarios"></a>Scénarios  
 Un fournisseur doit prendre en charge les scénarios suivants :  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a>Écriture d'un fournisseur avec mappage de type symétrique  
 Vous pouvez écrire un fournisseur pour le Entity Framework où chaque type de magasin est mappé à un type EDM unique, indépendamment du sens du mappage. Pour un type de fournisseur ayant un mappage très simple correspondant à un type EDM, vous pouvez utiliser une solution symétrique parce que le système de type est simple ou correspond à des types EDM.  
  
 Vous pouvez utiliser la simplicité de leur domaine et produire un manifeste du fournisseur déclaratif statique.  
  
 Vous écrivez un fichier XML qui a deux sections :  
  
- Liste de types de fournisseurs exprimés en termes d'« équivalent EDM » d'un type ou d'une fonction de banque. Les types de banque ont des types EDM équivalents. Les fonctions de banque ont des fonctions EDM correspondantes. Par exemple, varchar est un type SQL Server mais le type EDM correspondant est chaîne.  
  
- Liste de fonctions prises en charge par le fournisseur dans lesquelles les types de paramètres et les types de retour sont exprimés en termes EDM.  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a>Écriture d'un fournisseur avec mappage de type asymétrique  
 Lors de l’écriture d’un fournisseur de magasin de données pour le Entity Framework, le mappage de type EDM-à-fournisseur pour certains types peut être différent du mappage de type fournisseur-à-EDM. Par exemple, unbounded EDM PrimitiveTypeKind.String peut être mappé à nvarchar (4000) sur le fournisseur, alors que nvarchar (4000) est mappé à EDM PrimitiveTypeKind.String (MaxLength=4000).  
  
 Vous écrivez un fichier XML qui a deux sections :  
  
- Liste des types de fournisseurs exprimés en termes EDM et définition du mappage pour les deux sens : EDM-à-fournisseur et fournisseur-à-EDM.  
  
- Liste de fonctions prises en charge par le fournisseur dans lesquelles les types de paramètres et les types de retour sont exprimés en termes EDM.  
  
## <a name="provider-manifest-discoverability"></a>Manifeste du fournisseur Discoverability  
 Le manifeste est utilisé de manière indirecte par plusieurs types de composants dans les Services d'entités (par exemple Outils ou Requête), mais il est plus directement exploité par les métadonnées via l'utilisation du chargeur de métadonnées de la banque de données.  
  
 ![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](./media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")  
  
 Toutefois, un fournisseur donné peut prendre en charge différentes banques ou différentes versions de la même banque. Par conséquent, un fournisseur doit signaler un manifeste différent pour chaque banque de données prise en charge.  
  
### <a name="provider-manifest-token"></a>Jeton du manifeste du fournisseur.  
 Lorsqu'une connexion de banque de données est ouverte, le fournisseur peut demander des informations pour retourner le bon manifeste. Cela risque de ne pas être possible dans les scénarios hors connexion où les informations de connexion ne sont pas disponibles ou lorsqu'il est impossible de se connecter à la banque. Identifiez le manifeste en utilisant l'attribut `ProviderManifestToken` de l'élément `Schema` dans le fichier .ssdl. Il n'existe aucun format obligatoire pour cet attribut ; le fournisseur choisit les informations minimales nécessaires pour identifier un manifeste sans ouvrir une connexion à la banque.  
  
 Par exemple :  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a>Modèle de programmation de manifeste du fournisseur  
 Les fournisseurs dérivent de <xref:System.Data.Common.DbXmlEnabledProviderManifest>, qui leur permet de spécifier leurs manifestes de façon déclarative. L'illustration suivante montre la hiérarchie de classes d'un fournisseur :  
  
 ![None](./media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")  
  
### <a name="discoverability-api"></a>API Discoverability  
 Le manifeste du fournisseur est chargé par le chargeur de métadonnées de la banque (StoreItemCollection), à l'aide d'une connexion de la banque de données ou d'un jeton du manifeste du fournisseur.  
  
#### <a name="using-a-data-store-connection"></a>Utilisation d'une connexion de banque de données  
 Lorsque la connexion au magasin de données est disponible <xref:System.Data.Common.DbProviderServices.GetProviderManifestToken%2A?displayProperty=nameWithType> , appelez pour retourner le jeton qui est passé <xref:System.Data.Common.DbProviderServices.GetProviderManifest%2A> à la méthode, <xref:System.Data.Common.DbProviderManifest>qui retourne. Cette méthode délègue à l’implémentation du fournisseur `GetDbProviderManifestToken`de.  
  
```csharp
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a>Utilisation d'un jeton du manifeste du fournisseur.  
 Pour le scénario hors connexion, le jeton est sélectionné dans une représentation SSDL. Le langage SSDL vous permet de spécifier un ProviderManifestToken (voir [élément Schema (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) pour plus d’informations). Par exemple, si une connexion ne peut pas être ouverte, le langage SSDL a un jeton du manifeste du fournisseur qui spécifie des informations sur le manifeste.  
  
```  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
### <a name="provider-manifest-schema"></a>Schéma de manifeste du fournisseur  
 Le schéma d'informations défini pour chaque fournisseur contient des informations statiques à consommer par des métadonnées :  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema elementFormDefault="qualified"  
   xmlns:xs="http://www.w3.org/2001/XMLSchema"  
   targetNamespace="http://schemas.microsoft.com/ado/2006/04/edm/providermanifest"  
   xmlns:pm="http://schemas.microsoft.com/ado/2006/04/edm/providermanifest">  
  
  <xs:element name="ProviderManifest">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="Types" type="pm:TTypes" minOccurs="1" maxOccurs="1" />  
        <xs:element name="Functions" type="pm:TFunctions" minOccurs="0" maxOccurs="1"/>  
      </xs:sequence>  
      <xs:attribute name="Namespace" type="xs:string" use="required"/>  
    </xs:complexType>  
  </xs:element>  
  <xs:complexType name="TVersion">  
    <xs:attribute name="Major" type="xs:int" use="required" />  
    <xs:attribute name="Minor" type="xs:int" use="required" />  
    <xs:attribute name="Build" type="xs:int" use="required" />  
    <xs:attribute name="Revision" type="xs:int" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TIntegerFacetDescription">  
    <xs:attribute name="Minimum" type="xs:int" use="optional" />  
    <xs:attribute name="Maximum" type="xs:int" use="optional" />  
    <xs:attribute name="DefaultValue" type="xs:int" use="optional" />  
    <xs:attribute name="Constant" type="xs:boolean" default="false" />  
  </xs:complexType>  
  
  <xs:complexType name="TBooleanFacetDescription">  
    <xs:attribute name="DefaultValue" type="xs:boolean" use="optional" />  
    <xs:attribute name="Constant" type="xs:boolean" default="true" />  
  </xs:complexType>  
  
  <xs:complexType name="TDateTimeFacetDescription">  
    <xs:attribute name="Constant" type="xs:boolean" default="false" />  
  </xs:complexType>  
  
  <xs:complexType name="TFacetDescriptions">  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="Precision" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="Scale" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="MaxLength" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="Unicode" minOccurs="0" maxOccurs="1" type="pm:TBooleanFacetDescription"/>  
      <xs:element name="FixedLength" minOccurs="0" maxOccurs="1" type="pm:TBooleanFacetDescription"/>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:complexType name="TType">  
    <xs:sequence>  
      <xs:element name="FacetDescriptions" type="pm:TFacetDescriptions" minOccurs="0" maxOccurs="1"/>  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="required"/>  
    <xs:attribute name="PrimitiveTypeKind" type="pm:TPrimitiveTypeKind" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TTypes">  
    <xs:sequence>  
      <xs:element name="Type" type="pm:TType" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:sequence>  
  </xs:complexType>  
  
  <xs:attributeGroup name="TFacetAttribute">  
    <xs:attribute name="Precision" type="xs:int" use="optional"/>  
    <xs:attribute name="Scale" type="xs:int" use="optional"/>  
    <xs:attribute name="MaxLength" type="xs:int" use="optional"/>  
    <xs:attribute name="Unicode" type="xs:boolean" use="optional"/>  
    <xs:attribute name="FixedLength" type="xs:boolean" use="optional"/>  
  </xs:attributeGroup>  
  
  <xs:complexType name="TFunctionParameter">  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attributeGroup ref="pm:TFacetAttribute" />  
    <xs:attribute name="Mode" type="pm:TParameterDirection" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TReturnType">  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attributeGroup ref="pm:TFacetAttribute" />  
  </xs:complexType>  
  
  <xs:complexType name="TFunction">  
    <xs:choice minOccurs="0" maxOccurs ="unbounded">  
      <xs:element name ="ReturnType" type="pm:TReturnType" minOccurs="0" maxOccurs="1" />  
      <xs:element name="Parameter" type="pm:TFunctionParameter" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:choice>  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Aggregate" type="xs:boolean" use="optional" />  
    <xs:attribute name="BuiltIn" type="xs:boolean" use="optional" />  
    <xs:attribute name="StoreFunctionName" type="xs:string" use="optional" />  
    <xs:attribute name="NiladicFunction" type="xs:boolean" use="optional" />  
    <xs:attribute name="ParameterTypeSemantics" type="pm:TParameterTypeSemantics" use="optional" default="AllowImplicitConversion" />  
  </xs:complexType>  
  
  <xs:complexType name="TFunctions">  
    <xs:sequence>  
      <xs:element name="Function" type="pm:TFunction" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:sequence>  
  </xs:complexType>  
  
  <xs:simpleType name="TPrimitiveTypeKind">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Binary"/>  
      <xs:enumeration value="Boolean"/>  
      <xs:enumeration value="Byte"/>  
      <xs:enumeration value="Decimal"/>  
      <xs:enumeration value="DateTime"/>  
      <xs:enumeration value="Time"/>  
      <xs:enumeration value="DateTimeOffset"/>          
      <xs:enumeration value="Double"/>  
      <xs:enumeration value="Guid"/>  
      <xs:enumeration value="Single"/>  
      <xs:enumeration value="SByte"/>  
      <xs:enumeration value="Int16"/>  
      <xs:enumeration value="Int32"/>  
      <xs:enumeration value="Int64"/>  
      <xs:enumeration value="String"/>  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="TParameterDirection">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="In"/>  
      <xs:enumeration value="Out"/>  
      <xs:enumeration value="InOut"/>  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="TParameterTypeSemantics">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="ExactMatchOnly" />  
      <xs:enumeration value="AllowImplicitPromotion" />  
      <xs:enumeration value="AllowImplicitConversion" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
#### <a name="types-node"></a>Nœud de types  
 Le nœud de types dans le manifeste du fournisseur contient des informations sur les types pris en charge en mode natif par la banque de données ou via le fournisseur.  
  
##### <a name="type-node"></a>Nœud Type  
 Chaque nœud Type définit un type de fournisseur en termes d'EDM. Le nœud Type décrit le nom du type de fournisseur, ainsi que les informations liées au type de modèle auquel il est mappé et les facettes pour décrire ce mappage de type.  
  
 Pour exprimer ces informations de type dans le manifeste du fournisseur, chaque déclaration TypeInformation doit définir plusieurs descriptions de facette pour chaque Type :  
  
|Nom d'attribut|Type de données|Obligatoire|Valeur par défaut|Description|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Nom|String|Oui|N/A|Nom de type de données spécifique au fournisseur|  
|PrimitiveTypeKind|PrimitiveTypeKind|Oui|N/A|Nom du type EDM|  
  
###### <a name="function-node"></a>Nœud Function  
 Chaque Function définit une fonction unique disponible via le fournisseur.  
  
|Nom d'attribut|Type de données|Obligatoire|Valeur par défaut|Description|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Nom|String|Oui|N/A|Identificateur/nom de la fonction|  
|ReturnType|String|Non|Void|Type de retour EDM de la fonction|  
|Aggregate|Boolean|Non|False|True si la fonction est une fonction d'agrégation|  
|BuiltIn|Boolean|Non|True|True si la fonction est intégrée à la banque de données|  
|StoreFunctionName|String|Non|\<Name>|Nom de fonction dans la banque de données.  Permet un niveau de redirection de noms de fonction.|  
|NiladicFunction|Boolean|Non|False|True si la fonction ne requiert pas de paramètres et est appelée sans paramètre|  
|ParameterType<br /><br /> Sémantique|ParameterSemantics|Non|AllowImplicit<br /><br /> Conversion|Choix de la façon dont le pipeline de requête doit gérer la substitution de type de paramètre :<br /><br /> -   ExactMatchOnly<br />-   AllowImplicitPromotion<br />-   AllowImplicitConversion|  
  
 **Nœud Paramètres**  
  
 Chaque fonction a une collection d’un ou plusieurs nœuds de paramètre.  
  
|Nom d'attribut|Type de données|Obligatoire|Valeur par défaut|Description|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Nom|String|Oui|N/A|Identificateur/nom du paramètre.|  
|Type|String|Oui|N/A|Type EDM du paramètre.|  
|Mode|Paramètre<br /><br /> Direction|Oui|N/A|Direction de paramètre :<br /><br /> -   in<br />-out<br />-   inout|  
  
##### <a name="namespace-attribute"></a>Attribut Namespace  
 Chaque fournisseur de banque de données doit définir un espace de noms ou un groupe d'espaces de noms pour les informations définies dans le manifeste. Cet espace de noms peut être utilisé dans les requêtes Entity SQL pour résoudre des noms de fonctions et de types. Par exemple : Biais. Cet espace de noms doit être différent de l'espace de noms canonique, EDM, défini par les Services d'entités pour les fonctions standard à prendre en charge par les requêtes Entity SQL.  
  
## <a name="see-also"></a>Voir aussi

- [Écriture d’un fournisseur de données Entity Framework](writing-an-ef-data-provider.md)
