---
title: Sérialisation avec tolérance de version
description: Le .NET Framework 2,0 introduit la sérialisation avec tolérance de version, un ensemble de fonctionnalités qui facilitent la modification des types sérialisables.
ms.date: 08/08/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- version tolerant serialization
- serialization, custom serialization
- serialization, version tolerant
- serialization, controlling
- versions and serialization
- BinaryFormatter class, samples
- serialization, attributes
ms.assetid: bea0ffe3-2708-4a16-ac7d-e586ed6b8e8d
ms.openlocfilehash: 87bdc0f0328e7a75477672432c0944818dbef244
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380097"
---
# <a name="version-tolerant-serialization"></a><span data-ttu-id="e05c9-103">Sérialisation avec tolérance de version</span><span class="sxs-lookup"><span data-stu-id="e05c9-103">Version tolerant serialization</span></span>

<span data-ttu-id="e05c9-104">Dans les versions 1.0 et 1.1 du .NET Framework, la création de types sérialisables pouvant être réutilisés d'une version d'application à l'autre était problématique.</span><span class="sxs-lookup"><span data-stu-id="e05c9-104">In version 1.0 and 1.1 of the .NET Framework, creating serializable types that would be reusable from one version of an application to the next was problematic.</span></span> <span data-ttu-id="e05c9-105">Si un type était modifié via l'ajout de champs supplémentaires, les problèmes suivants étaient susceptibles de se produire :</span><span class="sxs-lookup"><span data-stu-id="e05c9-105">If a type was modified by adding extra fields, the following problems would occur:</span></span>

- <span data-ttu-id="e05c9-106">Les versions antérieures d'une application pouvaient lever des exceptions lorsque l'utilisateur tentait de désérialiser les nouvelles versions du type précédent.</span><span class="sxs-lookup"><span data-stu-id="e05c9-106">Older versions of an application would throw exceptions when asked to deserialize new versions of the old type.</span></span>
- <span data-ttu-id="e05c9-107">Les versions plus récentes d'une application pouvaient lever des exceptions lors de la désérialisation de versions antérieures d'un type ayant des données manquantes.</span><span class="sxs-lookup"><span data-stu-id="e05c9-107">Newer versions of an application would throw exceptions when deserializing older versions of a type with missing data.</span></span>

<span data-ttu-id="e05c9-108">La Sérialisation avec tolérance de version (VTS) comprend un ensemble de fonctionnalités introduites dans .NET Framework 2.0 et qui simplifient, au fil du temps, la modification des types sérialisables.</span><span class="sxs-lookup"><span data-stu-id="e05c9-108">Version Tolerant Serialization (VTS) is a set of features introduced in .NET Framework 2.0 that makes it easier, over time, to modify serializable types.</span></span> <span data-ttu-id="e05c9-109">Plus précisément, les fonctions VTS sont activées pour les classes auxquelles l'attribut <xref:System.SerializableAttribute> a été appliqué, y compris des types génériques.</span><span class="sxs-lookup"><span data-stu-id="e05c9-109">Specifically, the VTS features are enabled for classes to which the <xref:System.SerializableAttribute> attribute has been applied, including generic types.</span></span> <span data-ttu-id="e05c9-110">VTS permet d'ajouter de nouveaux champs à ces classes en assurant la compatibilité avec d'autres versions du type.</span><span class="sxs-lookup"><span data-stu-id="e05c9-110">VTS makes it possible to add new fields to those classes without breaking compatibility with other versions of the type.</span></span> <span data-ttu-id="e05c9-111">Pour obtenir un exemple d’application opérationnelle, consultez [Sérialisation avec tolérance de version, exemple de technologie](version-tolerant-serialization-technology-sample.md).</span><span class="sxs-lookup"><span data-stu-id="e05c9-111">For a working sample application, see [Version Tolerant Serialization Technology Sample](version-tolerant-serialization-technology-sample.md).</span></span>

<span data-ttu-id="e05c9-112">Les fonctions VTS sont activées lors de l'utilisation de <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span><span class="sxs-lookup"><span data-stu-id="e05c9-112">The VTS features are enabled when using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span> <span data-ttu-id="e05c9-113">En outre, toutes les fonctionnalités, hormis la tolérance de données étrangères, sont également activées lors de l'utilisation de <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span><span class="sxs-lookup"><span data-stu-id="e05c9-113">Additionally, all features except extraneous data tolerance are also enabled when using the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span></span> <span data-ttu-id="e05c9-114">Pour plus d’informations sur l’utilisation de ces classes pour la sérialisation, consultez [Sérialisation binaire](binary-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="e05c9-114">For more information about using these classes for serialization, see [Binary Serialization](binary-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="feature-list"></a><span data-ttu-id="e05c9-115">Liste des fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="e05c9-115">Feature list</span></span>

<span data-ttu-id="e05c9-116">Cette liste comprend les fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="e05c9-116">The set of features includes the following:</span></span>

- <span data-ttu-id="e05c9-117">Tolérance de données étrangères ou inattendues.</span><span class="sxs-lookup"><span data-stu-id="e05c9-117">Tolerance of extraneous or unexpected data.</span></span> <span data-ttu-id="e05c9-118">Cette fonctionnalité permet aux versions plus récentes du type d'envoyer des données aux versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="e05c9-118">This enables newer versions of the type to send data to older versions.</span></span>
- <span data-ttu-id="e05c9-119">Tolérance de données facultatives manquantes.</span><span class="sxs-lookup"><span data-stu-id="e05c9-119">Tolerance of missing optional data.</span></span> <span data-ttu-id="e05c9-120">Cette fonctionnalité permet aux versions antérieures d'envoyer des données aux versions plus récentes.</span><span class="sxs-lookup"><span data-stu-id="e05c9-120">This enables older versions to send data to newer versions.</span></span>
- <span data-ttu-id="e05c9-121">Rappels de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="e05c9-121">Serialization callbacks.</span></span> <span data-ttu-id="e05c9-122">Cette fonctionnalité active le paramètre de valeur par défaut intelligent en cas de données manquantes.</span><span class="sxs-lookup"><span data-stu-id="e05c9-122">This enables intelligent default value setting in cases where data is missing.</span></span>

<span data-ttu-id="e05c9-123">Une fonctionnalité permet en outre de générer une déclaration lors de l'ajout d'un nouveau champ facultatif.</span><span class="sxs-lookup"><span data-stu-id="e05c9-123">In addition, there is a feature for declaring when a new optional field has been added.</span></span> <span data-ttu-id="e05c9-124">Il s'agit de la propriété <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> de l'attribut <xref:System.Runtime.Serialization.OptionalFieldAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e05c9-124">This is the <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> property of the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute.</span></span>

<span data-ttu-id="e05c9-125">Ces fonctionnalités sont abordées plus en détail dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="e05c9-125">These features are discussed in greater detail in the following sections.</span></span>

### <a name="tolerance-of-extraneous-or-unexpected-data"></a><span data-ttu-id="e05c9-126">Tolérance de données étrangères ou inattendues</span><span class="sxs-lookup"><span data-stu-id="e05c9-126">Tolerance of extraneous or unexpected data</span></span>

<span data-ttu-id="e05c9-127">Auparavant, lors de la désérialisation, toute donnée étrangère ou inattendue entraînait la levée d'exceptions.</span><span class="sxs-lookup"><span data-stu-id="e05c9-127">In the past, during deserialization, any extraneous or unexpected data caused exceptions to be thrown.</span></span> <span data-ttu-id="e05c9-128">Avec VTS, dans la même situation, toutes les données étrangères ou inattendues sont ignorées au lieu de provoquer la levée d'exceptions.</span><span class="sxs-lookup"><span data-stu-id="e05c9-128">With VTS, in the same situation, any extraneous or unexpected data is ignored instead of causing exceptions to be thrown.</span></span> <span data-ttu-id="e05c9-129">Cela permet aux applications qui utilisent des versions plus récentes d'un type (autrement dit, une version qui inclut plus de champs) d'envoyer des informations aux applications qui nécessitent des versions antérieures du même type.</span><span class="sxs-lookup"><span data-stu-id="e05c9-129">This enables applications that use newer versions of a type (that is, a version that includes more fields) to send information to applications that expect older versions of the same type.</span></span>

<span data-ttu-id="e05c9-130">Dans l'exemple suivant, les données supplémentaires contenues dans le champ `CountryField` de la version 2.0 de la classe `Address` sont ignorées lorsqu'une application plus ancienne désérialise la version plus récente.</span><span class="sxs-lookup"><span data-stu-id="e05c9-130">In the following example, the extra data contained in the `CountryField` of version 2.0 of the `Address` class is ignored when an older application deserializes the newer version.</span></span>

```csharp  
// Version 1 of the Address class.  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
}  
// Version 2.0 of the Address class.  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
    // The older application ignores this data.  
    public string CountryField;  
}  
```  
  
```vb  
' Version 1 of the Address class.  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
End Class  
  
' Version 2.0 of the Address class.  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
    ' The older application ignores this data.  
    Public CountryField As String  
End Class  
```  

### <a name="tolerance-of-missing-data"></a><span data-ttu-id="e05c9-131">Tolérance de données manquantes</span><span class="sxs-lookup"><span data-stu-id="e05c9-131">Tolerance of missing data</span></span>

<span data-ttu-id="e05c9-132">Les champs peuvent être marqués comme facultatifs en leur appliquant l'attribut <xref:System.Runtime.Serialization.OptionalFieldAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e05c9-132">Fields can be marked as optional by applying the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to them.</span></span> <span data-ttu-id="e05c9-133">Lors de la désérialisation, si des données facultatives sont manquantes, le moteur de sérialisation ignore leur absence et ne lève aucune exception.</span><span class="sxs-lookup"><span data-stu-id="e05c9-133">During deserialization, if the optional data is missing, the serialization engine ignores the absence and does not throw an exception.</span></span> <span data-ttu-id="e05c9-134">Les applications qui nécessitent des versions antérieures d'un type peuvent ainsi envoyer des données aux applications qui nécessitent des versions plus récentes du même type.</span><span class="sxs-lookup"><span data-stu-id="e05c9-134">Thus, applications that expect older versions of a type can send data to applications that expect newer versions of the same type.</span></span>

<span data-ttu-id="e05c9-135">L'exemple suivant illustre la version 2.0 de la classe `Address`, avec le champ `CountryField` marqué comme facultatif.</span><span class="sxs-lookup"><span data-stu-id="e05c9-135">The following example shows version 2.0 of the `Address` class with the `CountryField` field marked as optional.</span></span> <span data-ttu-id="e05c9-136">Si une application plus ancienne envoie la version 1 à une application plus récente qui nécessite la version 2.0, l'absence des données est ignorée.</span><span class="sxs-lookup"><span data-stu-id="e05c9-136">If an older application sends version 1 to a newer application that expects version 2.0, the absence of the data is ignored.</span></span>

```csharp
[Serializable]
public class Address
{
    public string Street;
    public string City;

    [OptionalField]
    public string CountryField;
}
```

```vb
<Serializable> _
Public Class Address
    Public Street As String
    Public City As String

    <OptionalField> _
    Public CountryField As String
End Class
```
  
### <a name="serialization-callbacks"></a><span data-ttu-id="e05c9-137">Rappels de sérialisation</span><span class="sxs-lookup"><span data-stu-id="e05c9-137">Serialization callbacks</span></span>

<span data-ttu-id="e05c9-138">Les rappels de sérialisation correspondent à un mécanisme qui fournit des raccordements lors du processus de sérialisation/désérialisation au niveau de quatre points.</span><span class="sxs-lookup"><span data-stu-id="e05c9-138">Serialization callbacks are a mechanism that provides hooks into the serialization/deserialization process at four points.</span></span>

|<span data-ttu-id="e05c9-139">Attribut</span><span class="sxs-lookup"><span data-stu-id="e05c9-139">Attribute</span></span>|<span data-ttu-id="e05c9-140">Lorsque la méthode associée est appelée</span><span class="sxs-lookup"><span data-stu-id="e05c9-140">When the Associated Method is Called</span></span>|<span data-ttu-id="e05c9-141">Utilisation courante</span><span class="sxs-lookup"><span data-stu-id="e05c9-141">Typical Use</span></span>|
|---------------|------------------------------------------|-----------------|
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="e05c9-142">Avant la désérialisation.\*</span><span class="sxs-lookup"><span data-stu-id="e05c9-142">Before deserialization.\*</span></span>|<span data-ttu-id="e05c9-143">Initialisez des valeurs par défaut pour les champs facultatifs.</span><span class="sxs-lookup"><span data-stu-id="e05c9-143">Initialize default values for optional fields.</span></span>|
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="e05c9-144">Après la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="e05c9-144">After deserialization.</span></span>|<span data-ttu-id="e05c9-145">Corrigez des valeurs de champ facultatives selon le contenu d'autres champs.</span><span class="sxs-lookup"><span data-stu-id="e05c9-145">Fix optional field values based on contents of other fields.</span></span>|
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="e05c9-146">Avant la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="e05c9-146">Before serialization.</span></span>|<span data-ttu-id="e05c9-147">Préparez la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="e05c9-147">Prepare for serialization.</span></span> <span data-ttu-id="e05c9-148">Par exemple, créez des structures de données facultatives.</span><span class="sxs-lookup"><span data-stu-id="e05c9-148">For example, create optional data structures.</span></span>|
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="e05c9-149">Après la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="e05c9-149">After serialization.</span></span>|<span data-ttu-id="e05c9-150">Enregistrez des événements de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="e05c9-150">Log serialization events.</span></span>|

 <span data-ttu-id="e05c9-151">\* Ce rappel est appelé avant le constructeur de désérialisation, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="e05c9-151">\* This callback is invoked before the deserialization constructor, if one is present.</span></span>

#### <a name="using-callbacks"></a><span data-ttu-id="e05c9-152">Utilisation de rappels</span><span class="sxs-lookup"><span data-stu-id="e05c9-152">Using callbacks</span></span>

<span data-ttu-id="e05c9-153">Pour utiliser des rappels, appliquez l'attribut approprié à une méthode qui accepte un paramètre <xref:System.Runtime.Serialization.StreamingContext>.</span><span class="sxs-lookup"><span data-stu-id="e05c9-153">To use callbacks, apply the appropriate attribute to a method that accepts a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span> <span data-ttu-id="e05c9-154">Une seule méthode par classe peut être marquée avec chacun de ces attributs.</span><span class="sxs-lookup"><span data-stu-id="e05c9-154">Only one method per class can be marked with each of these attributes.</span></span> <span data-ttu-id="e05c9-155">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e05c9-155">For example:</span></span>

```csharp
[OnDeserializing]
private void SetCountryRegionDefault(StreamingContext sc)
{
    CountryField = "Japan";
}
```

```vb
<OnDeserializing>
Private Sub SetCountryRegionDefault(sc As StreamingContext)
    CountryField = "Japan"
End Sub
```

<span data-ttu-id="e05c9-156">Ces méthodes sont destinées à être utilisées pour le versioning.</span><span class="sxs-lookup"><span data-stu-id="e05c9-156">The intended use of these methods is for versioning.</span></span> <span data-ttu-id="e05c9-157">Pendant la désérialisation, un champ facultatif ne peut pas être initialisé correctement si les données du champ sont manquantes.</span><span class="sxs-lookup"><span data-stu-id="e05c9-157">During deserialization, an optional field may not be correctly initialized if the data for the field is missing.</span></span> <span data-ttu-id="e05c9-158">Cela peut être corrigé en créant la méthode qui assigne la valeur correcte, puis en appliquant l’attribut **OnDeserializingAttribute** ou **OnDeserializedAttribute** à la méthode.</span><span class="sxs-lookup"><span data-stu-id="e05c9-158">This can be corrected by creating the method that assigns the correct value, then applying either the **OnDeserializingAttribute** or **OnDeserializedAttribute** attribute to the method.</span></span>

<span data-ttu-id="e05c9-159">L'exemple suivant illustre la méthode dans le cadre d'un type.</span><span class="sxs-lookup"><span data-stu-id="e05c9-159">The following example shows the method in the context of a type.</span></span> <span data-ttu-id="e05c9-160">Si une version antérieure d'une application envoie une instance de la classe `Address` à une version ultérieure de l'application, les données du champ `CountryField` sont omises.</span><span class="sxs-lookup"><span data-stu-id="e05c9-160">If an earlier version of an application sends an instance of the `Address` class to a later version of the application, the `CountryField` field data will be missing.</span></span> <span data-ttu-id="e05c9-161">Mais après la désérialisation, le champ est défini sur une valeur par défaut « Japan ».</span><span class="sxs-lookup"><span data-stu-id="e05c9-161">But after deserialization, the field will be set to a default value "Japan".</span></span>

```csharp
[Serializable]
public class Address
{
    public string Street;
    public string City;
    [OptionalField]
    public string CountryField;

    [OnDeserializing]
    private void SetCountryRegionDefault(StreamingContext sc)
    {
        CountryField = "Japan";
    }
}
```

```vb
<Serializable> _
Public Class Address
    Public Street As String
    Public City As String
    <OptionalField> _
    Public CountryField As String

    <OnDeserializing> _
    Private Sub SetCountryRegionDefault(sc As StreamingContext)
        CountryField = "Japan"
    End Sub
End Class
```

## <a name="the-versionadded-property"></a><span data-ttu-id="e05c9-162">Propriété VersionAdded</span><span class="sxs-lookup"><span data-stu-id="e05c9-162">The VersionAdded property</span></span>

<span data-ttu-id="e05c9-163">**OptionalFieldAttribute** a la propriété **VersionAdded**.</span><span class="sxs-lookup"><span data-stu-id="e05c9-163">The **OptionalFieldAttribute** has the **VersionAdded** property.</span></span> <span data-ttu-id="e05c9-164">Dans la version 2.0 de .NET Framework, cette propriété n’est pas utilisée.</span><span class="sxs-lookup"><span data-stu-id="e05c9-164">In version 2.0 of the .NET Framework, this isn't used.</span></span> <span data-ttu-id="e05c9-165">Toutefois, il est important de définir correctement cette propriété pour garantir la compatibilité du type avec les futurs moteurs de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="e05c9-165">However, it's important to set this property correctly to ensure that the type will be compatible with future serialization engines.</span></span>

<span data-ttu-id="e05c9-166">La propriété indique quelle version d'un type a été ajoutée à un champ donné.</span><span class="sxs-lookup"><span data-stu-id="e05c9-166">The property indicates which version of a type a given field has been added.</span></span> <span data-ttu-id="e05c9-167">Elle doit être incrémentée d'une seule valeur (à partir de 2) à chaque fois que le type est modifié, comme illustré dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="e05c9-167">It should be incremented by exactly one (starting at 2) every time the type is modified, as shown in the following example:</span></span>

```csharp
// Version 1.0
[Serializable]
public class Person
{
    public string FullName;
}

// Version 2.0
[Serializable]
public class Person
{
    public string FullName;

    [OptionalField(VersionAdded = 2)]
    public string NickName;
    [OptionalField(VersionAdded = 2)]
    public DateTime BirthDate;
}

// Version 3.0
[Serializable]
public class Person
{
    public string FullName;

    [OptionalField(VersionAdded=2)]
    public string NickName;
    [OptionalField(VersionAdded=2)]
    public DateTime BirthDate;

    [OptionalField(VersionAdded=3)]
    public int Weight;
}
```

```vb
' Version 1.0
<Serializable> _
Public Class Person
    Public FullName
End Class

' Version 2.0
<Serializable> _
Public Class Person
    Public FullName As String

    <OptionalField(VersionAdded := 2)> _
    Public NickName As String
    <OptionalField(VersionAdded := 2)> _
    Public BirthDate As DateTime
End Class

' Version 3.0
<Serializable> _
Public Class Person
    Public FullName As String

    <OptionalField(VersionAdded := 2)> _
    Public NickName As String
    <OptionalField(VersionAdded := 2)> _
    Public BirthDate As DateTime

    <OptionalField(VersionAdded := 3)> _
    Public Weight As Integer
End Class
```

## <a name="serializationbinder"></a><span data-ttu-id="e05c9-168">SerializationBinder</span><span class="sxs-lookup"><span data-stu-id="e05c9-168">SerializationBinder</span></span>

<span data-ttu-id="e05c9-169">Certains utilisateurs doivent contrôler la classe à sérialiser et désérialiser, car une version différente de la classe est requise sur le serveur et le client.</span><span class="sxs-lookup"><span data-stu-id="e05c9-169">Some users may need to control which class to serialize and deserialize because a different version of the class is required on the server and client.</span></span> <span data-ttu-id="e05c9-170"><xref:System.Runtime.Serialization.SerializationBinder> est une classe abstraite utilisée pour contrôler les types réels utilisés lors de la sérialisation et de la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="e05c9-170"><xref:System.Runtime.Serialization.SerializationBinder> is an abstract class used to control the actual types used during serialization and deserialization.</span></span> <span data-ttu-id="e05c9-171">Pour tirer parti de cette classe, dérivez une classe de <xref:System.Runtime.Serialization.SerializationBinder> et substituez une méthode aux deux suivantes : <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> et <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A>.</span><span class="sxs-lookup"><span data-stu-id="e05c9-171">To use this class, derive a class from <xref:System.Runtime.Serialization.SerializationBinder> and override the <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> and <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> methods.</span></span> <span data-ttu-id="e05c9-172">Pour plus d’informations, consultez [contrôle de la sérialisation et de la désérialisation avec SerializationBinder](../../framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).</span><span class="sxs-lookup"><span data-stu-id="e05c9-172">For more information, see [Controlling Serialization and Deserialization with SerializationBinder](../../framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).</span></span>

## <a name="best-practices"></a><span data-ttu-id="e05c9-173">Meilleures pratiques</span><span class="sxs-lookup"><span data-stu-id="e05c9-173">Best practices</span></span>

<span data-ttu-id="e05c9-174">Pour garantir un comportement de versioning correct, suivez les règles ci-dessous lors de la modification d'un type d'une version à l'autre :</span><span class="sxs-lookup"><span data-stu-id="e05c9-174">To ensure proper versioning behavior, follow these rules when modifying a type from version to version:</span></span>

- <span data-ttu-id="e05c9-175">Ne supprimez jamais un champ sérialisé.</span><span class="sxs-lookup"><span data-stu-id="e05c9-175">Never remove a serialized field.</span></span>
- <span data-ttu-id="e05c9-176">N'appliquez jamais l'attribut <xref:System.NonSerializedAttribute> à un champ si cet attribut n'a pas été appliqué au champ dans la version antérieure.</span><span class="sxs-lookup"><span data-stu-id="e05c9-176">Never apply the <xref:System.NonSerializedAttribute> attribute to a field if the attribute was not applied to the field in the previous version.</span></span>
- <span data-ttu-id="e05c9-177">Ne modifiez jamais le nom ou le type d'un champ sérialisé.</span><span class="sxs-lookup"><span data-stu-id="e05c9-177">Never change the name or the type of a serialized field.</span></span>
- <span data-ttu-id="e05c9-178">Quand vous ajoutez un nouveau champ sérialisé, appliquez l’attribut **OptionalFieldAttribute**.</span><span class="sxs-lookup"><span data-stu-id="e05c9-178">When adding a new serialized field, apply the **OptionalFieldAttribute** attribute.</span></span>
- <span data-ttu-id="e05c9-179">Quand vous supprimez un attribut **NonSerializedAttribute** d’un champ (qui n’était pas sérialisable dans une version antérieure), appliquez l’attribut **OptionalFieldAttribute**.</span><span class="sxs-lookup"><span data-stu-id="e05c9-179">When removing a **NonSerializedAttribute** attribute from a field (that was not serializable in a previous version), apply the **OptionalFieldAttribute** attribute.</span></span>
- <span data-ttu-id="e05c9-180">Assignez des valeurs par défaut significatives à tous les champs facultatifs à l’aide des rappels de sérialisation, sauf si les valeurs par défaut 0 ou **null** sont acceptables.</span><span class="sxs-lookup"><span data-stu-id="e05c9-180">For all optional fields, set meaningful defaults using the serialization callbacks unless 0 or **null** as defaults are acceptable.</span></span>

<span data-ttu-id="e05c9-181">Pour garantir la compatibilité d'un type avec les futurs moteurs de sérialisation, suivez ces indications :</span><span class="sxs-lookup"><span data-stu-id="e05c9-181">To ensure that a type will be compatible with future serialization engines, follow these guidelines:</span></span>

- <span data-ttu-id="e05c9-182">Définissez toujours la propriété **VersionAdded** sur l’attribut **OptionalFieldAttribute** de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="e05c9-182">Always set the **VersionAdded** property on the **OptionalFieldAttribute** attribute correctly.</span></span>
- <span data-ttu-id="e05c9-183">Évitez le versioning avec des branches.</span><span class="sxs-lookup"><span data-stu-id="e05c9-183">Avoid branched versioning.</span></span>

## <a name="see-also"></a><span data-ttu-id="e05c9-184">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e05c9-184">See also</span></span>

- <xref:System.SerializableAttribute>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- <xref:System.NonSerializedAttribute>
- [<span data-ttu-id="e05c9-185">Sérialisation binaire</span><span class="sxs-lookup"><span data-stu-id="e05c9-185">Binary Serialization</span></span>](binary-serialization.md)
