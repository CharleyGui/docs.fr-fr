---
title: Sérialisation avec tolérance de version
description: En savoir plus sur la sérialisation avec tolérance de version, un ensemble de fonctionnalités qui facilitent la modification des types sérialisables.
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
ms.openlocfilehash: e7c4d6ca4c72390c3e0803502aa9c1a675e02345
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282412"
---
# <a name="version-tolerant-serialization"></a>Sérialisation avec tolérance de version

Dans les premières versions de .NET Framework, la création de types sérialisables pouvant être réutilisables d’une version d’une application à la suivante était problématique. Si un type était modifié via l'ajout de champs supplémentaires, les problèmes suivants étaient susceptibles de se produire :

- Les versions antérieures d'une application pouvaient lever des exceptions lorsque l'utilisateur tentait de désérialiser les nouvelles versions du type précédent.
- Les versions plus récentes d'une application pouvaient lever des exceptions lors de la désérialisation de versions antérieures d'un type ayant des données manquantes.

La sérialisation avec tolérance de version (STM) est un ensemble de fonctionnalités qui facilite, au fil du temps, la modification de types sérialisables. Plus précisément, les fonctions VTS sont activées pour les classes auxquelles l'attribut <xref:System.SerializableAttribute> a été appliqué, y compris des types génériques. VTS permet d'ajouter de nouveaux champs à ces classes en assurant la compatibilité avec d'autres versions du type. Pour obtenir un exemple d’application opérationnelle, consultez [Sérialisation avec tolérance de version, exemple de technologie](basic-serialization-technology-sample.md).

Les fonctions VTS sont activées lors de l'utilisation de <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. En outre, toutes les fonctionnalités, hormis la tolérance de données étrangères, sont également activées lors de l'utilisation de <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Pour plus d’informations sur l’utilisation de ces classes pour la sérialisation, consultez [Sérialisation binaire](binary-serialization.md).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="feature-list"></a>Liste des fonctionnalités

Cette liste comprend les fonctionnalités suivantes :

- Tolérance de données étrangères ou inattendues. Cette fonctionnalité permet aux versions plus récentes du type d'envoyer des données aux versions antérieures.
- Tolérance de données facultatives manquantes. Cette fonctionnalité permet aux versions antérieures d'envoyer des données aux versions plus récentes.
- Rappels de sérialisation. Cette fonctionnalité active le paramètre de valeur par défaut intelligent en cas de données manquantes.

Une fonctionnalité permet en outre de générer une déclaration lors de l'ajout d'un nouveau champ facultatif. Il s'agit de la propriété <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> de l'attribut <xref:System.Runtime.Serialization.OptionalFieldAttribute>.

Ces fonctionnalités sont abordées plus en détail dans les sections suivantes.

### <a name="tolerance-of-extraneous-or-unexpected-data"></a>Tolérance de données étrangères ou inattendues

Auparavant, lors de la désérialisation, toute donnée étrangère ou inattendue entraînait la levée d'exceptions. Avec VTS, dans la même situation, toutes les données étrangères ou inattendues sont ignorées au lieu de provoquer la levée d'exceptions. Cela permet aux applications qui utilisent des versions plus récentes d'un type (autrement dit, une version qui inclut plus de champs) d'envoyer des informations aux applications qui nécessitent des versions antérieures du même type.

Dans l'exemple suivant, les données supplémentaires contenues dans le champ `CountryField` de la version 2.0 de la classe `Address` sont ignorées lorsqu'une application plus ancienne désérialise la version plus récente.

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

### <a name="tolerance-of-missing-data"></a>Tolérance de données manquantes

Les champs peuvent être marqués comme facultatifs en leur appliquant l'attribut <xref:System.Runtime.Serialization.OptionalFieldAttribute>. Lors de la désérialisation, si des données facultatives sont manquantes, le moteur de sérialisation ignore leur absence et ne lève aucune exception. Les applications qui nécessitent des versions antérieures d'un type peuvent ainsi envoyer des données aux applications qui nécessitent des versions plus récentes du même type.

L'exemple suivant illustre la version 2.0 de la classe `Address`, avec le champ `CountryField` marqué comme facultatif. Si une application plus ancienne envoie la version 1 à une application plus récente qui nécessite la version 2.0, l'absence des données est ignorée.

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
  
### <a name="serialization-callbacks"></a>Rappels de sérialisation

Les rappels de sérialisation correspondent à un mécanisme qui fournit des raccordements lors du processus de sérialisation/désérialisation au niveau de quatre points.

|Attribut|Lorsque la méthode associée est appelée|Utilisation courante|
|---------------|------------------------------------------|-----------------|
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|Avant la désérialisation.\*|Initialisez des valeurs par défaut pour les champs facultatifs.|
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|Après la désérialisation.|Corrigez des valeurs de champ facultatives selon le contenu d'autres champs.|
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|Avant la sérialisation.|Préparez la sérialisation. Par exemple, créez des structures de données facultatives.|
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|Après la sérialisation.|Enregistrez des événements de sérialisation.|

 \* Ce rappel est appelé avant le constructeur de désérialisation, le cas échéant.

#### <a name="using-callbacks"></a>Utilisation de rappels

Pour utiliser des rappels, appliquez l'attribut approprié à une méthode qui accepte un paramètre <xref:System.Runtime.Serialization.StreamingContext>. Une seule méthode par classe peut être marquée avec chacun de ces attributs. Par exemple :

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

Ces méthodes sont destinées à être utilisées pour le versioning. Pendant la désérialisation, un champ facultatif ne peut pas être initialisé correctement si les données du champ sont manquantes. Cela peut être corrigé en créant la méthode qui assigne la valeur correcte, puis en appliquant l’attribut **OnDeserializingAttribute** ou **OnDeserializedAttribute** à la méthode.

L'exemple suivant illustre la méthode dans le cadre d'un type. Si une version antérieure d'une application envoie une instance de la classe `Address` à une version ultérieure de l'application, les données du champ `CountryField` sont omises. Mais après la désérialisation, le champ est défini sur une valeur par défaut « Japan ».

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

## <a name="the-versionadded-property"></a>Propriété VersionAdded

**OptionalFieldAttribute** a la propriété **VersionAdded**. La propriété indique quelle version d'un type a été ajoutée à un champ donné. Elle doit être incrémentée d'une seule valeur (à partir de 2) à chaque fois que le type est modifié, comme illustré dans l'exemple suivant :

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

## <a name="serializationbinder"></a>SerializationBinder

Certains utilisateurs doivent contrôler la classe à sérialiser et désérialiser, car une version différente de la classe est requise sur le serveur et le client. <xref:System.Runtime.Serialization.SerializationBinder> est une classe abstraite utilisée pour contrôler les types réels utilisés lors de la sérialisation et de la désérialisation. Pour tirer parti de cette classe, dérivez une classe de <xref:System.Runtime.Serialization.SerializationBinder> et substituez une méthode aux deux suivantes : <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> et <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A>. Pour plus d’informations, consultez [contrôle de la sérialisation et de la désérialisation avec SerializationBinder](../../framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).

## <a name="best-practices"></a>meilleures pratiques recommandées.

Pour garantir un comportement de versioning correct, suivez les règles ci-dessous lors de la modification d'un type d'une version à l'autre :

- Ne supprimez jamais un champ sérialisé.
- N'appliquez jamais l'attribut <xref:System.NonSerializedAttribute> à un champ si cet attribut n'a pas été appliqué au champ dans la version antérieure.
- Ne modifiez jamais le nom ou le type d'un champ sérialisé.
- Quand vous ajoutez un nouveau champ sérialisé, appliquez l’attribut **OptionalFieldAttribute**.
- Quand vous supprimez un attribut **NonSerializedAttribute** d’un champ (qui n’était pas sérialisable dans une version antérieure), appliquez l’attribut **OptionalFieldAttribute**.
- Assignez des valeurs par défaut significatives à tous les champs facultatifs à l’aide des rappels de sérialisation, sauf si les valeurs par défaut 0 ou **null** sont acceptables.

Pour garantir la compatibilité d'un type avec les futurs moteurs de sérialisation, suivez ces indications :

- Définissez toujours la propriété **VersionAdded** sur l’attribut **OptionalFieldAttribute** de manière appropriée.
- Évitez le versioning avec des branches.

## <a name="see-also"></a>Voir aussi

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
- [Sérialisation binaire](binary-serialization.md)
