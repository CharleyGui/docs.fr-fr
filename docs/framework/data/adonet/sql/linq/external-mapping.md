---
title: Mappage externe
ms.date: 03/30/2017
ms.assetid: 076606b8-d889-4ba0-b5da-ae577b146f23
ms.openlocfilehash: 79427cde0784746480e851cf1be56c8bce854919
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161384"
---
# <a name="external-mapping"></a>Mappage externe

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prend en charge le *mappage externe*, un processus par lequel vous utilisez un fichier XML distinct pour spécifier le mappage entre le modèle de données de la base de données et votre modèle objet. Les avantages de l'utilisation d'un fichier de mappage externe sont notamment les suivants :  
  
- Vous pouvez conserver votre code de mappage en dehors de votre code d'application. Cette méthode permet de réduire l'encombrement dans votre code d'application.  
  
- Vous pouvez traiter un fichier de mappage externe un peu comme un fichier de configuration. Par exemple, vous pouvez modifier la manière dont votre application se comporte après l'envoi des binaires par la simple permutation du fichier binaire externe.  
  
## <a name="requirements"></a>Spécifications  

 Le fichier de mappage doit être un fichier XML et le fichier doit être validé par rapport à un [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fichier de définition de schéma (. xsd).  
  
 Les règles suivantes s’appliquent :  
  
- Le fichier de mappage doit être un fichier XML.  
  
- Le fichier de mappage XML doit être valide par rapport au fichier de définition de schéma XML. Pour plus d’informations, consultez [Comment : valider dbml et les fichiers de mappage externes](how-to-validate-dbml-and-external-mapping-files.md).  
  
- Le mappage externe substitue le mappage basé sur les attributs. En d'autres termes, lorsque vous utilisez une source de mappage externe pour créer un <xref:System.Data.Linq.DataContext>, le <xref:System.Data.Linq.DataContext> ignore tous les attributs de mappage que vous avez créés sur les classes. Ce comportement est vrai si la classe est incluse dans le fichier de mappage externe.  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ne prend pas en charge l'utilisation hybride des deux approches de mappage (basé sur les attributs et externe).  
  
## <a name="xml-schema-definition-file"></a>Fichier de définition de schéma XML  

 Le mappage externe dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] doit être valide par rapport à la définition de schéma XML suivante.  
  
 Ce fichier de définition de schéma est différent du fichier de définition de schéma utilisé pour valider un fichier DBML. Pour plus d’informations, consultez [génération de code dans LINQ to SQL](code-generation-in-linq-to-sql.md)).  
  
> [!NOTE]
> Les utilisateurs de Visual Studio trouveront également ce fichier XSD dans la boîte de dialogue schémas XML en tant que « LinqToSqlMapping. xsd ». Pour utiliser correctement ce fichier pour valider un fichier de mappage externe, consultez [Comment : valider dbml et les fichiers de mappage externes](how-to-validate-dbml-and-external-mapping-files.md).  
  
```xml  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://schemas.microsoft.com/linqtosql/mapping/2007" xmlns="http://schemas.microsoft.com/linqtosql/mapping/2007"  
elementFormDefault="qualified" >  
  <xs:element name="Database" type="Database" />  
  <xs:complexType name="Database">  
    <xs:sequence>  
      <xs:element name="Table" type="Table" minOccurs="0" maxOccurs="unbounded" />  
      <xs:element name="Function" type="Function" minOccurs="0" maxOccurs="unbounded" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Provider" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Table">  
    <xs:sequence>  
      <xs:element name="Type" type="Type" minOccurs="1" maxOccurs="1" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Type">  
    <xs:sequence>  
      <xs:choice minOccurs="0" maxOccurs="unbounded">  
        <xs:element name="Column" type="Column" minOccurs="0" maxOccurs="unbounded" />  
        <xs:element name="Association" type="Association" minOccurs="0" maxOccurs="unbounded" />  
      </xs:choice>  
      <xs:element name="Type" type="Type" minOccurs="0" maxOccurs="unbounded" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="InheritanceCode" type="xs:string" use="optional" />  
    <xs:attribute name="IsInheritanceDefault" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Column">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="required" />  
    <xs:attribute name="Storage" type="xs:string" use="optional" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
    <xs:attribute name="IsPrimaryKey" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsDbGenerated" type="xs:boolean" use="optional" />  
    <xs:attribute name="CanBeNull" type="xs:boolean" use="optional" />  
    <xs:attribute name="UpdateCheck" type="UpdateCheck" use="optional" />  
    <xs:attribute name="IsDiscriminator" type="xs:boolean" use="optional" />  
    <xs:attribute name="Expression" type="xs:string" use="optional" />  
    <xs:attribute name="IsVersion" type="xs:boolean" use="optional" />  
    <xs:attribute name="AutoSync" type="AutoSync" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Association">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="required" />  
    <xs:attribute name="Storage" type="xs:string" use="optional" />  
    <xs:attribute name="ThisKey" type="xs:string" use="optional" />  
    <xs:attribute name="OtherKey" type="xs:string" use="optional" />  
    <xs:attribute name="IsForeignKey" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsUnique" type="xs:boolean" use="optional" />  
    <xs:attribute name="DeleteRule" type="xs:string" use="optional" />  
    <xs:attribute name="DeleteOnNull" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Function">  
    <xs:sequence>  
      <xs:element name="Parameter" type="Parameter" minOccurs="0" maxOccurs="unbounded" />  
      <xs:choice>  
        <xs:element name="ElementType" type="Type" minOccurs="0" maxOccurs="unbounded" />  
        <xs:element name="Return" type="Return" minOccurs="0" maxOccurs="1" />  
      </xs:choice>  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Method" type="xs:string" use="required" />  
    <xs:attribute name="IsComposable" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Parameter">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Parameter" type="xs:string" use="required" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
    <xs:attribute name="Direction" type="ParameterDirection" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Return">  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:simpleType name="UpdateCheck">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Always" />  
      <xs:enumeration value="Never" />  
      <xs:enumeration value="WhenChanged" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="ParameterDirection">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="In" />  
      <xs:enumeration value="Out" />  
      <xs:enumeration value="InOut" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="AutoSync">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Never" />  
      <xs:enumeration value="OnInsert" />  
      <xs:enumeration value="OnUpdate" />  
      <xs:enumeration value="Always" />  
      <xs:enumeration value="Default" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Génération de code dans LINQ to SQL](code-generation-in-linq-to-sql.md)
- [Référence](reference.md)
- [Procédure : Générer le modèle objet sous forme de fichier externe](how-to-generate-the-object-model-as-an-external-file.md)
