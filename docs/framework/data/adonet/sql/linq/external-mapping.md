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
# <a name="external-mapping"></a><span data-ttu-id="9032a-102">Mappage externe</span><span class="sxs-lookup"><span data-stu-id="9032a-102">External Mapping</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="9032a-103">prend en charge le *mappage externe*, un processus par lequel vous utilisez un fichier XML distinct pour spécifier le mappage entre le modèle de données de la base de données et votre modèle objet.</span><span class="sxs-lookup"><span data-stu-id="9032a-103">supports *external mapping*, a process by which you use a separate XML file to specify mapping between the data model of the database and your object model.</span></span> <span data-ttu-id="9032a-104">Les avantages de l'utilisation d'un fichier de mappage externe sont notamment les suivants :</span><span class="sxs-lookup"><span data-stu-id="9032a-104">Advantages of using an external mapping file include the following:</span></span>  
  
- <span data-ttu-id="9032a-105">Vous pouvez conserver votre code de mappage en dehors de votre code d'application.</span><span class="sxs-lookup"><span data-stu-id="9032a-105">You can keep your mapping code out of your application code.</span></span> <span data-ttu-id="9032a-106">Cette méthode permet de réduire l'encombrement dans votre code d'application.</span><span class="sxs-lookup"><span data-stu-id="9032a-106">This approach reduces clutter in your application code.</span></span>  
  
- <span data-ttu-id="9032a-107">Vous pouvez traiter un fichier de mappage externe un peu comme un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="9032a-107">You can treat an external mapping file something like a configuration file.</span></span> <span data-ttu-id="9032a-108">Par exemple, vous pouvez modifier la manière dont votre application se comporte après l'envoi des binaires par la simple permutation du fichier binaire externe.</span><span class="sxs-lookup"><span data-stu-id="9032a-108">For example, you can update how your application behaves after shipping the binaries by just swapping out the external mapping file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9032a-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9032a-109">Requirements</span></span>  

 <span data-ttu-id="9032a-110">Le fichier de mappage doit être un fichier XML et le fichier doit être validé par rapport à un [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fichier de définition de schéma (. xsd).</span><span class="sxs-lookup"><span data-stu-id="9032a-110">The mapping file must be an XML file, and the file must validate against a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] schema definition (.xsd) file.</span></span>  
  
 <span data-ttu-id="9032a-111">Les règles suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="9032a-111">The following rules apply:</span></span>  
  
- <span data-ttu-id="9032a-112">Le fichier de mappage doit être un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="9032a-112">The mapping file must be an XML file.</span></span>  
  
- <span data-ttu-id="9032a-113">Le fichier de mappage XML doit être valide par rapport au fichier de définition de schéma XML.</span><span class="sxs-lookup"><span data-stu-id="9032a-113">The XML mapping file must be valid against the XML schema definition file.</span></span> <span data-ttu-id="9032a-114">Pour plus d’informations, consultez [Comment : valider dbml et les fichiers de mappage externes](how-to-validate-dbml-and-external-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="9032a-114">For more information, see [How to: Validate DBML and External Mapping Files](how-to-validate-dbml-and-external-mapping-files.md).</span></span>  
  
- <span data-ttu-id="9032a-115">Le mappage externe substitue le mappage basé sur les attributs.</span><span class="sxs-lookup"><span data-stu-id="9032a-115">External mapping overrides attribute-based mapping.</span></span> <span data-ttu-id="9032a-116">En d'autres termes, lorsque vous utilisez une source de mappage externe pour créer un <xref:System.Data.Linq.DataContext>, le <xref:System.Data.Linq.DataContext> ignore tous les attributs de mappage que vous avez créés sur les classes.</span><span class="sxs-lookup"><span data-stu-id="9032a-116">In other words, when you use an external mapping source to create a <xref:System.Data.Linq.DataContext>, the <xref:System.Data.Linq.DataContext> ignores all mapping attributes you have created on classes.</span></span> <span data-ttu-id="9032a-117">Ce comportement est vrai si la classe est incluse dans le fichier de mappage externe.</span><span class="sxs-lookup"><span data-stu-id="9032a-117">This behavior is true whether the class is included in the external mapping file.</span></span>  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="9032a-118">ne prend pas en charge l'utilisation hybride des deux approches de mappage (basé sur les attributs et externe).</span><span class="sxs-lookup"><span data-stu-id="9032a-118">does not support the hybrid use of the two mapping approaches (attribute-based and external).</span></span>  
  
## <a name="xml-schema-definition-file"></a><span data-ttu-id="9032a-119">Fichier de définition de schéma XML</span><span class="sxs-lookup"><span data-stu-id="9032a-119">XML Schema Definition File</span></span>  

 <span data-ttu-id="9032a-120">Le mappage externe dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] doit être valide par rapport à la définition de schéma XML suivante.</span><span class="sxs-lookup"><span data-stu-id="9032a-120">External mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be valid against the following XML schema definition.</span></span>  
  
 <span data-ttu-id="9032a-121">Ce fichier de définition de schéma est différent du fichier de définition de schéma utilisé pour valider un fichier DBML.</span><span class="sxs-lookup"><span data-stu-id="9032a-121">Distinguish this schema definition file from the schema definition file that is used to validate a DBML file.</span></span> <span data-ttu-id="9032a-122">Pour plus d’informations, consultez [génération de code dans LINQ to SQL](code-generation-in-linq-to-sql.md)).</span><span class="sxs-lookup"><span data-stu-id="9032a-122">For more information, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9032a-123">Les utilisateurs de Visual Studio trouveront également ce fichier XSD dans la boîte de dialogue schémas XML en tant que « LinqToSqlMapping. xsd ».</span><span class="sxs-lookup"><span data-stu-id="9032a-123">Visual Studio users will also find this XSD file in the XML Schemas dialog box as "LinqToSqlMapping.xsd".</span></span> <span data-ttu-id="9032a-124">Pour utiliser correctement ce fichier pour valider un fichier de mappage externe, consultez [Comment : valider dbml et les fichiers de mappage externes](how-to-validate-dbml-and-external-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="9032a-124">To use this file correctly for validating an external mapping file, see [How to: Validate DBML and External Mapping Files](how-to-validate-dbml-and-external-mapping-files.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9032a-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9032a-125">See also</span></span>

- [<span data-ttu-id="9032a-126">Génération de code dans LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="9032a-126">Code Generation in LINQ to SQL</span></span>](code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="9032a-127">Référence</span><span class="sxs-lookup"><span data-stu-id="9032a-127">Reference</span></span>](reference.md)
- [<span data-ttu-id="9032a-128">Procédure : Générer le modèle objet sous forme de fichier externe</span><span class="sxs-lookup"><span data-stu-id="9032a-128">How to: Generate the Object Model as an External File</span></span>](how-to-generate-the-object-model-as-an-external-file.md)
