---
title: Comparaison des services Web ASP.NET et de WCF du point de vue du développement
ms.date: 03/30/2017
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
ms.openlocfilehash: c5a2145a6d7b631a666df94eb0c1fc53cbc3c55f
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202262"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a><span data-ttu-id="f8324-102">Comparaison des services Web ASP.NET et de WCF du point de vue du développement</span><span class="sxs-lookup"><span data-stu-id="f8324-102">Comparing ASP.NET Web Services to WCF Based on Development</span></span>

<span data-ttu-id="f8324-103">Windows Communication Foundation (WCF) dispose d’une option de mode de compatibilité ASP.NET pour permettre aux applications WCF d’être programmées et configurées comme les services Web ASP.NET, et de reproduire leur comportement.</span><span class="sxs-lookup"><span data-stu-id="f8324-103">Windows Communication Foundation (WCF) has an ASP.NET compatibility mode option to enable WCF applications to be programmed and configured like ASP.NET Web services, and mimic their behavior.</span></span> <span data-ttu-id="f8324-104">Les sections suivantes comparent les services Web ASP.NET et WCF en fonction de ce qui est requis pour développer des applications à l’aide de ces deux technologies.</span><span class="sxs-lookup"><span data-stu-id="f8324-104">The following sections compare ASP.NET Web services and WCF based on what is required to develop applications using both technologies.</span></span>

## <a name="data-representation"></a><span data-ttu-id="f8324-105">Représentation des données</span><span class="sxs-lookup"><span data-stu-id="f8324-105">Data Representation</span></span>

<span data-ttu-id="f8324-106">Le développement d'un service Web avec ASP.NET commence en général par la définition de tous les types de données complexes que le service doit utiliser.</span><span class="sxs-lookup"><span data-stu-id="f8324-106">The development of a Web service with ASP.NET typically begins with defining any complex data types the service is to use.</span></span> <span data-ttu-id="f8324-107">ASP.NET repose sur le <xref:System.Xml.Serialization.XmlSerializer> pour traduire en XML des données représentées par les types .NET Framework pour la transmission en direction ou depuis un service et pour traduire des données reçues comme XML en objets .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f8324-107">ASP.NET relies on the <xref:System.Xml.Serialization.XmlSerializer> to translate data represented by .NET Framework types to XML for transmission to or from a service and to translate data received as XML into .NET Framework objects.</span></span> <span data-ttu-id="f8324-108">La définition des types de données complexes à utiliser par un service ASP.NET nécessite de définir les classes .NET Framework que le <xref:System.Xml.Serialization.XmlSerializer> peut sérialiser depuis le XML ou vers celui-ci.</span><span class="sxs-lookup"><span data-stu-id="f8324-108">Defining the complex data types that an ASP.NET service is to use requires the definition of .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML.</span></span> <span data-ttu-id="f8324-109">Ces classes peuvent être écrites manuellement ou générées à partir des définitions des types dans le schéma XML à l'aide de l'utilitaire de prise en charge des types de données/schémas XML de ligne de commande, xsd.exe.</span><span class="sxs-lookup"><span data-stu-id="f8324-109">Such classes can be written manually, or generated from definitions of the types in XML Schema using the command-line XML Schemas/Data Types Support Utility, xsd.exe.</span></span>

<span data-ttu-id="f8324-110">Les éléments suivants répertorient les problèmes clés à connaître lors de la définition des classes .NET Framework que le <xref:System.Xml.Serialization.XmlSerializer> peut sérialiser en XML ou depuis celui-ci :</span><span class="sxs-lookup"><span data-stu-id="f8324-110">The following is a list of key issues to know when defining .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML:</span></span>

- <span data-ttu-id="f8324-111">Seuls les champs et les propriétés publics des objets .NET Framework sont traduits en XML.</span><span class="sxs-lookup"><span data-stu-id="f8324-111">Only the public fields and properties of .NET Framework objects are translated into XML.</span></span>

- <span data-ttu-id="f8324-112">Les instances de classes de collection peuvent être sérialisées en XML uniquement si les classes implémentent l’interface <xref:System.Collections.IEnumerable> ou <xref:System.Collections.ICollection>.</span><span class="sxs-lookup"><span data-stu-id="f8324-112">Instances of collection classes can be serialized into XML only if the classes implement either the <xref:System.Collections.IEnumerable> or <xref:System.Collections.ICollection> interface.</span></span>

- <span data-ttu-id="f8324-113">Les classes qui implémentent l'interface <xref:System.Collections.IDictionary>, telles que <xref:System.Collections.Hashtable>, ne peuvent pas être sérialisées en XML.</span><span class="sxs-lookup"><span data-stu-id="f8324-113">Classes that implement the <xref:System.Collections.IDictionary> interface, such as <xref:System.Collections.Hashtable>, cannot be serialized into XML.</span></span>

- <span data-ttu-id="f8324-114">Le grand nombre de types d'attributs dans l'espace de noms <xref:System.Xml.Serialization> peut être ajouté à une classe .NET Framework et à ses membres pour contrôler le mode de représentation en XML des instances de la classe.</span><span class="sxs-lookup"><span data-stu-id="f8324-114">The great many attribute types in the <xref:System.Xml.Serialization> namespace can be added to a .NET Framework class and its members to control how instances of the class are represented in XML.</span></span>

<span data-ttu-id="f8324-115">Le développement d’applications WCF commence généralement par la définition de types complexes.</span><span class="sxs-lookup"><span data-stu-id="f8324-115">WCF application development usually also begins with the definition of complex types.</span></span> <span data-ttu-id="f8324-116">WCF peut être configuré pour utiliser les mêmes types de .NET Framework que les services Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f8324-116">WCF can be made to use the same .NET Framework types as ASP.NET Web services.</span></span>

<span data-ttu-id="f8324-117">WCF <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> peuvent être ajoutés aux types de .NET Framework pour indiquer que les instances du type doivent être sérialisées en XML, et quels champs ou propriétés particuliers du type doivent être sérialisés, comme indiqué dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="f8324-117">The WCF<xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> can be added to .NET Framework types to indicate that instances of the type are to be serialized into XML, and which particular fields or properties of the type are to be serialized, as shown in the following sample code.</span></span>

```csharp
//Example One:
[DataContract]
public class LineItem
{
    [DataMember]
    public string ItemNumber;
    [DataMember]
    public decimal Quantity;
    [DataMember]
    public decimal UnitPrice;
}

//Example Two:
public class LineItem
{
    [DataMember]
    private string itemNumber;
    [DataMember]
    private decimal quantity;
    [DataMember]
    private decimal unitPrice;

    public string ItemNumber
    {
      get
      {
          return this.itemNumber;
      }

      set
      {
          this.itemNumber = value;
      }
    }

    public decimal Quantity
    {
        get
        {
            return this.quantity;
        }

        set
        {
            this.quantity = value;
        }
    }

    public decimal UnitPrice
    {
      get
      {
          return this.unitPrice;
      }

      set
      {
          this.unitPrice = value;
      }
    }
}

//Example Three:
public class LineItem
{
     private string itemNumber;
     private decimal quantity;
     private decimal unitPrice;

     [DataMember]
     public string ItemNumber
     {
       get
       {
          return this.itemNumber;
       }

       set
       {
           this.itemNumber = value;
       }
     }

     [DataMember]
     public decimal Quantity
     {
          get
          {
              return this.quantity;
          }

          set
          {
             this.quantity = value;
          }
     }

     [DataMember]
     public decimal UnitPrice
     {
          get
          {
              return this.unitPrice;
          }

          set
          {
              this.unitPrice = value;
          }
     }
}
```

<span data-ttu-id="f8324-118"><xref:System.Runtime.Serialization.DataContractAttribute> signifie que zéro ou plusieurs des champs ou des propriétés d'un type vont être sérialisés, alors que <xref:System.Runtime.Serialization.DataMemberAttribute> indique qu'une propriété ou un champ particulier va être sérialisé.</span><span class="sxs-lookup"><span data-stu-id="f8324-118">The <xref:System.Runtime.Serialization.DataContractAttribute> signifies that zero or more of a type’s fields or properties are to be serialized, while the <xref:System.Runtime.Serialization.DataMemberAttribute> indicates that a particular field or property is to be serialized.</span></span> <span data-ttu-id="f8324-119"><xref:System.Runtime.Serialization.DataContractAttribute> peut être appliqué à une classe ou à une structure.</span><span class="sxs-lookup"><span data-stu-id="f8324-119">The <xref:System.Runtime.Serialization.DataContractAttribute> can be applied to a class or structure.</span></span> <span data-ttu-id="f8324-120">Le <xref:System.Runtime.Serialization.DataMemberAttribute> peut être appliqué à un champ ou à une propriété, et les champs et les propriétés auxquels l'attribut est appliqué peuvent être publics ou privés.</span><span class="sxs-lookup"><span data-stu-id="f8324-120">The <xref:System.Runtime.Serialization.DataMemberAttribute> can be applied to a field or a property, and the fields and properties to which the attribute is applied can be either public or private.</span></span> <span data-ttu-id="f8324-121">Les instances de types qui ont <xref:System.Runtime.Serialization.DataContractAttribute> été appliquées à elles sont appelées contrats de données dans WCF.</span><span class="sxs-lookup"><span data-stu-id="f8324-121">Instances of types that have the <xref:System.Runtime.Serialization.DataContractAttribute> applied to them are referred to as data contracts in WCF.</span></span> <span data-ttu-id="f8324-122">Elles sont sérialisées en XML à l'aide de <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f8324-122">They are serialized into XML using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

<span data-ttu-id="f8324-123">Les éléments suivants répertorient une liste des différences principales entre l'utilisation de <xref:System.Runtime.Serialization.DataContractSerializer> et celle de <xref:System.Xml.Serialization.XmlSerializer> et les divers attributs de l'espace de noms <xref:System.Xml.Serialization>.</span><span class="sxs-lookup"><span data-stu-id="f8324-123">The following is a list of the important differences between using the <xref:System.Runtime.Serialization.DataContractSerializer> and using the <xref:System.Xml.Serialization.XmlSerializer> and the various attributes of the <xref:System.Xml.Serialization> namespace.</span></span>

- <span data-ttu-id="f8324-124">Le <xref:System.Xml.Serialization.XmlSerializer> et les attributs de l'espace de noms <xref:System.Xml.Serialization> sont conçus pour vous permettre de mapper des types .NET Framework à des types valides définis dans le schéma XML, ils fournissent ainsi un contrôle très précis sur la manière de représenter un type en XML.</span><span class="sxs-lookup"><span data-stu-id="f8324-124">The <xref:System.Xml.Serialization.XmlSerializer> and the attributes of the <xref:System.Xml.Serialization> namespace are designed to allow you to map .NET Framework types to any valid type defined in XML Schema, and so they provide for very precise control over how a type is represented in XML.</span></span> <span data-ttu-id="f8324-125">Les <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> fournissent très peu de contrôle sur la manière de représenter un type en XML.</span><span class="sxs-lookup"><span data-stu-id="f8324-125">The <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> provide very little control over how a type is represented in XML.</span></span> <span data-ttu-id="f8324-126">Vous pouvez spécifier uniquement les espaces de noms et les noms utilisés pour représenter le type et ses champs ou propriétés dans le XML, et la séquence dans laquelle les champs et propriétés apparaissent dans le XML :</span><span class="sxs-lookup"><span data-stu-id="f8324-126">You can only specify the namespaces and names used to represent the type and its fields or properties in the XML, and the sequence in which the fields and properties appear in the XML:</span></span>

  ```csharp
  [DataContract(
  Namespace="urn:Contoso:2006:January:29",
  Name="LineItem")]
  public class LineItem
  {
        [DataMember(Name="ItemNumber",IsRequired=true,Order=0)]
        public string itemNumber;
        [DataMember(Name="Quantity",IsRequired=false,Order = 1)]
        public decimal quantity;
        [DataMember(Name="Price",IsRequired=false,Order = 2)]
        public decimal unitPrice;
  }
  ```

  <span data-ttu-id="f8324-127">Tout ce qui concerne la structure du XML utilisé pour représenter le type .NET est déterminé par le <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f8324-127">Everything else about the structure of the XML used to represent the .NET type is determined by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

- <span data-ttu-id="f8324-128">En ne permettant qu'un contrôle limité sur la manière de représenter un type en XML, le processus de sérialisation devient très prévisible pour le <xref:System.Runtime.Serialization.DataContractSerializer>, et, par conséquent, plus facile à optimiser.</span><span class="sxs-lookup"><span data-stu-id="f8324-128">By not permitting much control over how a type is to be represented in XML, the serialization process becomes highly predictable for the <xref:System.Runtime.Serialization.DataContractSerializer>, and, thereby, easier to optimize.</span></span> <span data-ttu-id="f8324-129">Un avantage pratique de la conception de <xref:System.Runtime.Serialization.DataContractSerializer> est d'offrir de meilleures performances, une amélioration d'environ dix pour cent.</span><span class="sxs-lookup"><span data-stu-id="f8324-129">A practical benefit of the design of the <xref:System.Runtime.Serialization.DataContractSerializer> is better performance, approximately ten percent better performance.</span></span>

- <span data-ttu-id="f8324-130">Les attributs à utiliser avec le <xref:System.Xml.Serialization.XmlSerializer> n'indiquent pas quels champs ou propriétés du type sont sérialisés en XML, alors que le <xref:System.Runtime.Serialization.DataMemberAttribute> à utiliser avec le <xref:System.Runtime.Serialization.DataContractSerializer> indique explicitement les champs ou les propriétés sérialisées.</span><span class="sxs-lookup"><span data-stu-id="f8324-130">The attributes for use with the <xref:System.Xml.Serialization.XmlSerializer> do not indicate which fields or properties of the type are serialized into XML, whereas the <xref:System.Runtime.Serialization.DataMemberAttribute> for use with the <xref:System.Runtime.Serialization.DataContractSerializer> shows explicitly which fields or properties are serialized.</span></span> <span data-ttu-id="f8324-131">Par conséquent, les contrats de données sont des contrats explicites sur la structure des données qu'une application doit envoyer et recevoir.</span><span class="sxs-lookup"><span data-stu-id="f8324-131">Therefore, data contracts are explicit contracts about the structure of the data that an application is to send and receive.</span></span>

- <span data-ttu-id="f8324-132">Le <xref:System.Xml.Serialization.XmlSerializer> peut traduire uniquement les membres publics d’un objet .NET en XML, le <xref:System.Runtime.Serialization.DataContractSerializer> peut traduire les membres des objets en XML indépendamment des modificateurs d’accès de ces membres.</span><span class="sxs-lookup"><span data-stu-id="f8324-132">The <xref:System.Xml.Serialization.XmlSerializer> can only translate the public members of a .NET object into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> can translate the members of objects into XML regardless of the access modifiers of those members.</span></span>

- <span data-ttu-id="f8324-133">Étant donné qu'il peut sérialiser en XML les membres non publics des types, le <xref:System.Runtime.Serialization.DataContractSerializer> offre moins de restrictions sur la variété des types .NET qu'il peut sérialiser en XML.</span><span class="sxs-lookup"><span data-stu-id="f8324-133">As a consequence of being able to serialize the non-public members of types into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> has fewer restrictions on the variety of .NET types that it can serialize into XML.</span></span> <span data-ttu-id="f8324-134">En particulier, il peut traduire en XML des types tels que <xref:System.Collections.Hashtable> qui implémentent l'interface <xref:System.Collections.IDictionary>.</span><span class="sxs-lookup"><span data-stu-id="f8324-134">In particular, it can translate into XML types like <xref:System.Collections.Hashtable> that implement the <xref:System.Collections.IDictionary> interface.</span></span> <span data-ttu-id="f8324-135">Il est plus probable que <xref:System.Runtime.Serialization.DataContractSerializer> puisse sérialiser les instances d'un type .NET préexistant en XML sans avoir à modifier la définition du type ou à développer un wrapper qui lui sera destiné.</span><span class="sxs-lookup"><span data-stu-id="f8324-135">The <xref:System.Runtime.Serialization.DataContractSerializer> is much more likely to be able to serialize the instances of any pre-existing .NET type into XML without having to either modify the definition of the type or develop a wrapper for it.</span></span>

- <span data-ttu-id="f8324-136">Une autre conséquence de la capacité de <xref:System.Runtime.Serialization.DataContractSerializer> d'accéder aux membres non publics d'un type est qu'il requiert une confiance totale, ce qui n'est pas le cas de <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f8324-136">Another consequence of the <xref:System.Runtime.Serialization.DataContractSerializer> being able to access the non-public members of a type is that it requires full trust, whereas the <xref:System.Xml.Serialization.XmlSerializer> does not.</span></span> <span data-ttu-id="f8324-137">L’autorisation d’accès au code de confiance totale donne un accès complet à toutes les ressources sur un ordinateur accessibles à l’aide des informations d’identification sous lesquelles le code s’exécute.</span><span class="sxs-lookup"><span data-stu-id="f8324-137">The Full Trust code access permission gives complete access to all resources on a machine that can be accessed using the credentials under which the code is executing.</span></span> <span data-ttu-id="f8324-138">Cette option doit être utilisée avec précaution, car le code d’un niveau de confiance totale accède à toutes les ressources de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f8324-138">This option should be used with care as fully trusted code accesses all resources on your machine.</span></span>

- <span data-ttu-id="f8324-139">Le <xref:System.Runtime.Serialization.DataContractSerializer> incorpore une prise en charge du suivi des versions :</span><span class="sxs-lookup"><span data-stu-id="f8324-139">The <xref:System.Runtime.Serialization.DataContractSerializer> incorporates some support for versioning:</span></span>

  - <span data-ttu-id="f8324-140">Le <xref:System.Runtime.Serialization.DataMemberAttribute> a une propriété <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> qui peut prendre une valeur false pour les membres ajoutés aux nouvelles versions d'un contrat de données qui ne figuraient pas dans les versions antérieures, ce qui permet aux applications avec la version plus récente du contrat de traiter des versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="f8324-140">The <xref:System.Runtime.Serialization.DataMemberAttribute> has an <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property that can be assigned a value of false for members that are added to new versions of a data contract that were not present in earlier versions, thereby allowing applications with the newer version of the contract to be able to process earlier versions.</span></span>

  - <span data-ttu-id="f8324-141">En implémentant l'interface <xref:System.Runtime.Serialization.IExtensibleDataObject> par le contrat de données, il est possible pour le <xref:System.Runtime.Serialization.DataContractSerializer> de passer des membres définis dans des versions plus récentes d'un contrat de données par l'intermédiaire d'applications avec des versions antérieures du contrat.</span><span class="sxs-lookup"><span data-stu-id="f8324-141">By having a data contract implement the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface, one can allow the <xref:System.Runtime.Serialization.DataContractSerializer> to pass members defined in newer versions of a data contract through applications with earlier versions of the contract.</span></span>

<span data-ttu-id="f8324-142">En dépit de toutes ces différences, le XML dans lequel <xref:System.Xml.Serialization.XmlSerializer> sérialise un type par défaut est sémantiquement identique au XML dans lequel <xref:System.Runtime.Serialization.DataContractSerializer> sérialise un type, à condition que l'espace de noms du XML soit défini explicitement.</span><span class="sxs-lookup"><span data-stu-id="f8324-142">Despite all of the differences, the XML into which the <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="f8324-143">La classe suivante, qui a des attributs à utiliser avec les deux sérialiseurs, est traduite en XML sémantiquement identique par le <xref:System.Xml.Serialization.XmlSerializer> et par le <xref:System.Runtime.Serialization.DataContractAttribute> :</span><span class="sxs-lookup"><span data-stu-id="f8324-143">The following class, which has attributes for use with both of the serializers, is translated into semantically identical XML by the <xref:System.Xml.Serialization.XmlSerializer> and by the <xref:System.Runtime.Serialization.DataContractAttribute>:</span></span>

```csharp
[Serializable]
[XmlRoot(Namespace="urn:Contoso:2006:January:29")]
[DataContract(Namespace="urn:Contoso:2006:January:29")]
public class LineItem
{
     [DataMember]
     public string ItemNumber;
     [DataMember]
     public decimal Quantity;
     [DataMember]
     public decimal UnitPrice;
}
```

<span data-ttu-id="f8324-144">Le kit de développement logiciel (SDK) Windows comprend un outil en ligne de commande appelé outil de l' [utilitaire de métadonnées ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f8324-144">The Windows software development kit (SDK) includes a command-line tool called the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="f8324-145">À l’instar de l’outil Xsd. exe utilisé avec les services Web ASP.NET, Svcutil. exe peut générer des définitions de types de données .NET à partir d’un schéma XML.</span><span class="sxs-lookup"><span data-stu-id="f8324-145">Like the xsd.exe tool used with ASP.NET Web services, Svcutil.exe can generate definitions of .NET data types from XML Schema.</span></span> <span data-ttu-id="f8324-146">Les types sont des contrats de données si le <xref:System.Runtime.Serialization.DataContractSerializer> peut émettre du XML au format défini par le schéma XML ; sinon, ils sont destinés à être sérialisés à l'aide du <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f8324-146">The types are data contracts if the <xref:System.Runtime.Serialization.DataContractSerializer> can emit XML in the format defined by the XML Schema; otherwise, they are intended for serialization using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="f8324-147">Svcutil. exe peut également générer un schéma XML à partir de contrats de données à l’aide de son `dataContractOnly` commutateur.</span><span class="sxs-lookup"><span data-stu-id="f8324-147">Svcutil.exe can also generate an XML schema from data contracts by using its `dataContractOnly` switch.</span></span>

> [!NOTE]
> <span data-ttu-id="f8324-148">Bien que les services Web ASP.NET utilisent le <xref:System.Xml.Serialization.XmlSerializer> , et le mode de compatibilité ASP.net WCF fait que les services WCF imitent le comportement des services web ASP.net, l’option de compatibilité ASP.net ne limite pas l’utilisation de <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="f8324-148">Although ASP.NET Web services use the <xref:System.Xml.Serialization.XmlSerializer>, and WCF ASP.NET compatibility mode makes WCF services mimic the behavior of ASP.NET Web services, the ASP.NET compatibility option does not restrict one to using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="f8324-149">Il est toujours possible d'utiliser le <xref:System.Runtime.Serialization.DataContractSerializer> avec des services qui s'exécutent en mode de compatibilité ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f8324-149">One can still use the <xref:System.Runtime.Serialization.DataContractSerializer> with services running in the ASP.NET compatibility mode.</span></span>

## <a name="service-development"></a><span data-ttu-id="f8324-150">Développement des services</span><span class="sxs-lookup"><span data-stu-id="f8324-150">Service Development</span></span>

<span data-ttu-id="f8324-151">Pour développer un service à l'aide d'ASP.NET, il est d'usage d'ajouter l'attribut <xref:System.Web.Services.WebService> à une classe, et le <xref:System.Web.Services.WebMethodAttribute> à une des méthodes de cette classe qui servent d'opérations du service :</span><span class="sxs-lookup"><span data-stu-id="f8324-151">To develop a service using ASP.NET, it has been customary to add the <xref:System.Web.Services.WebService> attribute to a class, and the <xref:System.Web.Services.WebMethodAttribute> to any of that class’ methods that are to be operations of the service:</span></span>

```csharp
[WebService]
public class Service : T:System.Web.Services.WebService
{
    [WebMethod]
    public string Echo(string input)
    {
       return input;
    }
}
```

<span data-ttu-id="f8324-152">ASP.NET 2.0 introduit la possibilité d'ajouter l'attribut <xref:System.Web.Services.WebService> et <xref:System.Web.Services.WebMethodAttribute> à une interface plutôt qu'à une classe, et d'écrire une classe pour implémenter l'interface :</span><span class="sxs-lookup"><span data-stu-id="f8324-152">ASP.NET 2.0 introduced the option of adding the attribute <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> to an interface rather than to a class, and writing a class to implement the interface:</span></span>

```csharp
[WebService]
public interface IEcho
{
    [WebMethod]
    string Echo(string input);
}

public class Service : IEcho
{

   public string Echo(string input)
   {
        return input;
    }
}
```

<span data-ttu-id="f8324-153">L'utilisation de cette option est recommandée, car l'interface avec l'attribut <xref:System.Web.Services.WebService> représente un contrat pour les opérations effectuées par le service qui peuvent être réutilisées avec différentes classes qui implémentent éventuellement ce même contrat de différentes façons.</span><span class="sxs-lookup"><span data-stu-id="f8324-153">Using this option is to be preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>

<span data-ttu-id="f8324-154">Un service WCF est fourni en définissant un ou plusieurs points de terminaison WCF.</span><span class="sxs-lookup"><span data-stu-id="f8324-154">A WCF service is provided by defining one or more WCF endpoints.</span></span> <span data-ttu-id="f8324-155">Un point de terminaison est défini par une adresse, une liaison et un contrat de service.</span><span class="sxs-lookup"><span data-stu-id="f8324-155">An endpoint is defined by an address, a binding and a service contract.</span></span> <span data-ttu-id="f8324-156">L'adresse définit l'emplacement du service.</span><span class="sxs-lookup"><span data-stu-id="f8324-156">The address defines where the service is located.</span></span> <span data-ttu-id="f8324-157">La liaison spécifie le mode de communication avec le service.</span><span class="sxs-lookup"><span data-stu-id="f8324-157">The binding specifies how to communicate with the service.</span></span> <span data-ttu-id="f8324-158">Le contrat de service définit les opérations que le service peut effectuer.</span><span class="sxs-lookup"><span data-stu-id="f8324-158">The service contract defines the operations that the service can perform.</span></span>

<span data-ttu-id="f8324-159">Le contrat de service est défini habituellement en premier en ajoutant <xref:System.ServiceModel.ServiceContractAttribute> et <xref:System.ServiceModel.OperationContractAttribute> à une interface :</span><span class="sxs-lookup"><span data-stu-id="f8324-159">The service contract is usually defined first, by adding <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> to an interface:</span></span>

```csharp
[ServiceContract]
public interface IEcho
{
     [OperationContract]
     string Echo(string input);
}
```

<span data-ttu-id="f8324-160"><xref:System.ServiceModel.ServiceContractAttribute>Spécifie que l’interface définit un contrat de service WCF et le <xref:System.ServiceModel.OperationContractAttribute> indique, le cas échéant, les méthodes de l’interface qui définissent les opérations du contrat de service.</span><span class="sxs-lookup"><span data-stu-id="f8324-160">The <xref:System.ServiceModel.ServiceContractAttribute> specifies that the interface defines a WCF service contract, and the <xref:System.ServiceModel.OperationContractAttribute> indicates which, if any, of the methods of the interface define operations of the service contract.</span></span>

<span data-ttu-id="f8324-161">Une fois qu'un contrat de service a été défini, il est implémenté dans une classe, en implémentant par la classe l'interface qui définit le contrat de service :</span><span class="sxs-lookup"><span data-stu-id="f8324-161">Once a service contract has been defined, it is implemented in a class, by having the class implement the interface by which the service contract is defined:</span></span>

```csharp
public class Service : IEcho
{
    public string Echo(string input)
    {
       return input;
    }
}
```

<span data-ttu-id="f8324-162">Une classe qui implémente un contrat de service est appelée type de service dans WCF.</span><span class="sxs-lookup"><span data-stu-id="f8324-162">A class that implements a service contract is referred to as a service type in WCF.</span></span>

<span data-ttu-id="f8324-163">L’étape suivante consiste à associer une adresse et une liaison à un type de service.</span><span class="sxs-lookup"><span data-stu-id="f8324-163">The next step is to associate an address and a binding with a service type.</span></span> <span data-ttu-id="f8324-164">Cela s’effectue généralement dans un fichier de configuration, soit en modifiant le fichier directement, soit à l’aide d’un éditeur de configuration fourni avec WCF.</span><span class="sxs-lookup"><span data-stu-id="f8324-164">That is typically done in a configuration file, either by editing the file directly, or by using a configuration editor provided with WCF.</span></span> <span data-ttu-id="f8324-165">Voici un exemple d'un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="f8324-165">Here is an example of a configuration file.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
     <system.serviceModel>
      <services>
      <service name="Service ">
       <endpoint
        address="EchoService"
        binding="basicHttpBinding"
        contract="IEchoService "/>
      </service>
      </services>
     </system.serviceModel>
</configuration>
```

<span data-ttu-id="f8324-166">La liaison spécifie le jeu de protocoles permettant de communiquer avec l’application.</span><span class="sxs-lookup"><span data-stu-id="f8324-166">The binding specifies the set of protocols for communicating with the application.</span></span> <span data-ttu-id="f8324-167">Le tableau suivant répertorie les liaisons fournies par le système qui représentent des options courantes.</span><span class="sxs-lookup"><span data-stu-id="f8324-167">The following table lists the system-provided bindings that represent common options.</span></span>

|<span data-ttu-id="f8324-168">Nom</span><span class="sxs-lookup"><span data-stu-id="f8324-168">Name</span></span>|<span data-ttu-id="f8324-169">Objectif</span><span class="sxs-lookup"><span data-stu-id="f8324-169">Purpose</span></span>|
|----------|-------------|
|<span data-ttu-id="f8324-170">BasicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="f8324-170">BasicHttpBinding</span></span>|<span data-ttu-id="f8324-171">Interopérabilité avec les services et les clients Web qui prennent en charge WS-BasicProfile 1.1 et Basic Security Profile 1.0.</span><span class="sxs-lookup"><span data-stu-id="f8324-171">Interoperability with Web services and clients supporting the WS-BasicProfile 1.1 and Basic Security Profile 1.0.</span></span>|
|<span data-ttu-id="f8324-172">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="f8324-172">WSHttpBinding</span></span>|<span data-ttu-id="f8324-173">Interopérabilité avec les services et clients Web qui prennent en charge les protocoles WS-\* sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="f8324-173">Interoperability with Web services and clients that support the WS-\* protocols over HTTP.</span></span>|
|<span data-ttu-id="f8324-174">WSDualHttpBinding</span><span class="sxs-lookup"><span data-stu-id="f8324-174">WSDualHttpBinding</span></span>|<span data-ttu-id="f8324-175">Communication HTTP en duplex au cours de laquelle le récepteur d'un message initial ne répond pas directement à l'expéditeur initial, mais peut transmettre pendant un certain temps un nombre illimité de réponses à l'aide de HTTP conformément aux protocoles WS-\*.</span><span class="sxs-lookup"><span data-stu-id="f8324-175">Duplex HTTP communication, by which the receiver of an initial message does not reply directly to the initial sender, but may transmit any number of responses over a period of time by using HTTP in conformity with WS-\* protocols.</span></span>|
|<span data-ttu-id="f8324-176">WSFederationBinding</span><span class="sxs-lookup"><span data-stu-id="f8324-176">WSFederationBinding</span></span>|<span data-ttu-id="f8324-177">Communication HTTP au cours de laquelle l'accès aux ressources d'un service peut être contrôlé en fonction des informations d'identification émises par un fournisseur d'informations d'identification identifié explicitement.</span><span class="sxs-lookup"><span data-stu-id="f8324-177">HTTP communication, in which access to the resources of a service can be controlled based on credentials issued by an explicitly-identified credential provider.</span></span>|
|<span data-ttu-id="f8324-178">NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="f8324-178">NetTcpBinding</span></span>|<span data-ttu-id="f8324-179">Communication sécurisée, fiable et hautes performances entre les entités logicielles WCF sur un réseau.</span><span class="sxs-lookup"><span data-stu-id="f8324-179">Secure, reliable, high-performance communication between WCF software entities across a network.</span></span>|
|<span data-ttu-id="f8324-180">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="f8324-180">NetNamedPipeBinding</span></span>|<span data-ttu-id="f8324-181">Communication sécurisée, fiable et hautes performances entre les entités logicielles WCF sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f8324-181">Secure, reliable, high-performance communication between WCF software entities on the same machine.</span></span>|
|<span data-ttu-id="f8324-182">NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="f8324-182">NetMsmqBinding</span></span>|<span data-ttu-id="f8324-183">Communication entre les entités de logiciels WCF à l’aide de MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f8324-183">Communication between WCF software entities by using MSMQ.</span></span>|
|<span data-ttu-id="f8324-184">MsmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="f8324-184">MsmqIntegrationBinding</span></span>|<span data-ttu-id="f8324-185">Communication entre une entité de logiciel WCF et une autre entité logicielle à l’aide de MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f8324-185">Communication between a WCF software entity and another software entity by using MSMQ.</span></span>|
|<span data-ttu-id="f8324-186">NetPeerTcpBinding</span><span class="sxs-lookup"><span data-stu-id="f8324-186">NetPeerTcpBinding</span></span>|<span data-ttu-id="f8324-187">Communication entre les entités logicielles WCF à l’aide de la mise en réseau pair à pair Windows.</span><span class="sxs-lookup"><span data-stu-id="f8324-187">Communication between WCF software entities by using Windows Peer-to-Peer Networking.</span></span>|

<span data-ttu-id="f8324-188">La liaison fournie par le système, <xref:System.ServiceModel.BasicHttpBinding>, incorpore le jeu de protocoles pris en charge par les services Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f8324-188">The system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>, incorporates the set of protocols supported by ASP.NET Web services.</span></span>

<span data-ttu-id="f8324-189">Les liaisons personnalisées pour les applications WCF sont facilement définies en tant que collections des classes d’éléments de liaison que WCF utilise pour implémenter des protocoles individuels.</span><span class="sxs-lookup"><span data-stu-id="f8324-189">Custom bindings for WCF applications are easily defined as collections of the binding element classes that WCF uses to implement individual protocols.</span></span> <span data-ttu-id="f8324-190">Les nouveaux éléments de liaison peuvent être écrits pour représenter des protocoles supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="f8324-190">New binding elements can be written to represent additional protocols.</span></span>

<span data-ttu-id="f8324-191">Le comportement interne des types de service peut être ajusté à l'aide des propriétés d'une famille de classes appelées des comportements.</span><span class="sxs-lookup"><span data-stu-id="f8324-191">The internal behavior of service types can be adjusted using the properties of a family of classes called behaviors.</span></span> <span data-ttu-id="f8324-192">Dans ce contexte, la classe <xref:System.ServiceModel.ServiceBehaviorAttribute> est utilisée pour spécifier que le type de service doit être multithread.</span><span class="sxs-lookup"><span data-stu-id="f8324-192">Here, the <xref:System.ServiceModel.ServiceBehaviorAttribute> class is used to specify that the service type is to be multithreaded.</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple)]
public class DerivativesCalculatorServiceType: IDerivativesCalculator
```

<span data-ttu-id="f8324-193">Certains comportements, comme <xref:System.ServiceModel.ServiceBehaviorAttribute>, sont des attributs.</span><span class="sxs-lookup"><span data-stu-id="f8324-193">Some behaviors, like <xref:System.ServiceModel.ServiceBehaviorAttribute>, are attributes.</span></span> <span data-ttu-id="f8324-194">Ceux dont les propriétés peuvent être définies par les administrateurs, peuvent être modifiés dans la configuration d'une application.</span><span class="sxs-lookup"><span data-stu-id="f8324-194">Others, the ones with properties that administrators would want to set, can be modified in the configuration of an application.</span></span>

<span data-ttu-id="f8324-195">Pour programmer des types de service, la classe <xref:System.ServiceModel.OperationContext> est fréquemment utilisée.</span><span class="sxs-lookup"><span data-stu-id="f8324-195">In programming service types, frequent use is made of the <xref:System.ServiceModel.OperationContext> class.</span></span> <span data-ttu-id="f8324-196">Sa propriété statique <xref:System.ServiceModel.OperationContext.Current%2A> fournit l'accès aux informations du contexte d'exécution d'une opération.</span><span class="sxs-lookup"><span data-stu-id="f8324-196">Its static <xref:System.ServiceModel.OperationContext.Current%2A> property provides access to information about the context in which an operation is running.</span></span> <span data-ttu-id="f8324-197"><xref:System.ServiceModel.OperationContext> est semblable aux classes <xref:System.Web.HttpContext> et <xref:System.EnterpriseServices.ContextUtil>.</span><span class="sxs-lookup"><span data-stu-id="f8324-197"><xref:System.ServiceModel.OperationContext> is similar to both the <xref:System.Web.HttpContext> and <xref:System.EnterpriseServices.ContextUtil> classes.</span></span>

## <a name="hosting"></a><span data-ttu-id="f8324-198">Hébergement</span><span class="sxs-lookup"><span data-stu-id="f8324-198">Hosting</span></span>

<span data-ttu-id="f8324-199">Les services Web ASP.NET sont compilés dans un assembly de bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="f8324-199">ASP.NET Web services are compiled into a class library assembly.</span></span> <span data-ttu-id="f8324-200">Un fichier appelé le fichier de service est fourni avec l'extension .asmx et contient une directive `@ WebService` qui identifie la classe qui contient le code pour le service et l'assembly qui la contient.</span><span class="sxs-lookup"><span data-stu-id="f8324-200">A file called the service file is provided that has the extension .asmx and contains an `@ WebService` directive that identifies the class that contains the code for the service and the assembly in which it is located.</span></span>

`<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>`

<span data-ttu-id="f8324-201">Le fichier de service est copié dans une racine d'application ASP.NET dans les services IIS (Internet Information Services), et l'assembly est copié dans le sous-répertoire \bin de cette racine de l'application.</span><span class="sxs-lookup"><span data-stu-id="f8324-201">The service file is copied into an ASP.NET application root in Internet Information Services (IIS), and the assembly is copied into the \bin subdirectory of that application root.</span></span> <span data-ttu-id="f8324-202">L'application est ensuite accessible depuis l'URL du fichier de service dans la racine de l'application.</span><span class="sxs-lookup"><span data-stu-id="f8324-202">The application is then accessible by using the uniform resource locator (URL) of the service file in the application root.</span></span>

<span data-ttu-id="f8324-203">Les services WCF peuvent être hébergés facilement dans IIS 5,1 ou 6,0, le service d’activation des processus Windows (WAS) fourni dans le cadre d’IIS 7,0 et dans toute application .NET.</span><span class="sxs-lookup"><span data-stu-id="f8324-203">WCF services can readily be hosted within IIS 5.1 or 6.0, the Windows Process Activation Service (WAS) that is provided as part of IIS 7.0, and within any .NET application.</span></span> <span data-ttu-id="f8324-204">Pour héberger un service dans les services IIS 5.1 ou 6.0, le service doit utiliser HTTP comme protocole de transport de communications.</span><span class="sxs-lookup"><span data-stu-id="f8324-204">To host a service in IIS 5.1 or 6.0, the service must use HTTP as the communications transport protocol.</span></span>

<span data-ttu-id="f8324-205">Pour héberger un service dans les services IIS 5.1, 6.0 ou dans le service WAS, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="f8324-205">To host a service within IIS 5.1, 6.0 or within WAS, use the follows steps:</span></span>

1. <span data-ttu-id="f8324-206">Compilez le type de service dans un assembly de bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="f8324-206">Compile the service type into a class library assembly.</span></span>

2. <span data-ttu-id="f8324-207">Créez un fichier de service avec une extension .svc et une directive `@ ServiceHost` pour identifier le type de service :</span><span class="sxs-lookup"><span data-stu-id="f8324-207">Create a service file with a .svc extension with an `@ ServiceHost` directive to identify the service type:</span></span>

    `<%@ServiceHost language="c#" Service="MyService" %>`

3. <span data-ttu-id="f8324-208">Copiez le fichier de service dans un répertoire virtuel, et l'assembly dans le sous-répertoire \bin de ce répertoire virtuel.</span><span class="sxs-lookup"><span data-stu-id="f8324-208">Copy the service file into a virtual directory, and the assembly into the \bin subdirectory of that virtual directory.</span></span>

4. <span data-ttu-id="f8324-209">Copiez le fichier de configuration dans le répertoire virtuel et nommez-le Web.config.</span><span class="sxs-lookup"><span data-stu-id="f8324-209">Copy the configuration file into the virtual directory, and name it Web.config.</span></span>

<span data-ttu-id="f8324-210">L'application est ensuite accessible depuis l'URL du fichier de service dans la racine de l'application.</span><span class="sxs-lookup"><span data-stu-id="f8324-210">The application is then accessible by using the URL of the service file in the application root.</span></span>

<span data-ttu-id="f8324-211">Pour héberger un service WCF dans une application .NET, compilez le type de service dans un assembly de bibliothèque de classes référencé par l’application et programmez l’application pour héberger le service à l’aide de la <xref:System.ServiceModel.ServiceHost> classe.</span><span class="sxs-lookup"><span data-stu-id="f8324-211">To host a WCF service within a .NET application, compile the service type into a class library assembly referenced by the application, and program the application to host the service using the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="f8324-212">Les éléments suivants sont un exemple de la programmation de base requise :</span><span class="sxs-lookup"><span data-stu-id="f8324-212">The following is an example of the basic programming required:</span></span>

```csharp
string httpBaseAddress = "http://www.contoso.com:8000/";
string tcpBaseAddress = "net.tcp://www.contoso.com:8080/";

Uri httpBaseAddressUri = new Uri(httpBaseAddress);
Uri tcpBaseAddressUri = new Uri(tcpBaseAddress);

Uri[] baseAddresses = new Uri[] {
 httpBaseAddressUri,
 tcpBaseAddressUri};

using(ServiceHost host = new ServiceHost(
typeof(Service), //"Service" is the name of the service type baseAddresses))
{
     host.Open();

     […] //Wait to receive messages
     host.Close();
}
```

<span data-ttu-id="f8324-213">Cet exemple indique comment les adresses pour un ou plusieurs protocoles de transport sont spécifiées dans la construction d'un <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="f8324-213">This example shows how addresses for one or more transport protocols are specified in the construction of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="f8324-214">Ces adresses sont connues sous le nom d'adresses de base.</span><span class="sxs-lookup"><span data-stu-id="f8324-214">These addresses are referred to as base addresses.</span></span>

<span data-ttu-id="f8324-215">L’adresse fournie pour tout point de terminaison d’un service WCF est une adresse relative à l’adresse de base de l’hôte du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="f8324-215">The address provided for any endpoint of a WCF service is an address relative to a base address of the endpoint’s host.</span></span> <span data-ttu-id="f8324-216">L'hôte peut avoir une adresse de base pour chaque protocole de transport de communication.</span><span class="sxs-lookup"><span data-stu-id="f8324-216">The host can have one base address for each communication transport protocol.</span></span> <span data-ttu-id="f8324-217">Dans l'exemple de configuration du fichier de configuration précédent, l'objet <xref:System.ServiceModel.BasicHttpBinding> sélectionné comme point de terminaison fait appel à HTTP comme protocole de transport, l'adresse du point de terminaison, `EchoService`, est donc relative à l'adresse de base HTTP de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="f8324-217">In the sample configuration in the preceding configuration file, the <xref:System.ServiceModel.BasicHttpBinding> selected for the endpoint uses HTTP as the transport protocol, so the address of the endpoint, `EchoService`, is relative to the host’s HTTP base address.</span></span> <span data-ttu-id="f8324-218">Dans le cas de l’hôte dans l’exemple précédent, l’adresse de base HTTP est `http://www.contoso.com:8000/` .</span><span class="sxs-lookup"><span data-stu-id="f8324-218">In the case of the host in the preceding example, the HTTP base address is `http://www.contoso.com:8000/`.</span></span> <span data-ttu-id="f8324-219">Pour un service hébergé dans les services IIS ou WAS, l'adresse de base est l'URL du fichier de service du service.</span><span class="sxs-lookup"><span data-stu-id="f8324-219">For a service hosted within IIS or WAS, the base address is the URL of the service’s service file.</span></span>

<span data-ttu-id="f8324-220">Seuls les services hébergés dans IIS ou WAS, et ceux qui sont configurés avec HTTP comme protocole de transport exclusivement, peuvent être utilisés pour utiliser l’option de mode de compatibilité WCF ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f8324-220">Only services hosted in IIS or WAS, and which are configured with HTTP as the transport protocol exclusively, can be made to use WCF ASP.NET compatibility mode option.</span></span> <span data-ttu-id="f8324-221">L'activation de cette option requiert les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="f8324-221">Turning that option on requires the following steps.</span></span>

1. <span data-ttu-id="f8324-222">Le programmeur doit ajouter l'attribut <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> au type de service et spécifier que le mode de compatibilité ASP.NET est autorisé ou requis.</span><span class="sxs-lookup"><span data-stu-id="f8324-222">The programmer must add the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> attribute to the service type and specify that ASP.NET compatibility mode is either allowed or required.</span></span>

    ```csharp
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(
          RequirementsMode=AspNetCompatibilityRequirementsMode.Require)]
    public class DerivativesCalculatorServiceType: IDerivativesCalculator
    ```

2. <span data-ttu-id="f8324-223">L'administrateur doit configurer l'application pour qu'elle utilise le mode de compatibilité ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f8324-223">The administrator must configure the application to use the ASP.NET compatibility mode.</span></span>

    ```xml
    <configuration>
         <system.serviceModel>
          <services>
          […]
          </services>
          <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
        </system.serviceModel>
    </configuration>
    ```

    <span data-ttu-id="f8324-224">Les applications WCF peuvent également être configurées pour utiliser le fichier. asmx en tant qu’extension de leurs fichiers de service plutôt que. svc.</span><span class="sxs-lookup"><span data-stu-id="f8324-224">WCF applications can also be configured to use .asmx as the extension for their service files rather than .svc.</span></span>

    ```xml
    <system.web>
         <compilation>
          <compilation debug="true">
          <buildProviders>
           <remove extension=".asmx"/>
           <add extension=".asmx"
            type="System.ServiceModel.ServiceBuildProvider,
            System.ServiceModel,
            Version=3.0.0.0,
            Culture=neutral,
            PublicKeyToken=b77a5c561934e089" />
          </buildProviders>
          </compilation>
         </compilation>
    </system.web>
    ```

    <span data-ttu-id="f8324-225">Cette option peut vous éviter d’avoir à modifier les clients configurés pour utiliser les URL des fichiers de service. asmx lors de la modification d’un service pour utiliser WCF.</span><span class="sxs-lookup"><span data-stu-id="f8324-225">That option can save you from having to modify clients that are configured to use the URLs of .asmx service files when modifying a service to use WCF.</span></span>

## <a name="client-development"></a><span data-ttu-id="f8324-226">Développement client</span><span class="sxs-lookup"><span data-stu-id="f8324-226">Client Development</span></span>

<span data-ttu-id="f8324-227">Les clients pour les services Web ASP.NET sont générés à l'aide de l'outil de ligne de commande, WSDL.exe, qui fournit l'URL du fichier .asmx comme entrée.</span><span class="sxs-lookup"><span data-stu-id="f8324-227">Clients for ASP.NET Web services are generated using the command-line tool, WSDL.exe, which provides the URL of the .asmx file as input.</span></span> <span data-ttu-id="f8324-228">L’outil correspondant fourni par WCF est l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f8324-228">The corresponding tool provided by WCF is [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="f8324-229">Il génère un module de code avec la définition du contrat de service et la définition d’une classe de client WCF.</span><span class="sxs-lookup"><span data-stu-id="f8324-229">It generates a code module with the definition of the service contract and the definition of a WCF client class.</span></span> <span data-ttu-id="f8324-230">Il génère également un fichier de configuration avec l'adresse et la liaison du service.</span><span class="sxs-lookup"><span data-stu-id="f8324-230">It also generates a configuration file with the address and binding of the service.</span></span>

<span data-ttu-id="f8324-231">Pour programmer un client d’un service distant, il est généralement recommandé de programmer selon un modèle asynchrone.</span><span class="sxs-lookup"><span data-stu-id="f8324-231">In programming a client of a remote service it is generally advisable to program according to an asynchronous pattern.</span></span> <span data-ttu-id="f8324-232">Le code généré par l'outil WSDL.exe fournit toujours un modèle synchrone et asynchrone par défaut.</span><span class="sxs-lookup"><span data-stu-id="f8324-232">The code generated by the WSDL.exe tool always provides for both a synchronous and an asynchronous pattern by default.</span></span> <span data-ttu-id="f8324-233">Le code généré par l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) peut fournir l’un ou l’autre modèle.</span><span class="sxs-lookup"><span data-stu-id="f8324-233">The code generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) can provide for either pattern.</span></span> <span data-ttu-id="f8324-234">Il fournit le modèle synchrone par défaut.</span><span class="sxs-lookup"><span data-stu-id="f8324-234">It provides for the synchronous pattern by default.</span></span> <span data-ttu-id="f8324-235">Si l’outil est exécuté avec le commutateur `/async`, le code généré fournit le modèle asynchrone.</span><span class="sxs-lookup"><span data-stu-id="f8324-235">If the tool is executed with the `/async` switch, then the generated code provides for the asynchronous pattern.</span></span>

<span data-ttu-id="f8324-236">Il n’y a aucune garantie que les noms des classes de client WCF générées par ASP. Par défaut, l’outil WSDL. exe du réseau correspond aux noms des classes de client WCF générées par l’outil Svcutil. exe.</span><span class="sxs-lookup"><span data-stu-id="f8324-236">There is no guarantee that names in the WCF client classes generated by ASP.NET’s WSDL.exe tool, by default, match the names in WCF client classes generated by the Svcutil.exe tool.</span></span> <span data-ttu-id="f8324-237">En particulier, les noms des propriétés des classes qui doivent être sérialisées à l'aide du <xref:System.Xml.Serialization.XmlSerializer> reçoivent par défaut le suffixe Property dans le code généré par l'outil Svcutil.exe, ce qui n'est pas le cas avec l'outil WSDL.exe.</span><span class="sxs-lookup"><span data-stu-id="f8324-237">In particular, the names of the properties of classes that have to be serialized using the <xref:System.Xml.Serialization.XmlSerializer> are, by default, given the suffix Property in the code generated by the Svcutil.exe tool, which is not the case with the WSDL.exe tool.</span></span>

## <a name="message-representation"></a><span data-ttu-id="f8324-238">Représentation de message</span><span class="sxs-lookup"><span data-stu-id="f8324-238">Message Representation</span></span>

<span data-ttu-id="f8324-239">Les en-têtes des messages SOAP envoyés et reçus par les services Web ASP.NET peuvent être personnalisés.</span><span class="sxs-lookup"><span data-stu-id="f8324-239">The headers of the SOAP messages sent and received by ASP.NET Web services can be customized.</span></span> <span data-ttu-id="f8324-240">Une classe est dérivée de <xref:System.Web.Services.Protocols.SoapHeader> pour définir la structure de l'en-tête, puis, le <xref:System.Web.Services.Protocols.SoapHeaderAttribute> est utilisé pour indiquer la présence de l'en-tête.</span><span class="sxs-lookup"><span data-stu-id="f8324-240">A class is derived from <xref:System.Web.Services.Protocols.SoapHeader> to define the structure of the header, and then the <xref:System.Web.Services.Protocols.SoapHeaderAttribute> is used to indicate the presence of the header.</span></span>

```csharp
public class SomeProtocol : SoapHeader
{
     public long CurrentValue;
     public long Total;
}

[WebService]
public interface IEcho
{
     SomeProtocol ProtocolHeader
     {
      get;
     set;
     }

     [WebMethod]
     [SoapHeader("ProtocolHeader")]
     string PlaceOrders(PurchaseOrderType order);
}

public class Service: WebService, IEcho
{
     private SomeProtocol protocolHeader;

     public SomeProtocol ProtocolHeader
     {
         get
         {
              return this.protocolHeader;
         }

         set
         {
              this.protocolHeader = value;
         }
     }

     string PlaceOrders(PurchaseOrderType order)
     {
         long currentValue = this.protocolHeader.CurrentValue;
     }
}
```

<span data-ttu-id="f8324-241">WCF fournit les attributs,, <xref:System.ServiceModel.MessageContractAttribute> <xref:System.ServiceModel.MessageHeaderAttribute> et <xref:System.ServiceModel.MessageBodyMemberAttribute> pour décrire la structure des messages SOAP envoyés et reçus par un service.</span><span class="sxs-lookup"><span data-stu-id="f8324-241">The WCF provides the attributes, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, and <xref:System.ServiceModel.MessageBodyMemberAttribute> to describe the structure of the SOAP messages sent and received by a service.</span></span>

```csharp
[DataContract]
public class SomeProtocol
{
     [DataMember]
     public long CurrentValue;
     [DataMember]
     public long Total;
}

[DataContract]
public class Item
{
     [DataMember]
     public string ItemNumber;
     [DataMember]
     public decimal Quantity;
     [DataMember]
     public decimal UnitPrice;
}

[MessageContract]
public class ItemMessage
{
     [MessageHeader]
     public SomeProtocol ProtocolHeader;
     [MessageBody]
     public Item Content;
}

[ServiceContract]
public interface IItemService
{
     [OperationContract]
     public void DeliverItem(ItemMessage itemMessage);
}
```

<span data-ttu-id="f8324-242">Cette syntaxe génère une représentation explicite de la structure des messages, alors que la structure des messages est impliquée par le code d'un service Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f8324-242">This syntax yields an explicit representation of the structure of the messages, whereas the structure of messages is implied by the code of an ASP.NET Web service.</span></span> <span data-ttu-id="f8324-243">En outre, dans la syntaxe ASP.NET, les en-têtes de message sont représentés comme des propriétés du service, telles que la `ProtocolHeader` propriété dans l’exemple précédent, tandis que dans la syntaxe WCF, elles sont représentées plus précisément comme des propriétés de messages.</span><span class="sxs-lookup"><span data-stu-id="f8324-243">Also, in the ASP.NET syntax, message headers are represented as properties of the service, such as the `ProtocolHeader` property in the previous example, whereas in WCF syntax, they are more accurately represented as properties of messages.</span></span> <span data-ttu-id="f8324-244">WCF permet également d’ajouter des en-têtes de message à la configuration des points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="f8324-244">Also, WCF allows message headers to be added to the configuration of endpoints.</span></span>

```xml
<service name="Service ">
     <endpoint
      address="EchoService"
      binding="basicHttpBinding"
      contract="IEchoService ">
      <headers>
      <dsig:X509Certificate
       xmlns:dsig="http://www.w3.org/2000/09/xmldsig#">
       ...
      </dsig:X509Certificate>
      </headers>
     </endpoint>
</service>
```

<span data-ttu-id="f8324-245">Cette option vous permet d'éviter toute référence aux en-têtes de protocole d'infrastructure dans le code pour un client ou un service : les en-têtes sont ajoutés aux messages selon le mode de configuration du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="f8324-245">That option allows you to avoid any reference to infrastructural protocol headers in the code for a client or service: the headers are added to messages because of how the endpoint is configured.</span></span>

## <a name="service-description"></a><span data-ttu-id="f8324-246">Description du service</span><span class="sxs-lookup"><span data-stu-id="f8324-246">Service Description</span></span>

<span data-ttu-id="f8324-247">L'émission d'une demande HTTP GET pour le fichier .asmx d'un service Web ASP.NET avec la requête WSDL entraîne la génération de WSDL par ASP.NET pour décrire le service.</span><span class="sxs-lookup"><span data-stu-id="f8324-247">Issuing an HTTP GET request for the .asmx file of an ASP.NET Web service with the query WSDL causes ASP.NET to generate WSDL to describe the service.</span></span> <span data-ttu-id="f8324-248">Il retourne ce WSDL en réponse à la demande.</span><span class="sxs-lookup"><span data-stu-id="f8324-248">It returns that WSDL as the response to the request.</span></span>

<span data-ttu-id="f8324-249">ASP.NET 2.0 permet de valider la conformité d'un service avec Basic Profile 1.1 de Web Services-Interoperability Organization (WS-I), et d'insérer une revendication que le service est conforme dans son WSDL.</span><span class="sxs-lookup"><span data-stu-id="f8324-249">ASP.NET 2.0 made it possible to validate that a service is compliant with the Basic Profile 1.1 of the Web Services-Interoperability Organization (WS-I), and to insert a claim that the service is compliant into its WSDL.</span></span> <span data-ttu-id="f8324-250">Cette opération est effectuée à l'aide des paramètres `ConformsTo` et `EmitConformanceClaims` de l'attribut <xref:System.Web.Services.WebServiceBindingAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f8324-250">That is done using the `ConformsTo` and `EmitConformanceClaims` parameters of the <xref:System.Web.Services.WebServiceBindingAttribute> attribute.</span></span>

```csharp
[WebService(Namespace = "http://tempuri.org/")]
[WebServiceBinding(
     ConformsTo = WsiProfiles.BasicProfile1_1,
     EmitConformanceClaims=true)]
public interface IEcho
```

<span data-ttu-id="f8324-251">Le WSDL généré par ASP.NET pour un service peut être personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f8324-251">The WSDL that ASP.NET generates for a service can be customized.</span></span> <span data-ttu-id="f8324-252">Les personnalisations s'effectuent en créant une classe dérivée de <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> pour ajouter des éléments au WSDL.</span><span class="sxs-lookup"><span data-stu-id="f8324-252">Customizations are made by creating a derived class of <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> to add items to the WSDL.</span></span>

<span data-ttu-id="f8324-253">L’émission d’une requête HTTP-HTTP avec la requête WSDL pour le fichier. svc d’un service WCF avec un point de terminaison HTTP hébergé dans IIS 51, 6,0 ou WAS a pour effet que WCF répondait avec WSDL pour décrire le service.</span><span class="sxs-lookup"><span data-stu-id="f8324-253">Issuing an HTTP GET request with the query WSDL for the .svc file of a WCF service with an HTTP endpoint hosted within IIS 51, 6.0 or WAS causes WCF to respond with WSDL to describe the service.</span></span> <span data-ttu-id="f8324-254">L'émission d'une demande HTTP GET avec la requête WSDL à l'adresse de base HTTP d'un service hébergé dans une application .NET a le même effet si httpGetEnabled a la valeur true.</span><span class="sxs-lookup"><span data-stu-id="f8324-254">Issuing an HTTP GET request with the query WSDL to the HTTP base address of a service hosted within a .NET application has the same effect if httpGetEnabled is set to true.</span></span>

<span data-ttu-id="f8324-255">Toutefois, WCF répond également aux demandes WS-MetadataExchange avec WSDL qu’il génère pour décrire un service.</span><span class="sxs-lookup"><span data-stu-id="f8324-255">However, WCF also responds to WS-MetadataExchange requests with WSDL that it generates to describe a service.</span></span> <span data-ttu-id="f8324-256">Les services Web ASP.NET n'offrent pas de prise en charge intégrée pour les demandes WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="f8324-256">ASP.NET Web services do not have built-in support for WS-MetadataExchange requests.</span></span>

<span data-ttu-id="f8324-257">Le WSDL généré par WCF peut être largement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f8324-257">The WSDL that WCF generates can be extensively customized.</span></span> <span data-ttu-id="f8324-258">La classe <xref:System.ServiceModel.Description.ServiceMetadataBehavior> fournit des fonctions pour personnaliser le WSDL.</span><span class="sxs-lookup"><span data-stu-id="f8324-258">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class provides some facilities for customizing the WSDL.</span></span> <span data-ttu-id="f8324-259">Le WCF peut également être configuré pour ne pas générer WSDL, mais plutôt pour utiliser un fichier WSDL statique à une URL donnée.</span><span class="sxs-lookup"><span data-stu-id="f8324-259">The WCF can also be configured to not generate WSDL, but rather to use a static WSDL file at a given URL.</span></span>

```xml
<behaviors>
     <behavior name="DescriptionBehavior">
     <metadataPublishing
      enableMetadataExchange="true"
      enableGetWsdl="true"
      enableHelpPage="true"
      metadataLocation=
      "http://localhost/DerivativesCalculatorService/Service.WSDL"/>
     </behavior>
</behaviors>
```

## <a name="exception-handling"></a><span data-ttu-id="f8324-260">Gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="f8324-260">Exception Handling</span></span>

<span data-ttu-id="f8324-261">Dans les services Web ASP.NET, les exceptions non prises en charge sont retournées aux clients comme des erreurs SOAP.</span><span class="sxs-lookup"><span data-stu-id="f8324-261">In ASP.NET Web services, unhandled exceptions are returned to clients as SOAP faults.</span></span> <span data-ttu-id="f8324-262">Vous pouvez aussi lever explicitement des instances de la classe <xref:System.Web.Services.Protocols.SoapException> et avoir plus de contrôle sur le contenu de l'erreur SOAP transmise au client.</span><span class="sxs-lookup"><span data-stu-id="f8324-262">You can also explicitly throw instances of the <xref:System.Web.Services.Protocols.SoapException> class and have more control over the content of the SOAP fault that gets transmitted to the client.</span></span>

<span data-ttu-id="f8324-263">Dans les services WCF, les exceptions non gérées ne sont pas retournées aux clients en tant qu’erreurs SOAP pour empêcher les informations sensibles d’être exposées par inadvertance par le biais des exceptions.</span><span class="sxs-lookup"><span data-stu-id="f8324-263">In WCF services, unhandled exceptions are not returned to clients as SOAP faults to prevent sensitive information being inadvertently exposed through the exceptions.</span></span> <span data-ttu-id="f8324-264">Un paramètre de configuration est fourni pour que les exceptions non prises en charge soient retournées aux clients à des fins de débogage.</span><span class="sxs-lookup"><span data-stu-id="f8324-264">A configuration setting is provided to have unhandled exceptions returned to clients for the purpose of debugging.</span></span>

<span data-ttu-id="f8324-265">Pour retourner des erreurs SOAP aux clients, vous pouvez lever des instances du type générique, <xref:System.ServiceModel.FaultException%601>, à l'aide du type de contrat de données comme type générique.</span><span class="sxs-lookup"><span data-stu-id="f8324-265">To return SOAP faults to clients, you can throw instances of the generic type, <xref:System.ServiceModel.FaultException%601>, using the data contract type as the generic type.</span></span> <span data-ttu-id="f8324-266">Vous pouvez aussi ajouter des attributs <xref:System.ServiceModel.FaultContractAttribute> aux opérations pour spécifier les erreurs qu'une opération peut générer.</span><span class="sxs-lookup"><span data-stu-id="f8324-266">You can also add <xref:System.ServiceModel.FaultContractAttribute> attributes to operations to specify the faults that an operation might yield.</span></span>

```csharp
[DataContract]
public class MathFault
{
     [DataMember]
     public string operation;
     [DataMember]
     public string problemType;
}

[ServiceContract]
public interface ICalculator
{
     [OperationContract]
     [FaultContract(typeof(MathFault))]
     int Divide(int n1, int n2);
}
```

<span data-ttu-id="f8324-267">Cette opération entraîne la publication des erreurs possibles dans le WSDL pour le service, ce qui permet aux programmeurs du client d‘anticiper sur les erreurs possibles à l‘issue d‘une opération, et d‘écrire les instructions catch appropriées.</span><span class="sxs-lookup"><span data-stu-id="f8324-267">Doing so results in the possible faults being advertised in the WSDL for the service, allowing client programmers to anticipate which faults can result from an operation, and write the appropriate catch statements.</span></span>

```csharp
try
{
     result = client.Divide(value1, value2);
}
catch (FaultException<MathFault> e)
{
 Console.WriteLine("FaultException<MathFault>: Math fault while doing "
  + e.Detail.operation
  + ". Problem: "
  + e.Detail.problemType);
}
```

## <a name="state-management"></a><span data-ttu-id="f8324-268">Gestion des états</span><span class="sxs-lookup"><span data-stu-id="f8324-268">State Management</span></span>

<span data-ttu-id="f8324-269">La classe utilisée pour implémenter un service Web ASP.NET peut être dérivée de <xref:System.Web.Services.WebService>.</span><span class="sxs-lookup"><span data-stu-id="f8324-269">The class used to implement an ASP.NET Web service may be derived from <xref:System.Web.Services.WebService>.</span></span>

```csharp
public class Service : WebService, IEcho
{

 public string Echo(string input)
 {
  return input;
 }
}
```

<span data-ttu-id="f8324-270">Dans ce cas, la classe peut être programmée pour utiliser la propriété Context de la classe de base <xref:System.Web.Services.WebService> pour accéder à un objet <xref:System.Web.HttpContext>.</span><span class="sxs-lookup"><span data-stu-id="f8324-270">In that case, the class can be programmed to use the <xref:System.Web.Services.WebService> base class’ Context property to access a <xref:System.Web.HttpContext> object.</span></span> <span data-ttu-id="f8324-271">L'objet <xref:System.Web.HttpContext> peut être utilisé pour mettre à jour et récupérer des informations d'état d'application en utilisant sa propriété Application, et pour mettre à jour et récupérer des informations d'état de session en utilisant sa propriété Session.</span><span class="sxs-lookup"><span data-stu-id="f8324-271">The <xref:System.Web.HttpContext> object can be used to update and retrieve application state information by using its Application property, and can be used to update and retrieve session state information by using its Session property.</span></span>

<span data-ttu-id="f8324-272">ASP.NET permet un contrôle important sur l'emplacement de stockage réel des informations d'état de session accessibles à l'aide de la propriété Session du <xref:System.Web.HttpContext>.</span><span class="sxs-lookup"><span data-stu-id="f8324-272">ASP.NET provides considerable control over where the session state information accessed by using the Session property of the <xref:System.Web.HttpContext> is actually stored.</span></span> <span data-ttu-id="f8324-273">Elles peuvent être stockées dans des cookies, une base de données, la mémoire du serveur actuel ou la mémoire d'un serveur désigné.</span><span class="sxs-lookup"><span data-stu-id="f8324-273">It may be stored in cookies, in a database, in the memory of the current server, or in the memory of a designated server.</span></span> <span data-ttu-id="f8324-274">Le choix s'opère dans le fichier de configuration du service.</span><span class="sxs-lookup"><span data-stu-id="f8324-274">The choice is made in the service’s configuration file.</span></span>

<span data-ttu-id="f8324-275">WCF fournit des objets extensibles pour la gestion des États.</span><span class="sxs-lookup"><span data-stu-id="f8324-275">The WCF provides extensible objects for state management.</span></span> <span data-ttu-id="f8324-276">Les objets extensibles sont des objets qui implémentent <xref:System.ServiceModel.IExtensibleObject%601>.</span><span class="sxs-lookup"><span data-stu-id="f8324-276">Extensible objects are objects that implement <xref:System.ServiceModel.IExtensibleObject%601>.</span></span> <span data-ttu-id="f8324-277">Les objets extensibles les plus importants sont <xref:System.ServiceModel.ServiceHostBase> et <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="f8324-277">The most important extensible objects are <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="f8324-278">`ServiceHostBase` vous permet de maintenir l'état accessible par toutes les instances de tous les types de services sur le même hôte, alors que `InstanceContext` vous permet de maintenir l'état accessible par tout code s'exécutant dans la même instance d'un type de service.</span><span class="sxs-lookup"><span data-stu-id="f8324-278">`ServiceHostBase` allows you to maintain state that all of the instances of all of the service types on the same host can access, while `InstanceContext` allows you to maintain state that can be accessed by any code running within the same instance of a service type.</span></span>

<span data-ttu-id="f8324-279">Ici, le type de service, `TradingSystem` , a un <xref:System.ServiceModel.ServiceBehaviorAttribute> qui spécifie que tous les appels de la même instance de client WCF sont acheminés vers la même instance du type de service.</span><span class="sxs-lookup"><span data-stu-id="f8324-279">Here, the service type, `TradingSystem`, has a <xref:System.ServiceModel.ServiceBehaviorAttribute> that specifies that all calls from the same WCF client instance are routed to the same instance of the service type.</span></span>

```csharp
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]
public class TradingSystem: ITradingService
```

<span data-ttu-id="f8324-280">La classe, `DealData`, définit l'état accessible par tout code qui s'exécute dans la même instance d'un type de service.</span><span class="sxs-lookup"><span data-stu-id="f8324-280">The class, `DealData`, defines state that can be accessed by any code running in the same instance of a service type.</span></span>

```csharp
internal class DealData: IExtension<InstanceContext>
{
 public string DealIdentifier = null;
 public Trade[] Trades = null;
}
```

<span data-ttu-id="f8324-281">Dans le code du type de service qui implémente l'une des opérations du contrat de service, un objet d'état `DealData` est ajouté à l'état de l'instance actuelle du type de service.</span><span class="sxs-lookup"><span data-stu-id="f8324-281">In the code of the service type that implements one of the operations of the service contract, a `DealData` state object is added to the state of the current instance of the service type.</span></span>

```csharp
string ITradingService.BeginDeal()
{
 string dealIdentifier = Guid.NewGuid().ToString();
 DealData state = new DealData(dealIdentifier);
 OperationContext.Current.InstanceContext.Extensions.Add(state);
 return dealIdentifier;
}
```

<span data-ttu-id="f8324-282">Cet objet d'état peut être ensuite récupéré et modifié par le code qui implémente une autre opération des opérations du contrat de service.</span><span class="sxs-lookup"><span data-stu-id="f8324-282">That state object can then be retrieved and modified by the code that implements another of the service contract’s operations.</span></span>

```csharp
void ITradingService.AddTrade(Trade trade)
{
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();
 dealData.AddTrade(trade);
}
```

<span data-ttu-id="f8324-283">Tandis que ASP.NET permet de contrôler l’emplacement où les informations d’État dans la <xref:System.Web.HttpContext> classe sont réellement stockées, WCF, au moins dans sa version initiale, ne fournit aucun contrôle sur l’emplacement de stockage des objets extensibles.</span><span class="sxs-lookup"><span data-stu-id="f8324-283">Whereas ASP.NET provides control over where state information in the <xref:System.Web.HttpContext> class is actually stored, WCF, at least in its initial version, provides no control over where extensible objects are stored.</span></span> <span data-ttu-id="f8324-284">Cela constitue la meilleure raison de sélectionner le mode de compatibilité ASP.NET pour un service WCF.</span><span class="sxs-lookup"><span data-stu-id="f8324-284">That constitutes the very best reason for selecting the ASP.NET compatibility mode for a WCF service.</span></span> <span data-ttu-id="f8324-285">Si la gestion d'état configurable est impérative, choisir ensuite le mode de compatibilité ASP.NET vous permet d'utiliser les fonctions de la classe <xref:System.Web.HttpContext> exactement telles qu'elles sont utilisées dans ASP.NET, et de configurer aussi l'emplacement de stockage des informations d'état gérées à l'aide de la classe <xref:System.Web.HttpContext>.</span><span class="sxs-lookup"><span data-stu-id="f8324-285">If configurable state management is imperative, then opting for the ASP.NET compatibility mode allows you to use the facilities of the <xref:System.Web.HttpContext> class exactly as they are used in ASP.NET, and also to configure where state information managed by using the <xref:System.Web.HttpContext> class is stored.</span></span>

## <a name="security"></a><span data-ttu-id="f8324-286">Sécurité</span><span class="sxs-lookup"><span data-stu-id="f8324-286">Security</span></span>

<span data-ttu-id="f8324-287">Les options permettant de sécuriser les services Web ASP.NET sont celles qui permettent de sécuriser toute application IIS.</span><span class="sxs-lookup"><span data-stu-id="f8324-287">The options for securing ASP.NET Web services are those for securing any IIS application.</span></span> <span data-ttu-id="f8324-288">Étant donné que les applications WCF peuvent être hébergées non seulement dans IIS, mais également dans n’importe quel exécutable .NET, les options de sécurisation des applications WCF doivent être indépendantes des fonctionnalités d’IIS.</span><span class="sxs-lookup"><span data-stu-id="f8324-288">Because WCF applications can be hosted not only within IIS but also within any .NET executable, the options for securing WCF applications must be made independent from the facilities of IIS.</span></span> <span data-ttu-id="f8324-289">Toutefois, les fonctionnalités fournies pour les services Web ASP.NET sont également disponibles pour les services WCF qui s’exécutent en mode de compatibilité ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f8324-289">However, the facilities provided for ASP.NET Web services are also available for WCF services running in ASP.NET compatibility mode.</span></span>

### <a name="security-authentication"></a><span data-ttu-id="f8324-290">Sécurité : authentification</span><span class="sxs-lookup"><span data-stu-id="f8324-290">Security: Authentication</span></span>

<span data-ttu-id="f8324-291">Les services IIS fournissent des fonctions de contrôle de l’accès aux applications qui permettent de sélectionner un accès anonyme ou un ensemble de modes d’authentification : l’authentification Windows, l’authentification Digest, l’authentification de base et l’authentification .NET Passport.</span><span class="sxs-lookup"><span data-stu-id="f8324-291">IIS provides facilities for controlling access to applications by which you can select either anonymous access or a variety of modes of authentication: Windows Authentication, Digest Authentication, Basic Authentication, and .NET Passport Authentication.</span></span> <span data-ttu-id="f8324-292">L'option d'authentification Windows peut être utilisée pour contrôler l'accès aux services Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f8324-292">The Windows Authentication option can be used to control access to ASP.NET Web services.</span></span> <span data-ttu-id="f8324-293">Toutefois, lorsque les applications WCF sont hébergées dans IIS, IIS doit être configuré pour autoriser l’accès anonyme à l’application, afin que l’authentification puisse être gérée par WCF, qui prend en charge l’authentification Windows parmi d’autres options.</span><span class="sxs-lookup"><span data-stu-id="f8324-293">However, when WCF applications are hosted within IIS, IIS must be configured to permit anonymous access to the application, so that authentication can be managed by WCF itself, which does support Windows authentication among various other options.</span></span> <span data-ttu-id="f8324-294">Les autres options intégrées incluent les jetons de nom d'utilisateur, les certificats X.509, les jetons SAML et la carte CardSpace, mais il est possible de définir aussi des mécanismes d'authentification personnalisés.</span><span class="sxs-lookup"><span data-stu-id="f8324-294">The other options that are built-in include username tokens, X.509 certificates, SAML tokens, and CardSpace card, but custom authentication mechanisms can also be defined.</span></span>

### <a name="security-impersonation"></a><span data-ttu-id="f8324-295">Sécurité : emprunt d'identité</span><span class="sxs-lookup"><span data-stu-id="f8324-295">Security: Impersonation</span></span>

<span data-ttu-id="f8324-296">ASP.NET fournit un élément d'identité qui permet à un service Web ASP.NET d'emprunter à un utilisateur particulier son identité ou les informations d'identification de l'utilisateur fournies dans la demande actuelle.</span><span class="sxs-lookup"><span data-stu-id="f8324-296">ASP.NET provides an identity element by which an ASP.NET Web service can be made to impersonate a particular user or whichever user’s credentials are provided with the current request.</span></span> <span data-ttu-id="f8324-297">Cet élément peut être utilisé pour configurer l’emprunt d’identité dans les applications WCF s’exécutant en mode de compatibilité ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f8324-297">That element can be used to configure impersonation in WCF applications running in ASP.NET compatibility mode.</span></span>

<span data-ttu-id="f8324-298">Le système de configuration WCF fournit son propre élément Identity pour désigner un utilisateur particulier dont l’identité doit être empruntée.</span><span class="sxs-lookup"><span data-stu-id="f8324-298">The WCF configuration system provides its own identity element for designating a particular user to impersonate.</span></span> <span data-ttu-id="f8324-299">En outre, les clients et services WCF peuvent être configurés indépendamment pour l’emprunt d’identité.</span><span class="sxs-lookup"><span data-stu-id="f8324-299">Also, WCF clients and services can be independently configured for impersonation.</span></span> <span data-ttu-id="f8324-300">Les clients peuvent être configurés pour emprunter l'identité de l'utilisateur actuel lorsqu'ils transmettent des demandes.</span><span class="sxs-lookup"><span data-stu-id="f8324-300">Clients can be configured to impersonate the current user when they transmit requests.</span></span>

```xml
<behaviors>
     <behavior name="DerivativesCalculatorClientBehavior">
      <clientCredentials>
      <windows allowedImpersonationLevel="Impersonation"/>
      </clientCredentials>
     </behavior>
</behaviors>
```

<span data-ttu-id="f8324-301">Les opérations de service peuvent être configurées pour emprunter les informations d'identification de l'utilisateur qui fourni la demande actuelle.</span><span class="sxs-lookup"><span data-stu-id="f8324-301">Service operations can be configured to impersonate whichever user’s credentials are provided with the current request.</span></span>

```csharp
[OperationBehavior(Impersonation = ImpersonationOption.Required)]
public void Receive(Message input)
```

### <a name="security-authorization-using-access-control-lists"></a><span data-ttu-id="f8324-302">Sécurité : autorisation à l'aide des listes de contrôle d'accès</span><span class="sxs-lookup"><span data-stu-id="f8324-302">Security: Authorization using Access Control Lists</span></span>

<span data-ttu-id="f8324-303">Les listes de contrôle d'accès (ACL) peuvent être utilisées pour restreindre l'accès aux fichiers .asmx.</span><span class="sxs-lookup"><span data-stu-id="f8324-303">Access Control Lists (ACLs) can be used to restrict access to .asmx files.</span></span> <span data-ttu-id="f8324-304">Toutefois, les listes de contrôle d’accès des fichiers. svc WCF sont ignorées, sauf en mode de compatibilité ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f8324-304">However, ACLs on WCF .svc files are ignored except in ASP.NET compatibility mode.</span></span>

### <a name="security-role-based-authorization"></a><span data-ttu-id="f8324-305">Sécurité : autorisation basée sur les rôles</span><span class="sxs-lookup"><span data-stu-id="f8324-305">Security: Role-based Authorization</span></span>

<span data-ttu-id="f8324-306">L'option d'authentification IIS Windows peut être utilisée conjointement avec l'élément d'autorisation fourni par le langage de configuration ASP.NET pour faciliter l'autorisation basée sur les rôles pour les services Web ASP.NET selon les groupes Windows auxquels les utilisateurs sont assignés.</span><span class="sxs-lookup"><span data-stu-id="f8324-306">The IIS Windows Authentication option can be used in conjunction with the authorization element provided by the ASP.NET configuration language to facilitate role-based authorization for ASP.NET Web services based on the Windows groups to which users are assigned.</span></span> <span data-ttu-id="f8324-307">ASP.NET 2.0 introduit un mécanisme plus général d'autorisation basée sur les rôles : les fournisseurs de rôles.</span><span class="sxs-lookup"><span data-stu-id="f8324-307">ASP.NET 2.0 introduced a more general role-based authorization mechanism: role providers.</span></span>

<span data-ttu-id="f8324-308">Les fournisseurs de rôles sont des classes qui implémentent toutes une interface de base pour s'informer des rôles auxquels un utilisateur est assigné, mais chaque fournisseur de rôle sait comment récupérer ces information issues d'une source différente.</span><span class="sxs-lookup"><span data-stu-id="f8324-308">Role providers are classes that all implement a basic interface for enquiring about the roles to which a user is assigned, but each role provider knows how to retrieve that information from a different source.</span></span> <span data-ttu-id="f8324-309">ASP.NET 2.0 fournit un fournisseur de rôles qui peut récupérer des affectations de rôle d'une base de données Microsoft SQL Server, ainsi qu'un autre fournisseur qui peut récupérer des affectations de rôles issues du Gestionnaire d'autorisations Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="f8324-309">ASP.NET 2.0 provides a role provider that can retrieve role assignments from a Microsoft SQL Server database, and another that can retrieve role assignments from the Windows Server 2003 Authorization Manager.</span></span>

<span data-ttu-id="f8324-310">Le mécanisme de fournisseur de rôle peut en fait être utilisé indépendamment de ASP.NET dans n’importe quelle application .NET, y compris une application WCF.</span><span class="sxs-lookup"><span data-stu-id="f8324-310">The role provider mechanism can actually be used independently of ASP.NET in any .NET application, including a WCF application.</span></span> <span data-ttu-id="f8324-311">L’exemple de configuration suivant pour une application WCF montre comment l’utilisation d’un fournisseur de rôle ASP.NET est une option sélectionnée au moyen du <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> .</span><span class="sxs-lookup"><span data-stu-id="f8324-311">The following sample configuration for a WCF application shows how the use of an ASP.NET role provider is an option selected by means of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>

```xml
<system.serviceModel>
     <services>
         <service name="Service.ResourceAccessServiceType"
             behaviorConfiguration="ServiceBehavior">
             <endpoint
              address="ResourceAccessService"
              binding="wsHttpBinding"
              contract="Service.IResourceAccessContract"/>
         </service>
     </services>
     <behaviors>
       <behavior name="ServiceBehavior">
       <serviceAuthorization principalPermissionMode="UseAspNetRoles"/>
      </behavior>
     </behaviors>
</system.serviceModel>
```

### <a name="security-claims-based-authorization"></a><span data-ttu-id="f8324-312">Sécurité : autorisation basée sur les revendications</span><span class="sxs-lookup"><span data-stu-id="f8324-312">Security: Claims-based Authorization</span></span>

<span data-ttu-id="f8324-313">L’une des innovations les plus importantes de WCF est sa prise en charge complète pour autoriser l’accès aux ressources protégées basées sur les revendications.</span><span class="sxs-lookup"><span data-stu-id="f8324-313">One of the most important innovations of WCF is its thorough support for authorizing access to protected resources based on claims.</span></span> <span data-ttu-id="f8324-314">Les revendications se composent d'un type, d'un droit et d'une valeur, un permis de conduire, par exemple.</span><span class="sxs-lookup"><span data-stu-id="f8324-314">Claims consist of a type, a right and a value, a drivers’ license, for example.</span></span> <span data-ttu-id="f8324-315">Elle produit un jeu de revendications relatives au porteur, dont l'une d'entre elles est la date de naissance du porteur.</span><span class="sxs-lookup"><span data-stu-id="f8324-315">It makes a set of claims about the bearer, one of which is the bearer’s date of birth.</span></span> <span data-ttu-id="f8324-316">Le type de cette revendication est la date de naissance, la valeur de la revendication est la date de naissance du conducteur.</span><span class="sxs-lookup"><span data-stu-id="f8324-316">The type of that claim is date of birth, while the value of the claim is the driver’s birth date.</span></span> <span data-ttu-id="f8324-317">Le droit que confère une revendication au porteur spécifie ce que le porteur peut faire avec la valeur de la revendication.</span><span class="sxs-lookup"><span data-stu-id="f8324-317">The right that a claim confers on the bearer specifies what the bearer can do with the claim’s value.</span></span> <span data-ttu-id="f8324-318">Dans le cas de la revendication de la date de naissance du conducteur, ce droit est la propriété : le conducteur possède cette date de naissance mais il ne peut pas, par exemple, la modifier.</span><span class="sxs-lookup"><span data-stu-id="f8324-318">In the case of the claim of the driver’s date of birth, the right is possession: the driver possesses that date of birth but cannot, for example, alter it.</span></span> <span data-ttu-id="f8324-319">L'autorisation basée sur les revendications intègre l'autorisation basée sur les rôles, parce que les rôles sont un type de revendication.</span><span class="sxs-lookup"><span data-stu-id="f8324-319">Claims-based authorization encloses role-based authorization, because roles are a type of claim.</span></span>

<span data-ttu-id="f8324-320">L'autorisation basée sur les revendications s'accomplit en comparant un jeu de revendications aux spécifications d'accès de l'opération et, selon le résultat de cette comparaison, l'accès à l'opération est accordé ou refusé.</span><span class="sxs-lookup"><span data-stu-id="f8324-320">Authorization based on claims is accomplished by comparing a set of claims to the access requirements of the operation and, depending on the outcome of that comparison, granting or denying access to the operation.</span></span> <span data-ttu-id="f8324-321">Dans WCF, vous pouvez spécifier une classe à utiliser pour exécuter l’autorisation basée sur les revendications, une fois encore, en affectant une valeur à la `ServiceAuthorizationManager` propriété de <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> .</span><span class="sxs-lookup"><span data-stu-id="f8324-321">In WCF, you can specify a class to use to run claims-based authorization, once again by assigning a value to the `ServiceAuthorizationManager` property of <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>

```xml
<behaviors>
     <behavior name='ServiceBehavior'>
     <serviceAuthorization
     serviceAuthorizationManagerType=
                   'Service.AccessChecker, Service' />
     </behavior>
</behaviors>
```

<span data-ttu-id="f8324-322">Les classes utilisées pour exécuter l'autorisation basée sur les revendications doivent dériver de <xref:System.ServiceModel.ServiceAuthorizationManager>, qui contient une méthode à substituer, `AccessCheck()`.</span><span class="sxs-lookup"><span data-stu-id="f8324-322">Classes used to run claims-based authorization must derive from <xref:System.ServiceModel.ServiceAuthorizationManager>, which has just one method to override, `AccessCheck()`.</span></span> <span data-ttu-id="f8324-323">WCF appelle cette méthode chaque fois qu’une opération du service est appelée et fournit un <xref:System.ServiceModel.OperationContext> objet, qui a les revendications pour l’utilisateur dans sa `ServiceSecurityContext.AuthorizationContext` propriété.</span><span class="sxs-lookup"><span data-stu-id="f8324-323">WCF calls that method whenever an operation of the service is invoked and provides a <xref:System.ServiceModel.OperationContext> object, which has the claims for the user in its `ServiceSecurityContext.AuthorizationContext` property.</span></span> <span data-ttu-id="f8324-324">WCF effectue le travail d’assemblage des revendications relatives à l’utilisateur à partir du jeton de sécurité fourni par l’utilisateur pour l’authentification, ce qui laisse la tâche d’évaluer si ces revendications suffisent pour l’opération en question.</span><span class="sxs-lookup"><span data-stu-id="f8324-324">WCF does the work of assembling claims about the user from whatever security token the user provided for authentication, which leaves the of task of evaluating whether those claims suffice for the operation in question.</span></span>

<span data-ttu-id="f8324-325">WCF assemble automatiquement les revendications à partir de n’importe quel type de jeton de sécurité est une innovation très importante, car elle rend le code d’autorisation basé sur les revendications entièrement indépendantes du mécanisme d’authentification.</span><span class="sxs-lookup"><span data-stu-id="f8324-325">That WCF automatically assembles claims from any kind of security token is a highly significant innovation, because it makes the code for authorization based on the claims entirely independent of the authentication mechanism.</span></span> <span data-ttu-id="f8324-326">Par contraste, l'autorisation à l'aide des listes de contrôle d'accès ou des rôles dans ASP.NET est étroitement liée à l'authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="f8324-326">By contrast, authorization using ACLs or roles in ASP.NET is closely tied to Windows authentication.</span></span>

### <a name="security-confidentiality"></a><span data-ttu-id="f8324-327">Sécurité : confidentialité</span><span class="sxs-lookup"><span data-stu-id="f8324-327">Security: Confidentiality</span></span>

<span data-ttu-id="f8324-328">La confidentialité des messages échangés avec les services Web ASP.NET peut être garantie au niveau du transport en configurant l'application dans les services IIS pour qu'elle utilise le protocole HTTPS (Secure Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="f8324-328">The confidentiality of messages exchanged with ASP.NET Web services can be ensured at the transport level by configuring the application within IIS to use the Secure Hypertext Transfer Protocol (HTTPS).</span></span> <span data-ttu-id="f8324-329">Il en est de même pour les applications WCF hébergées dans IIS.</span><span class="sxs-lookup"><span data-stu-id="f8324-329">The same can be done for WCF applications hosted within IIS.</span></span> <span data-ttu-id="f8324-330">Toutefois, les applications WCF hébergées en dehors d’IIS peuvent également être configurées pour utiliser un protocole de transport sécurisé.</span><span class="sxs-lookup"><span data-stu-id="f8324-330">However, WCF applications hosted outside of IIS can also be configured to use a secure transport protocol.</span></span> <span data-ttu-id="f8324-331">Plus important, les applications WCF peuvent également être configurées pour sécuriser les messages avant leur transport, à l’aide du protocole WS-Security.</span><span class="sxs-lookup"><span data-stu-id="f8324-331">More important, WCF applications can also be configured to secure the messages before they are transported, using the WS-Security protocol.</span></span> <span data-ttu-id="f8324-332">La sécurisation uniquement du corps d'un message à l'aide de WS-Security lui permet d'être transmis confidentiellement par des intermédiaires avant d'atteindre sa destination finale.</span><span class="sxs-lookup"><span data-stu-id="f8324-332">Securing just the body of a message using WS-Security allows it to be transmitted confidentially across intermediaries before reaching its final destination.</span></span>

## <a name="globalization"></a><span data-ttu-id="f8324-333">Globalisation</span><span class="sxs-lookup"><span data-stu-id="f8324-333">Globalization</span></span>

<span data-ttu-id="f8324-334">Le langage de configuration ASP.NET vous permet de spécifier la culture pour les services individuels.</span><span class="sxs-lookup"><span data-stu-id="f8324-334">The ASP.NET configuration language allows you to specify the culture for individual services.</span></span> <span data-ttu-id="f8324-335">WCF ne prend pas en charge ce paramètre de configuration, sauf en mode de compatibilité ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f8324-335">The WCF does not support that configuration setting except in ASP.NET compatibility mode.</span></span> <span data-ttu-id="f8324-336">Pour localiser un service WCF qui n’utilise pas le mode de compatibilité ASP.NET, compilez le type de service dans des assemblys spécifiques à la culture et avez des points de terminaison spécifiques à la culture distincts pour chaque assembly spécifique à la culture.</span><span class="sxs-lookup"><span data-stu-id="f8324-336">To localize a WCF service that does not use ASP.NET compatibility mode, compile the service type into culture-specific assemblies, and have separate culture-specific endpoints for each culture-specific assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8324-337">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8324-337">See also</span></span>

- [<span data-ttu-id="f8324-338">Comparaison des services Web ASP.NET et de WCF en fonction de l'objectif et des normes utilisées</span><span class="sxs-lookup"><span data-stu-id="f8324-338">Comparing ASP.NET Web Services to WCF Based on Purpose and Standards Used</span></span>](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
